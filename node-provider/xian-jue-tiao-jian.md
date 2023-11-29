# 先决条件

### 软件规格 <a href="#hpaxl" id="hpaxl"></a>

* Ubuntu 20.04 or Ubuntu 22.04 (Ubuntu 22.04 is recommended)
* 能够通过 SSH 远程连接
* 所有 GPU 节点[安装 NVIDIA 驱动](https://ubuntu.com/server/docs/nvidia-drivers-installation)

### 最低硬件规格 <a href="#lpzfz" id="lpzfz"></a>

在成为提供商之前，您需要了解一些必需的资源：

* 公网 IP
* 每个 GPU 有 4 个逻辑核心 + 2 个用于系统操作。
* 你的内存大小至少应等于所有 GPU 的总虚拟内存（vRAM）+ 4GB 用于系统操作。
  * 推荐使用 1TB 或更大容量的内存，适用于8个 80GB vRAM 的 GPU 配置。
* 1TiB 或更多的硬盘空闲空间
* NVIDIA GeForce RTX 30xx and RTX 40xx 系列或更高
*
