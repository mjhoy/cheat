Vim
---

#### Navigating

If in a large codebase, I like to search by tag (see `:help tag`). To do this, a tags
file must exist in the current directory (usually the root of the project). For instance,
in the root of the Rails code repository, I run:

     ctags -R .

which creates a `tags` file for Vim to use. In vim:

    :ta has_many        --> Search for a has_many definition, and jump to the first result
    :ts has_many        --> List the results for has_many definitions
    CTRL-]              --> Jump to the definition of the tag under the cursor
    CTRL-T              --> Jump back in the tag stack (see below)
    :tags               --> List the tags in the "tag stack" (which is a stack of all tags jumped to)

#### Shell

Map keys to a shell command. I use these _a lot_. It's worth using them manually
(mapping in your vim sessions, not vimrc) so your fingers will eventually remember
how to type them, and you can tweak ad hoc.

Running ruby tests:

    :map ,t :w\|!rspec %<cr>            --> maps ,t to
                                                write the current file,
                                                then run `rspec <filename>`
                                                (see :help cmdline-special)

Compiling and running c files:

    :map ,r :w\|!make %:r && ./%:r<cr>  --> maps ,r to
                                                write the current file,
                                                run `make <filename without extension>`
                                                run `./<filename without extension>`
                                                (i.e., compile and run the current file)
                                                (see :help %:r for filename modifiers)

Bringing output of a command into a new vim tab:

    :map ,x :tabnew \| r !valgrind ./#:r<cr> --> maps ,x to
                                                create a new tab,
                                                pipe in the output of `valgrind ./<filename without extension>`
                                                (see :help r!)
                                                

#### HTML

##### Tags

_Using tpope's [ragtag][ragtag]_

If used after the text "bob":

    <C-X><Space>  --> Wraps as a tag: <bob>^</bob>
    <C-X><CR>     --> Wraps as a tag: <bob>\n^\n</boc>
    <C-X>/        --> Close last HTML tag opened

##### Entities

_Using function `HtmlEntities` from my [vimrc][vimrc]_

With text selected in visual mode:

    <Leader>h     --> Convert &amp; -> & (etc)
    <Leader>H     --> Convert & -> &amp; (etc)

[ragtag]:https://github.com/tpope/vim-ragtag/blob/master/doc/ragtag.txt
[vimrc]:https://github.com/mjhoy/dotfiles/blob/master/vim/vimrc
