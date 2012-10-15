# Zipped Data 下载
使用豌豆荚下载 zip 压缩包，将压缩包内容解压后传输到手机 sd 卡的指定目录。

如果压缩包为游戏包 (压缩包中包含 apk 文件和游戏数据文件)，将压缩包内容解压，安装 apk 文件，然后将解压后传输到手机 sd 卡的指定目录。

----------

## 通用 zip 压缩包下载

使用 [豌豆荚下载协议](https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Download%20Link.md) 下载 zip 文件。

### 参数说明

content-type：application/zip，表示下载内容为 zip 文件。

filepath：解压文件传输到手机的路径。

其他参数同 [豌豆荚下载协议](https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Download%20Link.md)。

### Sample

`<a rel="download" href="http://www.example.com/sample.zip#name=example&content-type=application/zip&filepath=/sdcard/sample">example</a>`

将 sample.zip 解压后传输到手机 sd 卡的 sample 目录。

----------

## 游戏包下载

游戏包首先是 zip 文件，同时压缩包内不仅包含一个 APK 文件，同时还包括游戏运行时需要调用的资源文件。

### 游戏包数据格式

![数据格式][game_package_data_structure]

### 参数说明

content-type：application/zip，表示下载内容为 zip 文件。

filepath：解压文件传输到手机的路径。

action: install 表示该 zip 文件是游戏包，需要安装 APK 文件。

其他参数同 [豌豆荚下载协议](https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/Download%20Link.md)。

### Sample

sample.zip 的文件结构

sample.zip ----- sample.apk

      |
      
      |    ----- data  ...

`<a rel="download" href="http://www.example.com/sample.zip#name=example&content-type=application/zip&filepath=/sdcard/sample&action=install">example</a>`

将 sample.zip 解压后安装 sample.apk，然后传输压缩包中的 data 目录到手机 sd 卡的 sample 目录。

  [game_package_data_structure]: https://github.com/wandoulabs/developer-documents/blob/master/Doraemon/pictures/game_package.png?raw=true
