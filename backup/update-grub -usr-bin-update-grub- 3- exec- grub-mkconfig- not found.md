根据你提供的 `PATH` 环境变量输出，可以看到 `/usr/sbin` 并不在其中。这就是为什么系统无法找到 `grub-mkconfig` 命令的原因。

### 解决方法

你可以通过以下几种方法来解决这个问题：

#### 方法 1：使用完整路径运行命令

如前所述，你可以直接使用完整路径来运行 `grub-mkconfig` 命令：

    /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg
    

#### 方法 2：临时添加 `/usr/sbin` 到 PATH

如果你希望在当前会话中临时添加 `/usr/sbin` 到你的 `PATH`，可以执行以下命令：

    export PATH=$PATH:/usr/sbin
    

然后你就可以直接运行 `grub-mkconfig`：

    grub-mkconfig -o /boot/grub/grub.cfg
    

#### 方法 3：永久添加 `/usr/sbin` 到 PATH

如果你希望每次登录时都能使用 `/usr/sbin`，可以将其添加到你的 shell 配置文件中（例如 `~/.bashrc` 或 `~/.bash_profile`），在文件末尾添加以下行：

    export PATH=$PATH:/usr/sbin
    

然后，运行以下命令使更改生效：

    source ~/.bashrc
    

### 继续更新 GRUB

无论你选择哪种方法，运行完 `grub-mkconfig` 后，请确保再次运行 `update-grub`：

    update-grub
    

这样，你就可以顺利更新 GRUB 配置了。