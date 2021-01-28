spring官网userguide
https://spring.io/guides/gs/rest-service/
1.spring通过SpringApplication.run(RestServiceApplication.class, args);启动
2.启动后所有的controller映射的http服务可用
```yaml
@GetMapping("/greeting")
	public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name) {
		return new Greeting(counter.incrementAndGet(), String.format(template, name));
	}
```
3.这里返回的greeting对象，会被MappingJackson2HttpMessageConverter转换成json
4.通过springboot注解，根据类路径来添加bean
```yaml
@SpringBootApplication is a convenience annotation that adds all of the following:

@Configuration: 
Tags the class as a source of bean definitions for the application context.

@EnableAutoConfiguration: 
Tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings.
 For example, if spring-webmvc is on the classpath, this annotation flags the application as a web application and activates key behaviors, such as setting up a DispatcherServlet.

@ComponentScan: Tells Spring to look for other components, configurations, and services in the com/example package, letting it find the controllers.

The main() method uses Spring Boot’s SpringApplication.run() method to launch an application. 
Did you notice that there was not a single line of XML? 
There is no web.xml file, either. 
This web application is 100% pure Java and you did not have to deal with configuring any plumbing or infrastructure.
```