Spring Bean 的作用域主要有以下几种：

1. **Singleton**：默认作用域，每个 Spring 容器中只有一个 Bean 实例。
2. **Prototype**：每次请求都会创建一个新的 Bean 实例。
3. **Request**：每次 HTTP 请求都会创建一个新的 Bean，仅在 web 应用中有效。
4. **Session**：在一个 HTTP Session 中，一个 Bean 对应一个实例，仅在 web 应用中有效。
5. **Application**：在一个 ServletContext 中，一个 Bean 对应一个实例，同样仅在 web 应用中有效。
6. **WebSocket**：在 WebSocket 生命周期内，一个 Bean 对应一个实例，仅在 web 应用中有效。

Bean 的生命周期大致可以分为以下几个阶段：

1. **实例化**：创建 Bean 实例。
2. **属性赋值**：注入属性和依赖。
3. **初始化**：调用 Bean 的初始化方法，如使用 `@PostConstruct` 注解或 `init-method` 指定的方法。
4. **使用**：Bean 可以被使用了。
5. **销毁**：容器关闭时，调用 Bean 的销毁方法，如使用 `@PreDestroy` 注解或 `destroy-method` 指定的方法。

在这个过程中，可以通过实现特定的接口（如 `InitializingBean`, `DisposableBean`）或定义自定义的初始化和销毁方法来自定义 Bean 的行为。