auto-go
=======

Small tool to automate running a command repeatedly (in vim) during development.

Installation
============

Symlink or move auto-go to some place in your PATH, such as ~/bin.  I also
symlink it as ~/bin/,r for reasons which will be made obvious shortly.

Add the following rules to your .vimrc:

```vim
nnoremap <F4> :call AutoGo()<CR>
" <C-O> will keep in insert mode
inoremap <F4> <C-C>:call AutoGo()<CR>
noremap <silent> ,r :call AutoGo()<CR>
inoremap <silent> ,r <C-C>:call AutoGo()<CR>
func! AutoGo()
  exec "w"
  exec "!auto-go"
endfunc
```

Configuration
============

Create a .auto-go file anywhere you'd like.  It's contents should be a script
that will be ran whenever ,r is pressed.  As necessary, change the contents of
.auto-go.
