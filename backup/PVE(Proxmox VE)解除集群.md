
    # 解除 Proxmox 集群（不会删除虚拟机）
    
    运行以下命令来解除 Proxmox 集群，此操作不会删除任何虚拟机。
    
    ```bash
    systemctl stop pve-cluster corosync
    pmxcfs -l
    cp -a /etc/corosync /etc/corosync.bak
    rm /etc/corosync/*
    rm /etc/pve/corosync.conf
    killall pmxcfs
    systemctl start pve-cluster
    

其中 `/etc/corosync.bak` 是对原始 `/etc/corosync` 目录的备份，如果需要重新组建集群，可以直接使用备份文件（需要先清空子机的相关配置），然后重新启动 corosync 服务。

此时，可以分别使用各自的 root 用户在管理控制台登录。

您会发现有一些显示问号的虚拟机和已经解除集群的机器，现在可以放心地删除它们，因为集群连接已经被断开，不会影响到子机上的虚拟机。

    
    请注意，这些操作涉及到集群配置的修改，请在执行前确保已经充分了解每一步的作用，并在非生产环境中先进行测试。