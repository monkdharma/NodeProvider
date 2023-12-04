# 先决条件

### 软件规格 <a href="#hpaxl" id="hpaxl"></a>

* Ubuntu 22.04&#x20;
* 能够通过 SSH 远程连接
* 所有 GPU 节点[安装 NVIDIA 驱动](https://ubuntu.com/server/docs/nvidia-drivers-installation)

### 最低硬件规格 <a href="#lpzfz" id="lpzfz"></a>

在成为提供商之前，您需要了解一些必需的资源：

* GPU 显卡要求
  * 低配置：3090 或 4090 提供1台或多台拥有4个 GPU 的服务器。
  * 高配置：H100 或 A100 单机 8显卡机器，提供一台或多台。
* 静态的公共 IP 支持
* 200MB 的双向互联网速度。
  * 从这里测试您的互联网速度：[https://www.speedtest.net](https://www.speedtest.net)
* 每个 GPU 有 4 个逻辑核心 + 2 个用于系统操作。
* 你的内存大小至少应等于所有 GPU 的总虚拟内存（vRAM）+ 4GB 用于系统操作。
  * 推荐使用 1TB 或更大容量的内存，适用于8个 80GB vRAM 的 GPU 配置。
* 每个 GPU 至少需要1 TB 的 NVME 存储，2 TB 更佳。
