迁移命令：
                ssh -o 'HostKeyAlias=<Target node Name>' root@<Target node IP>
迁移示例：
                ssh -o 'HostKeyAlias=pve3' root@10.99.108.208


根据你提供的输出信息，系统在设置语言环境时仍然存在问题。虽然你已经尝试生成`en_US.UTF-8`语言环境，但似乎没有成功。下面是一些步骤来解决这个问题：

### 1\. 确认已生成语言环境

首先，确保`en_US.UTF-8`语言环境已经被正确生成。运行以下命令查看可用的语言环境：

    locale -a
    

确保输出中包含`en_US.UTF-8`。如果没有，请再次尝试生成：

    sudo locale-gen en_US.UTF-8
    

### 2\. 检查`/etc/default/locale`文件

确保`/etc/default/locale`文件的内容正确。运行以下命令打开文件：

    sudo nano /etc/default/locale
    

确保文件内容如下：

    LANG="en_US.UTF-8"
    LC_ALL="en_US.UTF-8"
    

如果你希望使用中文环境，可以将`LANG`和`LC_ALL`更改为`zh_CN.UTF-8`，但在这种情况下，确保`zh_CN.UTF-8`也已经生成。

### 3\. 重新生成语言环境

如果你在`locale -a`中没有看到`en_US.UTF-8`，可以尝试重新生成所有语言环境：

    sudo dpkg-reconfigure locales
    

在这个过程中，确保选择`en_US.UTF-8`和其他你需要的语言环境。

### 4\. 更新语言环境

完成上述步骤后，运行以下命令更新语言环境：

    sudo update-locale
    

### 5\. 检查系统环境变量

确保系统环境变量没有被其他配置覆盖。可以检查`/etc/environment`文件，确保没有冲突的设置：

    sudo nano /etc/environment
    

确保其内容类似于：

    LANG="en_US.UTF-8"
    LC_ALL="en_US.UTF-8"
    

### 6\. 重启系统或重新登录

为了使更改生效，可以重启系统或注销并重新登录：

    sudo reboot
    

### 7\. 验证更改

重新登录后，再次运行`locale`命令，检查语言环境是否已正确设置：

    locale
    

如果所有的环境变量都显示为`en_US.UTF-8`，那么问题就解决了。

### 其他注意事项

*   如果你希望使用其他语言环境，可以根据需要生成并设置相应的语言环境。
*   确保系统已安装`locales`包，可以使用以下命令安装：

    sudo apt-get install locales
    

通过以上步骤，你应该能够解决语言环境设置的问题。如果还有其他问题，请随时询问！
<!-- ##{"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekTOC.js'></script>"}## -->
