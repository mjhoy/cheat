Unix
----

Common, helpful unix commands.

#### find

    find .                --> list all files under the current directory
    find . -name '*swp'   -->  "    "   ending in `swp`
    find . -type d -name .git -prune -o -print    --> List all files under current
                                                      directory excluding any under .git/...

#### find + grep

Just had to throw this together to find Rails 3.0.x apps in a directory
(which is accomplished by grepping on the Gemfile). I'm not familiar with
the grep regular expression escaping, so this is best I came up with, to
be improved:

    find ~/rails -name 'Gemfile' -exec grep -E 'rails., .3.0' {} \; -print
          -----> List gemfiles under ~/rails containing the string "rails', '3.0"
