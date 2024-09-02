`@SpringBootApplication` 是一个方便的注解，它包括了 Spring Boot 的三个核心注解：

1. `@SpringBootConfiguration`：标记类为配置类，等同于 Spring 的 `@Configuration`。
2. `@EnableAutoConfiguration`：启用 Spring Boot 的自动配置机制。
3. `@ComponentScan`：自动扫描和加载符合条件的组件或服务。

关于自动装配，它是 Spring Boot 提供的一种机制，用于自动配置应用程序。当你添加了 `@EnableAutoConfiguration` 或 `@SpringBootApplication` 注解，Spring Boot 会自动根据你添加的依赖（比如数据库、Web 框架等）配置项目。它主要通过条件注解（如 `@ConditionalOnClass`）判断哪些配置应该在特定的条件下创建，从而减少手动配置的需要。简单来说，就是根据项目中的依赖，Spring Boot 自动帮你配置好了需要的组件。