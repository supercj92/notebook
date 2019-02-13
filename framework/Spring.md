bean初始化先后顺序：
Constructor > @PostConstruct > InitializingBean > init-method
CommonAnnotationBeanPostProcessor来处理@PostConstruct注解

beanPostProcessor > afterPropertySet > customInit
AbstractAutowireCapableBeanFactory.initializeBean()执行流程在这里

定位、加载、解析resource
AbstractBeanDefinitionReader.loadBeanDefinitions()

解析xml <bean/>生成beanDefinition
BeanDefinitionParserDelegate.parseBeanDefinitionElement()

注册beanDefinition
DefaultListableBeanFactory.registerBeanDefinition()

-------------------------依赖注入 getBean-----------------------

创建bean实例，自定义初始化逻辑
AbstractBeanFactory.doGetBean()

依赖注入入口
DefaultListableBeanFactory.getBean()
依赖注入
AbstractAutowireCapableBeanFactory.populateBean()
属性注入
BeanDefinitionValueResolver.resolveValueIfNecessary()
实际注入发生
AbstractNestablePropertyAccessor.setPropertyValue()

创建bean实例
AbstractAutowireCapableBeanFactory.createBean()
实际创建实例
AbstractAutowireCapableBeanFactory.createBeanInstance()
jdk反射、cglib两种实例化策略
SimpleInstantiationStrategy.instantiate()

bean的生命周期
初始化bean，调用init-method、后处理器、aware
AbstractAutowireCapableBeanFactory.initializeBean()

通过factoryBean获取bean
AbstractBeanFactory.getObjectForBeanInstance()

处理lazy-init入口
AbstractApplicationContext.finishBeanFactoryInitialization()
实际处理
DefaultListableBeanFactory.preInstantiateSingletons()

处理注解的processor
AnnotationConfigUtils.registerAnnotationConfigProcessors()

Spring容器启动步骤：
一、BeanDefinition的Resource定位
二、BeanDefinition载入和解析
三、BeanDefinition在IOC容器中的注册
四、IOC容器的依赖注入

单例bean实例：
org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.singletonObjects

处理@ Configuration注解的bean
org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors() ->
org.springframework.context.annotation.ConfigurationClassPostProcessor.postProcessBeanDefinitionRegistry


BeanPostProcessor的注册
org.springframework.context.support.AbstractApplicationContext.registerBeanPostProcessors

BeanPostProcessor的执行
org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyBeanPostProcessorsBeforeInitialization

BeanFactoryPostProcessor的执行
org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors
