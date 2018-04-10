```shell
"设置vundle
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
set rtp+=/usr/local/opt/fzf
call vundle#begin()
Plugin 'VundleVim/Vundle.vim'

Plugin 'c.vim' "c 支持
Plugin 'altercation/vim-colors-solarized' "solarized theme
Plugin 'joshdick/onedark.vim' "onedark theme
Plugin 'dracula/vim' "dracula theme
Plugin 'L9'
Plugin 'scrooloose/nerdtree'  "文件浏览
Plugin 'Xuyuanp/nerdtree-git-plugin' "nerdtree的git插件
Plugin 'godlygeek/tabular' "自动对齐
Plugin 'Tagbar' "结构预览
Plugin 'ctrlpvim/ctrlp.vim' "全局搜索
Plugin 'junegunn/fzf.vim' "内容搜索
Plugin 'itchyny/lightline.vim' "状态栏
Plugin 'tpope/vim-fugitive' "git栏
Plugin 'gregsexton/gitv' "git分支可视化
Plugin 'Shougo/vimproc.vim' "async
Plugin 'w0rp/ale' "异步语法检查
Plugin 'Yggdroot/indentLine' "垂直参考线
Plugin 'severin-lemaignan/vim-minimap' "预览图
Plugin 'airblade/vim-gitgutter' "vim git提示
Plugin 'kshenoy/vim-signature' "可视化书签
Plugin 'junegunn/goyo.vim' "沉浸模式
Plugin 'junegunn/limelight.vim' "专注模式
Plugin 'jpalardy/vim-slime' "与命令行交互
Plugin 'SirVer/ultisnips' "代码片段
Plugin 'honza/vim-snippets' "代码片段库

Plugin 'haskell.vim' "Haskell language
Plugin 'leafgarland/typescript-vim' "typescript高亮
Plugin 'pangloss/vim-javascript' "javascript高亮
Plugin 'reasonml-editor/vim-reason' "reasonml
Plugin 'mxw/vim-jsx' "react高亮
Plugin 'tpope/vim-rails' "rails.vim
Plugin 'luochen1990/rainbow' "彩虹括号
Plugin 'ternjs/tern_for_vim' "JS结构预览
Plugin 'eagletmt/ghcmod-vim' "ghc-mod
Plugin 'bitc/lushtags' "haskell结构预览
Plugin 'npm.vim' "npm commands
Plugin 'tpope/vim-obsession' "vim session store
Plugin 'Valloric/YouCompleteMe' "vim 自动补全

call vundle#end()            " required
filetype plugin indent on    " required

" 开启文件类型侦测
filetype on
" 根据侦测到的不同类型加载对应的插件
filetype plugin on

syntax on
syntax enable

" 自适应不同语言的智能缩进
filetype indent on
" 将制表符扩展为空格
set expandtab
" 设置编辑时制表符占用空格数
set tabstop=4
" 设置格式化时制表符占用空格数
set shiftwidth=4
" 让 vim 把连续数量的空格视为一个制表符
set softtabstop=4
set number
set ruler
set hlsearch
set showmatch
set autoindent
set cindent
set expandtab
set smarttab
set confirm


" 在 vim 启动的时候默认开启 NERDTree（autocmd 可以缩写为 au）
autocmd VimEnter * NERDTree

" 关闭 vim 的时候如果只剩下 NERDTree, 那么自动关闭 NERDTree
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

" 将 NERDTree 的窗口设置在 ddvim 窗口的右侧（默认为左侧）
" let NERDTreeWinPos="right"

" 当打开 NERDTree 窗口时，自动显示 Bookmarks
let NERDTreeShowBookmarks=1
```
