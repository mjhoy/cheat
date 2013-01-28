### Apply a commit from another repository

This is sometimes helpful when working on a Drupal project, or pulling in basic commits
to a Rails project that will apply cleanly. From the directory of the project to apply a
commit:

    git --git-dir /other/git/dir/.git --format-patch --stdout -1 SHA | git am

If the patch doesn't apply cleanly, use `patch` instead of `git am`:

    git [...format-patch...] | patch -p1
