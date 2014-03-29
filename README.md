Zing
====

Small tool to automate running a custom command repeatedly (in vim) during
development.

The command can be customized on a per-repository (or per-directory) basis.

Installation
============

Symlink or move `zing` to some place in your PATH, such as ~/bin.  I also
symlink it as ~/bin/,z for reasons which will be made obvious shortly.

Add the following rules to your .vimrc:

```vim
" Note: <C-O> will keep vim insert mode

" if you prefer F4
nnoremap <F4> :call AutoGo()<CR>
inoremap <F4> <C-C>:call AutoGo()<CR>

" if you prefer a leader
let mapleader = ","
noremap <silent> <Leader>z :call AutoGo()<CR>
inoremap <silent> <Leader>z <C-C>:call AutoGo()<CR>
func! AutoGo()
  exec "w"
  exec "!zing"
endfunc
```

Configuration
=============

Create a .zing file anywhere you'd like.  It's contents should be a script
that will be ran whenever ,z is pressed.  As necessary, change the contents of
.zing.
