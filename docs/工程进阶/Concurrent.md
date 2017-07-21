## 并发技术
在python2中只能使用系统级的进程、子进程和线程并发模式，且异步的网络请求支持也有限。

但如果你使用的是python3.2以上版本，并发有多种解决方案。

- threading
- multiprocessing
- concurrent.futures
- subprocess
- sched
- queue
- **asyncio**

特别是concurrent.futures模块提供了高阶的并发任务模式。

另外queue和multiprocessing这两个队列集合并发也支持高级并发，避免自己要关注资源共享和锁机制，避免出现难以追踪的调试和崩溃造成失去响应。

## 计算密集型并发
概念和示例待进一步补弃

## I/O密集型并发
概念和示例待进一步补弃
