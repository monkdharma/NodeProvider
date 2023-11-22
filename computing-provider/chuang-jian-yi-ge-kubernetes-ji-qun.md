# 创建一个 Kubernetes 集群

### STEP 1 - 先决条件 <a href="#q7ans" id="q7ans"></a>

本指南中的 Kubernetes 指令适用于具有以下技能和知识的受众。

* 服务器管理技能 - 具备一定的 Linux 操作知识和网络知识。
* Kubernetes 经验 - 强烈建议具备基本的 Kubernetes 管理技能。
* Kubernetes 版本应为 v1.27.0+。

### STEP 2 - 构建 Kubernetes 集群 <a href="#kfddd" id="kfddd"></a>

> NOTE - 使用 kubespray 构建 Kubernetes 集群，您无需预先在每个节点安装 Container RunTime。
>
> 我们推荐使用 Docker 因为它在使用上更加简单容易上手。

要创建一个 Kubernetes 集群，您可以使用像 kubespray 这样的部署工具。您可以按照以下步骤进行：

* [Kubespray Quick Start](https://github.com/kubernetes-sigs/kubespray)

如果您只有一个主机，希望运行一个 **all-in-one** 节点，无需额外配置，您可以正常创建 Pods。&#x20;

此外，如果您希望有一个独立的 **kube\_control\_plane** 节点，并且不希望此节点成为工作节点，您还需要修改 `inventory/mycluster/hosts.yaml` 以从 kube\_node 中删除该节点。

### STEP 3 - 安装 NVIDIA 插件 <a href="#qfp0u" id="qfp0u"></a>

#### 安装 NVIDIA Container Toolkit <a href="#rxq4w" id="rxq4w"></a>

> NOTE - 本节中的步骤应在托管 GPU 资源的所有 Kubernetes 节点上完成。

* [Installing the NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#nvidia-drivers)

#### 安装 NVIDIA GPU Operator <a href="#ihbbj" id="ihbbj"></a>

* [**Install NVIDIA GPU Operator**](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)

### STEP 4 - 安装 Ingress-nginx Controller <a href="#hclpq" id="hclpq"></a>

ingress-nginx 是一个用于 Kubernetes 的 Ingress 控制器，使用 NGINX 作为反向代理和负载均衡器。您可以运行以下命令进行安装：

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.2/deploy/static/provider/cloud/deploy.yaml
```

如果您已正确安装，可以通过以下命令查看：

```
kubectl get pods -n ingress-nginx
```

### STEP 5 - 安装 OpenKruise <a href="#uk1d4" id="uk1d4"></a>

OpenKruise is an extended component suite for Kubernetes, which mainly focuses on automated management of large-scale applications, such as _deployment, upgrade, ops and availability protection_.

Most features provided by OpenKruise are built primarily based on CRD extensions. They can work in pure Kubernetes clusters without any other dependencies.

* [Getting Started](https://openkruise.io/docs/installation/)

### STEP 6 - 维护 Kubernetes 集群 <a href="#mv9os" id="mv9os"></a>

#### 添加节点 <a href="#p9kjr" id="p9kjr"></a>

You may want to add worker, control plane or etcd nodes to your existing cluster. This can be done by re-running the cluster.yml playbook, or you can target the bare minimum needed to get kubelet installed on the worker and talking to your control planes. This is especially helpful when doing something like autoscaling your clusters.

* Add the new worker node to your inventory in the appropriate group (or utilize a [dynamic inventory](https://docs.ansible.com/ansible/latest/user\_guide/intro\_inventory.html)).
* Run the ansible-playbook command, substituting cluster.yml for scale.yml:

```
ansible-playbook -i inventory/mycluster/hosts.yml scale.yml -b -v \   --private-key=~/.ssh/private_key
```

#### 删除节点 <a href="#e2lpp" id="e2lpp"></a>

You may want to remove **control plane**, **worker**, or **etcd** nodes from your existing cluster. This can be done by re-running the remove-node.yml playbook. First, all specified nodes will be drained, then stop some kubernetes services and delete some certificates, and finally execute the kubectl command to delete these nodes. This can be combined with the add node function. This is generally helpful when doing something like autoscaling your clusters. Of course, if a node is not working, you can remove the node and install it again.

Use `--extra-vars "node=<nodename>,<nodename2>"` to select the node(s) you want to delete.

```
ansible-playbook -i inventory/mycluster/hosts.yml remove-node.yml -b -v \ --private-key=~/.ssh/private_key \ --extra-vars "node=nodename,nodename2"
```

If a node is completely unreachable by ssh, add `--extra-vars reset_nodes=false` to skip the node reset step. If one node is unavailable, but others you wish to remove are able to connect via SSH, you could set `reset_nodes=false` as a host var in inventory.

#### 删除集群 <a href="#amtil" id="amtil"></a>

Clean up old Kubernetes cluster with Ansible Playbook - run the playbook as root

The option `--become` is required, as for example cleaning up SSL keys in /etc/,

uninstalling old packages and interacting with various systemd daemons.

Without `--become` the playbook will fail to run!

And be mind it will remove the current kubernetes cluster (if it's running)!

```
ansible-playbook -i inventory/mycluster/hosts.yaml  --become --become-user=root reset.yml
```
