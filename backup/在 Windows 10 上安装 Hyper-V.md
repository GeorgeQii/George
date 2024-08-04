以下是将提供的信息转换为Markdown格式：

### 在 Windows 10 上安装 Hyper-V

#### 检查要求

*   **操作系统**：Windows 10 企业版、专业版或教育版
*   **硬件**：
    *   64 位处理器，支持二级地址转换 (SLAT)
    *   支持 VM 监视器模式扩展（Intel CPU 的 VT-c 技术）
    *   最少 4 GB 内存
*   **注意事项**：不支持在 Windows 10 家庭版上安装 Hyper-V 角色。如需安装，应从 Windows 10 家庭版升级到专业版。

#### 使用 PowerShell 启用 Hyper-V

1.  **以管理员身份打开 PowerShell 控制台**。
2.  **运行以下命令**：
    
        Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
        
    
    如果无法找到此命令，请确保以管理员身份运行 PowerShell。
3.  **安装完成后，请重启**。

#### 使用 CMD 和 DISM 启用 Hyper-V

1.  **以管理员身份打开 PowerShell 或 CMD 会话**。
2.  **键入以下命令**：
    
        DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V
        
    

#### 通过“设置”启用 Hyper-V 角色

1.  **右键单击 Windows 按钮并选择“应用和功能”**。
2.  **选择相关设置下右侧的“程序和功能”**。
3.  **选择“打开或关闭 Windows 功能”**。
4.  **选择“Hyper-V”，然后单击“确定”**。

#### 完成安装

安装完成后，系统会提示你重新启动计算机。