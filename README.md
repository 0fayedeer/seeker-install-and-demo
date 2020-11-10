# seeker-install-and-demo
* TOC
{:toc}
- [原项目链接](https://github.com/thewhiteh4t/seeker)本文档由原项目翻译而来并做了部分修改。
- seeker是一个概念验证工具，仅用于教育目的。

##  介绍

Seeker背后的概念很简单，就像我们用钓鱼网页来获取凭证一样，用一个假的网页来请求你的位置，网站要求位置权限，如果目标允许它，就会获得：

- 经度
- 纬度
- 准确度
- 高度 - 不一定有
- 方向 - 仅当用户在移动时才会出现
- 速度 - 仅当用户移动时可用

**除了位置信息，还可以在没有任何权限的情况下获得设备信息：**

- 操作系统
- 平台
- CPU核心数
- RAM数量--大概结果
- 屏幕分辨率
- GPU信息
- 浏览器名称和版本
- 公共IP地址
- 大陆（洲）
- 国家
- 地区
- 城市
- Org和ISP

**这个工具是一个概念验证，仅用于教育目的，Seeker展示了恶意网站可以收集你和你的设备的数据，以及为什么你不应该点击随机链接和允许关键权限，如位置等。**

## Seeker与IP GeoLocation的不同

- 其他工具和服务提供的IP地理位置完全不准确，并且不提供目标的位置，而是ISP的大概位置。
- Seeker使用HTML API并获取位置许可，然后使用设备中提供的GPS硬件获取经度和纬度，因此，如果GPS硬件（例如在笔记本电脑上）不存在，则Seeker可以最好地与智能手机配合使用，例如Seeker会回退到IP Geolocation否则它将查找缓存的坐标。
- 一般情况下，如果用户接受位置渗透，则接收到的信息的精度约为30米，精度取决于设备。

## 模板

(模板是可以更改的)

- NearYou
- Google Drive (Suggested by @Akaal_no_one)
- WhatsApp (Suggested by @Dazmed707)
- Telegram

## 已通过测试：

- Kali Linux
- BlackArch Linux
- Ubuntu
- Kali Nethunter
- Termux
- Parrot OS

## 安装

### Kali Linux / Ubuntu / Parrot OS

```shell
git clone https://github.com/thewhiteh4t/seeker.git
cd seeker/
chmod 777 install.sh
sudo ./install.sh
```

### BlackArch Linux

```shell
sudo pacman -S seeker
```

### Arch Linux

```shell
git clone https://github.com/thewhiteh4t/seeker.git
cd seeker/
chmod 777 arch_install.sh
sudo ./arch_install.sh
```

**注：还需要安装ngrok**

## 演示

下面是在archlinux环境下的演示，其他环境除了安装时有些细微的区别，使用起来都一样

### **安装**

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image01.png)

### **使用**

启动

```shell
python3 seeker.py -t manual
```

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image02.png)

选择模板和输入最后要转到的地址

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image03.png)

启动成功就是下面这样

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image04.png)

打开另一个终端，启动ngrok

```
ngrok http 8080
```

下图就是给目标的两个链接

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image05.png)

如果目标正在打开你的链接就会出现相应请求

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image06.png)

这是选择Google Drive模板时目标看到的界面

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image07.png)

目标点击Request access时会弹出获取位置信息

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image08.png)

**当目标成功跳转到你之前输入的地址时，在seeker界面会返回介绍中提到的信息**

这是在没有GPS硬件的电脑上点开链接返回的信息,位置是根据ip定位（相关隐私信息已做处理）

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image09.png)

这是在手机上点开链接返回的信息，位置是根据GPS定位（相关隐私信息已做处理）

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image10.png)

**点开链接返回信息中有经纬度等信息，同时还有一个谷歌地图的链接，点击打开就是seeker获得的位置地点。**（手机定位精度很高，多次测试发现和手机app获得的位置很接近）

## 伪装ngrok生成的链接

可以发现由ngrok生成的链接都是xxxxxxxx.ngrok.io格式,很容易就被一眼识破。

所以可以用一些方法来改变这个链接

如使用[短网址生成网站](https://sina.lt/)

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image11.png)

![image](https://cdn.jsdelivr.net/gh/chrysoskun/chrysoskun.github.io/assets/img/seeker/image12.png)

**seeker是一个概念验证工具，仅用于教育目的（重要的事情说三遍）**

