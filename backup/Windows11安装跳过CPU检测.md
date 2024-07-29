### Windows11安装跳过CPU检测

#### 更新日期：2024-07-029

#### 分类：Windows

Windows 11 会检测电脑CPU/TPM 以及其他设备是否存在与兼容，而Windows 10 的安全更新又即将停止。老电脑安装Windows 11 就需要一些对安装文件进行一定的修改，以便Windows 11 能正常安装。

**步骤 1：准备工作**

确保在msdn或其他正式版下载地址下载原版镜像，以及下载7-zip一类解压缩软件，并把ISO文件解压成文件的形式。

**步骤 2：找到appraiser.dll，并替换它**

首先创建一个txt文本，并改名：appraiser.dll；然后将新创建的appraiser.dll粘贴到sources文件夹中并替换原文件。

**步骤 3：正常使用exe或者压缩成ISO进行下一步安装操作**

然后就可以退出使用setup.exe或者压缩成ISO格式正常安装Windows 11 了。
