# Mac 常见设置


## 启动台行列

【终端】输入或粘贴以下命令，修改后面的数字更改行列数。

行数

```
defaults write com.apple.dock springboard-rows -int 7
```

列数

```
defaults write com.apple.dock springboard-columns -int 9
```

最后输入以下命令

```
killall Dock
```

## 程序坞显示时间

如果你习惯隐藏程序坞，鼠标放在屏幕底部，默认显示程序坞非常慢，你可以在【终端】输入或粘贴下面命令，将数值改为 `0`，这样，显示程序坞会变的很快。

```
defaults write com.apple.dock autohide-delay -int 0
```

再输入下面命令。

```
killall Dock
```


## 密码位数

管理员默认密码至少为 `4` 位，【终端】输入或粘贴以下命令支持将密码改为 `1` 位。

```
pwpolicy -clearaccountpolicies
```

## 深色显示浅色窗口

程序坞和菜单栏深色，窗口是浅色。

1. 终端输入或粘贴以下命令，按回车键
2. 注销并重新登录 Mac
3. 系统偏好设置 - 通用 - 深色。

```
defaults write -g NSRequiresAquaSystemAppearance -bool Yes
```

恢复

```
defaults delete -g NSRequiresAquaSystemAppearance
```

## SIP 状态

【终端】输入 `csrutil status`，按回车键。

### 关闭 SIP

1. Mac 开机立即按住 `Command-R`
2. 进入实用工具窗口，点击**实用工具**里【终端】，输入下面命令按回车键，重启 Mac

```
csrutil disable
```

### 开启 SIP

同上，【终端】输入下面命令。

```
csrutil enable
```
## 关闭输入法切换提示
终端里运行完以下两个命令后重启 Mac

```
sudo mkdir -p /Library/Preferences/FeatureFlags/Domain
```
```
sudo /usr/libexec/PlistBuddy -c "Add 'redesigned_text_cursor:Enabled' bool false" /Library/Preferences/FeatureFlags/Domain/UIKit.plist
```
 

## 网页显示方框里带问号

安装新字体时字体冲突，导致浏览器网页中字体显示成方块里带问号，需要清一下字体缓存。
![](https://i.imgur.com/Lkk0Gja.png)

1. 关闭所有 app
2. 打开终端 Terminal
3. 终端输入：`sudo atsutil databases -remove`
4. 输入电脑密码，按回车
5. 终端输入：`atsutil server -shutdown`
6. 终端输入：`atsutil server -ping`
7. 重启电脑

## 允许任何来源

【终端】输入或粘贴以下命令，按回车键，输入密码按回车键。

```
sudo spctl --master-disable
```

## 提示“已损坏，无法打开，移到废纸篓”

1. 打开允许任何来源（上方）
2. 打开终端，输入 `xattr -cr`（cr后面加入一个空格），将 App 拖到终端，按回车键

注1：Ventura 13 以上系统，先前往设置 - 隐私与安全性 - 完整磁盘访问权限中允许终端。然后才能操作，否则会遇到 Operation not permitted

注2：macOS 13+ 以上系统上操作之后如果还是提示损坏，右键软件选择【打开】
