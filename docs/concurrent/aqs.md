### AQS（AbstractQueuedSynchronizer）

AQS 是 Java 并发包中的一个核心抽象类，用于构建锁或其他同步组件。

#### 原理
AQS 使用一个 int 类型的变量表示同步状态，并通过内置的 FIFO 队列来管理多个线程的阻塞和唤醒。子类通过继承 AQS 并实现其方法来管理其同步状态。

### Semaphore（信号量）

Semaphore 是一个计数信号量，用于控制同时访问某个特定资源的操作数量。

#### 原理
Semaphore 内部使用 AQS 来实现。它维护一个许可集，线程可以通过 `acquire()` 方法获取许可，通过 `release()` 方法释放许可。

### CountDownLatch（倒计时锁存器）

CountDownLatch 允许一个或多个线程等待一系列指定操作的完成。

#### 原理
CountDownLatch 使用 AQS 实现。它维护一个计数器，该计数器被初始化为一个正数，表示需要等待的事件数量。`countDown()` 方法减少计数器，`await()` 方法等待计数器达到零。

#### 使用场景
我曾在初始化应用时使用 CountDownLatch，等待多个初始化任务完成后再继续执行。

### CyclicBarrier（循环屏障）

CyclicBarrier 允许一组线程相互等待，直到所有线程都到达某个公共屏障点。

#### 原理
CyclicBarrier 使用 ReentrantLock 和 Condition 实现。线程到达后调用 `await()`，当所有线程都到达后，屏障开放，所有等待线程被释放。

当然，让我们通过一些示例来更好地理解 Semaphore、CountDownLatch 和 CyclicBarrier 的用法：

### Semaphore 示例

```java
Semaphore semaphore = new Semaphore(3); // 最多允许3个线程同时执行

// 在多个线程中获取许可
semaphore.acquire(); // 获取一个许可
try {
    // 执行任务
} finally {
    semaphore.release(); // 释放许可
}
```

### CountDownLatch 示例

```java
CountDownLatch latch = new CountDownLatch(3); // 需要3个事件完成

// 在三个线程中分别执行事件
new Thread(() -> {
    // 执行任务
    latch.countDown(); // 完成一个事件
}).start();

// 主线程等待所有事件完成
latch.await();
// 继续执行
```

### CyclicBarrier 示例

```java
CyclicBarrier barrier = new CyclicBarrier(3, () -> {
    // 当所有线程都到达屏障时执行的操作
    System.out.println("所有线程已到达屏障");
});

// 在三个线程中
for(int i = 0; i < 3; i++) {
    new Thread(() -> {
        // 执行任务
        barrier.await(); // 等待其他线程
        // 继续执行
    }).start();
}
```

这些示例展示了如何在 Java 中创建和使用 Semaphore、CountDownLatch 和 CyclicBarrier，以控制线程的并发行为。