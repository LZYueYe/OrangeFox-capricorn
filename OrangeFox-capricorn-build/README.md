# OrangeFox Recovery for Xiaomi 5s (capricorn)

这是小米5s (capricorn) 的OrangeFox Recovery自动编译仓库。

## 使用方法

### 方法一：Fork到GitHub自动编译（推荐）

1. **注册GitHub账号**（如果没有的话）：https://github.com/signup
2. **Fork这个仓库**：点击右上角的 "Fork" 按钮
3. **进入Actions页面**：在你Fork的仓库中，点击顶部的 "Actions" 标签
4. **启用工作流**：如果出现提示，点击 "I understand my workflows, go ahead and enable them"
5. **运行编译**：
   - 点击左侧的 "Build OrangeFox Recovery for Xiaomi 5s (capricorn)"
   - 点击右侧的 "Run workflow" 按钮
   - 选择build variant（默认eng即可）
   - 点击绿色的 "Run workflow" 按钮
6. **等待编译完成**：大约需要1-2小时
7. **下载结果**：
   - 编译完成后，点击对应的运行记录
   - 在页面底部的 "Artifacts" 部分，点击 "OrangeFox-capricorn-recovery" 下载
   - 解压后得到 recovery.img 文件

### 方法二：本地编译

如果你想在本地编译，请确保：
- Ubuntu 20.04/22.04
- 至少16GB内存
- 至少50GB磁盘空间
- 2核以上CPU

然后运行：
```bash
mkdir ~/fox && cd ~/fox
curl -s https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
export PATH=~/bin:$PATH
repo init -u https://gitlab.com/OrangeFox/manifest.git -b fox_9.0
repo sync -c -j$(nproc --all)
# 把device/xiaomi/capricorn复制到对应位置
source build/envsetup.sh
lunch omni_capricorn-eng
mka recoveryimage
```

## 刷入方法

编译完成后，得到 recovery.img 文件：

### 临时启动验证（不修改系统）
```bash
fastboot boot recovery.img
```

### 正式刷入
```bash
fastboot flash recovery recovery.img
fastboot reboot recovery
```

## 设备信息

- 设备：小米5s (Mi 5s)
- 代号：capricorn
- 芯片：高通骁龙821 (MSM8996)
- 架构：arm64
- 分辨率：1080x1920
- Android版本：9 (Pie)
- Recovery版本：OrangeFox R11.1 (fox_9.0分支)

## 注意事项

- 编译需要较长时间，请耐心等待
- 确保bootloader已解锁
- 刷入前请备份重要数据
- 如果遇到问题，请查看Actions的日志
