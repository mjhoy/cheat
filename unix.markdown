Unix
----

Common, helpful unix commands.

#### bash substitution

Silly example: list files in the current directory, replacing "." with " - DOT - ":

    for i in *; do echo ${i//./ - DOT - }; done     --> Gemfile - DOT - lock, etc.
    
Rename all files in the current directory to lowercase, substituting underscores for spaces:
    
    for i in *; do y=$(echo $i | tr '[A-Z]' '[a-z]'); mv "$i" ${y//\ /_}; done

#### find

    find .                --> list all files under the current directory
    find . -name '*swp'   -->  "    "   ending in `swp`
    find . -type d -name .git -prune -o -print    --> List all files under current
                                                      directory excluding any under .git/...

Quick and dirty LOC measurement:

    find . -iname '*.hs' | xargs cat | wc -l    --> Number of lines of Haskell code (including whitespace, comments)

([Why not xargs wc -l][hn]?)

[hn]:http://news.ycombinator.com/item?id=4317007

#### find + parallel

Effectively you can parallelize find -exec, using `parallel`.

Non-parallel:

    find . -name '*.jpg' -exec convert -resize 1440 -quality 60 "{}" "converted/{}" \;

Parallel, with progress bar:

    find . -name '*.jpg' -print0 | parallel -0 -r --bar convert -resize 1440 -quality 60 "{}" "converted/{}" \;

#### xargs

The above `find` command is suboptimal. It pipes a list of filenames to `xargs`, and if those filenames
have any spaces in their names (or  other non-standard filename characters) bad things can happen.
To avoid this, you can instruct `find` to separate filenames with the NUL (`\0`) character and 
`xargs` to interpert that correctly:

    find . -iname '*.hs' -print0 | xargs -0 cat | wc -l

#### find + grep

Just had to throw this together to find Rails 3.0.x apps in a directory
(which is accomplished by grepping on the Gemfile). I'm not familiar with
the grep regular expression escaping, so this is best I came up with, to
be improved:

    find ~/rails -name 'Gemfile' -exec grep -E 'rails., .3.0' {} \; -print
          -----> List gemfiles under ~/rails containing the string "rails', '3.0"

#### ssh

Setting up a proxy server:

    ssh -ND 8887 -p 22 <remote>     --> Start a SOCKS server on local port 8887 that tunnels
                                        to <remote> through port 22. To proxy all web traffic,
                                        set up the proxy settings in System Prefs/Network/Proxies.

#### curl

Downloading a file from a website (basecamp) which requires an authorization
cookie (taken from a browser session):

    curl -H "Cookie: <...>" https://someone.basecamphq.com/file.mp3 > file.mp3

To get the header cookie info, use Chrome's Network tab in the inspector, and just
copy "Cookie: ..." from the headers.
