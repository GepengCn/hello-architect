
Spring MVC 是一个遵循 MVC（Model-View-Controller）设计模式的 Java Web 框架。其核心组件包括 Controller（处理用户请求和业务逻辑）、View（负责渲染结果的页面，如 JSP 或 Thymeleaf）和 Model（用于在 Controller 和 View 之间传递数据）。

工作原理的执行流程如下：

1. `DispatcherServlet`（前端控制器）接收 HTTP 请求。
2. `HandlerMapping` 确定请求由哪个 Controller 处理。
3. `DispatcherServlet` 调用相应的 Controller。
4. Controller 处理请求，执行业务逻辑，并返回模型和视图名。
5. `ViewResolver` 解析视图名，找到对应的 View。
6. View 使用模型数据进行渲染。
7. 渲染后的视图返回给客户端。
