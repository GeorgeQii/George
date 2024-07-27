**Office 软件部署相关**

1.  Office 软件部署工具：[https://www.microsoft.com/en-us/download/details.aspx?id=49117](https://www.microsoft.com/en-us/download/details.aspx?id=49117)
    
    *   下载完，创建文件夹后，软件自动创建 `setup.exe`
2.  Office 版本自定义工具：[https://config.office.com/deploymentsettings](https://config.office.com/deploymentsettings)
    
    *   把下载好的文件放入上一步创建好的文件夹
3.  打开 `powershell`，`cd` 命令导航到创建好的文件夹
    
    *   下载命令：
        
            setup /download config.xml
            示例： PS G:\\office>.\\setup.exe /download config.xml
            
        
    *   安装命令：
        
            setup /configure config.xml
            示例： PS G:\\office>.\\setup.exe /configure config.xml
            
        

**如果没有激活成功，所需输入的代码**

1.  `slmgr /skms kms.03k.org`
    
2.  `slmgr /ato`