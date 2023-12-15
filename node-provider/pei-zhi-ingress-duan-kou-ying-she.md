# 配置 Ingress 端口映射

* 配置端口映射

选项1：通过硬件防火墙配置端口映射，将 80 和 443 端口映射到 Ingress-nginx Controller 服务所在节点的内网80端口。

选项2：将公共静态 IP 配置在运行 Ingress-nginx Controller 的节点，注意这样会存在风险请做好安全防范。
