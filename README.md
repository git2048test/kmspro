### windows系统一句命令激活

#### 打开 命令提示符（管理员） 运行：slmgr /skms kms.v0v.bid && slmgr /ato

---

---

## Linux系统 自建KMS服务器

### 一键安装KMS服务 （Debian/Ubuntu/Mint 等）
```
wget -N --no-check-certificate git.io/k.sh && chmod +x k.sh && bash k.sh debian
```

### 一键安装KMS服务 （CentOS/Redhat/Fedora 等）（如果系统开启了防火墙 须自行开放 1688 端口）
```
wget -N --no-check-certificate git.io/k.sh && chmod +x k.sh && bash k.sh centos
```

### 启动KMS服务
```
bash k.sh start

服务器IP地址既是KMS服务器地址
也可以将域名解析至IP使用（支持IPv6 即AAAA记录）

更多详细教程：https://v0v.bid/kms.html
```

### 关闭KMS服务
```
bash k.sh stop
```

### 添加开机自启动KMS服务
```
bash k.sh auto
```

### 重启KMS服务
```
bash k.sh restart
```

### 查看KMS服务运行状态
```
bash k.sh status
```

### 卸载KMS服务
```
bash k.sh uninstall
```

## Windows系统 自建KMS服务器

### 一键安装KMS服务 （Windows系统 x86/x64）
```
访问下方地址：
https://github.com/Wind4/vlmcsd/releases
下载最新版本 binaries.tar.gz

解压后运行：
\binaries\Windows\intel\vlmcsd-Windows-x64.exe
或者：
\binaries\Windows\intel\vlmcsd-Windows-x86.exe
```

## 安卓手机 自建KMS服务器
```
访问下方地址：
https://v0v.bid/android.html
查看教程
```

需要改端口的可以照这样来操作。编辑/etc/init.d/kms文件，将

$DAEMON -p $PID_FILE这段改成$DAEMON -P(端口号) -p $PID_FILE，如$DAEMON -P30000 -p $PID_FILE,即端口号改成30000。然后重启KMS服务，搞定。




密钥管理服务 (KMS) 客户端激活和产品密钥
https://learn.microsoft.com/zh-cn/windows-server/get-started/kms-client-activation-keys

使用管理员权限运行 cmd 查看系统版本，命令如下：
wmic os get caption

使用管理员权限运行 cmd 安装从上面列表得到的 key，命令如下：
slmgr /ipk xxxxx-xxxxx-xxxxx-xxxxx-xxxxx

使用管理员权限运行 cmd 将 KMS 服务器地址设置为你自己的 IP 或 域名，后面最好再加上端口号（:1688），命令如下：
slmgr /skms Your IP or Domain:1688

**注意：**本脚本所做的工作就是此步骤。当你的 KMS 服务出于启动状态，那么此处就可以设置为你自己的 KMS 服务器地址。 使用管理员权限运行 cmd 手动激活系统，命令如下：
slmgr /ato


关于 Office 的激活，要求必须是 VOL 版本，否则无法激活。
Office 2019 & Office 2016：https://docs.microsoft.com/en-us/DeployOffice/vlactivation/gvlks
找到你的 Office 安装目录，32 位默认一般为 C:\Program Files (x86)\Microsoft Office\Office16 64 位默认一般为 C:\Program Files\Microsoft Office\Office16 Office16 是 Office 2016，Office15 就是 Office 2013，Office14 就是 Office 2010。 打开以上所说的目录，应该有个 OSPP.VBS 文件。 使用管理员权限运行 cmd 进入 Office 目录，命令如下：
cd "C:\Program Files (x86)\Microsoft Office\Office16"

使用管理员权限运行 cmd 注册 KMS 服务器地址：
cscript ospp.vbs /sethst:Your IP or Domain #激活地址
cscript ospp.vbs /setprt:1688 #激活端口

使用管理员权限运行 cmd 手动激活 Office，命令如下：
cscript ospp.vbs /act

注意： KMS 方式激活，其有效期只有 180 天。 每隔一段时间系统会自动向 KMS 服务器请求续期，请确保你自己的 KMS 服务正常运行。





## 版权声明：
### 此项目仅为bash一键脚本，脚本内所涉及到的任何软件版权和责任归原作者所有。
```
此项目脚本基于以下开源项目：
https://github.com/Wind4/vlmcsd
https://github.com/ThunderEX/py-kms
https://forums.mydigitallife.net/members/hotbird64.333466/
https://forums.mydigitallife.net/members/pantagruel.5805/
```
