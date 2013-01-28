I'm often moving data between development and staging (or production!) on Drupal sites.

I keep gzipped backup files on the remote server. In the Drupal project root directory,
I run:

    ssh remote "cat ~/path/to/backups/data.sql.gz" | gunzip | $(drush sql-connect)

This pipes in the compressed SQL, uncompresses, and pulls it into the database. I could
write this as a little bash script that would find the latest backup file for some project,
but I find it helps to type this sort of thing out manually to remember how it works, as
bash redirection is often handy.

Without gzipped backups, I could also run:

    ssh remote "cd /drupal/site && drush sql-dump | gzip" | gunzip | $(drush sql-connect)
