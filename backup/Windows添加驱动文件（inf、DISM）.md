首先在刻录好的u盘上提取“boot.wim”，复制到本地文件夹里。然后在同一个文件夹下，创建“mount”文件夹；并放置所需的drivers文件夹（带inf文件）。运行：
### 1\.挂载wim文件到mount文件夹：
    dism /mount-wim /wimfile:boot.wim /index:1 /mountdir:mount
部署映像服务和管理工具
版本: 10.0.17763.5830

正在安装映像
[==========================100.0%==========================]
操作成功完成。（**挂载成功**）

###2\.加载驱动文件到mount文件夹：
    dism /image:mount /add-driver:"Display.Driver" /recurse
Installing 48 of 48 - C:\Users\PC\Desktop\wim\Display.Driver\nvxisi.inf: The driver package was successfully installed.
操作成功完成。（**加载驱动成功**）

###3\.卸载mount文件到wim文件中：
    dism /unmount-wim /mountdir:mount /commit```

###4\.复制回u盘，结束


