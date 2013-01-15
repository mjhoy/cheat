Vim
---

#### HTML

Using tpope's [ragtag][ragtag]:

If used after the text "bob":

    <C-X><Space> <bob>^</bob>
    <C-X><CR>    <bob>\n^\n</boc>
    <C-X>/       Close last HTML tag opened

Using function `HtmlEntities` from my [vimrc][vimrc]:

With text selected in visual mode:

    <Leader>h Convert &amp; -> & (etc)
    <Leader>H Convert & -> &amp; (etc)

[ragtag]:https://github.com/tpope/vim-ragtag/blob/master/doc/ragtag.txt
[vimrc]:https://github.com/mjhoy/dotfiles/blob/master/vim/vimrc
