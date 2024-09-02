`ReentrantLock` 是 Java 中的一个同步锁工具，提供了与 `synchronized` 相似的同步功能，但更加灵活和功能丰富。它是 `java.util.concurrent.locks` 包中的一部分，提供了显式的锁操作。

### `ReentrantLock` 与 `synchronized` 的区别：

1. **锁的获取和释放控制**：
    - `ReentrantLock` 提供了显式的锁获取和释放方法（`lock()` 和 `unlock()`），而 `synchronized` 的锁获取和释放是隐式的，由 JVM 控制。

2. **等待可中断**：
    - 使用 `ReentrantLock` 时，等待锁的线程可以响应中断（使用 `lockInterruptibly()` 方法），而 `synchronized` 不支持中断等待锁的线程。

3. **公平性选择**：
    - `ReentrantLock` 可以设置为公平锁（等待时间最长的线程优先获得锁），而 `synchronized` 不保证这种公平性。

4. **锁投票**：
    - `ReentrantLock` 提供了 `tryLock()` 方法，允许线程尝试获取锁但不会无限期等待，`synchronized` 没有这样的功能。

5. **条件变量支持**：
    - `ReentrantLock` 支持条件变量（`Condition`），允许线程分组等待或接收特定条件的通知，而 `synchronized` 只有基于对象的等待/通知机制。
    
6. **性能差异**：
    - 在 JDK 1.6 之后，`synchronized` 的性能得到了显著提升，使得两者在性能上的差异不再显著。

`ReentrantLock` 提供了比 `synchronized` 更细粒度的锁控制和更丰富的功能，但使用起来也更复杂。选择哪一个通常取决于具体的应用场景和对功能的需求。