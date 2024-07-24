只需要运行以下命令就可以把集群解了
不会删除虚拟机
1.  **运行**
  systemctl stop pve-cluster corosync
  pmxcfs -l
  cp -a /etc/corosync /etc/corosync.bak
  rm /etc/corosync/*
  rm /etc/pve/corosync.conf
  killall pmxcfs
  systemctl start pve-cluster
其中/etc/corosync.bak是备份，如果要组回来可以直接用回他（重走流程要清空子机），再启动corosync服务即可

这时候可以各自用各自的root用户在管理控制台登录
会发现有一些问号的虚拟机，和已经解除集群的机器，那现在就可以放心的删除了，因为已经断开连接了，不会把子机的虚拟机删掉