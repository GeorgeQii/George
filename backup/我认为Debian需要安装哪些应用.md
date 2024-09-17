    ### 安装步骤
    
    1. **加速本地 DNS 访问**
       apt update
       apt install sudo && apt install curl
       curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
    

2.  **安装 Docker**
    
        curl -fsSL https://get.docker.com -o get-docker.sh    
        sudo sh get-docker.sh
        
    
3.  **百度网盘下载 Docker 镜像**
        
        mkdir baidunetdiskconfig
        mkdir downloads  
        docker create \
        --name=baidunetdisk \
        -p 5800:5800 \
        -p 5900:5900 \
        -v /baidunetdiskconfig:/config \
        -v /downloads:/config/baidunetdiskdownload \
        --restart unless-stopped \
        johngong/baidunetdisk:latest
        
    
4.  **迅雷下载 Docker 镜像**
       
        mkdir xunleiconfig    
        docker run -d \
        -v /xunleiconfig:/xunlei/data \
        -v /downloads:/xunlei/downloads \
        -p 2345:2345 \
        --privileged \
        cnk3x/xunlei
        
    
5.  **可选：安装 Nextcloud**
    
        docker run -d -p 8080:80 nextcloud
        apt update && apt install snapd -y
        snap install nextcloud
        
    
6.  **安装 Jumpserver**
    
        curl -sSL https://github.com/jumpserver/jumpserver/releases/latest/download/quick_start.sh | bash