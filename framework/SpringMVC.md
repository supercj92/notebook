
框架启动过程、处理http请求过程：

SpringMVC处理请求的流程，实际执行业务逻辑在handle()中

SpringMVC调用业务逻辑入口：
org.springframework.web.method.support.InvocableHandlerMethod.doInvoke

核心：
RequestMappingHandlerAdapter
RequestMappingHandlerMapping