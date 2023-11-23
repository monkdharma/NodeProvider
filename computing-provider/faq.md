# FAQ

使用本指南解决加入节点提供商出现的问题。

#### Pod 无法调度 GPU 资源

在 kubernetes control-plane 节点查看 Pod 事件日志

```
kubectl describe pod <POD_NAME>
```

如果 Events 事件中存在 `0/1 nodes are available: 1 Insufficient [nvidia.com/gpu.`] 类似的信息，请检查 **docker** 或 **containerd** 容器运行时的配置文件中 `default_runtime` 是否为 `nvidia`。

```
# docker config /etc/docker/daemon.json
"default-runtime": "nvidia",

# containerd config /etc/containerd/config.toml
default_runtime_name = "nvidia"
```

然后重启 docker 或 containerd 重新创建 Pod。

