To find the size of all databases (sorted largest to smallest):

    SELECT pg_database.datname, pg_database_size(pg_database.datname),
           pg_size_pretty(pg_database_size(pg_database.datname))
    FROM pg_database
    ORDER BY pg_database_size DESC;
