# 燃烧测试

在正式成为节点提供商之前应进行燃烧测试，已验证硬件的稳定性。

这是运行几天燃烧测试的简单指南。

然后，您可以输入以下命令启动 gpu-burn 对 GPU 进行测试：

```
docker run --rm --gpus all gshaibi/gpu-burn -d 36000
```

您还应该验证您的内存、CPU 和磁盘是否足够完成任务。您可以输入以下命令启动 stress-ng 对 CPU 和 Memory 进行测试:

* 开启6个 CPU 进程执行 sqrt 计算，程序将在1天后结束运行

```
docker run -it --rm podwise/stress-ng:latest --cpu 6 --timeout 86400s
```

\
\
