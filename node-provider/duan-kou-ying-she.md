# 配置端口映射

* 配置 Ingress 端口映射

通过防火墙配置端口映射，将公共 IP 的80和443端口将映射到 Ingress-nginx Controller 服务所在节点的内网80端口。

* 配置 api-server 端口映射

通过防火墙配置端口映射，将公共 IP 的6443端口映射到 api-server 服务所在的 Master 及节点，并通过白名单限制可访问该集群的 IP 。

