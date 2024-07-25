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

### 重新加入集群步骤

1. **全新安装Proxmox VE**：在目标服务器上进行Proxmox VE的全新安装。
2. **加入集群**：按照前一节中的说明，将服务器重新加入集群。

### 配置文件处理

在移除节点后，其配置文件仍然会保留在`/etc/pve/nodes/hp4`目录中。请恢复您仍然需要的任何配置，并在之后删除该目录。

### SSH指纹更新

**注意**：在移除节点后，其SSH指纹仍然会存在于其他节点的`known_hosts`文件中。如果在用相同的IP或主机名重新加入节点后遇到了SSH错误，请在重新加入的节点上执行一次`pvecm updatecerts`命令，以在集群范围内更新其指纹。
