# 性能测试

在正式成为节点提供商之前应进行相关性能测试。

然后，您可以输入以下命令启动 gpu-burn 对 GPU 进行测试：

```
docker run --rm --gpus all gshaibi/gpu-burn -d 36000
```

您还应该验证您的内存、CPU 和磁盘是否足够完成任务。您可以输入以下命令启动 stress-ng 对 CPU 和 Memory 进行测试:

* 开启4个进程分配内存，每次分配20GB内存，保持180秒后释放，180秒后退出。

```
docker run -it --rm podwise/stress-ng:latest --vm 4 --vm-bytes 20G --vm-hang 180 --timeout 180s
```

* 开启6个CPU进程执行sqrt计算，180秒后结束

```
docker run -it --rm podwise/stress-ng:latest --cpu 6 --timeout 180s
```

* 压测磁盘io，开启5个磁盘IO进程，每次写20GB数据到磁盘，180秒后退出

```
docker run -it --rm podwise/stress-ng:latest --hdd 5 --hdd-bytes 20G --timeout 180s
```

\
\
