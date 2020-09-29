# devenv_basic
## cygwin install
* 설치 파일 경로: https://www.cygwin.com/install.html
* Choose A Download Site가 나오면 User URL에 https://cygwin.com/mirrors.html를 참고하여 입력 (Korea에 있는 mirror site)
* 필수 설치할 package: wget
* 설치 완료 후 실행할 것
```
$ wget raw.github.com/transcode-open/apt-cyg/master/apt-cyg
$ chmod +x apt-cyg
$ mv apt-cyg /usr/local/bin
```
* 이후에는 apt-cyg를 통해서 패키지 설치 (vim, git, curl 등)
## bash setting
* .bashrc 파일의 alias setting 주석 해제
```bash
# Some example alias instructions
# If these are enabled they will be used instead of any instructions
# they may mask.  For example, alias rm='rm -i' will mask the rm
# application.  To override the alias instruction use a \ before, ie
# \rm will call the real rm not the alias.
#
# Interactive operation...
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
#
# Default to human readable figures
alias df='df -h'
alias du='du -h'
#
# Misc :)
alias less='less -r'                          # raw control characters
alias whence='type -a'                        # where, of a sort
alias grep='grep --color'                     # show differences in colour
alias egrep='egrep --color=auto'              # show differences in colour
alias fgrep='fgrep --color=auto'              # show differences in colour
#
# Some shortcuts for different directory listings
alias ls='ls -hF --color=tty'                 # classify files in colour
alias dir='ls --color=auto --format=vertical'
alias vdir='ls --color=auto --format=long'
alias ll='ls -l'                              # long list
alias la='ls -A'                              # all but . and ..
alias l='ls -CF'                              #
```
* python 관련 alias
```bash
alias python=python3
alias pip=pip3
```
## vim setting
* Vundle 설치
```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```
* .vimrc 기본 내용 채우기
```vim
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

set encoding=utf-8

set number

set softtabstop=4
set tabstop=4
set shiftwidth=4
set autoindent
set expandtab

set cursorline

let g:airline_theme='wombat'

map <C-n> :NERDTreeToggle<CR>

set scrolloff=0

function MyTabLabel(n)
  let buflist = tabpagebuflist(a:n)
  let winnr = tabpagewinnr(a:n)
  let label = bufname(buflist[winnr - 1])
  return ' (' . a:n . ') ' . fnamemodify(label, ":t")
endfunction
function MyTabLine()
  let s  = tabpagenr() . '/' . tabpagenr('$')
  for i in range(tabpagenr('$'))
    " select the highlighting
    if i + 1 == tabpagenr()
      let s .= '%#TabLineSel#'
    else
      let s .= '%#TabLine#'
    endif

    " set the tab page number (for mouse clicks)
    " let s .= '%' . (i + 1) . 'T'

    " the label is made by MyTabLabel()
    let s .= ' %{MyTabLabel(' . (i + 1) . ')} '
  endfor
  " after the last tab fill with TabLineFill and reset tab page nr
  let s .= '%#TabLineFill#%T'
  return s
endfunction
set tabline=%!MyTabLine()
highlight TabLineSel ctermfg=red
"highlight TabLine ctermfg=gray
"highlight TabLineSel ctermfg=white
```
* Plugin 설치
vim 실행 화면에서 `:PluginInstall`
