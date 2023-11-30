# 安装硬件资源导出器

节点资源收集器，用于机器节点的快速接入

**Note:** 此应用程序只能运行在 k8s 集群中

#### 快速开始 <a href="#usercontent-kuai-su-kai-shi" id="usercontent-kuai-su-kai-shi"></a>

1. 通过 helm 快速安装 crd 及对应的 chart

```
helm install podwise-exporter ./podwise-exporter-1.0.0.tgz
```

2. 查看 helm 是否安装成功

```
helm list | grep podwise-exporter
```

3. 查看 exporter 是否均已启动

```
kubectl get daemonset -n podwise-system
```

4. 验证节点数据是否已上报

```
kubectl get nodes.apps.podwise.io
```

5. 卸载 crd 及对应 chart

**Note** 卸载会级联删除已安装的 crd 及创建的 k8s 资源

```
helm uninstall podwise-exporter
```
