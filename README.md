# Mac-SetUp

本文档主要目的是如何快速在新的MacBook或iMac上配置好开发、工作环境。包括如下：

- 系统升级
- 系统偏好设置（个人偏好）
- 基础软件
- 开发、工作、学习必备软件（个人习惯）


## 系统升级

从屏幕左上角的苹果 Logo 中选取“系统偏好设置” > 点按“软件更新” > 如果有可用更新或升级，请点按“现在更新”或“立即升级”进行安装。


## 系统偏好设置

- 触控板 -> 单指轻点
- 键盘 -> 按键重复 -> 快（一直向右拉满）
- 键盘 -> 重复前延迟 -> 短（一直向右拉满）
- 程序坞 -> 自动显示和隐藏程序坞


## 基础软件

### 搜狗输入法

https://pinyin.sogou.com/mac/

### Chrome 浏览器

https://www.google.com/intl/zh-CN/chrome/

### Clash 科学上网工具

https://github.com/Fndroid/clash_for_windows_pkg


## 开发、工作、学习必备软件&插件

### Terminals

> 终端是一个码农最重要的武器之一。
#### iTerm2 终端

##### 安装 iTerm2

https://iterm2.com/

##### iTerm2 迁移配置（可选）

- 原电脑：点击 `preferences` -> 底部点击Other Actions -> Save Profile as JSON
- 新电脑：点击 `preferences` -> 底部点击Other Actions -> Import JSON Profiles

#### Warp 终端 - 重新定义终端

##### 安装 Warp

- https://www.warp.dev/
- `brew install --cask warp`

##### Feature

- 开箱即用，无需任何配置
- 更加便捷的智能化提示
- 智能记忆，会记录上一次执行的命令
- 区域选择
- 历史命令提示
- 命令导航
- AI
- 团队协作

##### 弊端

- 暂时仅支持 Mac
- 需要登录使用

#### 使用 zsh 来强化 iTerm2 终端

##### 安装 zsh

> 尽量在命令行添加代理去安装

https://ohmyz.sh/#install

##### 必备插件

> 除自带插件外，其余插件需要手动安装并在 `~/.zshrc` 中编辑生效

```vim
# 1. Clone this repository into $ZSH_CUSTOM/plugins (by default ~/.oh-my-zsh/custom/plugins)
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# 2.Add the plugin to the list of plugins for Oh My Zsh to load (inside ~/.zshrc):
# vim ~/.zshrc
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)

# 3. Restart zsh (such as by opening a new instance of your terminal emulator).
```

##### 常用配置
> 添加一些变量和别名
```
# 1. vim ~/.zshrc
export tb="--registry https://registry.npm.taobao.org/"
export npm="--registry https://registry.npmjs.com/"

alias show-dir="tree -l 3 -a --ignore node_modules,dist,.git"
alias git-config="git config user.name \"xxx\" && git config user.email \"xxx\" && echo \"Change git config success\""
alias git-log="git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

# 2. 生效
source ~/.zshrc
```

#### 使用 [powerlevel10k](https://github.com/romkatv/powerlevel10k) 美化

1. 安装 powerlevel10k

```
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

2. 下载安装字体

- [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
- [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
- [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
- [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

3. Type `p10k configure` or Restart zsh

### Homebrew 包管理工具

#### 安装

国外：

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

国内（包含镜像源的配置）：

`/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"`

#### 使用清华源，替换现有上游，加速下载

##### 替换
```
# 多种源替换
# brew.git
cd "$(brew --repo)"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

# homebrew-core.git
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

# 更新源
brew update

```

##### 重置

```
# 重置
cd "$(brew --repo)"
git remote set-url origin https://github.com/Homebrew/brew.git

cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://github.com/Homebrew/homebrew-core.git

# 更新
brew update
```

### git

#### 安装

`brew install git`

#### 配置账户

```
git config --global user.name "cy920820"
git config --global user.email "cuiyang673308817@gmail.com"
```

#### 其它配置

```
git config --global pull.rebase true
```

### node 

#### 安装 nvm

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`

#### 使用 nvm 安装 node

```
nvm install node
node -v
```

### VScode 编辑器

#### 下载安装

直接跳转到官网，复制下载链接并将下载链接中的域名替换成 `vscode.cdn.azure.cn` 加速

#### settings，可以长期维护一套，通过 sync 插件同步

#### 插件

... 待更新


### Python

... 待更新


### 效率 Apps

#### Bob 效率翻译软件

https://github.com/ripperhe/Bob

#### utools 工具集

https://u.tools/

#### SwitchHosts

https://github.com/oldj/SwitchHosts

#### Charles

https://www.charlesproxy.com/


#### LICEcap

https://github.com/justinfrankel/licecap


#### Typora

https://typora.io/

### Chrome 浏览器插件

... 待更新


### 多媒体工具

#### IINA

https://iina.io/


#### HandBrake

https://github.com/HandBrake/HandBrake


#### Kodi

https://github.com/xbmc


#### kantu

https://kantu.qq.com/
