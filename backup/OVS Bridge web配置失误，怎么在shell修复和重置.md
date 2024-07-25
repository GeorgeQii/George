正确的配置是创建bridge network之后，把物理port接口的ip以及route地址移交到bridge接口上，然后应用配置。

错误信息 "either local is duplicate or vmbridge0 is a garbage" 通常表示在 Open vSwitch（OVS）配置中存在冲突或错误。这可能是因为尝试创建的桥接名称与现有的接口名称冲突，或者是因为存在无效的配置。

以下是一些可能的解决步骤：

### 1\. 检查已存在的接口

首先，检查当前系统中已经存在的网络接口：

    ovs-vsctl show
    

查看输出中是否有与 `vmbridge0` 或您尝试创建的桥接名称冲突的接口。

### 2\. 删除错误的桥接或端口

如果发现存在错误的桥接或端口，您需要删除它们：

    ovs-vsctl del-br <错误的桥接名称>
    

或者，如果您需要删除特定的端口：

    ovs-vsctl del-port <桥接名称> <端口名称>
    

### 3\. 清理垃圾配置

如果 `vmbridge0` 是一个垃圾配置，您可能需要清理它：

    ovs-vsctl --all destroy port vmbridge0
    ovs-vsctl --all destroy bridge vmbridge0
    

请注意，上述命令会删除 `vmbridge0` 端口和桥接。请确保这是您想要的操作，因为这将移除与该名称相关的所有配置。

### 4\. 重新创建桥接

在清理完错误的配置之后，您可以尝试重新创建桥接：

    ovs-vsctl add-br <新的桥接名称>
    ovs-vsctl add-port <新的桥接名称> <物理网卡名称>
    

确保 `<新的桥接名称>` 与系统中现有的任何接口名称不冲突。

### 5\. 检查 IP 地址配置

在创建新的桥接后，不要忘记配置 IP 地址：

    ip addr add <IPv4地址>/24 dev <新的桥接名称>
    ip link set <新的桥接名称> up
    route add default gw <网关地址> dev <新的桥接名称>
    

### 6\. 重启网络服务

配置完成后，重启网络服务：

    systemctl restart networking
    

或者，如果您使用的是 NetworkManager：

    systemctl restart NetworkManager
    

### 7\. 验证配置

最后，验证新的配置是否工作：

    ping <外部地址>
    

如果上述步骤不能解决问题，可能需要检查 OVS 的日志文件 `/var/log/openvswitch/ovs-vswitchd.log` 来查找更详细的错误信息。此外，确认您的系统是否安装了最新的 OVS 版本，因为旧版本可能包含已知的错误或兼容性问题。