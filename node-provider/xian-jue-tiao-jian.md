# 先决条件

### 软件规格 <a href="#hpaxl" id="hpaxl"></a>

* Ubuntu 22.04&#x20;
* 能够通过 SSH 远程连接&#x20;
* 所有 GPU 节点[安装 NVIDIA 驱动](https://ubuntu.com/server/docs/nvidia-drivers-installation)

### 硬件规格 <a href="#lpzfz" id="lpzfz"></a>

在成为提供商之前，您需要了解一些必需的资源：

* 公共静态 IP&#x20;
* 2G 网络带宽
* &#x20;节点机器要求

#### GPUNet Lite (Lite Version  with 3090/4090)

| **GPU**          | 2x or 4x NVIDIA RTX **3090/4090,** Note: Server must use the same type of GPU card.   |
| ---------------- | ------------------------------------------------------------------------------------- |
| **CPU**          | Dual Socket AMD EPYC™, Recommended: 7543(32C/64T 2.8Ghz), Optionally 7342, 7542, 7742 |
| **Memory**       | 16x 32GB DDR4 ECC RAM or higher                                                       |
| **Storage**      | 4x 1TB NVMe SSD, At least 2,000 MB/s read speed is required                           |
| **Networking**   | <p>Dual Port 10G SFP or BASE-T<br></p>                                                |
| **Power Supply** | 2x 2000W High-efficiency PSUs                                                         |

#### GPUNet Pro (High-Performance Version with A100)

| **GPU**          | 8x NVIDIA A100                                                                                                                                                                                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CPU**          | <p>Dual Socket AMD EPYC™ or Intel Xeon, Recommended: </p><ul><li><strong>AMD EPYC 7003</strong> (Milan) Series Processors with up to 112 cores total</li><li><strong>Intel Xeon 3rd Gen</strong> (Ice Lake) Scalable Processors with up to 80 cores total</li></ul> |
| **Memory**       | 32x 32GB DDR4 ECC RAM or higher                                                                                                                                                                                                                                     |
| **Storage**      | 4x 3.2TB NVMe Mixed Mode (DWPD >= 3) with U.2 or U.3 interface                                                                                                                                                                                                      |
| **Networking**   | Dual Port 10G SFP or BASE-T                                                                                                                                                                                                                                         |
| **Power Supply** | 4x hot-swappable 3000W 80 PLUS Titanium PSUs（2 + 2）                                                                                                                                                                                                                 |

#### GPUNet Pro (High-Performance Version with H100)&#x20;

| **GPU**          | 8x NVIDIA H100                                                                                                                                                                                                                                                                                   |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **CPU**          | <p>Dual Socket AMD EPYC™ or Intel Xeon, Recommended: </p><ul><li><strong>AMD EPYC 7004 &#x26; 9004</strong> (Genoa &#x26; Bergamo) Series Processors with up to 256 cores</li><li>I<strong>ntel Xeon 4th Gen</strong> (Sapphire Rapids) Scalable Processors with up to 192 cores total</li></ul> |
| **Memory**       | 32x 64GB DDR5 ECC RAM or higher                                                                                                                                                                                                                                                                  |
| **Storage**      | 4x 3.2TB NVMe Mixed Mode (DWPD >= 3) with U.2 or U.3 interface                                                                                                                                                                                                                                   |
| **Networking**   | Dual Port 10G SFP or BASE-T                                                                                                                                                                                                                                                                      |
| **Power Supply** | 6x hot-swappable 3000W 80 PLUS Titanium PSUs（3 + 3）                                                                                                                                                                                                                                              |



