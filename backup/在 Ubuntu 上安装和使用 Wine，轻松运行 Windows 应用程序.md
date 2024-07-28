### 在 Ubuntu 上安装和使用 Wine，轻松运行 Windows 应用程序

#### 更新日期：2024-07-028

#### 分类：Linux

**Wine 9.5**

Wine（也称为 WineHQ）是一个关键的 Windows 兼容层，允许在类 Unix 操作系统（例如 Linux）上高效运行 Windows 应用程序，无需安装双系统或使用虚拟机。通过本文的指南，你将了解如何在 Ubuntu 系统上安装和配置 Wine，以运行各种 Windows 应用程序，包括办公软件、图形工具和游戏等。

**步骤 1：准备工作**

确保系统已更新，并简化安装过程。启用 32 位系统架构支持，以确保与大多数游戏和应用的兼容性。

    sudo apt update && sudo apt upgrade
    sudo apt install dirmngr ca-certificates software-properties-common apt-transport-https curl -y
    sudo dpkg --add-architecture i386
    

**步骤 2：添加 WineHQ 软件源**

导入 GPG 密钥并添加官方软件源，以便获取最新的稳定版本。

    curl -s https://dl.winehq.org/wine-builds/winehq.key | sudo gpg --dearmor | sudo tee /usr/share/keyrings/winehq.gpg > /dev/null
    echo deb [signed-by=/usr/share/keyrings/winehq.gpg] http://dl.winehq.org/wine-builds/ubuntu/ $(lsb_release -cs) main | sudo tee /etc/apt/sources.list.d/winehq.list
    sudo apt update
    

**步骤 3：通过 APT 安装 Wine**

从 WineHQ 安装最新稳定版的 Wine，推荐此方法以获取更可靠的版本。

    sudo apt install --install-recommends winehq-stable
    

**检查 Wine 版本**

安装完成后，验证 Wine 的版本。

    wine --version
    

**初始化 Wine 环境**

配置 Mono 等环境以运行 .NET 应用程序。

    winecfg
    

**安装 Winetricks**

Winetricks 是一个辅助脚本，用于轻松安装和管理 Windows 应用程序和库。

    sudo apt install winetricks -y
    

**使用 Winetricks 安装组件**

安装 Visual C++ 运行库、字体和 DirectX 等组件以提升兼容性和游戏性能。

    winetricks vcrun2022
    winetricks allfonts corefonts cjkfonts
    winetricks d3dx9 d3dx10 d3dx11
    

**运行 Windows 应用程序**

右键点击 Windows 应用程序文件，选择“使用其它程序打开”，然后选择 Wine。

**安装 Notepad++ 示例**

下载 Notepad++ 安装文件，右键选择使用 Wine 运行。

**管理 Wine 环境**

创建自定义 Wine 环境或配置 32 位应用支持。

    WINEPREFIX=~/.custom_wine_prefix winecfg
    

**配置中文支持**

在 Wine 前缀设置中添加 LC\_ALL=zh\_CN.UTF-8 参数。

**浏览 Wine 应用程序数据库**

访问 Wine AppDB 获取有关应用程序兼容性和优化配置的实用信息。

**常见问题解答**

*   解决中文乱码和方框问题：确保安装中文字体，并配置 Windows 库和 LC\_ALL 参数。
*   从 Ubuntu 中移除 Wine：卸载 Wine 应用程序、移除 WineHQ 仓库信息和删除 GPG 密钥。

**结论**

通过遵循本文的指南，你将在 Ubuntu 系统上成功安装和配置 Wine，从而运行各种 Windows 应用程序，享受无缝的跨平台体验。