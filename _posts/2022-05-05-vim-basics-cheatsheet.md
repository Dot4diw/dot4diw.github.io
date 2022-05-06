---
layout: post
title: Vim Basics Operator Cheat Sheet
subtitle: some basics keys in vim
categories: VIM
tags: [VIM, TOOLS]
---

## Introduction

Vim is a highly configurable text editor built to make creating and changing any kind of text very efficient. It is included as "vi" with most UNIX systems and with Apple OS X. 

 Vim is rock stable and is continuously being developed to become even better. Among its features are:

-   persistent, multi-level undo tree
-   extensive plugin system
-   support for hundreds of programming languages and file formats
-   powerful search and replace
-   integrates with many tools

 **Tip:** Run vimtutor in a terminal to learn the first Vim commands.  



## Move the edit cursor

| Keyboard or Shortcuts           | Actions                                                      |
| ------------------------------- | ------------------------------------------------------------ |
| `h`                             | Move the cursor back one character.                          |
| `j`                             | Move the cursor to the next line.                            |
| `k`                             | Move the cursor to the previous line.                        |
| `l`                             | Move the cursor forward one character.                       |
| `[number]h/eg: 5h`              | Move the cursor back 5 character.                            |
| `[number]j/eg: 5j`              | Move the cursor to the next 5 line.                          |
| `H`                             | Move the cursor to top of screen.                            |
| `M`                             | Move the cursor to middle of screen.                         |
| `L`                             | Move the cursor to bottom of screen.                         |
| `gg`                            | Move the cursor to the first line of the current file.       |
| `G`                             | Move the cursor to the last line of the current file.        |
| `5gg` or `5G` or `[number]gg/G` | Move the cursor to the line [number]/5 .                     |
| `f + x`                         | Jump to next character of x.                                 |
| `w`                             | Move forwards to the start of a word.                        |
| `e`                             | Move forwards to the end of a word.                          |
| `b`                             | Move backwards to the start of a word.                       |
| `ge`                            | Move backwards to the end of a word.                         |
| `%`                             | % - move to matching character (default supported pairs: '()', '{}', '[]' ) |
| `0`                             | Jump to the start of the current line.                       |
| `$`                             | Jump to the end of the current line.                         |

## Insert mode - inserting/appending text

| Keyboard or Shortcuts | Actions                                             |
| --------------------- | --------------------------------------------------- |
| `i`                   | Start insert before the current cursor.             |
| `I`                   | Start insert at the beginning of current line.      |
| `a`                   | Start insert or append after the current cursor.    |
| `A`                   | Start insert or append at the end of current line.  |
| `o`                   | Append or create a new line below the current line. |
| `O`                   | Append or create a new line above the current line. |
| `ESC`                 | Exit the insert mode.                               |

## Editing the text.

| Keyboard or Shortcuts | Actions                                                      |
| --------------------- | ------------------------------------------------------------ |
| `x`                   | Delete or cut the current character.                         |
| `dd`                  | Delete or cut the current line.                              |
| `ciw`                 | Change or replace entire word.                               |
| `ci"`                 | Change the content inside the double quotes.                 |
| `c$ or C`             | Change or replace from current cursor to the end of the line. |
| `c0`                  | Change or replace from current cursor to the end of the line. |
| `r`                   | Replace  the current single character.                       |
| `u`                   | Undo                                                         |
| `CTRL + r`            | Redo                                                         |
| `yy`                  | Copy or yank the current line.                               |
| `p`                   | Paste the clipboard after cursor.                            |
| `>>`                  | Indent or move right current line one shiftwidth.            |
| `<<`                  | De-indent or move left current line one shiftwidth.          |
| `.`                   | Repeat the last command.                                     |

## Visual mode

| Keyboard or Shortcuts | Actions                                                    |
| --------------------- | ---------------------------------------------------------- |
| `v`                   | Start visual mode and move the cursor to start the marker. |
| `V`                   | Start the linewise visual mode.                            |
| `CTRL + v`            | Start visual block mode.                                   |
| `d`                   | Delete or out the marked content.                          |
| `y`                   | Copy or yank the marked content.                           |
| `u`                   | Change the marked text to lowercase.                       |
| `U`                   | Change the marked text to uppercase.                       |
| `ESC`                 | Exit the current visual mode.                              |

## Search and replace

| Keyboard or Shortcuts | Actions                                                      |
| --------------------- | ------------------------------------------------------------ |
| `/pattern`            | Search forward for pattern .                                 |
| `?pattern`            | Search backward for pattern .                                |
| `\vpattern`           | 'very magic' pattern: non-alphanumeric characters are<br /> interpreted as special regex symbols (no escaping needed). |
| `n`                   | Jump to the next match.                                      |
| `N`                   | Jump to the previous match.                                  |
| `:%s/old/new/g`       | Replace all old with new throughout file.                    |
| `:%s/old/new/gc`      | Replace all old with new throughout file with confirmations. |

## Exiting the vim and save file

| Keyboard or Shortcuts | Actions                                    |
| --------------------- | ------------------------------------------ |
| `:w`                  | Write (save) the file, but don't exit.     |
| `:w !sudo tee %`      | Write out the current file using sudo.     |
| `:wq or :x or ZZ`     | Write (save) and quit.                     |
| `:q`                  | Quit (fails if there are unsaved changes). |
| `:q! or ZQ`           | Quit and throw away unsaved changes.       |
| `:wqa`                | Write (save) and quit on all tabs.         |

## Macros

1). `qa` - record macro and named `a`;          

2). `q` - stop recording macro;

3). `@a` - run macro `a`; 

4). `100@a` - run the macro `a` 100 times.

## My vim configure file 
```vimscript
"@My Configure file of vim editor
"@FileName : vimrc
"@Dot4diw
" Use ~/.vim/vimrc if exists
"if filereadable(expand("~/.vim/vimrc"))
"    source ~/.vim/vimrc
"endif

" Resove the E421: Color name or number not recognized: ctermbg=#A0A0A0
if &term =~ "xterm"
    "256 color --
    let &t_Co=256
    " restore screen after quitting
    "set t_ti=ESC7ESC[rESC[?47h t_te=ESC[?47lESC8
    " if has("terminfo")
    "     let &t_Sf="\ESC[3%p1%dm"
    "     let &t_Sb="\ESC[4%p1%dm"
    " else
    "     let &t_Sf="\ESC[3%dm"
    "     let &t_Sb="\ESC[4%dm"
    " endif
endif

let mapleader=" "

set nocompatible
set mouse=""
syntax on
filetype on
filetype plugin on
filetype indent on
filetype plugin indent on

" Adjust the terminal color
let &t_ut=''

set encoding=utf-8
set number
set relativenumber
set cursorline

" set spell

set ruler
set showmode
set showcmd
set autoindent
set smartindent
set smarttab
set expandtab
set shiftwidth=4
set tabstop=4
set softtabstop=4
" set list

set scrolloff=5
set laststatus=2
set autochdir

"set wrap
set nowrap
set backspace=indent,eol,start

set wildmenu
set hlsearch
set incsearch
exec "nohlsearch"
set ignorecase
set smartcase
set lazyredraw
set ttyfast

"Setting the theme for vim
"colorscheme murphy
"colorscheme pablo
"colorscheme ron
colorscheme slate
"colorscheme snazzy
"let g:SnazzyTransparent = 1
"Rmap the key.

hi CursorLine term=bold cterm=bold ctermbg=235

map s <nop>
map S :w<CR>
map Q :q<CR>
map R :source $MYVIMRC<CR>

map sr :set splitright<CR>:vsplit<CR>
map sl :set nosplitright<CR>:vsplit<CR>
map su :set nosplitbelow<CR>:split<CR>
map sd :set splitbelow<CR>:split<CR>
map sv <C-w>t<C-w>H
map sh <C-w>t<C-w>K

"map <up> :res +5<CR>
"map <down> :res -5<CR>
"map <left> :vertival resize-5<CR>
"map <right> :vertival resize+5<CR>


map <LEADER>l <C-w>l
map <LEADER>k <C-w>k
map <LEADER>h <C-w>h
map <LEADER>j <C-w>j
map <LEADER>n :bn<CR>
map <LEADER>p :bp<CR>

map tu :tabe<CR>
map tn :-tabnext<CR>
map tp :+tabnext<CR>

noremap J 5j
noremap K 5k
noremap = nzz
noremap - Nzz
noremap <LEADER><CR> :nohlsearch<CR>

noremap <Up> <Nop>
noremap <Down> <Nop>
noremap <Left> <Nop>
noremap <Right> <Nop>
" Recoder the position of the last out.
au BufReadPost * if line("'\"") > 0 | if line("'\"") <= line("$") | exe("norm '\"") | else |exe "norm $"| endif | endif

"<<<<<NerdTree Config
map tt :NERDTreeToggle<CR>

">>>>>NerdTree Config

"<<<<<YouCompleteME Config
    let g:ycm_global_ycm_extra_conf = "~/.vim/bundle/YouCompleteMe/cpp/ycm/.ycm_extra_conf.py"
    let g:ycm_key_invoke_completion = ''
    let g:ycm_min_num_identifier_candidate_chars = 2
    let g:ycm_goto_buffer_command = 'horizontal-split'
    let g:ycm_seed_identifiers_with_syntax=1
    map <F2> :YcmCompleter GoTo<CR>
    let g:ycm_error_symbol = '>>'
    let g:ycm_warning_symbol = '>*'
">>>>>YouCompleteME Config


"<<<<<ale config
let b:ale_linters = ['pylint']
let b:ale_fixers = ['autopep8', 'yapf']
">>>>>ale config

"<<<<<Goyo
map <LEADER>gy :Goyo<CR>
">>>>>Goyo

"<<<<<indentLine config
    let g:indentLine_char='¦'
    let g:indentLine_enabled = 1
    let g:indentLine_color_term = 239
    " let g:indentLine_bgcolor_term = 202
    " let g:indentLine_bgcolor_gui = '#FF5F00'
    " let g:indentLine_setConceal = 0
    " let g:indentLine_setColors = 0
    " let g:indentLine_defaultGroup = 'SpecialKey'
    
    " none X terminal
    let g:indentLine_color_tty_light = 7 " (default: 4)
    let g:indentLine_color_dark = 1 " (default: 2)
    " Background (Vim, GVim)

">>>>>indentLine config


"<<<<<vim-autoformat config
    " Push the F6 button to auto format.
    nnoremap <F6> :Autoformat<CR> " Push the F6 button to auto format.
    let g:autoformat_autoindent = 0
    let g:autoformat_retab = 0
    let g:autoformat_remove_triling_soace = 0
">>>>>vim-autoformat config
"<<<<<vim-org-mode config
    let g:org_agenda_files=['~/.vim/org/index.org']
">>>>>vim-org-mode congig

"<<<<<vim-rainbow config
    let g:rainbow_active = 1 "0 if you want to enable it later via :RainbowToggle
    let g:rainbow_conf = {
        \   'guifgs': ['royalblue3', 'darkorange3', 'seagreen3', 'firebrick'],
        \   'ctermfgs': ['lightblue', 'lightyellow', 'lightcyan', 'lightmagenta'],
        \   'operators': '_,_',
        \   'parentheses': ['start=/(/ end=/)/ fold', 'start=/\[/ end=/\]/ fold', 'start=/{/ end=/}/ fold'],
        \   'separately': {
        \       '*': {},
        \       'tex': {
        \           'parentheses': ['start=/(/ end=/)/', 'start=/\[/ end=/\]/'],
        \       },
        \       'lisp': {
        \           'guifgs': ['royalblue3', 'darkorange3', 'seagreen3', 'firebrick', 'darkorchid3'],
        \       },
        \       'vim': {
        \           'parentheses': ['start=/(/ end=/)/', 'start=/\[/ end=/\]/', 'start=/{/ end=/}/ fold', 'start=/(/ end=/)/ containedin=vimFuncBody', 'start=/\[/ end=/\]/ containedin=vimFuncBody', 'start=/{/ end=/}/ fold containedin=vimFuncBody'],
        \       },
        \       'html': {
        \           'parentheses': ['start=/\v\<((area|base|br|col|embed|hr|img|input|keygen|link|menuitem|meta|param|source|track|wbr)[ >])@!\z([-_:a-zA-Z0-9]+)(\s+[-_:a-zA-Z0-9]+(\=("[^"]*"|'."'".'[^'."'".']*'."'".'|[^ '."'".'"><=`]*))?)*\>/ end=#</\z1># fold'],
        \       },
        \       'css': 0,
        \   }
        \}
">>>>>vim-rainbow config

"Plug Install List
call plug#begin('~/.vim/plugged')

Plug 'vim-airline/vim-airline'
Plug 'connorholyday/vim-snazzy'
Plug 'preservim/nerdtree'
" Plug 'ycm-core/YouCompleteMe'
Plug 'dense-analysis/ale'
Plug 'junegunn/goyo.vim'
Plug 'Yggdroot/indentLine'
Plug 'Chiel92/vim-autoformat'
Plug 'luochen1990/rainbow'
Plug 'jceb/vim-orgmode'
Plug 'tpope/vim-speeddating'
Plug 'mattn/calendar-vim'
Plug 'majutsushi/tagbar'

call plug#end()
```
