`Future` 类在 Java 并发编程中用于表示异步计算的结果。它提供了检查计算是否完成的方法，以及获取计算结果的方法。使用 `Future`，你可以写出非阻塞性的代码，通过这种方式提高程序的响应性。

`Callable` 与 `Future` 的关系在于，`Callable` 是一个返回结果并可能抛出异常的任务，而 `Future` 用于获取 `Callable` 执行的结果。

`CompletableFuture` 是 `Future` 的一个增强版本，提供了更多的功能和灵活性。它不仅可以用于表示异步计算的结果，还允许你以声明式的方式处理异步计算的结果，支持流式操作，组合多个异步操作，处理异步操作的结果和异常等。这使得 `CompletableFuture` 成为构建复杂的异步逻辑和流水线的强大工具。

当然，让我们通过一些示例来更好地理解 `Future`, `Callable` 和 `CompletableFuture` 的用法：

### `Future` 和 `Callable` 示例

```java
ExecutorService executor = Executors.newFixedThreadPool(1);
Callable<String> task = () -> {
    Thread.sleep(1000);
    return "结果";
};

Future<String> future = executor.submit(task);

// 稍后获取结果
try {
    String result = future.get(); // 阻塞直到任务完成
    System.out.println(result);
} catch (InterruptedException | ExecutionException e) {
    e.printStackTrace();
}

executor.shutdown();
```

### `CompletableFuture` 示例

```java
CompletableFuture<String> completableFuture = CompletableFuture.supplyAsync(() -> {
    try {
        Thread.sleep(1000);
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
    return "异步结果";
});

completableFuture.thenAccept(result -> System.out.println(result)); // 非阻塞，结果就绪时执行

// 继续其他任务，不必等待 CompletableFuture 完成
```

这些示例展示了如何在 Java 中创建和使用 `Future`, `Callable` 和 `CompletableFuture`，以实现异步编程和非阻塞性的任务执行。