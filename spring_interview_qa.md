# Spring Framework & Spring Boot - Interview Questions and Answers

> **Prepared for Java Full Stack Interview Preparation**
> Simple English, Deep Answers, Interview-Ready

---

## 1. Spring Framework Core

### Fundamentals

---

**Q1. What is the Spring Framework? Why is it so popular?**

Spring Framework is an open-source Java framework that makes it easier to build enterprise-level Java applications. It was created by Rod Johnson in 2003 and is maintained by Pivotal (now VMware).

Think of it like this: when you build a big Java application, you have to do a lot of "boring" setup work — managing objects, connecting to databases, handling transactions, etc. Spring takes care of all that for you so you can focus on writing your actual business logic.

**Why is it so popular?**
- It reduces a lot of boilerplate code (code that you have to write again and again)
- It follows best practices like Dependency Injection and Separation of Concerns
- It has a huge ecosystem — Spring Boot, Spring Security, Spring Data, Spring MVC, etc.
- It is very flexible — you can use only the parts you need
- Great community support and documentation

**In interview words:** "Spring is a lightweight, non-invasive framework that helps in building loosely coupled, testable, and maintainable Java enterprise applications by providing features like DI, AOP, and transaction management."

---

**Q2. What are the main features and benefits of Spring Framework?**

Main features:
- **Dependency Injection (DI):** Spring manages object creation and their dependencies
- **Aspect-Oriented Programming (AOP):** Helps separate cross-cutting concerns like logging, security
- **Spring MVC:** For building web applications
- **Data Access:** Easy integration with JDBC, JPA, Hibernate
- **Transaction Management:** Declarative transaction handling
- **Security:** Through Spring Security
- **Testing support:** Easy to write unit and integration tests

Benefits:
- Reduces tight coupling between classes
- Makes code more modular and testable
- Less boilerplate code
- Huge community and ecosystem

---

**Q3. What are the different modules in Spring Framework?**

Spring is divided into multiple modules. Important ones are:

| Module | Purpose |
|--------|---------|
| **Spring Core** | IoC container, Dependency Injection |
| **Spring Beans** | Bean factory, bean lifecycle management |
| **Spring Context** | ApplicationContext, events, i18n |
| **Spring AOP** | Aspect-Oriented Programming support |
| **Spring JDBC** | Database access with JDBC |
| **Spring ORM** | Integration with Hibernate, JPA |
| **Spring Web MVC** | Web applications using MVC pattern |
| **Spring WebFlux** | Reactive web programming |
| **Spring Security** | Authentication and Authorization |
| **Spring Test** | Unit and integration testing |

---

**Q4. What is Inversion of Control (IoC)?**

Normally in Java, when Class A needs an object of Class B, Class A itself creates the object:
```java
// Traditional way
class A {
    B b = new B(); // A is controlling the creation
}
```

With IoC, this control is **inverted** — instead of the class creating the object itself, an **external container** (Spring) creates and provides the object.

Simple analogy: Normally you cook your own food (you are in control). With IoC, a restaurant cooks and serves you food (control is inverted — restaurant is in control).

**In interview words:** "IoC is a design principle where the control of creating and managing objects is transferred from the application code to a container (like Spring IoC container). This reduces coupling and makes the code more testable."

---

**Q5. What is Dependency Injection (DI)?**

Dependency Injection is the **implementation** of IoC. When a class needs another object (dependency), instead of creating it, it is **injected** from outside.

Example:
```java
// Without DI
class OrderService {
    PaymentService paymentService = new PaymentService(); // tightly coupled
}

// With DI
class OrderService {
    PaymentService paymentService; // Spring will inject this

    OrderService(PaymentService paymentService) {
        this.paymentService = paymentService; // injected from outside
    }
}
```

**In interview words:** "DI is a pattern where an object's dependencies are provided (injected) by an external entity rather than the object creating them itself. Spring container does this injection automatically."

---

**Q6. What are the types of Dependency Injection in Spring?**

Three types:

1. **Constructor Injection** — dependency is injected through the constructor
```java
@Component
class OrderService {
    private PaymentService paymentService;

    @Autowired
    OrderService(PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

2. **Setter Injection** — dependency is injected through a setter method
```java
@Component
class OrderService {
    private PaymentService paymentService;

    @Autowired
    public void setPaymentService(PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

3. **Field Injection** — dependency is directly injected into the field (most common but not recommended for production)
```java
@Component
class OrderService {
    @Autowired
    private PaymentService paymentService;
}
```

---

**Q7. What is the difference between IoC and DI?**

| IoC | DI |
|-----|-----|
| IoC is a **principle/concept** | DI is an **implementation** of IoC |
| "Control of object creation should be inverted" | "Dependencies should be injected from outside" |
| Broader concept | More specific mechanism |
| Achieved through DI, Service Locator, etc. | One way to achieve IoC |

Simple way to remember: **IoC is the goal, DI is the way to achieve that goal.**

---

**Q8. Explain the Spring IoC Container.**

The Spring IoC Container is the heart of the Spring Framework. It is responsible for:
- Creating objects (beans)
- Configuring them
- Managing their lifecycle
- Injecting dependencies

It reads configuration (XML, annotations, or Java config), creates all the beans, and maintains them. When you ask for a bean, the container gives it to you.

Two main types of containers:
1. **BeanFactory** — basic container
2. **ApplicationContext** — advanced container (recommended)

---

**Q9. What is the difference between BeanFactory and ApplicationContext?**

| Feature | BeanFactory | ApplicationContext |
|---------|-------------|-------------------|
| Basic DI support | Yes | Yes |
| Eager loading of beans | No (lazy by default) | Yes (eager by default) |
| Event publishing | No | Yes |
| Internationalization (i18n) | No | Yes |
| AOP integration | Limited | Full support |
| Annotation support | Limited | Full support |
| MessageSource (i18n) | No | Yes |
| Memory usage | Less | More |

---

**Q10. Which one should you use: BeanFactory or ApplicationContext?**

**Always use ApplicationContext** in real applications.

BeanFactory is only useful when memory is a very serious concern (like embedded systems). For all standard enterprise applications, ApplicationContext is preferred because it provides:
- Automatic bean detection via annotations
- Event handling
- Internationalization support
- AOP support

**Common implementations of ApplicationContext:**
- `ClassPathXmlApplicationContext` — for XML configs on classpath
- `FileSystemXmlApplicationContext` — for XML configs from file system
- `AnnotationConfigApplicationContext` — for Java-based configs
- `WebApplicationContext` — for web applications

---

### Spring Beans

---

**Q11. What is a Spring Bean?**

A Spring Bean is simply a Java object that is managed by the Spring IoC container. When you tell Spring about a class (via annotations or XML), Spring creates an instance of it and manages its lifecycle. That managed instance is called a Bean.

**In interview words:** "Any object whose lifecycle (creation, dependency injection, destruction) is managed by the Spring IoC container is called a Spring Bean."

---

**Q12. What is the lifecycle of a Spring Bean?**

Spring Bean lifecycle has these steps:

1. **Instantiation** — Spring creates the bean object
2. **Populate Properties** — Spring injects dependencies
3. **BeanNameAware** — Spring sets the bean name
4. **BeanFactoryAware** — Spring sets the BeanFactory
5. **Pre-initialization (BeanPostProcessor)** — `postProcessBeforeInitialization()` is called
6. **afterPropertiesSet()** — if bean implements `InitializingBean`
7. **Custom init-method** — your custom `@PostConstruct` or `init-method`
8. **Post-initialization (BeanPostProcessor)** — `postProcessAfterInitialization()` is called
9. **Bean is ready to use**
10. **destroy() / @PreDestroy** — called when container shuts down

Simple version to say in interview: "Bean is created → dependencies are injected → init methods are called → bean is used → destroy methods are called when container closes."

---

**Q13. What are the different bean scopes in Spring?**

| Scope | Description |
|-------|-------------|
| **singleton** | Only ONE instance per Spring container (default) |
| **prototype** | NEW instance every time you request the bean |
| **request** | ONE instance per HTTP request (web apps only) |
| **session** | ONE instance per HTTP session (web apps only) |
| **application** | ONE instance per ServletContext (web apps only) |
| **websocket** | ONE instance per WebSocket session |

---

**Q14. What is the default bean scope in Spring?**

**Singleton** is the default scope. This means Spring creates only one instance of the bean and returns the same instance every time you request it.

---

**Q15. Explain the singleton and prototype bean scopes.**

**Singleton:**
- Only one object is created per Spring container
- Same object is returned every time
- Good for stateless beans (like Service, Repository classes)
```java
@Component // singleton by default
class UserService { }
```

**Prototype:**
- A new object is created every time the bean is requested
- Good for stateful beans
```java
@Component
@Scope("prototype")
class ShoppingCart { }
```

---

**Q16. What is the difference between singleton and prototype scope?**

| Singleton | Prototype |
|-----------|-----------|
| One instance per container | New instance every request |
| Default scope | Must explicitly declare |
| Container manages full lifecycle | Container only manages creation |
| @PreDestroy is called | @PreDestroy is NOT called by container |
| Suitable for stateless beans | Suitable for stateful beans |

---

**Q17. How do you create a Spring Bean?**

Three ways:

1. **Using @Component annotation** (and its variants like @Service, @Repository, @Controller)
```java
@Component
public class MyBean { }
```

2. **Using @Bean in a @Configuration class**
```java
@Configuration
public class AppConfig {
    @Bean
    public MyBean myBean() {
        return new MyBean();
    }
}
```

3. **Using XML configuration**
```xml
<bean id="myBean" class="com.example.MyBean"/>
```

---

**Q18. What is bean wiring in Spring?**

Bean wiring means connecting beans together — telling Spring how beans relate to each other and how to inject one bean into another.

There are two types:
- **Explicit wiring** — you manually define which bean goes where (in XML or @Bean methods)
- **Autowiring** — Spring automatically finds and injects the correct bean

---

**Q19. What is autowiring in Spring?**

Autowiring is when Spring automatically resolves and injects the dependencies of a bean without you explicitly specifying them.

You just put `@Autowired` and Spring finds the matching bean by type and injects it.

```java
@Service
class OrderService {
    @Autowired
    private PaymentService paymentService; // Spring automatically injects this
}
```

---

**Q20. What are the different autowiring modes in Spring?**

In XML-based configuration, there are 4 modes:

| Mode | Description |
|------|-------------|
| **no** | Default — no autowiring, manual wiring required |
| **byName** | Autowire by the property name matching bean name |
| **byType** | Autowire by matching the property type |
| **constructor** | Autowire through constructor by type |

In annotation-based, `@Autowired` works **byType** by default.

---

**Q21. What is the difference between @Autowired and @Inject?**

| @Autowired | @Inject |
|------------|---------|
| Spring-specific annotation | Java standard annotation (JSR-330) |
| Has `required` attribute (default true) | No `required` attribute |
| Part of Spring Framework | Part of Java EE / Jakarta EE |
| Works same way as @Inject | Same behavior |

If you want your code to be portable (not tied to Spring), use @Inject. In practice, most people use @Autowired.

---

**Q22. What is the difference between @Autowired and @Resource?**

| @Autowired | @Resource |
|------------|-----------|
| Spring annotation | Java standard (JSR-250) |
| Injects **by type** first | Injects **by name** first |
| Use @Qualifier to specify name | Has `name` attribute built-in |
| `@Autowired @Qualifier("myBean")` | `@Resource(name="myBean")` |

---

**Q23. What is @Qualifier annotation used for?**

When you have multiple beans of the same type, Spring gets confused about which one to inject. `@Qualifier` helps you specify exactly which bean to use.

```java
@Component("upiPayment")
class UpiPaymentService implements PaymentService { }

@Component("cardPayment")
class CardPaymentService implements PaymentService { }

@Service
class OrderService {
    @Autowired
    @Qualifier("upiPayment") // tell Spring which one to inject
    private PaymentService paymentService;
}
```

---

**Q24. What is @Primary annotation?**

When there are multiple beans of the same type, you can mark one with `@Primary` to make it the default choice. When no `@Qualifier` is specified, Spring will use the `@Primary` bean.

```java
@Component
@Primary // this will be used by default
class UpiPaymentService implements PaymentService { }

@Component
class CardPaymentService implements PaymentService { }
```

---

**Q25. What is constructor injection and setter injection?**

**Constructor Injection:** Dependencies are passed through the constructor.
```java
@Service
class OrderService {
    private final PaymentService paymentService;

    @Autowired
    public OrderService(PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

**Setter Injection:** Dependencies are passed through setter methods.
```java
@Service
class OrderService {
    private PaymentService paymentService;

    @Autowired
    public void setPaymentService(PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

---

**Q26. Which is better: constructor injection or setter injection?**

**Constructor injection is recommended** for most cases. Here's why:

| Constructor Injection | Setter Injection |
|----------------------|-----------------|
| Dependencies are mandatory | Dependencies can be optional |
| Makes the object immutable (use `final`) | Object remains mutable |
| Easier to test (no Spring needed for tests) | Harder to test |
| Fails fast if dependency is missing | Fails later at runtime |
| Recommended by Spring team | Use only for optional dependencies |

**In interview words:** "Constructor injection is preferred because it ensures all required dependencies are provided at creation time, supports immutability, and makes the code easier to test."

---

### Spring Configuration

---

**Q27. What is a Spring configuration file?**

A Spring configuration file tells the Spring container what beans to create, how to configure them, and how to wire them together. There are three ways to provide this configuration:
1. XML file (traditional)
2. Java @Configuration class (modern)
3. Annotations like @Component, @Service (most common today)

---

**Q28. What are the different ways to configure Spring application?**

1. **XML-based configuration** — beans defined in an XML file (old approach)
2. **Java-based configuration** — using @Configuration and @Bean annotations
3. **Annotation-based configuration** — using @Component, @Service, @Repository, @Controller with @ComponentScan

Modern Spring Boot applications mainly use annotation-based and Java-based configurations.

---

**Q29. What is XML-based configuration?**

In XML configuration, you define beans in an XML file called `applicationContext.xml` or similar.

```xml
<beans>
    <bean id="userService" class="com.example.UserService">
        <property name="userRepository" ref="userRepository"/>
    </bean>
    <bean id="userRepository" class="com.example.UserRepository"/>
</beans>
```

This approach is **rarely used now** but you should know it for legacy projects and interviews.

---

**Q30. What is Java-based configuration?**

Using `@Configuration` class with `@Bean` methods to define beans.

```java
@Configuration
public class AppConfig {

    @Bean
    public UserRepository userRepository() {
        return new UserRepository();
    }

    @Bean
    public UserService userService() {
        return new UserService(userRepository()); // injecting dependency
    }
}
```

---

**Q31. What is annotation-based configuration?**

Using annotations like @Component, @Service, @Repository, @Controller to mark classes as beans. Spring auto-detects them using @ComponentScan.

```java
@Service
public class UserService { // Spring automatically creates a bean of this class

    @Autowired
    private UserRepository userRepository; // Spring automatically injects
}
```

---

**Q32. What is @Configuration annotation?**

`@Configuration` tells Spring that "this is a configuration class, treat the @Bean methods inside it as bean definitions."

```java
@Configuration
public class AppConfig {
    @Bean
    public DataSource dataSource() {
        return new HikariDataSource();
    }
}
```

It's like a replacement for the XML config file.

---

**Q33. What is @Bean annotation?**

`@Bean` is placed on a method inside a `@Configuration` class. It tells Spring: "the object returned by this method is a Spring bean — manage it."

```java
@Bean
public UserService userService() {
    return new UserService();
}
```

The method name becomes the bean name by default.

---

**Q34. What is @Component annotation?**

`@Component` is a general-purpose annotation that marks a class as a Spring-managed bean. Spring will automatically detect and register it as a bean during component scanning.

```java
@Component
public class EmailSender { // Spring will create and manage this object }
```

---

**Q35. What is @ComponentScan annotation?**

`@ComponentScan` tells Spring where to look for classes annotated with @Component and its variants. Without this, Spring won't auto-detect your beans.

```java
@Configuration
@ComponentScan(basePackages = "com.example") // scan this package and sub-packages
public class AppConfig { }
```

In Spring Boot, `@SpringBootApplication` includes `@ComponentScan` automatically.

---

**Q36. What is the difference between @Component, @Repository, @Service, and @Controller?**

All four are **functionally the same** — they all mark a class as a Spring bean. But they have different semantic meanings:

| Annotation | Used for | Special behavior |
|------------|----------|-----------------|
| `@Component` | Generic bean | None |
| `@Repository` | DAO / Data access layer | Translates DB exceptions to Spring's `DataAccessException` |
| `@Service` | Business logic layer | None (just semantic clarity) |
| `@Controller` | Web layer / MVC controller | Enables request mapping, returns views |

**In interview words:** "All are specializations of @Component. The main difference is semantic clarity and that @Repository provides automatic exception translation."

---

**Q37. What is the difference between @Component and @Bean?**

| @Component | @Bean |
|------------|-------|
| Class-level annotation | Method-level annotation |
| Auto-detected via component scan | Defined inside @Configuration class |
| Spring creates the object | You create the object in the method |
| Good for your own classes | Good for third-party classes you can't annotate |

**Example:** You can't put @Component on a class from an external library. But you can create a @Bean method that returns an instance of it.

---

**Q38. What is @Value annotation?**

`@Value` is used to inject values from properties files, environment variables, or expressions into Spring beans.

```java
@Component
public class AppConfig {

    @Value("${app.name}")         // from application.properties
    private String appName;

    @Value("${server.port:8080}") // with default value
    private int port;

    @Value("#{2 * 3}")            // SpEL expression
    private int result;
}
```

---

**Q39. What is @PropertySource annotation?**

`@PropertySource` is used to load a specific properties file into the Spring environment.

```java
@Configuration
@PropertySource("classpath:myconfig.properties")
public class AppConfig {
    @Value("${db.url}")
    private String dbUrl;
}
```

In Spring Boot, `application.properties` is automatically loaded, so you often don't need @PropertySource.

---

**Q40. How do you externalize configuration in Spring?**

Externalizing configuration means keeping configuration outside the code so you can change it without recompiling.

Ways to externalize:
1. **application.properties / application.yml** — most common in Spring Boot
2. **@PropertySource** — load custom properties files
3. **Environment variables** — `System.getenv()`
4. **Command-line arguments** — `--server.port=9090`
5. **@ConfigurationProperties** — bind a group of properties to a class

---

### Advanced Core Concepts

---

**Q41. What is lazy initialization in Spring?**

By default, Spring creates all singleton beans eagerly when the container starts. **Lazy initialization** means the bean is created only when it is first requested, not at startup.

This can speed up application startup time when you have many beans that are rarely used.

---

**Q42. What is @Lazy annotation?**

`@Lazy` delays the creation of a bean until it is first needed.

```java
@Component
@Lazy // this bean won't be created until someone requests it
public class HeavyResourceLoader {
    // some heavy initialization
}
```

You can also use it at the injection point:
```java
@Autowired
@Lazy
private HeavyResourceLoader loader;
```

---

**Q43. What are inner beans in Spring?**

Inner beans are beans defined inside another bean definition. They are only used within the outer bean and cannot be accessed from outside.

In XML:
```xml
<bean id="outerBean" class="com.example.Outer">
    <property name="inner">
        <bean class="com.example.Inner"/> <!-- inner bean -->
    </property>
</bean>
```

In Java, it's rarely needed — you just create and return the object inline.

---

**Q44. What is a BeanPostProcessor?**

`BeanPostProcessor` is an interface that allows you to modify or wrap Spring beans **after they are created** but before they are used.

Spring itself uses BeanPostProcessors internally (for @Autowired processing, AOP proxies, etc.).

```java
@Component
public class MyBeanPostProcessor implements BeanPostProcessor {

    @Override
    public Object postProcessBeforeInitialization(Object bean, String beanName) {
        // called before init methods
        return bean;
    }

    @Override
    public Object postProcessAfterInitialization(Object bean, String beanName) {
        // called after init methods — you can return a proxy here
        return bean;
    }
}
```

---

**Q45. What is a BeanFactoryPostProcessor?**

`BeanFactoryPostProcessor` allows you to modify **bean definitions** (configuration metadata) before any beans are instantiated. It operates on the BeanFactory itself.

Example: `PropertySourcesPlaceholderConfigurer` is a BeanFactoryPostProcessor that replaces `${...}` placeholders with actual property values before beans are created.

---

**Q46. What is the difference between BeanPostProcessor and BeanFactoryPostProcessor?**

| BeanPostProcessor | BeanFactoryPostProcessor |
|-------------------|--------------------------|
| Works on **bean instances** | Works on **bean definitions/metadata** |
| Called after bean is created | Called before any bean is created |
| Can modify/wrap the actual bean object | Can modify bean configuration (like property values) |
| One per bean | One per container startup |

---

**Q47. What is ApplicationContext event handling?**

Spring supports an event system where beans can publish and listen to events. This is useful for decoupled communication between beans.

```java
// Publishing an event
@Autowired
private ApplicationEventPublisher publisher;

publisher.publishEvent(new OrderCreatedEvent(this, orderId));

// Listening to an event
@EventListener
public void handleOrderCreated(OrderCreatedEvent event) {
    // handle the event
}
```

---

**Q48. What are the different types of events in Spring?**

Spring provides several built-in events:

| Event | When it fires |
|-------|--------------|
| `ContextRefreshedEvent` | When ApplicationContext is initialized or refreshed |
| `ContextStartedEvent` | When context is started using start() |
| `ContextStoppedEvent` | When context is stopped using stop() |
| `ContextClosedEvent` | When context is closed |
| `RequestHandledEvent` | After an HTTP request is handled (web apps) |

You can also create **custom events** by extending `ApplicationEvent`.

---

**Q49. What is @EventListener annotation?**

`@EventListener` marks a method as an event listener. Spring automatically calls this method when the specified event is published.

```java
@Component
public class OrderEventHandler {

    @EventListener
    public void onOrderCreated(OrderCreatedEvent event) {
        System.out.println("Order created: " + event.getOrderId());
    }

    @EventListener(ContextRefreshedEvent.class)
    public void onApplicationStart() {
        System.out.println("Application started!");
    }
}
```

---

**Q50. What is the difference between Spring and Java EE?**

| Spring | Java EE (Jakarta EE) |
|--------|----------------------|
| Open-source framework | Specification by Oracle/Eclipse |
| Lightweight, flexible | Heavier, more rigid |
| Easy to configure | Complex configuration |
| Has own DI (@Autowired) | Uses CDI for DI |
| Spring Boot for rapid development | No equivalent built-in |
| More popular in modern development | Used in traditional enterprise apps |
| Works with simple Java objects (POJOs) | Relies on heavyweight containers |

**In interview words:** "Spring is a more flexible and developer-friendly alternative to Java EE. Spring Boot especially has made it much faster to build production-ready applications compared to traditional Java EE."

---

## 2. Spring Boot

### Spring Boot Fundamentals

---

**Q51. What is Spring Boot?**

Spring Boot is built on top of Spring Framework. It removes the pain of all the configuration you had to do with Spring. It gives you a ready-to-run application with minimal setup.

Think of it like this: Spring Framework gives you all the ingredients. Spring Boot is like a pre-cooked meal — you just heat it and eat.

**In interview words:** "Spring Boot is an opinionated framework built on top of Spring that simplifies the development of production-ready applications by providing auto-configuration, embedded servers, and starter dependencies."

---

**Q52. What are the advantages of Spring Boot over Spring Framework?**

- **Auto-configuration:** No need to manually configure beans — Spring Boot does it automatically
- **Embedded server:** No need to deploy WAR files — application runs with embedded Tomcat/Jetty
- **Starter dependencies:** One dependency pulls in all related dependencies (e.g., `spring-boot-starter-web`)
- **Production-ready features:** Health checks, metrics via Spring Actuator
- **No XML config:** Pure Java and annotation-based
- **Fast development:** From zero to running app in minutes
- **Opinionated defaults:** Sensible defaults so you spend less time configuring

---

**Q53. What is the difference between Spring and Spring Boot?**

| Spring Framework | Spring Boot |
|-----------------|-------------|
| Requires manual configuration | Auto-configuration |
| No embedded server | Has embedded Tomcat/Jetty |
| Complex setup | Quick setup |
| You manage all dependencies | Starter dependencies manage it |
| Need to deploy WAR to server | Run as standalone JAR |
| More flexible but more work | Opinionated, less work |

---

**Q54. What problem does Spring Boot solve?**

Spring Boot solves the problem of **configuration overhead** in Spring. Earlier, to set up a simple Spring web app, you needed:
- Web.xml
- applicationContext.xml
- DispatcherServlet configuration
- Multiple Maven dependencies (and version conflicts!)
- External Tomcat server setup

Spring Boot eliminates all of this. You add one starter dependency, write your controller, and run — that's it!

---

**Q55. What are the main features of Spring Boot?**

1. **Auto-configuration** — automatically configures beans based on what's on the classpath
2. **Spring Boot Starters** — pre-built dependency bundles
3. **Embedded servers** — Tomcat, Jetty, Undertow built-in
4. **Spring Boot Actuator** — production monitoring (health, metrics, info)
5. **Spring Boot DevTools** — hot reload during development
6. **Externalized configuration** — application.properties / application.yml
7. **Spring Boot CLI** — command-line tool for rapid prototyping
8. **Profiles** — different config for different environments (dev, prod)

---

**Q56. What is auto-configuration in Spring Boot?**

Auto-configuration means Spring Boot automatically creates beans that you would otherwise have to configure manually, based on:
- What dependencies/JARs are on the classpath
- What properties you've set
- What beans you've already defined

Example: If you add `spring-boot-starter-data-jpa` to pom.xml and provide database URL in properties, Spring Boot automatically creates `DataSource`, `EntityManagerFactory`, `TransactionManager` — you don't have to write any configuration!

---

**Q57. How does Spring Boot auto-configuration work?**

It works through this mechanism:

1. `@SpringBootApplication` includes `@EnableAutoConfiguration`
2. Spring Boot scans all JARs for `META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports` file
3. This file lists all auto-configuration classes (like `DataSourceAutoConfiguration`, `WebMvcAutoConfiguration`)
4. Each auto-configuration class uses `@Conditional` annotations to check if it should apply
5. If conditions are met, it creates the relevant beans

Example: `DataSourceAutoConfiguration` runs only if you have a database driver JAR on classpath AND haven't already defined a DataSource bean.

---

**Q58. What is @SpringBootApplication annotation?**

`@SpringBootApplication` is a convenience annotation that combines three annotations:

```java
@SpringBootConfiguration  // same as @Configuration
@EnableAutoConfiguration  // enables auto-configuration
@ComponentScan            // scans current package and sub-packages
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}
```

It's the main annotation you put on your main class.

---

**Q59. What does @EnableAutoConfiguration do?**

`@EnableAutoConfiguration` tells Spring Boot to start adding beans based on what's on the classpath. It triggers the auto-configuration mechanism.

You can exclude specific auto-configurations:
```java
@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class})
```

---

**Q60. What is the difference between @SpringBootApplication and @EnableAutoConfiguration?**

| @SpringBootApplication | @EnableAutoConfiguration |
|------------------------|--------------------------|
| Combination of 3 annotations | Single-purpose annotation |
| Includes @ComponentScan | Does not include @ComponentScan |
| Includes @SpringBootConfiguration | Does not include @Configuration |
| Used on main class | Can be used standalone |
| Recommended | @SpringBootApplication is preferred |

---

### Spring Boot Starters

---

**Q61. What are Spring Boot starters?**

Starters are pre-packaged sets of dependencies. Instead of adding 10 individual dependencies (and worrying about version compatibility), you add one starter.

Example: Instead of adding Jackson, Hibernate Validator, Spring MVC, Tomcat separately — you just add:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
And Spring Boot handles the rest!

---

**Q62. What is spring-boot-starter-parent?**

`spring-boot-starter-parent` is a parent POM that provides:
- Default configurations for Maven plugins
- Dependency management (versions of all libraries are pre-defined)
- Java version settings
- Resource filtering configuration

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>3.2.0</version>
</parent>
```

Using this, you don't need to specify version numbers for Spring-related dependencies — they are inherited.

---

**Q63. What are the most commonly used Spring Boot starters?**

| Starter | Purpose |
|---------|---------|
| `spring-boot-starter-web` | Web apps, REST APIs (includes Tomcat, Spring MVC, Jackson) |
| `spring-boot-starter-data-jpa` | JPA/Hibernate database access |
| `spring-boot-starter-security` | Authentication & Authorization |
| `spring-boot-starter-test` | Testing (JUnit, Mockito, AssertJ) |
| `spring-boot-starter-thymeleaf` | Thymeleaf template engine |
| `spring-boot-starter-mail` | Email sending |
| `spring-boot-starter-cache` | Caching support |
| `spring-boot-starter-actuator` | Production monitoring |
| `spring-boot-starter-validation` | Bean validation (JSR-380) |

---

**Q64. What is spring-boot-starter-web?**

`spring-boot-starter-web` includes everything needed to build web applications and REST APIs:
- Spring MVC (web framework)
- Embedded Tomcat server
- Jackson (JSON serialization/deserialization)
- Hibernate Validator (request validation)

When you add this, your app becomes a web server without any additional configuration.

---

**Q65. What is spring-boot-starter-data-jpa?**

`spring-boot-starter-data-jpa` includes everything for database access using JPA:
- Spring Data JPA
- Hibernate (JPA implementation)
- Spring JDBC
- HikariCP (connection pool)

You just provide the database driver separately (like H2, MySQL, PostgreSQL driver).

---

**Q66. What is spring-boot-starter-test?**

`spring-boot-starter-test` includes everything for testing:
- JUnit 5 (unit testing)
- Mockito (mocking)
- AssertJ (fluent assertions)
- Spring Test (integration testing with @SpringBootTest)
- Hamcrest (matchers)
- JSONAssert (JSON assertions)

---

**Q67. What is spring-boot-starter-security?**

`spring-boot-starter-security` adds Spring Security to your application. When you add it, your entire application is automatically secured — all endpoints require authentication. You then customize the security rules as per your requirements.

---

**Q68. How do Spring Boot starters help in development?**

- **Saves time:** No need to search for compatible library versions
- **No version conflicts:** All versions in a starter are tested to work together
- **Convention over configuration:** Sensible defaults out of the box
- **One dependency instead of many:** Reduces pom.xml complexity

---

**Q69. Can you create your own custom starter?**

Yes! A custom starter is useful when you have common configuration that should be shared across multiple projects in your organization.

Steps to create a custom starter:
1. Create an auto-configuration class with `@Configuration`
2. Use `@Conditional` annotations to control when it applies
3. Register it in `META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports`
4. Package it as a JAR and add to other projects as a dependency

Naming convention: `your-company-spring-boot-starter` (not starting with `spring-boot` which is reserved for official starters)

---

### Spring Boot Configuration

---

**Q70. What is application.properties file?**

`application.properties` is the main configuration file in Spring Boot, placed in `src/main/resources/`. It uses key=value format.

```properties
server.port=8080
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=secret
spring.jpa.show-sql=true
app.name=My Application
```

---

**Q71. What is application.yml file?**

`application.yml` is the YAML-format alternative to `application.properties`. It has a more readable, hierarchical structure.

```yaml
server:
  port: 8080

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
    username: root
    password: secret
  jpa:
    show-sql: true

app:
  name: My Application
```

---

**Q72. What is the difference between application.properties and application.yml?**

| application.properties | application.yml |
|------------------------|-----------------|
| Key-value flat format | Hierarchical YAML format |
| Easy to read for simple configs | Better for complex/nested configs |
| No indentation issues | Indentation-sensitive (can cause bugs) |
| More popular in older projects | Preferred in newer projects |
| Both are supported equally | Both are supported equally |

Both work the same way — it's a matter of preference.

---

**Q73. How do you change the default port in Spring Boot?**

Default port is **8080**. Change it in `application.properties`:

```properties
server.port=9090
```

Or in `application.yml`:
```yaml
server:
  port: 9090
```

Or via command line:
```bash
java -jar myapp.jar --server.port=9090
```

---

**Q74. What are Spring Boot profiles?**

Profiles allow you to have different configurations for different environments like development, testing, and production.

For example:
- In dev: use H2 in-memory database
- In prod: use MySQL database

You can define environment-specific configuration and activate only what you need.

---

**Q75. How do you define different profiles in Spring Boot?**

Create separate properties files for each profile:
- `application.properties` — default
- `application-dev.properties` — for dev profile
- `application-prod.properties` — for prod profile
- `application-test.properties` — for test profile

Or use YAML with `---` separator in one file:
```yaml
# Default
server:
  port: 8080
---
spring:
  config:
    activate:
      on-profile: dev
server:
  port: 8081
---
spring:
  config:
    activate:
      on-profile: prod
server:
  port: 80
```

---

**Q76. How do you activate a specific profile?**

Several ways:

1. **In application.properties:**
```properties
spring.profiles.active=dev
```

2. **Command line:**
```bash
java -jar myapp.jar --spring.profiles.active=prod
```

3. **Environment variable:**
```bash
export SPRING_PROFILES_ACTIVE=prod
```

4. **Programmatically:**
```java
SpringApplication app = new SpringApplication(MyApp.class);
app.setAdditionalProfiles("dev");
app.run(args);
```

---

**Q77. What is @ConfigurationProperties annotation?**

`@ConfigurationProperties` binds a group of related properties from `application.properties` to a Java class. It's cleaner than using multiple `@Value` annotations.

```properties
# application.properties
app.mail.host=smtp.gmail.com
app.mail.port=587
app.mail.username=test@gmail.com
```

```java
@Component
@ConfigurationProperties(prefix = "app.mail")
public class MailProperties {
    private String host;
    private int port;
    private String username;
    // getters and setters
}
```

---

**Q78. What is @Value annotation and how is it used?**

`@Value` injects a single property value into a field. (Already covered in Q38, but here's the Spring Boot context)

```java
@Value("${app.name}")
private String appName;

@Value("${server.port:8080}") // 8080 is default value
private int port;

@Value("#{T(java.lang.Math).PI}") // SpEL expression
private double pi;
```

---

**Q79. How do you override default configuration in Spring Boot?**

Several ways:
1. **application.properties** — simply set the property
2. **Environment-specific properties file** — `application-prod.properties`
3. **Command-line arguments** — highest priority: `--server.port=9090`
4. **Environment variables** — `SERVER_PORT=9090`
5. **@Bean definition** — if you define a bean, auto-configuration backs off

**Priority order (highest to lowest):**
Command line > Environment variables > Profile-specific properties > application.properties > Default values

---

**Q80. What is spring.factories file?**

`spring.factories` (in older Spring Boot) or `AutoConfiguration.imports` (in newer Spring Boot 2.7+) is a file inside `META-INF/spring/` that lists all auto-configuration classes.

Spring Boot reads this file at startup to know which auto-configurations to apply. When you create a custom starter, you register your auto-configuration class here.

---

### Embedded Servers

---

**Q81. What are embedded servers in Spring Boot?**

Instead of packaging your application as a WAR and deploying to an external server like Tomcat, Spring Boot **embeds the server inside your JAR**. So you run: `java -jar myapp.jar` and the server starts automatically.

This makes deployment much simpler — no need to install or configure an external application server.

---

**Q82. What is the default embedded server in Spring Boot?**

**Apache Tomcat** is the default embedded server in Spring Boot (via `spring-boot-starter-web`).

---

**Q83. What are the different embedded servers supported by Spring Boot?**

1. **Apache Tomcat** — default
2. **Jetty** — lightweight alternative
3. **Undertow** — high-performance, non-blocking

---

**Q84. How do you change the embedded server from Tomcat to Jetty?**

1. Exclude Tomcat from `spring-boot-starter-web`
2. Add Jetty starter

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
</dependency>

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jetty</artifactId>
</dependency>
```

---

**Q85. How do you disable the embedded server?**

Use `spring.main.web-application-type=none` in `application.properties`:

```properties
spring.main.web-application-type=none
```

Or programmatically:
```java
SpringApplication app = new SpringApplication(MyApp.class);
app.setWebApplicationType(WebApplicationType.NONE);
app.run(args);
```

This is useful for batch processing applications that don't need a web server.

---

**Q86. Can you deploy a Spring Boot application on an external server?**

Yes! You can:
1. Change packaging from JAR to WAR in pom.xml
2. Extend `SpringBootServletInitializer`
3. Override the `configure` method

```java
@SpringBootApplication
public class MyApp extends SpringBootServletInitializer {

    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
        return builder.sources(MyApp.class);
    }

    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}
```

Then deploy the WAR to Tomcat/WildFly/etc.

---

**Q87. What is the difference between JAR and WAR packaging?**

| JAR | WAR |
|-----|-----|
| Java ARchive | Web ARchive |
| Includes embedded server | Deployed to external server |
| Self-contained runnable | Needs external container |
| `java -jar app.jar` to run | Deploy to Tomcat, JBoss, etc. |
| Preferred for microservices | Used for traditional deployments |
| Spring Boot default | Needs extra configuration |

---

### Spring Boot DevTools

---

**Q88. What is Spring Boot DevTools?**

Spring Boot DevTools is a development-time tool that makes development faster by providing features like automatic restart and live reload. It is only active in development, not in production.

Add to pom.xml:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
```

---

**Q89. What are the features of Spring Boot DevTools?**

1. **Automatic Restart** — application restarts when classpath files change
2. **LiveReload** — browser auto-refreshes when resources change
3. **Property defaults** — disables template caching (good for development)
4. **Remote debugging** — remote application restart support
5. **Global settings** — configure in `~/.spring-boot-devtools.properties`

---

**Q90. What is LiveReload in DevTools?**

LiveReload is a feature where the browser automatically refreshes when you make changes to frontend files (HTML, CSS, JS, templates). You need the LiveReload browser extension installed.

When you save a file, DevTools triggers a browser refresh — no need to manually press F5.

---

**Q91. What is automatic restart in DevTools?**

When you change a Java class and save/rebuild, DevTools automatically restarts the Spring application. This is faster than a full JVM restart because DevTools uses two classloaders:
- **Base classloader** — loads unchanged classes (libraries, etc.)
- **Restart classloader** — loads your code

Only the restart classloader is reloaded, making restart much faster than a full restart.

---

**Q92. How does DevTools improve developer productivity?**

- No need to manually restart server after every change
- Browser auto-refreshes for frontend changes
- Disables template caching so template changes show immediately
- Property defaults set to development-friendly values (e.g., `spring.thymeleaf.cache=false`)
- Remote restart support for remote development

---

### Spring Boot Advanced

---

**Q93. What is @Conditional annotation?**

`@Conditional` allows a bean or configuration to be created **only if a certain condition is true**. Spring Boot uses this heavily in auto-configuration.

```java
@Bean
@Conditional(MyCondition.class)
public MyBean myBean() {
    return new MyBean();
}
```

You create a class implementing `Condition` interface that returns true/false.

---

**Q94. What are the different @Conditional annotations in Spring Boot?**

Spring Boot provides many ready-made conditions:

| Annotation | Condition |
|------------|-----------|
| `@ConditionalOnClass` | Class is present on classpath |
| `@ConditionalOnMissingClass` | Class is NOT on classpath |
| `@ConditionalOnBean` | Bean of type exists in context |
| `@ConditionalOnMissingBean` | Bean does NOT exist in context |
| `@ConditionalOnProperty` | Property has specific value |
| `@ConditionalOnResource` | Resource file exists |
| `@ConditionalOnWebApplication` | Is a web application |
| `@ConditionalOnNotWebApplication` | Is NOT a web application |
| `@ConditionalOnExpression` | SpEL expression is true |

---

**Q95. What is @ConditionalOnClass?**

`@ConditionalOnClass` means: "Create this bean/configuration only if the specified class is present on the classpath."

Used in auto-configuration to avoid errors when a library is not added.

```java
@Configuration
@ConditionalOnClass(DataSource.class) // only if DataSource class is on classpath
public class DataSourceAutoConfiguration {
    // configure datasource
}
```

---

**Q96. What is @ConditionalOnMissingBean?**

`@ConditionalOnMissingBean` means: "Create this bean only if the user hasn't already defined a bean of this type."

This is how Spring Boot auto-configuration **backs off** when you provide your own configuration:

```java
@Bean
@ConditionalOnMissingBean(DataSource.class)
public DataSource defaultDataSource() {
    return new EmbeddedDatabaseBuilder().build(); // only if user hasn't defined their own DataSource
}
```

This is a very important concept — Spring Boot respects your custom beans and doesn't override them.

---

**Q97. What is @ConditionalOnProperty?**

`@ConditionalOnProperty` means: "Create this bean only if a specific property exists and/or has a specific value."

```java
@Bean
@ConditionalOnProperty(name = "feature.email.enabled", havingValue = "true")
public EmailService emailService() {
    return new EmailService();
}
```

In application.properties:
```properties
feature.email.enabled=true
```

---

**Q98. How do you create a custom auto-configuration?**

Steps:
1. Create a configuration class with conditions
```java
@Configuration
@ConditionalOnClass(SomeLibrary.class)
@EnableConfigurationProperties(MyProperties.class)
public class MyAutoConfiguration {

    @Bean
    @ConditionalOnMissingBean
    public MyService myService(MyProperties props) {
        return new MyService(props.getApiKey());
    }
}
```

2. Register it in `src/main/resources/META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports`:
```
com.example.MyAutoConfiguration
```

3. Package as a JAR and use as a dependency in other projects.

---

**Q99. What is the Spring Boot Banner?**

The Spring Boot banner is the ASCII art that is displayed when the application starts. By default, it shows the Spring Boot logo and version.

```
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
...
```

---

**Q100. How do you customize the Spring Boot Banner?**

1. **Custom text banner:** Create `banner.txt` in `src/main/resources/` with your ASCII art
2. **Image banner:** Use `banner.png/jpg` file
3. **Disable banner:**
```properties
spring.main.banner-mode=off
```
4. **Programmatically:**
```java
SpringApplication app = new SpringApplication(MyApp.class);
app.setBannerMode(Banner.Mode.OFF);
```

---

**Q101. What is CommandLineRunner interface?**

`CommandLineRunner` is an interface with a single `run(String... args)` method. If a bean implements this, Spring Boot calls `run()` after the application context is loaded.

It receives command-line arguments as a String array.

```java
@Component
public class StartupRunner implements CommandLineRunner {

    @Override
    public void run(String... args) throws Exception {
        System.out.println("Application started with args: " + Arrays.toString(args));
        // Load data, check connections, etc.
    }
}
```

---

**Q102. What is ApplicationRunner interface?**

Similar to `CommandLineRunner`, but `run()` receives `ApplicationArguments` instead of a String array — giving more control over parsed arguments.

```java
@Component
public class StartupRunner implements ApplicationRunner {

    @Override
    public void run(ApplicationArguments args) throws Exception {
        System.out.println("Option names: " + args.getOptionNames());
        // --name=John → args.getOptionValues("name") returns ["John"]
    }
}
```

---

**Q103. What is the difference between CommandLineRunner and ApplicationRunner?**

| CommandLineRunner | ApplicationRunner |
|-------------------|-------------------|
| `run(String... args)` | `run(ApplicationArguments args)` |
| Raw string array | Parsed ApplicationArguments object |
| Less functionality | Can access option args and non-option args separately |
| Simpler to use | More powerful |

Both are called at the same time (after context loads). You can use `@Order` to control execution order if you have multiple runners.

---

**Q104. How do you execute code at application startup?**

Several ways in Spring Boot:

1. **CommandLineRunner:**
```java
@Bean
public CommandLineRunner startup() {
    return args -> System.out.println("Started!");
}
```

2. **ApplicationRunner:** Similar to above with parsed args

3. **@PostConstruct:** Called after bean creation
```java
@Component
public class MyBean {
    @PostConstruct
    public void init() {
        System.out.println("Bean initialized!");
    }
}
```

4. **ApplicationListener:** Listen to `ApplicationReadyEvent`
```java
@EventListener(ApplicationReadyEvent.class)
public void onReady() {
    System.out.println("App is ready!");
}
```

5. **InitializingBean:** Implement `afterPropertiesSet()` method

---

**Q105. What is @PostConstruct annotation?**

`@PostConstruct` marks a method to be called **after the bean is created and dependencies are injected**, but **before the bean is put into use**.

```java
@Component
public class CacheLoader {

    @Autowired
    private CacheRepository cacheRepository;

    @PostConstruct
    public void loadCache() {
        // At this point, cacheRepository is already injected
        // Safe to use it here
        cacheRepository.loadAll();
        System.out.println("Cache loaded at startup!");
    }
}
```

The opposite is `@PreDestroy` — called just before the bean is destroyed (when container shuts down).

```java
@PreDestroy
public void cleanup() {
    System.out.println("Bean is being destroyed, cleanup resources!");
}
```

---

## Quick Revision Summary

| Topic | Key Point |
|-------|-----------|
| IoC | Control of object creation given to Spring container |
| DI | Dependencies are injected (not created by the class) |
| BeanFactory vs ApplicationContext | Always use ApplicationContext |
| Default Bean Scope | Singleton |
| Constructor vs Setter Injection | Constructor is preferred |
| @Component vs @Bean | Class-level vs method-level; own class vs third-party |
| Spring Boot auto-configuration | Based on classpath + conditions |
| @SpringBootApplication | = @Configuration + @ComponentScan + @EnableAutoConfiguration |
| Default embedded server | Apache Tomcat |
| Profiles | Different config for dev/prod environments |
| CommandLineRunner vs ApplicationRunner | String args vs ApplicationArguments |
| @PostConstruct | Code to run after bean initialization |

---

*All the best for your interview! You've got this! 🚀*
