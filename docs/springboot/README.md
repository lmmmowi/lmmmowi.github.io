# SpringBoot启动过程

## 一、构造阶段
1. 推断Web应用类型
2. 加载Spring应用上下文初始化器
3. 加载Spring应用事件监听器
4. 推断应用引导类

## 二、配置阶段（提供Builder模式API）
1. 调整SpringApplication配置
2. 增加SpringApplication配置源
    + @Configuration Class
    + XML
    + package to scan
3. 调整SpringBoot外部化配置

## 三、运行阶段——准备阶段
1. ApplicationArguments
    + 底层使用SimpleCommandLinePropertySource实现
2. SpringApplicationRunListeners
    + EventPublishingRunListener是SpringBoot唯一内建的SpringApplicationRunListener实现，使用SimpleApplicationEventMulticaster发布事件
    + SpringBoot事件：starting、environmentPrepared、contextPrepared、contextLoaded、started、running、failed
3. ConfigurableEnvironment
4. Banner
5. ConfigurableApplicationContext
    + 创建Spring应用上下文：当未指定applicationContextClass时，通过WebApplicationType推断决定应用上下文类型
    + Spring应用上下文运行前准备：
6. SpringBootExceptionReporter

## 四、运行阶段
CommandLineRunner、ApplicationRunner

## Spring事件监听/机制
1. EventObject、EventListener
2. ApplicationEvent、ApplicationListener
3. SmartApplicationListener