# install oh-my-zsh
- 安装`zsh`
```shell script
brew install zsh
```
- 设置`zsh`为默认终端
```shell script
which zsh >> /etc/shells
```

- 安装`oh-my-zsh`
```shell script
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

- 添加`zsh-syntax-highlighting`和`zsh-autosuggestions`插件

- 下载插件
```shell script
cd ~/.oh-my-zsh/custom/plugins
git clone git://github.com/zsh-users/zsh-syntax-highlighting.git
git clone https://github.com/zsh-users/zsh-autosuggestions.git
```
- 编辑配置文件
```shell script
vi ~/.zshrc
```
- 将插件添加到配置文件
```plaintext
plugins=( [plugins...] zsh-syntax-highlighting zsh-autosuggestions)
```
- 重新载入配置
```shell script
source ~/.zshrc
```