Zing
====

Small tool to automate running a custom command repeatedly (in vim) during
development.

The command can be customized on a per-repository (or per-directory) basis.

Installation
------------

Symlink or move `zing` to some place in your PATH, such as ~/bin.  I also
symlink it as ~/bin/,z for reasons which will be made obvious shortly.

Add the following rules to your .vimrc:

```vim
" Note: Add <C-O> if you'd prefer for vim to stay in insert mode after
"       running the zing script

" if you prefer F4
nnoremap <F4> :call Zing()<CR>
inoremap <F4> <C-C>:call Zing()<CR>

" if you prefer a leader
let mapleader = ","
noremap <silent> <Leader>z :call Zing()<CR>
inoremap <silent> <Leader>z <C-C>:call Zing()<CR>
func! Zing()
  exec "w"
  exec "!zing"
endfunc
```

Ignoring with git globally
-----------------

I ignore the `.zing` files in all repositories by adding the following to `~/.gitconfig`:

```
[core]
  excludesfile = /home/jewel/.gitignore_global
```

And the following content in `~/.gitignore_global`:

```
.zing
```

Usage
-----

Create a `.zing` file anywhere you'd like.  It's contents should be a script
that will be ran whenever `,z` is pressed.  As your project progresses or you
need want to focus on a specific area, change the contents of `.zing`.
