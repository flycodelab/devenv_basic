# devenv_basic
## cygwin install
* 설치 파일 경로: https://www.cygwin.com/install.html
* Choose A Download Site가 나오면 User URL에 http://ftp.daum.net/cygwin 입력
* 필수 설치할 package: vim, curl, git, openssh, python3, python3-pip
## bash setting
* .bashrc 파일의 alias setting 주석 해제
* python 관련 alias
```
alias python=python3
alias pip=pip3
```
## vim setting
* Vundle 설치
```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```
* .vimrc 기본 내용 채우기
```
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'
Plugin 'tpope/vim-fugitive'
Plugin 'The-NERD-tree'
Plugin 'ctrlp.vim'
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line

set number

set softtabstop=4
set tabstop=4
set shiftwidth=4
set autoindent
set expandtab

set cursorline

let g:airline_theme='wombat'

map <C-n> :NERDTree<CR>
imap <expr> <tab> emmet#expandAbbrIntelligent("\<tab>")
```
* Plugin 설치
vim 실행 화면에서 `:PluginInstall`
