Vim
---

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
