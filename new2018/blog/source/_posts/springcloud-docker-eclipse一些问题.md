---
title: springcloud+docker+eclipse一些问题
date: 2018-12-07 02:56:40
tags:
---
#<center>springcloud+docker+eclipse</center>
Application.java代码如下
 
 package com.thoughtmechanix.simpleservice;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.PathVariable;

@SpringBootApplication
@RestController
@RequestMapping(value="hello")
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @RequestMapping(value="/{firstName}/{lastName}",method = RequestMethod.GET)
    public String hello( @PathVariable("firstName") String firstName,
                         @PathVariable("lastName") String lastName) {

        return String.format("{\"message\":\"Hello %s %s\"}", firstName, lastName);
    }
}


ubuntu@linux:~/new2018/git_springcloud/spmia-chapter1$ ls
docker  pom.xml  README.md  simpleservice  target
ubuntu@linux:~/new2018/git_springcloud/spmia-chapter1$ 
项目根目录为spmia-chapter1
在根目录通过以下命令启动docker容器
docker-compose  -f  docker/common/docker-compose.yml up

控制台打印以下，可以看到正常启动springcloud项目
ubuntu@linux:~/new2018/git_springcloud/spmia-chapter1$ docker-compose  -f  docker/common/docker-compose.yml up
Starting common_simpleservice_1 ... done
Attaching to common_simpleservice_1
simpleservice_1  | ********************************************************
simpleservice_1  | Starting simple-service 
simpleservice_1  | ********************************************************
simpleservice_1  | 
simpleservice_1  |   .   ____          _            __ _ _
simpleservice_1  |  /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
simpleservice_1  | ( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
simpleservice_1  |  \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
simpleservice_1  |   '  |____| .__|_| |_|_| |_\__, | / / / /
simpleservice_1  |  =========|_|==============|___/=/_/_/_/
simpleservice_1  |  :: Spring Boot ::        (v1.4.4.RELEASE)
simpleservice_1  | 
simpleservice_1  | 2018-12-06 19:17:04.694  INFO 7 --- [           main] c.t.simpleservice.Application            : Starting Application v0.0.1-SNAPSHOT on df7b33572b9b with PID 7 (/usr/local/simple-service/simple-service-0.0.1-SNAPSHOT.jar started by root in /)
simpleservice_1  | 2018-12-06 19:17:04.697  INFO 7 --- [           main] c.t.simpleservice.Application            : No active profile set, falling back to default profiles: default
simpleservice_1  | 2018-12-06 19:17:04.849  INFO 7 --- [           main] ationConfigEmbeddedWebApplicationContext : Refreshing org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@69663380: startup date [Thu Dec 06 19:17:04 GMT 2018]; root of context hierarchy
simpleservice_1  | 2018-12-06 19:17:08.094  INFO 7 --- [           main] s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat initialized with port(s): 8080 (http)
simpleservice_1  | 2018-12-06 19:17:08.128  INFO 7 --- [           main] o.apache.catalina.core.StandardService   : Starting service Tomcat
simpleservice_1  | 2018-12-06 19:17:08.130  INFO 7 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet Engine: Apache Tomcat/8.5.11
simpleservice_1  | 2018-12-06 19:17:08.440  INFO 7 --- [ost-startStop-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
simpleservice_1  | 2018-12-06 19:17:08.446  INFO 7 --- [ost-startStop-1] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 3625 ms
simpleservice_1  | 2018-12-06 19:17:08.719  INFO 7 --- [ost-startStop-1] o.s.b.w.servlet.ServletRegistrationBean  : Mapping servlet: 'dispatcherServlet' to [/]
simpleservice_1  | 2018-12-06 19:17:08.732  INFO 7 --- [ost-startStop-1] o.s.b.w.servlet.FilterRegistrationBean   : Mapping filter: 'characterEncodingFilter' to: [/*]
simpleservice_1  | 2018-12-06 19:17:08.734  INFO 7 --- [ost-startStop-1] o.s.b.w.servlet.FilterRegistrationBean   : Mapping filter: 'hiddenHttpMethodFilter' to: [/*]
simpleservice_1  | 2018-12-06 19:17:08.734  INFO 7 --- [ost-startStop-1] o.s.b.w.servlet.FilterRegistrationBean   : Mapping filter: 'httpPutFormContentFilter' to: [/*]
simpleservice_1  | 2018-12-06 19:17:08.735  INFO 7 --- [ost-startStop-1] o.s.b.w.servlet.FilterRegistrationBean   : Mapping filter: 'requestContextFilter' to: [/*]
simpleservice_1  | 2018-12-06 19:17:09.150  INFO 7 --- [           main] s.w.s.m.m.a.RequestMappingHandlerAdapter : Looking for @ControllerAdvice: org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@69663380: startup date [Thu Dec 06 19:17:04 GMT 2018]; root of context hierarchy
simpleservice_1  | 2018-12-06 19:17:09.230  INFO 7 --- [           main] s.w.s.m.m.a.RequestMappingHandlerMapping : Mapped "{[/hello/{firstName}/{lastName}],methods=[GET]}" onto public java.lang.String com.thoughtmechanix.simpleservice.Application.hello(java.lang.String,java.lang.String)
simpleservice_1  | 2018-12-06 19:17:09.232  INFO 7 --- [           main] s.w.s.m.m.a.RequestMappingHandlerMapping : Mapped "{[/error],produces=[text/html]}" onto public org.springframework.web.servlet.ModelAndView org.springframework.boot.autoconfigure.web.BasicErrorController.errorHtml(javax.servlet.http.HttpServletRequest,javax.servlet.http.HttpServletResponse)
simpleservice_1  | 2018-12-06 19:17:09.233  INFO 7 --- [           main] s.w.s.m.m.a.RequestMappingHandlerMapping : Mapped "{[/error]}" onto public org.springframework.http.ResponseEntity<java.util.Map<java.lang.String, java.lang.Object>> org.springframework.boot.autoconfigure.web.BasicErrorController.error(javax.servlet.http.HttpServletRequest)
simpleservice_1  | 2018-12-06 19:17:09.270  INFO 7 --- [           main] o.s.w.s.handler.SimpleUrlHandlerMapping  : Mapped URL path [/webjars/**] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
simpleservice_1  | 2018-12-06 19:17:09.270  INFO 7 --- [           main] o.s.w.s.handler.SimpleUrlHandlerMapping  : Mapped URL path [/**] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
simpleservice_1  | 2018-12-06 19:17:09.362  INFO 7 --- [           main] o.s.w.s.handler.SimpleUrlHandlerMapping  : Mapped URL path [/**/favicon.ico] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
simpleservice_1  | 2018-12-06 19:17:09.585  INFO 7 --- [           main] o.s.j.e.a.AnnotationMBeanExporter        : Registering beans for JMX exposure on startup
simpleservice_1  | 2018-12-06 19:17:09.677  INFO 7 --- [           main] s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat started on port(s): 8080 (http)
simpleservice_1  | 2018-12-06 19:17:09.680  INFO 7 --- [           main] c.t.simpleservice.Application            : Started Application in 5.884 seconds (JVM running for 8.0)

然后访问
http://localhost:8080/hello/aaa/bbb/
输出
{"message":"Hello aaa bbb"}
测试通过******************


遇到的一些问题

Docker：Failed to start docker.service: Unit docker.service is masked.
解决方法
执行如下三条指令

systemctl unmask docker.service
systemctl unmask docker.socket
systemctl start docker.service

eclipse桌面快捷启动报错，才发现是jdk版本问题，用的是jdk11了，把它切换回jdk8就行，通过以下命令切换jdk版本
$ sudo update-alternatives --config   java  



