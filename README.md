# LunarVim


> [Lunarvim](https://www.lunarvim.org/) 简称Lvim，是Neovim的一个预配置，旨在提供开箱即用的Neovim使用体验

 <img src="https://www.lunarvim.org/assets/images/lunarvim_logo-ea848294964e3ff5fd5af2ea28e2f23f.png" >

效果演示：

![a](https://www.lunarvim.org/img/lunarvim_preview.png)



## 安装

- 确保提前安装了 `NeoVim 0.8 +`
- 系统上安装[`git`](https://cli.github.com/)，[`make`](https://cmake.org/)，[`pip`](https://pypi.org/project/pip/)，[`python`](https://www.python.org/) [`npm`](https://npmjs.com/)，[`node`](https://nodejs.org/)和[`cargo`](https://www.rust-lang.org/tools/install)
- 建议使用`Nerd Fonts`字体

```bash
bash <(curl -s https://raw.githubusercontent.com/lunarvim/lunarvim/master/utils/installer/install.sh)
```



## 入门基本使用

> 支持的[语言](https://github.com/nvim-treesitter/nvim-treesitter#supported-languages)

如果终端无法使用命令 将文件夹添加到环境变量，默认安装文件夹为 。`lvim` `~/.local/bin`

```
export PATH=$PATH:/home/$USER/.local/bin
```



安装使用语言语法突出以及树形图支持：

```
:TSInstall <TAB> -- tab切换选项
```

语言服务器安装：

```
:LspInstall <TAB>
```



## 按键绑定概述

[LVim 按键绑定完整模板](https://www.lunarvim.org/docs/keybind-overview)

`<leader>` 默认为空格按键，`config.lua`配置修改

`<leader>sk <leader>`  查看常见并且以及在使用的按键

### 插件

| .key                | 描述                                                         | 模式 |
| ------------------- | ------------------------------------------------------------ | ---- |
| `<leader>`          | [哪个](https://github.com/folke/which-key.nvim)键（键绑定弹出窗口（1 秒后显示）） | 正常 |
| `<leader>e`         | [NVIMTREE](https://github.com/nvim-tree/nvim-tree.lua)（侧面文件浏览器） | 正常 |
| `<leader>f`         | （查找文件）                                                 | 正常 |
| `<leader>;`         | (仪表板)                                                     | 正常 |
| `<C-\>` `<M-1/2/3>` | [切换术语](https://github.com/akinsho/toggleterm.nvim)（终端） | 正常 |

### 语言服务提供商

| .key | 描述           | 模式 |
| ---- | -------------- | ---- |
| `K`  | 悬停信息       | 正常 |
| `gd` | 转到定义       | 正常 |
| `gD` | 转到声明       | 正常 |
| `gr` | 转到参考资料   | 正常 |
| `gI` | 转到实施       | 正常 |
| `gs` | 显示签名帮助   | 正常 |
| `gl` | 显示生产线诊断 | 正常 |

### 编辑

| .key        | 描述     | 模式       |
| ----------- | -------- | ---------- |
| `<leader>/` | 评论     | 正常，可视 |
| `gb`        | 阻止评论 | 视觉       |
| `<M-k>`     | 上移线路 | 正常，可视 |
| `<M-j>`     | 下移线   | 正常，可视 |

### 窗户

| .key        | 描述         | 模式 |
| ----------- | ------------ | ---- |
| `<C-h>`     | 转到左侧窗口 | 正常 |
| `<C-j>`     | 转到下部窗口 | 正常 |
| `<C-k>`     | 转到上部窗口 | 正常 |
| `<C-l>`     | 转到右侧窗口 | 正常 |
| `<C-Up>`    | 减小窗口高度 | 正常 |
| `<C-Down>`  | 增加窗口高度 | 正常 |
| `<C-Left>`  | 减小窗口宽度 | 正常 |
| `<C-Right>` | 增加窗口宽度 | 正常 |

### 杂项

| .key         | 描述               | 模式 |
| ------------ | ------------------ | ---- |
| `<leader>Lc` | 编辑配置.lua       | 正常 |
| `<leader>h`  | 清除搜索突出显示   | 正常 |
| `<leader>sh` | 搜索浏览`:help`    | 正常 |
| `<leader>sr` | 打开最近使用的文件 | 正常 |
| `<leader>pS` | 已安装插件列表     | 正常 |



## 配置

> 配置文件配置 LunarVim `~/.config/lvim/config.lua`

[按键绑定的修改和配置](https://www.lunarvim.org/docs/configuration/keybindings)

demo：

```
vim.opt.backup=false--创建备份文件
vim.opt.clipboard=“unnamedplus”--允许neovim访问系统剪贴板
vim.opt.cmdheight=2--neovim命令行中用于显示消息的更多空间
vim.opt.colorcolumn=“99999”--暂时修复缩进线
vim.opt.completeopt={“menuone”，“noselect”}
vim.opt.conceallevel=0--以便“”在markdown文件中可见
vim.opt.fileencoding=“utf-8”--写入文件的编码
vim.opt.foldmethod=“manual”--折叠设置为“expr”，用于基于树保姆的折叠
vim.opt.foldexpr=“”--设置为“nvim_treesiter#foldexpr（）”，用于基于treesiter的折叠
vim.opt.guifont=“monospace:h17”--图形neovim应用程序中使用的字体
vim.opt.hidden=true--需要保留多个缓冲区并打开多个缓冲
vim.opt.hlsearch=true--突出显示上一搜索模式中的所有匹配项
vim.opt.ignorecase=true--忽略搜索模式中的大小写
vim.opt.mouse=“a”--允许在neovim中使用鼠标
vim.opt.pumheight=10--弹出菜单高度
vim.opt.showmode=false--我们不需要再看到像--INSERT这样的内容
vim.opt.showtabline=2--始终显示选项卡
vim.opt.smartcase=true--智能案例
vim.opt.smartindent=true--使缩进更智能
vim.opt.splitbelow=true--强制所有水平拆分位于当前窗口下方
vim.opt.spliitright=true--强制所有垂直拆分到当前窗口的右侧
vim.opt.swapfile=false--创建swapfile
vim.opt.termguicolors=true--设置术语gui颜色（大多数终端支持此选项）
vim.opt.timeoutlen=100—等待映射序列完成的时间（毫秒）
vim.opt.title=true--将窗口的标题设置为标题字符串的值
vim.opt.titlestring=“%<%F%=%l/%l-nvim”--窗口的标题将设置为什么
vim.opt.undodir=vim.fn.stdpath“缓存”。。“撤消”
vim.opt.undofile=true--启用持久撤消
vim.opt.updatetime=300--更快完成
vim.opt.writebackup=false——如果文件正在被另一个程序编辑（或在用另一个软件编辑时被写入文件），则不允许编辑
vim.opt.expandtab=true--将制表符转换为空格
vim.opt.shiftwidth=2—每个缩进插入的空格数
vim.opt.tabstop=2—为选项卡插入2个空格
vim.opt.cursolline=true--突出显示当前行
vim.opt.number=true--设置编号行
vim.opt.relativinumber=false—设置相对编号的行
vim.opt.numberwidth=4—将数字列宽度设置为2｛默认值4｝
vim.opt.signcolumn=“yes”--始终显示符号列，否则每次都会移动文本
vim.opt.wrap=false--将行显示为一条长线
vim.opt.spell=假
vim.opt.spelllang=“en”
vim.opt.scrolloff=8 
vim.opt.sidescrolloff=8
```

## 主题配置

https://www.lunarvim.org/docs/configuration/colorschemes



## 插件管理

> `Neovim` 0.5 以后一般都会推荐使用 `lua` 原生的 [packer.nvim](https://link.zhihu.com/?target=https%3A//github.com/wbthomason/packer.nvim) 做插件管理 

按照管理的方法安装后 ，`lua/packer.lua`为 配置文件

```bash
--重新生成编译的加载程序文件
：PackerCompile

--删除所有禁用或未使用的插件
：PackerClean

--清理，然后安装缺失的插件
：PackerInstall

--清理，然后更新和安装插件
：PackerUpdate

--执行“打包更新”，然后执行“打包编译”`
：PackerSync

--立即加载opt插件
：PackerLoad completion-nvim al
```



# Vim

> [Vim 官方绑定介绍](https://devhints.io/vim)



Vimrc

```
set nu
set ai
filetype on
set cursorline
set ruler
syntax on 
set t_Co=256
set mouse=a
set selection=exclusive
set selectmode=mouse,key
set hlsearch
set showmatch
```



## 命令模式：

H左  J下	K上	L右

`w`移动到这个单词的末尾
`b`移动到这个单词的末前面
`gg`移动到最开头
`GG`移动到末尾
`Ctrl+u`	向上翻页
`Ctrl+d`	向下翻页
`0`移动到当前行的前面
`$`移动到当前行的末尾
`x`删除字符
`u`撤销
`U`撤销所有
`Ctrl+r`重复上一个动作

## 编辑模式：

`i`插入
`I`行开头插入
`a`在光标末尾插入
`A`行末尾插入
`o`在下一行开始输入`O`在上一行输入
`r\R`替换模式

`y`复制当前选择中字符
`y0` 则表示复制到第1行，异次类推

`yy/Y`复制一行  
`yay` 复制这个单词

`p`粘贴
`d`剪切字符  `dd`剪切一行 

`X`向`前`删除一个，`x`向`后`删除一个

`J` 将光标所在行与下一行的数据结合成同一行

`yG`复制光标到行末尾的字符
`y0`复制光标到行开头的字符

`d$`删除光标到行末尾的字符
`d0`删除光标到行开头的字符

`Shift + ~`   字母大小写控制
`Ctrl+a` 数字大小+1
`Ctrl+x` 数字大小-1

```shell
删除全文:s
:1,$ d
gg光标最顶上,`dG`删除
:%d


16进制模式 %!xxd
退出保存%!xxd -r

`ci"`  表示删除"sss"中的字符并进入写入模式，类似的有, `ci(`  `ci#``
```

### 选中模式：

`shift+v` 行选择
`Ctrl+q` 列选择
`ctrl + v`  块选择

选择后c 剪切

## 命令模式：

`:g` 代表全文范围
`/^`代表行开始
`$`代表行结束
`s*`代表空白字符
`d`删除
`%`全部
`s`匹配空白字符(包tab)，`S`匹配非空白字符

特殊字符加/反转义

> 删除注释行`g/^#/d` ,删除空白行`g/^$/d`
>
> 删除行首空格,`%s/^\s*//g`
>
> 行末尾`%s/\s\*$//g`

行首 `:%s/^/your_word/`

行尾 `:%s/$/your_word/`

`?`从当前行以`上`开始搜索字符,`n`下一个,`N`上一个

`/`从当前行以`下`开始搜索字符,`n`下一个,`N`上一个 



### Vim 字符替换

| `:s/a/s`把`当前行的一个`a替换为s  | `:s/a/s/g`替换`当前行所有`的a为s |
| --------------------------------- | -------------------------------- |
| `:10/a/s`把第10行的一个a替换为s   | `:10/a/s/g`把10行的所有a换成s    |
| `:%s/a/s`把所有行的第一个a替换为s | `:%s/a/s/g`把所有的a替换为s      |



# SpaceVim

## 常用指令

| 键盘   | 物理案件 |
| ------ | -------- |
| Leader | \        |
| SPC    | 空格键   |
| Window | s        |

| 快捷键        |                        指令                        |
| :------------ | :------------------------------------------------: |
| Leader + 数字 |                  跳转到不同的tab                   |
| SPC + 数字    |                 跳转到不同的 窗口                  |
| SPC b f       |                     格式化代码                     |
| `SPC f v d`   |                   `打开配置文件`                   |
| SPC b d       |                   s关闭当前buff                    |
| SPC f o       | 打开文件所在位置(按‘N’可以创建文件'.'隐藏文件显示) |
| F3            |                       目录树                       |
| `SPC +s+e`    |                   多光标的单词！                   |
| SPC + c +l    |           注释/反注释选中的内容或当前行            |
| SPC+s+c       |                 清除高亮和:noh一样                 |
| spc s s       |                    当前文件搜索                    |
| spc s d       |                    当前目录搜索                    |
| scp l r       |                    直接运行代码                    |
| SPC x d w     |                 删除行尾空白字符！                 |

## 注释模式

| 快捷键    | 功能描述                   |
| :-------- | :------------------------- |
| SPC c  l  | 注释/反注释当前行          |
| SPC c     | 注释/反注释同时复制        |
| SPC c  $  | 从光标位置开始注释当前行   |
| SPC+c+t/T | t向上注释N行，T向下注释N行 |

## Window

| 快捷键       | 功能描述                   |
| :----------- | :------------------------- |
| `q`          | 智能关闭当前窗口           |
| `[Window] v` | 水平分屏                   |
| `[Window] V` | 水平分屏，并编辑上一个文件 |
| `[Window] g` | 垂直分屏                   |
| `[Window] G` | 垂直分屏，并编辑上一个文件 |
| `[Window] o` | 一键关闭其他窗口           |



# 其他

Vim粘帖复制问题解决：`set paste`

Dos  ->  unix 	:set fileformat =unix

