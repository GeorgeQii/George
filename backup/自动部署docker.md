    # 使用 apt 自动下载 Docker 并部署 Hello World 容器
    
    ## 步骤 1: 更新系统包列表
    
    ```bash
    sudo apt-get update
    

步骤 2: 安装 Docker
---------------

    # 安装软件包依赖
    sudo apt-get install \\
        apt-transport-https \\
        ca-certificates \\
        curl \\
        gnupg2 \\
        software-properties-common
    
    # 添加 Docker 的 GPG 密钥
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    
    # 添加以下三个在中国可用的镜像源
    
    # 阿里云
    sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
    
    # 网易
    sudo add-apt-repository "deb [arch=amd64] http://mirrors.163.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
    
    # 清华大学
    sudo add-apt-repository "deb [arch=amd64] https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
    
    # 安装 Docker CE
    sudo apt-get install docker-ce
    
    # 验证 Docker 是否安装成功
    sudo docker --version
    

步骤 3: 部署 Hello World 容器
-----------------------

    # 运行 Hello World 容器
    sudo docker run hello-world
    

以上命令会从 Docker Hub 下载并运行一个官方的 "hello-world" 容器，您应该会看到以下输出：

    Hello from Docker!
    This message shows that your installation appears to be working correctly.
    
    To generate this message, Docker took the following steps:
    1. The Docker client contacted the Docker daemon.
    2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    3. The Docker daemon created a new container from that image which runs as a command line interface.
    4. Finally, the container executed the command `echo "Hello from Docker!"` and exited.
    
    To run this image, use the following command -> docker run hello-world
    

完成以上步骤后，您就成功地在您的系统上使用 Docker 部署了一个 "Hello World" 容器。


