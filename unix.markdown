Unix
----

Common, helpful unix commands.

#### find

    find .                --> list all files under the current directory
    find . -name '*swp'   -->  "    "   ending in `swp`
    find . -type d -name .git -prune -o -print    --> List all files under current
                                                      directory excluding any under .git/...
