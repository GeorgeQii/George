在安装 Windows 11 时，系统会检查你的 CPU 是否受支持。如果你的 CPU 不在支持列表中，你可以通过编辑注册表来绕过这一检查。以下是详细的步骤：

### 步骤 1: 打开注册表编辑器
1. 点击开始菜单。
2. 在搜索框中输入 `regedit`。
3. 点击 `Enter` 键或选择 `regedit` 应用程序以启动注册表编辑器。

### 步骤 2: 导航到 MoSetup 键
1. 在注册表编辑器中，使用左侧的树状目录导航到以下路径：
   ```
   Computer\HKEY_LOCAL_MACHINE\SYSTEM\Setup\MoSetup
   ```

### 步骤 3: 创建新的 DWORD 值
1. 在 `MoSetup` 键下，右键点击空白区域。
2. 选择 `New` > `DWORD (32-bit) Value`。
3. 将新创建的值命名为 `AllowUpgradesWithUnsupportedTPMOrCPU`。

### 步骤 4: 修改值数据
1. 双击你刚刚创建的 `AllowUpgradesWithUnsupportedTPMOrCPU` 值。
2. 在弹出的编辑窗口中，将 `Value data` 设置为 `1`。
3. 确保 `Base` 选择的是 `Hexadecimal`（十六进制）。

### 步骤 5: 保存并关闭
1. 点击 `OK` 保存更改。
2. 关闭注册表编辑器。

### 注意事项
- 编辑注册表之前，请确保你已经备份了注册表，以防万一需要恢复。
- 绕过 CPU 检查可能会带来兼容性问题，建议在了解风险的情况下进行。
- 这种方法并不保证 Windows 11 能够完全正常运行，因为可能还有其他硬件或软件兼容性问题。

### 步骤 6: 开始安装 Windows 11
现在，你可以尝试安装 Windows 11，注册表的修改应该允许安装过程继续，即使 CPU 不在官方支持列表中。

请按照这些步骤操作，如果你遇到任何问题，可以查看微软的官方文档或寻求专业帮助。
