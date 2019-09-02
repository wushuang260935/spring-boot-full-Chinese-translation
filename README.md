# spring-boot-full-Chinese-translation
spring boot全文档中文版翻译

# 第一部分. Spring boot 文档

 这个部分对spring boot 索引做了一个简要介绍。他是本文章的地图。
 
## 关于文档

 spring boot 索引文档可以转换成
> html
> pdf
> epub
 最新文档可以访问[docs.spring.io/spring-boot/docs/current/reference](http://docs.spring.io/spring-boot/docs/current/reference).对本文挡的复制只能用于你个人和其他人。你不能用此文档向其他人收费。
 
## 帮助中心

 如果你对spring boot有疑问。你可以:
> 试试 [how-to-documents](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#howto).这里会回答你一些最常见的问题。
> 学习spring基础.spring boot是在很多其他spring项目上开发出来的。查看[spring.io](https://spring.io/)获取更多文档。
> 可以在stackoverflow上面问问题。我们会监控stackoverflow上面带spring-boot标签的问题。
> 在[ github.com/spring-projects/spring-boot/issues.](http://github.com/spring-projects/spring-boot/issues)上提交bug.

## 开始学习的第一步

你可以从下面着手你的spring boot之旅。

> 从零开始:[Overview](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#getting-started-introducing-spring-boot) | [Requirements](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#getting-started-system-requirements) | [installation](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#getting-started-installing-spring-boot)
> 指导: [Part1](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#getting-started-first-application) | [Part2](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#getting-started-first-application-executable-jar)
> 运行你自己的项目： [Part 1](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#getting-started-first-application-run) | [Part2](https://docs.spring.io/spring-boot/docs/2.1.5.RELEASE/reference/htmlsingle/#getting-started-first-application-executable-jar);

## 用spring boot做开发

准备好使用springboot做开发了吗 本文档也对下面的技术做了说明，详情请看下面的章节:
> maven,graddle,ant,starters,IDE,Packaged,Code structure , @Configuration , @EnableAutoConfiguration , Beans and Dependency Injection,Production jars,Using the CLI

## 学习spring boot特性

下面是spring boot的核心特性，详情请看下面的章节:

> 核心特性: SpringApplication,External Configuration,Profiles,Logging
> web应用: MVC,Embedded Containers
> 数据库交互: SQL,NO-SQL
> 消息: Overview,JMS
> 测试: Overview,Boot Application,Utils
> 扩展： 自动配置,@Condition

## 转换至产品

当你准备把spring boot发布至生产环境的时候，我们有一些建议要给你，详情请看下面的章节:

> 管理节点: Overview,Customization
> 连接选项: HTTP,JMX
> 监控: Metrics,Auditing,Tracing,Process

## 高级属性

下面的高级属性适合于一些特定的用户和场景.

> Spring boot应用部署: 云部署,操作系统服务
> 建构工具插件: maven,graddle.
> 附录: Application Properties,自动配置 classes,可执行jar包

# 第二部分,牛刀小试

这部分的目的，主要是服务于spring boot的初学者，它将会回答你们“什么”，“怎样”，“为什么”等问题。它包含spring boot介绍，spring boot结构。然后带你构建第一个spring boot项目。顺带讨论一下spring
 boot的核心原则。
 
## spring boot介绍

spring boot可以让你创建独立的，生产级，基于spring的项目更简单。我们从spring平台和第三方库中最常用的东西开始，以便你能迅速上手，很多spring boot只需要很少的配置就可以满足它的需求。

利用spring boot 可以 创建可执行jar包项目，也就是说你新建的项目只需要用java -jar 就可以运行，当然你也可以选择打war包。我们也提供命令工具，以便运行spring script.我们的主要目标是:

> 为所有的spring开发人员提供极速和普遍接受的开发经验
> 提供一系列在大大型项目中无功能性的特性。
> 绝对的无代码生成和无XML配置

## 系统要求

spring boot2.1.5 RELEASE.需要jdk1.8以上。spring framework5.1.7RELEASE以上。项目建构工具maven3.3以上,gradle4.4以上

## servlet容器

spring boot支持下列内嵌的servlet容器:
Name	       Servlet Version

Tomcat 9.0     4.0

Jetty 9.4      3.1

Undertow 2.0   4.0

你可以在任何servlet3.1以上servlet容器中部署spring boot.

## 安装spring boot

spring boot可以作为经典部署工具，也可以安装成命令工具。当然最主流的还是用spring boot标准库。包括恰当地使用spring-boot-*.jar项目。spring boot对IDE没有具体要求。任何IDE都可以。我们建议你使用建构工具开发spring boot.

## 安装maven

spring boot需要maven3.3以上，你可以在maven.apache.org中安装maven。spring boot依赖使用统一编号:org.springframework.boot.所有的spring boot子项目都继承了spring-boot-starter-parent项目，spring boot也提供一个可选的maven插件。以便你创建可以执行jar包。下面是标准的pom.xml文件:

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.example</groupId>
	<artifactId>myproject</artifactId>
	<version>0.0.1-SNAPSHOT</version>

	<!-- Inherit defaults from Spring Boot -->
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.1.5.RELEASE</version>
	</parent>

	<!-- Add typical dependencies for a web application -->
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
	</dependencies>

	<!-- Package as an executable jar -->
	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```

spring boot项目继承自spring-boot-starter-parent会非常方便。但有时我们可能需要继承我们自己的项目。因此在后面的章节我们会讲到用其他方式来提供spring boot便捷服务。

## 安装spring boot CLI

spring boot cli是命令行工具。你可以使用它快速规范出一个spring.cli让你运行groovy脚本。他的语法和java类似。也许你不需要使用cli来规范你的spring boot项目。但是使用CLI无疑是所有工具中规范spring项目最快的一个。

### 手动安装

你可以在spring依赖工具中下载cli
[spring-boot-cli-2.1.5.RELEASE-bin.zip](https://repo.spring.io/release/org/springframework/boot/spring-boot-cli/2.1.5.RELEASE/spring-boot-cli-2.1.5.RELEASE-bin.zip)
[spring-boot-cli-2.1.5.RELEASE-bin.tar.gz](https://repo.spring.io/release/org/springframework/boot/spring-boot-cli/2.1.5.RELEASE/spring-boot-cli-2.1.5.RELEASE-bin.tar.gz)

下载之后，跟随INSTALL.txt的指引，在bin目录中有一个spring.bat或者spring脚本。

### 一个简单的cli样例

创建一个app.groovy文件。内容如下

```
@RestController
class ThisWillActuallyRun {
	@RequestMapping("/")
	String home() {
		"Hello World!"
	}
}
```

然后使用cli运行。

>spring run app.groovy

最开始会很慢，但是当所有的依赖都下载完成了之后，就快多了。然后打开浏览器，输入localhost:8080你就可以看见hello world

## 开发你的第一个spring boot项目

下面开始介绍怎么开发一个简单的spring boot项目。如何使用sprin boot的一写关键特性。我们使用maven作为建构工具。

### 创建pom.xml

就从下面的例子开始:

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.example</groupId>
	<artifactId>myproject</artifactId>
	<version>0.0.1-SNAPSHOT</version>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.1.5.RELEASE</version>
	</parent>

	<!-- Additional lines to be added here... -->

</project>
```
要打包上面的maven项目，直接使用mvn package命令。就会生成target目录，里面含有一个jar包，上面的例子，因为没有代码，所以是一个空项目。

### 添加运行依赖

sprin boot提供了一系列运行依赖。这些依赖最后需要到运行路径下。上面的例子已经用了spring-boot-starter-parent作为父母元素。spring-boot-starter-parent是一个特殊的starter。里面特工了很多有用的maven默认值。特别是dependencyManagement.他可以让你的依赖省略version标签。其他的starter提供的依赖也是你需要的。下面我们会继续引入spring-boot-starter-web依赖。但是在引入他之前，我们可以使用下面的命令来查看我们现在都有哪些依赖了。


$ mvn dependency:tree

[INFO] com.example:myproject:jar:0.0.1-SNAPSHOT

mvn dependency:tree命令打印了一个表示你项目依赖的树。下面添加更多的依赖。spring-boot-starter-web

<dependencies>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
</dependencies>

然后再运行mvn dependency:tree.就又会不一样了

### 写代码

下面开始写一个java文件。默认的，maven从java/main/src中编译java文件。所以我们构建一个src/main/java/Example.java文件。下面是代码:

	```
	import org.springframework.boot.*;
	import org.springframework.boot.autoconfigure.*;
	import org.springframework.web.bind.annotation.*;
	
	@RestController
	@EnableConfiguration
	public class Example{
			
		@RequestMapping("/")
		String name(){
			return "hello world";
		}
		
		public static void main(String[] args){
			SpringApplication.run(Example.class,args);
		}
	}
	```
	
虽然这里面代码不多，但是却包含很多内容。我们慢慢地舔砖加瓦

#### @RestController和@RequestMapping注解

这两个注解并不陌生，请查看MVC 章节对他们的解释

#### @EnableConfiguration注解

这个注解告诉spring boot你将怎么配置这个spring项目。很多配置选项就在你引入的依赖中。spring-boot-starter-web添加了tomcat和spring mvc。所以你可以直接默认的配置来部署你的spring项目。这个叫做自动配置，他和starter结合得很好。但是他们并不是耦合在一起的，你可以你可以自由地选择使用哪些配置。

#### main方法

最后就是main方法了。我们都知道main方法java为了方便使用而提供的入口。在这里就是用SpringApplication的run方法借助main方法并引导spring项目启动。启动spring项目，就会启用自动配置的tomcat Server。我们需要把Example.class作为参数传入run方法中。以此告诉SpringApplication我们的项目最重要的配置在哪里。


### 运行上面的例子。

就这样，spring boot已经可以运行了。在你的项目根节点输入:mvn spring-boot:run。你会看到spring boot项目启动

## 创建一个可执行jar包

我们创建一个依赖完全自含。可以在生产环境中使用的可运行jar包。它里面包含了很多编译的classes

> 如果想要某个可执行jar包从一个文件中获取必须的jar包依赖。java暂时还没有提供，有时候这是个问题。	为了解决这个问题。很多开发人员使用uber jar包。uber jar包会把所有的依赖都打进一个jar包里面。当然问题也就又产生了。你很难通过看它的jar包库分辨出这个可执行jar包引入了哪些依赖。有时候我们的jar包依赖还会有重复。
>于是spring boot提供了另一个解决方案。

为了创建一个完全自含，单独运行的jar包，我们需要引入spring-boot-maven-plugin到dependencies下面:

	```
	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>
	```

> spring-boot-maven-plugin包含了一个execution配置。这个配置是为了绑定重新打包的目标。如果你没有使用parent属性。你需要自己配置这个属性。后面的章节会介绍

然后我们在打包一次。成功之后，在target目录中， 你就会发现，你打包了一个至少10M的jar包。如果你想查看包中的内容。可以使用java -tvf命令。

我们可以直接运行这个jar包。使用java -jar命令。

# 第三部分 使用spring boot

 这部分将详细介绍怎么使用spring boot.内容包括: 建构系统。自动化配置，怎么运行你的项目。我们还加入了一些很好的例子。虽然spring boot不是什么新的特性。不过我们有很多建议。这些建议可以让你的部署过程更加简单。

## 建构系统

 强烈建议您使用建构系统。能够管理您的依赖。使用maven 或者graddle。其他的也可以，只是我们队他们的支持不是很好。
 
### 依赖管理

虽然每一个spring boot都需要与他相关的依赖。但是在实践中，你不需要为每一个依赖提供版本号，因为专门有一个负责关闭版本号的spring boot依赖。叫做spring-boot-dependencies

### maven

maven用户中。继承自spring-boot-starter-parent项目可以获得以下好处:

> 默认设置了jdk1.8的编译器
> UTF-8编码
> 获取上节所说的依赖管理功能。
> 重新打包功能
> 资源过滤高敏感(容易察觉,便于热启动)
> 插件配置高敏感

需要注意的是,自从application.properties和application.yml接受spring式占位符${},maven就把自己的占位符改了@..@.(你可以设置maven的resource.delimiter来修改占位符)

#### 不继承spring-boot-starter-parent而使用spring boot 的其他方式

如果你要继承其他的项目。你可以使用依赖管理，不过要先做如下配置:

	```
	<dependencyManagement>
		<dependencies>
			<dependency>
				<!-- Import dependency management from Spring Boot -->
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-dependencies</artifactId>
				<version>2.1.5.RELEASE</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>
	```
	
还有一种方式就是使用spring-boot-dependencies.:

	```
		<dependencyManagement>
			<dependencies>
				<!-- Override Spring Data release train provided by Spring Boot -->
				<dependency>
					<groupId>org.springframework.data</groupId>
					<artifactId>spring-data-releasetrain</artifactId>
					<version>Fowler-SR2</version>
					<type>pom</type>
					<scope>import</scope>
				</dependency>
				<dependency>
					<groupId>org.springframework.boot</groupId>
					<artifactId>spring-boot-dependencies</artifactId>
					<version>2.1.5.RELEASE</version>
					<type>pom</type>
					<scope>import</scope>
				</dependency>
			</dependencies>
		</dependencyManagement> 	
 	```  

### starter

每一个starter可以为开发人员提供很多经典的依赖。有了他你就可以一站式获取他们。而不用到处复制粘贴。你只需要找到对应的starter就行,如:spring-boot-starter-data-jpa为spring jpa提供了绝大多数依赖。

> 官方的starter都是这种格式:spring-boot-starter-*.
>第三方仿照spring boot的依赖都是这种格式:*-spring-boot-starter。如:druid的相关依赖

下面是一些常用的starter

	|名称 | 描述| 
	|-|-|
	spring-boot-starter | 核心starter,包括自动配置支持，日志和YAML
	spring-boot-starter-activemq | apache ActiveMQ 消息队列的依赖
	spring-boot-starter-amqp | RabbitMQ 的依赖
	spring-boot-starter-aop | spring aop和aspectJ的依赖
	spring-boot-starter-artemis | apache 消息队列Artemis的依赖
	spring-boot-starter-batch | Spring batch的依赖
	spring-boot-starter-cache | spring 缓存的依赖
	spring-boot-starter-cloud-collection | spring cloud 连接器的依赖。能够简化连接到云服务器的步骤，就像Cloud Foundry和Heroku
	spring-boot-starter-data-cassandra | Cassandra分发式数据库和Spring data Cassandra的依赖
	spring-boot-starter-data-cassandra-reactive | 同上
	spring-boot-starter-data-couchbase | 文档形数据库Couchbase的依赖
	spring-boot-starter--data-couchbase-reactive | 同上
	spring-boot-starter-data-elasticsearch Elasticsearch搜索服务和analytics引擎的依赖
	spring-boot-starter-data-jdbc Spring data jdbc的依赖
	spring-boot-starter-jpa hibernate jpa的依赖
	spring-boot-starter-ldap Spring data LDAP的依赖
	spring-boot-starter-data-mongodb 
	spring-boot-starter-data-mongodb-reactive
	spring-boot-starter-data-neo4j
	spring-boot-starter-data-redis
	spring-boot-starter-data-redis-reactive
	spring-boot-starter-data-rest 通过REST暴露spring data库的依赖
	spring-boot-starter--data-solr
	spring-boot-starter-data-freemarker
	spring-boot-starter-groovy-templates
	spring-boot-starter-hateoas
	spring-boot-starter-integration
	spring-boot-starter-jdbc
	spring-boot-starter-jersey
	spring-boot-starter-jooq
	spring-boot-starter-json | 读写json的依赖
	spring-boot-starter-jta-atomikos
	spring-boot-starter-jta-bitronix
	spring-boot-starter-mail
	spring-boot-starter-mustache
	spring-boot-starter-oauth2-client 使用spring security oauth2连接客户端的依赖
	spring-boot-starter-oauth2-resource-server
	spring-boot-starter-quartz 
	spring-boot-starter-security
	spring-boot-starter-test spring boot的测试依赖，内涵junit Mockito
	spring-boot-starter-thymeleaf
	spring-boot-starter-validation
	spring-boot-starter-web web项目的依赖，包括RESTFUL，SpringMVC，tomcat
	spring-boot-starter-web-service WebService的依赖
	spring-boot-starter-webflux
	spring-boot-starter-websocket

>除了以上的依赖之外，还有一个特殊的依赖，被用来加到即将部署的项目依赖中

> spring-boot-starter-Actuator 通过他来查看项目中有用的监控数据。

最后spring boot也支持了下面的技术，当你需要时你可以用下面的替换掉默认的依赖。
> spring-boot-starter-jetty,spring-boot-starter-tomcat的备选项。
> spring-boot-starter-log4j2,spring-boot-starter-logging的备选项
> spring-boot-starter-logging,默认的日志依赖
> spring-boot-starter-reactor-jetty
>spring-boot-starter-undertow

## 组装你的代码

spring boot并没有特定的编码格式。但是下面的实践很有价值

### 使用默认的包路径

当一个class没有声明包路径。那么就是在默认包路径下。我们不鼓励使用默认包路径。因为当spring boot使用@ComponentScan和@EntityScan和@SpringBootApplication注解的时候，会出一些很特别的问题。
>我们建议你使用成熟的包路径套路:com.example.project,org.group.project

### 合理安置Application.class主应用类

我们建议你把Application.class入口类放到项目的根目录下。@SpringApplication注解通常用在入口类中。然后他会为了找特定属性而定义“查询包路径”。比如：你写一个JPA项目，那么@springapplication注解就是用来查询@Entity的。最后，放到根目录的另一个好处就是组建扫描的时候只会扫描到你的项目上。

>如果你不想用@SpringBootApplication,这个注解的某一些功能可以用@EnableConfiguration和@ComponentScan代替。

下面的例子，展示了一个标准的层级结构:

	com
	 +- example
	     +- myapplication
	         +- Application.java
	         |
	         +- customer
	         |   +- Customer.java
	         |   +- CustomerController.java
	         |   +- CustomerService.java
	         |   +- CustomerRepository.java
	         |
	         +- order
	             +- Order.java
	             +- OrderController.java
	             +- OrderService.java
	             +- OrderRepository.java
	
## 配置class

spring boot喜欢java-based配置。我们虽然也可以使用xml配置，但是我们建议你把@Configuration注解用到一个单独的静态资源加载类中。并且这个类包含java入口main方法，正如application.java

### 引入额外的配置class

你并不需要吧所有的配置都放入单个class中。@Import注解可以用来引入额外的配置类。最终，你可以使用@ComponentScan扫描项目中所有的组件，包括Configuration类。

### 引入xml配置

如果你必须使用xml配置，我们建议你仍然以配置了@Configuration注解的class作为起点。然后你可以使用@ImportResource注解来加载XML配置

## 自动配置

Spring boot 自动装配会根据你在包依赖(maven,或者graddle)中添加的jar包。来自动配置你的Spring应用,比如HSQLDB在你的类路径中。那么你就可以不用手动配置数据库连接类了。spring boot自动帮你配置.
但是，要使用这个功能你需要把@EnableAutoConfiguration或者@SpringBootApplication添加到你的配置类(添加了@Configuration的那个类)中。

> 建议你要么只添加一个@EnableAutoConfiguation，要么只添加一个@SpringBootApplication到你的配置类中。

### 手动替代自动装配

自动装配是无侵入式的，你可以随时使用手动装配替换自动装配，比如，你可以添加自己的数据库类.那么内嵌的数据库自动配置就会不会被启用。如果你想知道自动装配的具体原理，你可以启动应用的时候打开调试模式,就是这个而命令:--debug.这个命令可以让控制台打印出debug级别的日志。

### 禁用某一个自动装配类

如果你发现某一个正在被使用的自动装配是你不想要的。你可以使用@EnableAutoConfiguration注解中的exclue属性来排除他们。下面就是一个例子:

```
import org.springframework.boot.autoconfigure.*;
import org.springframework.boot.autoconfigure.jdbc.*;
import org.springframework.context.annotation.*;

@Configuration
@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})
public class MyConfiguration {
}
```

如果这个配置不在执行类上。你可以使用注解中的excludeName属性来指定全类名(org.example.AutoConfiguration)。或者干脆在配置文件上配置spring.autoconfigure.exclude属性.

>上面介绍的注解上的排除项和配置文件上的排除项可以同时使用

## spring类和依赖注入

你可以使用任何标准的spring技术来定义你的类或者对他们的依赖进行注入。为了更简化，我们发现使用@ComponentScan和@Autowired配合得更好,如果你按照上面所说的方式来组装你的代码（也就是把启动类放到根目录下)，那么你使用@ComponentScan的时候就不用参数.在这种情况下，所有的组件(@Component,@Service,@Reposity,@Controller等等)都会自动自动装配进来。

下面的例子展示了一个@Service类的构造函数的参数是怎么被注入的:

```
package com.example.service;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class DatabaseAccountService implements AccountService {

	private final RiskAssessor riskAssessor;

	@Autowired
	public DatabaseAccountService(RiskAssessor riskAssessor) {
		this.riskAssessor = riskAssessor;
	}

	// ...

}
```

如果一个bean有一个构造函数，那么你就可以省略@Autowired注解。下面就是一个例子:

```
@Service
public class DatabaseAccountService implements AccountService {

	private final RiskAssessor riskAssessor;

	public DatabaseAccountService(RiskAssessor riskAssessor) {
		this.riskAssessor = riskAssessor;
	}

	// ...

}
```

> 请注意如何使用构造器注入，才能让riskAssessor被标记为final.也就是说他不能被修改。

## 使用@SpringBootApplication注解

很多spring boot开发人员喜欢使用自动配置。而@SpringBootApplication就包含了下面的三个注解的功能:

> @EnableAutoConfiguration:这个注解就表示启用了自动装配
> @ComponentScan: 让应用上的@Component所在的包被扫描到。就像配置文件<component-scan>
> @Configuration: 这个注解允许向上下文中注册新的bean。或者是引入额外的配置文件。

使用了@SpringBootApplication就等同于同时使用了上面的三个注解。

> @SpringBootApplication还可以设置@EnableAutoConfiguration和@ComponentScan中属性的别名

> 设置别名并不是强制性的，可能有的时候你只需要上面三个注解中的一部分功能。比如:你可能不想使用组件扫描功能,例子如下：

```
package com.example.myapplication;

import org.springframework.boot.SpringApplication;
import org.springframework.context.annotation.ComponentScan
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Import;

@Configuration
@EnableAutoConfiguration
@Import({ MyConfig.class, MyAnotherConfig.class })
public class Application {

	public static void main(String[] args) {
			SpringApplication.run(Application.class, args);
	}

}
```

> 上面的例子中，加上@ComponentScan就等于@SpringBootApplication。但是使用@Import就只导入了MyConfig.class和MYAnotherConfig.class

## 运行你的应用

把整个应用打包成一个jar包，并且把HTTP Server内嵌到jar包中有一个很大的好处。那就是你可以自由运行你的项目而不受环境限制。而且调试也很简单。你并不需要特殊的IDE或者插件。

### 从IDE中运行

在IDE上运行spring boot跟运行一个main方法是一样的。

> 有时候你会不小心运行了两次spring boot应用。这时候你会收到Port already in use提示，这个是tomcat的端口被占用了。使用spring tool suite的开发人员可以点击relanch按钮。以保证之前的项目被关闭了。

### 运行一个打包应用

使用java -ar命令。

```
$ java -jar target/myapplication-0.0.1-SNAPSHOT.jar
```

如果你开启了远程调试支持。那么你也可以通过下面的方式来运行你的应用个：添加一个开发者到你的应用程序中

```
$ java -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n \
       -jar target/myapplication-0.0.1-SNAPSHOT.jar
```

### 使用maven插件

spring boot maven插件包含了run 命令。这个命令可以迅速编译和运行你的项目。

```
$ mvn spring-boot:run
```

有可能你需要配置一下maven的环境：

```
$ export MAVEN_OPTS=-Xmx1024m
```

### 热替换

自从spring boot把应用变成了普通应用了之后，虚拟机热替换技术就迫切需要了。但是热替换技术因为不能准确地替换字节码而受到限制。后来我们使用JRebel技术。

而另一个解决方案就是使用spring-boot-devtools，它也支持快速重启技术。能够使你的项目快速重启。

## 开发者工具

为了让开发过程更加顺利，spring boot添加了一些辅助工具。集成在了spring-boot-devtools中。

> 如果你的应用使用java -jar启动或者通过特定的classloader启动。那么你的应用就会被看作是生产级应用。这个时候，spring-boot-devtools会被禁用。但是万一不行的话，你可以使用java -Dspring.devtools.restart.enabled=false系统属性来排除devtools。

> 标记spring-boot-devtools这个依赖为Optional很有用。因为如果你的应用被其他应用引用了。这个标记能够组织其他应用也加在这个依赖。

> 默认情况下，重新打包文档不会包含devtools.如果你想用某一个devtools特性。你需要禁用excludeDevtools属性。

### 默认属性

很多spring boot支持的库会使用缓存来提供效率。比如：模板引擎为了避免重复编译同一个文件，会在在编译的时候缓存模板，Spring MVC和http也会有缓存。虽然缓存在生产模式很有用。但是在开发阶段却是相反的。然而，spring-boot-devtools默认就带了禁用缓存的功能。由于你在开发spring MVC的过程中需要更多的日志信息，devtool将会启用DEBUG模式，之后，包括请求过程中，响应过程中的日志都会打印。如果你想打印全部细节信息，包括请求中的敏感信息，你可以打开spring.http.log-request-details属性。

> 如果你想禁用默认属性你可以在application.properties中设置spring.devtools.add-properties=false

>下面还会介绍完整的devtool属性

### 自动重启机制

如果应用使用了spring-boot-devtool就可以在应用的classpath中的文件有修改的时候自动重启。这个特性在使用IDE进行开发的时候非常有用。默认的，classpath中任意文件夹下的实体类都会被监控是否有修改。需要注意的是，静态资源和视图模板(html等),不需要重启。

```
触发一次重启
由于devtool监控classpath上的资源。触发一次重启的唯一方式就是更新classpath。在eclipse中，保存一个已修改的文件会引起classpath更新，从而触发一次重启，在IDEA中，建构一次工程也有同样的效果
```

> 在重启的时候，devtool依赖于应用上下文的关闭钩子。如果你禁用了关闭钩子SpringApplication.setRegisterShutDownHook(false).那么devtool就不能正常工作。


重启VS重新加载

```
spring boot提供的这个重启技术需要借助两个加载器才能工作。不会改变的类(比如引入的jar包中的类)会使用基础加载器。而你正在开发的类会使用重启加载器。当应用重启过后，重启加载器就会被弃用然后再创建一个新的重启加载器。这种方式就意味着重启速度比冷启动快。但是前提条件是基础加载器正在工作。如果你发现你的热启动一点都不快或者遇到加载问题。你可以考虑使用JRebel(ZeroTurnaround)重新加载技术。他们的工作原理是在启动并加载类的时候会重写所有的类，让重写过后的类会更适合重启。
 ```
 
### 情况改变时日志也会改变

默认的，每次你的应用一重启，就会有一个评估报告被记录。只要你新增或者删除bean或者是设置配置参数等操作，这个报告会显示你的应用中自动配置的改变情况，要禁用这个功能，就要设置下面的属性:

```
spring.devtools.restart.log-condition-evluation-delta=false
```

### 排除静态资源

有一些静态资源改变之后也许不需要触发重启。比如MVC的视图模板，默认的，改变/META-INF/maven,/META-INF/resources,/resources,/static,/public,/templates文件夹中的资源文件不会触发重启但是会触发实时重新加载。
但是如果你想要自定义你的排除项，你就需要使用spring.devtools.restart.exclude属性。比如，如果只想排除/static,/public你可以设置下面的属性:

```
spring.devtools.restart.exclude=static/**,public/**
```

> 如果你想要在保持默认排除项的基础上再额外增加排除项，就需要使用spring.devtools.restart.additional-exclude属性，而不是使用上面的属性(上面的那个属性是改变默认的排除项)。

### 监听额外的路径

如果你修改了某些不在classpath上的文件之后，也想触发自动重启的话，可以配置spring.devtools.restart.additional-paths属性来监听额外的路径。这样发生改变的时候也会触发重启，大多数情况下，你可以把这个属性放到application.properties文件中(但是这么做虽然会初始化重启加载器，但是它不会监听文件改变)。如果你需要完全禁用重启功能，你可以设置spring.devtools.restart.enabled=false.请注意，这里不同的是，这是个系统(System)属性。
因此，你需要放到SpringApplication.run()前面。如下图:

```
public static void main(String[] args) {
	System.setProperty("spring.devtools.restart.enabled", "false");
	SpringApplication.run(MyApp.class, args);
}
```

### 使用触发文件

如果你使用的IDE需要不停地编译修改的文件，你可能更需要在具体的时间点触发重启。因此就需要触发文件。当你想触发一次重启检查的时候，这个触发文件必须被修改。换句话说，修改这个文件只会触发重启检查，而触发重启只能等到devtools自己检测到需要重启的时候。触发文件可以手动修改也可以使用IDE插件修改。要使用触发文件的话，就需要设置spring.devtools.restart.trigger-file属性的值。这个值就是你的触发文件所在的路径。

>你可以把spring.devtools.restart.trigger-file设置为全局属性(比如src/main/java/**)。那么你所有的路径都只会触发重启检测。

### 自定义重启加载器

在上面的重启VS重新加载章节中。重启需要两个加载器。这种方式绝大多数的应用都可以正常使用。但是，有时候会引起加载问题： 默认地，你的IDE中任何正在开发的代码都需要重启加载器加载。而任何任何普通jar文件都是普通加载器加载的。但是如果你的想科目有多项目协同(这种情况比较多),并且不是所有的模块都被加载到了IDE中(这种情况比较少)，遇到这种情况，你需要设置META-INF/spring-devtools.properties文件。这个文件中可以设置restart.exclude(只是一个前缀，具体如下图）属性和restart.include(只是一个前缀，具体如下图)属性。include属性设置的东西使用基础加载器加载。exclude属性设置的东西使用基础加载器加载。请注意，这两个参数的值是正则表达式，用来过滤出classpath中的路径。如下图:

```
restart.exclude.companycommonlibs=/mycorp-common-[\\w-]+\.jar
restart.include.projectcommon=/mycorp-myproj-[\\w-]+\.jar
```

> 所有属性的键必须是唯一的，只要属性以restart.exclude或者restart.include为前缀，这个属性就会生效。

> 所有classpath上的/META-INF/spring-devtools.properties都会被加载,你可以把文件打包到你的项目中，或者打包到你项目的某一个仓库中。

### 已知的限制

现目前已知的是，重启功能并不适合由标准的ObjectInputStream反序列化出来的项目，如果你需要反序列化数据，你需要使用spring的ConfigurableObjectInputStream。并结合Thread.currentThread().getContextClassLoader()使用。不幸的是，很多第三方库在反序列化话的时候没有考虑上下文。如果你发现了这个问题，你需要找这个库的原作者修复这个问题。


### 实时重新加载

spring-boot-devtools模块包含一个内置的实时重新加载服务器。当资源被修改的时候，他能够用来触发浏览器刷新。livereload.com上的实时重新加载浏览器插件，谷歌浏览器，火狐浏览器和Safari浏览器都支持。如果你运行应用的时候，不需要启动实时重新加载服务器启动。你可以设置spring.devtools.livereload.enabled=false.

> 同一时间只能运行一个实时重新加载服务器。因此在你的应用启动之前，需要保证没有运行其他的重新加载服务器。如果你在IDE中启动多个项目，只有第一个服务器会有效。

## 全局设置

配置全局devtools设置需要添加一个文件：添加一个叫做.spring-boot-devtools.properties文件到你的操作系统根目录下(Linux $HOME,windows C:/uses/xxx),添加到这个文件中的属性会应用到所有的使用了spring-boot-tools的spring boot项目中。比如：使用触发文件来重启，你需要添加下面的属性：

```
C:/users/xxx/.spring-boot-devtools.properties

spring.devtools.reload.trigger-file=.reloadtrigger
```

> 在.spring-boot-devtools.properties文件中开启的profile.不会影响profile-specific配置文件的加载。

## 远程应用

spring-boot-devtools不限于本地开发。当你远程运行项目的时候，你也可以使用它的很多应用。远程支持是可选功能，要使用他的话，你需要保证devtools没有被排除，如下所示:

```
<build>
	<plugins>
		<plugin>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-maven-plugin</artifactId>
			<configuration>
				<excludeDevtools>false</excludeDevtools>
			</configuration>
		</plugin>
	</plugins>
</build>
```

然后你需要设置spring.devtools.remote.secret属性。spring.devtools.remote.secret=xxxxxx

>远程项目中启用spring-boot-devtools是有风险的，不能在生产环境中使用

>远程devtools由这两个模块提供支持：一个是服务端中负责接收连接的endpoint（它也可以接收客户端应用），当spring.devtools.remote.secret设置了启用，服务端会自动启用。（如果是客户端则必须手动发布）

### 运行远程客户端应用

你需要用你的本地IDE运行远程客户端应用。你需要使用org.springframework.boot.devtools.RemoteSpringApplication来启动你的远程应用，但是你的远程应用的classpath必须和你运行RemoteSpringApplication的classpath一样。举个例子,如果你使用的IDE是eclipse或者STS开发一个叫做my-app的项目。但是这个项目在云服务器上,你可以按照下面的步骤，令你的IDE开发云服务器上的项目。

```
1. 从run菜单中选择run configuration.
2. 在java application中选中 "launch configuration"这个启动类.
3. 点击browser按钮查找my-app项目。
4. 点击search按钮，使用org.springframework.boot.devtools.RemoteSpringApplication作为他们的主方法
```

你就会看见控制台正在运行了。上面的例子有以下几个特点:

```
1. 远程客户端使用的是和本地应用相同的classpath。所以他能够直接读取相关参数。
2. 建议使用https协议，这样交互的数据都是加密的。
3. 如果你想在远程桌面中使用代理，可以配置spring.devtools.remote.proxy.host和spring.devtools.remote.proxy.port属性。
```

### 远程更新

远程桌面会像本地重启一样监视你classpath中的任何改变。一旦检测到了改变就会被推送到远程桌面上并出发重启。只有当远程客户单在运行的时候，文件的修改才能被检测到，否则就不会搜索到。


## 打包应用以供生产环境使用 

可执行jar包是可以用于生产环境的。由于可执行jar包自包含了他们需要的依赖，他们也非常适合在云服务上部署。如果你需要以下这些生产级别特性：比如系统稳定性，可监控程度，REST和JMX 端点。你需要用到spring-boot-actuator.

### 接下来要了解的

现在你应该了解了怎么使用spring boot了。接下来你可以到“深度spring boot特性”去做研究。或者你可以直接跳过“深度spring boot特性”。转而研究spring boot在生产环境下的知识。

# 第四部分 深度 spring boot特性

这部分会详细研究spring boot的特性。你可以从这部分中学到spring boot的关键特性。如果你感觉学习这部分比较吃力，请回滚第二部分和第三部分的内容。

## SpringApplication

SpringApplication类提供了一个方便启动“spring application应用”的方法。那就是main方法。大多数情况下你只需要使用SpringApplication.run方法来启动你的spring boot项目。默认情况下，控制台打印的日志级别是info,日志打印的是与启动相关的细节。比如启动应用的是哪一个用户，端口号，启动完成时间。

>如果你需要比info级别更大的日志。请查看后面的章节  日志级别

### 启动失败

如果你的spring boot启动失败了。你就会看到控制台中的failureAnalyzer(失败分析器) 在分析你的错误原因。然后会定位到你错误的关键点上。如下所示：

```
***************************
APPLICATION FAILED TO START
***************************

Description:

Embedded servlet container failed to start. Port 8080 was already in use.

Action:

Identify and stop the process that's listening on port 8080 or configure this application to listen on another port.
```

失败分析器分析了失败原因后，找到了错误的关键点。就是你的端口重复了。

>spring boot提供了很多的错误编辑器，而且你还可以自定义哦。

如果没有一个failureAnalyzer可以处理当前发生的错误。你也可以通过配置相关参数得到一个当前的分析报告。只需要把org.springframework.boot.autoconfigure.logging.ConditionEvaluationReportLoggingListener.的日志级别调整到debug。就可以了

> 你也可以这样调整: java -jar myproject-0.0.1-SNAPSHOT.jar --debug

### 自定义banner

打印到控制台的banner是可以修改的。你只需要在classpath中加入一个你的banner.txt就可以了。或者通过设置spring.banner.location来指定你的banner.txt的位置.如果你的banner不能置顶utf-8格式，那么你需要设置spring.banner.charset。除了banner.txt之外，你还可以加一个banner.gif/jpg/png.图片文件在banner.txt前面。或者设置spring.banner.image.location。这些文件会被转换成ASCII打印在banner.txt的前面。

在banner.txt中。你可以使用下面的占位符。

> ${application.version}  应用的版本号。这个版本号来自MANIFEST.MF.比如Implementation-Version: 1.0那么它就会打印1.0
> ${application.formatted-version} 同样也是应用的版本号。也是来自MANIFEST.MF。只是这个是以v开头的那个版本号。比如：(v1.0)
> ${spring-boot.version} 你使用的spring boot版本号。举例:2.1.7.RELEASE
> ${spring-boot.formatted-version} 类似的。举例：v2.1.7.RELEASE
> ${Ansi.NAME} or ${AnsiColor.NAME or ${AnsiBackground.NAME} or ${AnsiStyle.NAME}  这个是ANSI空挡符。可以参考AnsiPropertySource源码
> ${application.title}  应用的标题。定义在MANIFEST.MF中。比如Implementation-Title: MyApp那么它就会打印MyApp

如果你想使用代码生成banner。你可以使用SpringApplication.setBanner()方法。但是需要实现org.springframework.boot.banner接口。你也可以使用spring.main.banner-mode属性来选择打印在哪：控制台，还是日志文件或者关闭。
注入的banner 在容器中是单例的。bean的名称是springBanner。spring.yml中注意下面的双引号:

```
spring:
	main:
		banner-mode: "off"
```

### 自定义SpringApplication

如果默认的SpringApplication不符合你的胃口。你可以自定义你自己的springApplication。比如：你有一个自定义的MySpringConfiguration，那么：

```
	SpringApplication app = new SpringApplication(MySpringConfiguration.class);
	app.setBannerMode(Banner.Mode.OFF);
	app.run(args);
```

MySpringConfiguration是一个Spring beans配置类。换句话说就是MySpringConfiguration把所有有@Configuration的类都配置到了Spring中。

除此之外，你也可以通过通过配置文件(application.properties/.yml)来配置SpringApplication。具体见后面的“额外配置”。

### 流畅配置API

如果你想以接续的方式配置ApplicationContext。或者说你想使用流畅配置API。你可以使用SpringApplicationBuilder。它可以让你链式地配置多个属性。比如：

```
	new SpringApplicationBuilder()
		.sources(Parent.class)
		.child(Application.class)
		.bannerMode(Banner.Mode.OFF)
		.run(args);
```

当创建SpringApplicationBuilder的时候会有一些限制。比如Web组件不能配置在第一级中。只能配置在子级中。但是Environment都可以配置。

### 应用事件和监听器

除了常规的springframework事件之外。比如：ContextRefreshedEvent就是一个常规事件。SpringApplication还会发送一些额外的应用事件：

> 某些事件会在ApplicationContext创建之前触发。所以你不能在这些事件中注入监听器bean。但是你可以通过SpringApplication.addListeners方法或者SpringApplicationBuilder.listeners()方法来注入这些监听器bean。
>如果你确实想让这些监听器自动注入而不用考虑ApplicationContext是否创建的话，你就需要添加一个META-INF/spring.factories文件。然后就像这样：org.springframework.context.ApplicationListener=com.example.project.MyListener配置你的监听器。

当你的应用启动的时候，所有的应用事件会按照下面的顺序发送出去：

> 1 除了注入监听器和加载器之外，一个ApplicationStartingEvent事件是在执行开始但是还没有做任何操作之间被发送出去的 
> 2 ApplicationEnvironmentPreparedEvent事件是在context中的某一个Environment即将被应用但是还没创建之前被发送出去的
> 3 ApplicationPreparedEvent 事件是在bean定义被加载了之后但是刷新开始之前被发送出去的
> 4 ApplicationStartedEvent 事件是在Context被刷新之后但是任何线程还没有被调用之前被发送出去的
> 5 ApplicationReadyEvent 事件是在任何线程被调用之后被发送出去的。这个事件的发生表明应用已经准备好接收请求了。
> 6 ApplicationFailedEvent 事件是在启动过程中有异常抛出的时候被发送出去的

也许你不需要使用应用事件。但是你需要了解他们的存在。实际上，spring boot使用事件来处理很多的任务。

应用事件是由spring framework的事件发布机制发送的。这个机制的部分功能可以确保：在某一个子context中。某一个被发送到监听器的事件。也会被发送到上级context中。这样做的结果就是：你的应用会使用一个有序的SpringApplication实例。某一个监听器会接受到多个相同的事件。但是这些事件却来自不同的上下文实例。如果你想让你的监听器区分哪些应用来自你本身的上下文，哪些是下级上下文的。就需要保证这个上下文是被注入的。这样就可以和其他的上下文进行比较。你可以通过实现ApplicationContextAware接口注入。或者也可以使用 @Autowired注入。

### Web环境

开始的时候，SpringApplication会根据你操作的代码创建一个适合这个应用的上下文(ApplicationContext):其实决定创建哪一个Web应用很简单：

> 如果使用了Spring MVC,那么就会创建AnnotationConfigServletWebServerApplicationContext 
> 如果没使用Spring MVC 但是使用了WebFlux 就会创建AnnotationConfigReactiveWebServerApplicationContext
> 其他情况下就会创建AnnotationConfigApplicationContext 

这就意味着，如果你在同一个应用中同时使用Spring MVC和Spring WebFlux.那么当某一个请求来临的时候，默认就是用Spring MVC去处理的。但是如果这时候你想用Spring WebFlux的话，就需要使用setWebApplicationType(WebApplicationType)方法来重载默认值。

如果你想完全指定某一个ApplicationContext，那么你可以直接使用setApplicationContextClass()方法.

### 获取应用级别的参数

如果你需要获取传递给SpringApplication.run()方法的应用级别参数。你需要注入一个org.springframework.boot.ApplicationArguments bean.之后应用级参数接口就会提供String[]数组参数和转换好了的option还有非必填参数。举例如下:

```
	@Autowired
	public MyBean(ApplicationArguments args) {
		boolean debug = args.containsOption("debug");
		List<String> files = args.getNonOptionArgs();
		// if run with "--debug logfile.txt" debug=true, files=["logfile.txt"]
	}
```

spring boot同样会注入一个县城属性源(CommandLinePropertySource) 到应用上下文中。它允许你使用@Value注解注入单例应用级别的参数

### 使用(应用运行器)ApplicationRunner和线程运行器(CommandLineRunner)

如果你想在Spring 应用创建之后马上运行一段特定的代码。你可以实现ApplicationRunner接口或者实现CommandLineRunner。两个接口的工作方式是一样的。他们都只有一个run()方法。他会在Spring.run()调用完成之后立即调用。

线程运行器（CommandLineRunner）接口中的run方法中的参数就是应用级别的参数字符数组,但是,应用运行器（ApplicationRunner)会先于线程运行器(CommandLineRunner)调用ApplicationArguments中的方法.这就意味着他会先得到应用级别参数。

如果你有多个线程运行器(CommandLineRunner)和应用运行器(ApplicationRunner)并且需要对他们进行排序的话，你可以额外继承org.springframework.core.Ordered 接口。你也可以直接注解方式@org.springframework.core.annotation.Order

### 退出应用

每一个spring应用会注册一个关闭钩子到虚拟机中。这样能够确保当关闭应用的时候应用上下文(ApplicationContext)会被优雅地关闭。所有的标准Spring生命周期回掉都可以被使用。比如：DisposableBean接口或者@PreDestroy注解。

除此之外，实现了org.springframework.boot.ExitCodeGenerator接口的bean也会在SpringApplication.exit()被调用的时候返回一段指定的退出码(举例:-1,-2,-3....)。这些退出特码会最终传递到System.exit()方法中.然后Sysatem.exit()方法会返回退出码作为整个系统的状态码。如下所示:

```
@SpringBootApplication
public class ExitCodeApplication {

	@Bean
	public ExitCodeGenerator exitCodeGenerator() {
		return () -> 42;
	}

	public static void main(String[] args) {
		System.exit(SpringApplication.exit(SpringApplication.run(ExitCodeApplication.class, args)));
	}

}
```

同样的道理.退出码生成器(ExitCodeGenerator)接口也许会被异常类实现.当遇到错误时，Spring boot会返回退出码，这些退出码由getExitCode提供。

### 管理员特性

设置spring.application.admin.enabled属性就能启用与管理员相关的特性。开启这个属性之后，MBeanServer会暴露SpringApplicationAdminMXBean到javax.management.MBeanServer接口中。你可以使用这个属性远程管理你的spring boot 应用。实际上这个特性在很多的应用中都很用。

> 如果你想知道你的应用端口号，你就需要找local.server.port属性的值。

请注意: 使用这个特性时请保持谨慎,因为MBean暴露了一个可以关闭应用的方法。

## 外部配置

Spring boot 允许手动配置各种外部参数。这样你就可以根据需要配置出不同的外部环境。你可以使用属性文件。YAML文件，环境参数。或者直接配置spring 提供的抽象环境。或者直接通过@ConfigurationProperties构建相关环境对象。

spring boot 使用一种非常特殊的PropertySource顺序。这种顺序被用来重载那些比较敏感的参数。下面是一般的属性顺序:

1.根目录中依赖Devtools(开发工具jar包）的全局设置参数。(当然前提是devtool被使用)
2.测试类中@TestPropertySource注解
3.测试类中其他参数。这些参数是在@SpringBootTest用到的参数。还可以是在test相关注解中用于测试特殊应用功能的注解
4.线程参数。
5.SPRING_APPLICATION_JSON中的参数（主要是应用环境中或者系统属性中内嵌的JSON需要用到的参数）
6.ServletInitConfig的初始化参数
7.ServletContext的初始化参数
8.java:comp/env中的JNDI参数
9.java系统级参数（主要是System.getProperties()中的参数)
10.操作系统环境参数
11.有一个RandomValuePropertySource对象。它里面的部分参数。来自包：random.*
12.你的jar包中需要的特定参数。比如数据库需要的参数
13.你的jar包内含的特定参数。
14.你的jar包需要的外部应用参数。比如spring-web。需要的spring-core的相关参数
15.你的jar包内含的应用级别承诺书。比如：默认的端口8080
16.你在某个有@Configuration的类中使用@PropertySource的注解
17.默认参数.主要是SpringApplicatgion.setDefaultProperties(MAP).

下面通过一个列子来了解。假设你创建了一个	组件@Component。这个组件有一个name属性。如下:

```
import org.springframework.stereotype.*;
import org.springframework.beans.factory.annotation.*;

@Component
public class MyBean {

    @Value("${name}")
    private String name;

    // ...

}
```

在你的应用路径中(classpath).你可以设置一个application.properties文件。这个文件提供一个默认的参数值给name属性。当我们在某一个新的环境中运行的时候。我们就可以在外部
application.properties文件中提供重新顶一个一个值来重写more你的name属性的值。如果是一次性启动。你就可以使用命令行开关进行发布(java -jar app.jar --name="Spring")。

the spring_application_json属性也可以使用命令行进行赋值。比如：你可以使用下面的UNIX脚本语句：

>$ SPRING_APPLICATION_JSON='{"acme":{"name":"test"}}' java -jar myapp.jar

在下面的例子中。你可以以acme.name=test结尾。你同样可以使用json格式为name赋值。然后把json传给系统参数中的spring.application.json.如下所示:
$ java -Dspring.application.json='{"name":"test"}' -jar myapp.jar

当然你也可以用命令行:
$ java -jar myapp.jar -- spring.application.json = '{"name":"test"}'

最后，你也可以以JNDI参数的方式赋值:
java:comp/env/spring.application.json

### 配置随机值(RandomValuePropertySource中的随机值)

RandomValuePropertySource对于注入随机值很有用（比如：内部密钥或者测试案例）。这个类可以生成Integers,longs.uuids.或者strings如下:
my.secret=${random.value}
my.number=${random.int}
my.bignumber=${random.long}
my.uuid=${random.uuid}
my.unmber.less.than.ten=${random.int(10)}
my.number.in.range=${random.int[1024,65536]}

random.int*语法被称为(开发式值 value,(,max值) 关闭值).也就是说你传入的OPEN值可以是任意的字符类型.最后得到的CLOSE值是也可以是任意字符。但是value,max是integer值。如果你提供的是max值。那么value就是最小值(minimum)

### 获取命令行参数

默认地，SPringApplication可以转换任何命令行参数（就是那个以--开头的参数。比如server.port=90).转换之后的参数会被添加到Spring Environment中。正如前面提到过的一样。命令行参数总是在其他参数的前面。

如果你不想使用命令行参数赋值的方式。你可以使用SpringApplication.setAddCommandLineProperties(false).禁用他们。

### 应用属性文件

SpringApplication对象从application.properties文件中加载参数。SpringApplication一般会从下面的部分查找application.properties文件。并且把文件中的参数加载到Spring环境中:

1.当前SpringApplication所在路径的/config文件中
2.当前路径中
3.classpath中的/config路径
4.classpath中

以上四个根据优先级排序（更高的层级的参数会覆盖低层级的参数)

> 除了application.properties,你也可以使用application.yml

如果你不喜欢application.properties作为你的文件名称。你可以通过修改spring.config.name环境参数的值来改变文件的名称。你也可以使用spring.config.location环境参数来指向某一个明确的位置。（不同位置之间用,号分隔).下面的列子展示了怎么定义不同的文件名称:

>$ java -jar myproject.jar --spring.config.name=myapplication

下面的例子展示了怎么指定两个位置:

>$ java -jar myproject.jar --spring.config.location=classpath:/default.properties,classpath:/another.properties

spring.config.name和spring.config.location中的值会在很早的时候就被加载。因为需要用里面的参数决定下一步的加载项。因此他们两个必须是环境参数。(操作系统参数，系统级参数。命令行参数，都属于环境参数).

如果spring.config.location包含有路径。那么location应该以/结尾。因为在运行的时候。系统会使用spring.config.location+spring.config.name来定位参数文件。因此需要以/结尾。

配置路径是倒序搜索的。默认上，配置的路径像这几个:classpath:/,classpath:/config,file:./,file:./config/.那么搜索顺序就会这样:
1. file:./config
2. file:./
3. classpath:/config/
4. classpath:/

当自定义的配置通过spring.config.location找到的时候。他们就会替换默认的路径。比如说:如果spring.config.location=classpath:/custom-config/,file:./custom-config/.那么搜索的顺序如下:

1. file:./custom-config/
2. classpath:custom-config/

另外，如果自定义配置使用的是spring.config.additional-location来确定位置.那么spring boot就会优先搜索spring.config.additional-location的属性。然后再搜索默认的属性。比如：多了两个:classpath:/custom-config/,file:./custom-config/
1. file:./custom-config/
2. classpath:.custom-config/
3. file:./config/
4. file:./
5. classpath:/config/
6. classpath:/

了解了这些顺序后，我们就可以使用某些配置中的部分默认配置，而再在某些配置中使用新的配置把默认的配置覆盖掉。你可以在application.yml中提供默认的配置，然后当切换其他环境是。你就是用不同的配置。

>如果你更喜欢用环境参数而不是用系统参数。大多数操作系统不允许分隔键名(比如空格 "config name或者config.name")。但是你可以使用下划线:spring_config_name

>如果你在容器中运行你的应用。那么JNDI属性或者是servlet加载参数也可以使用了。而不只是环境参数和系统参数。

### 详细配置参数

除了application.properties之外详细配置参数仍然可以通过这种格式:application-{profile}.properties文件来定义。spring 环境中有一连串默认配置。当没有其他活跃的参数被设置的时候，就是用这些默认的配置。也就是说，如果没有其他的参数被激活，那么就会使用默认的application-default.properties.不管你的详细配置文件在你的jar包内部还是jar包外部，你定义的详细配置参数总是会覆盖非详细配置参数。

如果有多个地方配置了同一个参数。那么只是用最后一个参数的配置。比如：spring.profiles.active指定的配置会在SpringApplication中配置的参数加载之后再加载。这样前者的优先级就比后者高。如果你使用spring.config.location指定了某一个具体的配置文件。那么这一个具体的配置文件中的详细配置变量是不会被应用的。

### 使用YAML替代properties

YAML是一连串的json格式的spring参数设置文件。SpringApplication文件自动支持YAML格式作为额外的配置文件。YAML不需要额外的jar包支持。

>如果你使用starter。SnakeYAML自动由spring-boot-starter配置。

#### 加载YAML

spring framework提供两个class来很方便地加载YAML文件。YamlPropertiesFactoryBean对象会把YAML加载成参数。YamlMapFactoryBean 对象会把YamlMapFactoryBean 加载成Map。

例如: 考虑到下面的YAML文档:
```
environments:
	dev:
		url: https://dev.example.com
		name: Developer Setup
	prod:
		url: https://another.example.com
		name: My Cool App
```

下面的例子是把上面的格式转换成下面的老格式:

```
environments.dev.url=https://dev.example.com
environments.dev.name=Developer Setup
environments.prod.url=https://another.example.com
environments.prod.name=My Cool App
```

YAML列表会被分隔成一个个带有数组下标的属性:例如:

```
my:
servers:
	- dev.example.com
	- another.example.com
```

转换之后就成了止痒:

```
my.servers[0]=dev.example.com
my.servers[1]=another.example.com
```

在使用spring boot的 绑定器(Binder)的时候，我们为了实现上面的转换效果(其实这个也是@ConfigurationProperties的工作原理)。我们需要有一个java.util.List类型的属性。把这个属性作为目标bean.以便以后加载到spring容器中.如下:

```
@ConfigurationProperties(prefix="my")
public class Config{
	private List<String> servers = new ArrayList<String>();
	
	public List<String> getServers(){
		return this.servers;
	}
}
```

联合上面的两个例子和下面的一个例子。我们看到my属于class级别。prefix=my.然后就是属性servers。正巧这个属性是列表。如果后面还有属性。那么就是另一个class对象。这样依次下去。

#### 在spring环境中把yaml显示为属性

YamlPropertySourceLoader 类就是用来把yaml显示为属性的。它会把yaml转换成PropertySource对象。这样的做法就允许你在代码中使用@Value注解+占位符语法获取yaml中设置的参数值

#### 多个yaml配置文档

你可以在同一个目录中指定多个yaml文件配置。只需要使用spring.profiles来指定哪一个文件会被使用就可以了。如下所示:

```
server:
 address: 192.168.1.100
 
 
 
spring:
 profiles: development
server:
 address: 127.0.0.1
 
 
 
spring:
 profiles: production & eu-central
server:
 address: 192.168.1.120
```

上面的例子中存在三个文件。如果选择的是development配置。那么第二个文件被使用。服务器地址就是127.0.0.1。如果第三个production and eu-central被使用。那么服务器地址就是192.168.1.120.如果既不选择development也不选择product and eu-central。那么就只能使用第一个。默认的192.168.1.100

> 因此我们可以在spring.profiles包含一个简单的配置名称或者一个的配置表达式。这个表达式可以表述复杂的逻辑，比如：production & (eu-central | eu-west).

如果应用启动的时候没有配置好的活跃参数。那么就使用默认的配置。下面的例子中，我们为spring.secruity.user.password设置了一个密码。这个密码只在默认配置中有效:

```
server:
  port: 8000
---
spring:
  profiles: default
  security:
    user:
      password: weak
```

然而，下面的列子中。密码永远会被设置好，因为它是默认配置

```
server:
  port: 8000
spring:
  security:
    user:
      password: weak
```

通过spring.profiles指定的spring 配置可以通过!符合忽略。如果有一个未加!的配置和一个加了!的配置同时存在于同一个文件中。那么至少一个未加!的配置会被应用。而加了!也许会匹配成功

#### YAML缺点

yaml中的配置不能够用@PropertySource注解加载。在这种情况下，如果需要在有PropertySource类中加载配置的值的话，不能使用yaml文件。而需要使用属性文件。

在详细配置	YAML文件中使用多个YAML文档语法会导致不可预期的而错误。举例：假设application-dev.yml中有如下配置，然后启用的配置文件是dev:

```
server:
  port: 8000
---
spring:
  profiles: !test
  security:
    user:
      password: weak
```

如上，配置会被忽略并且配置表达式并不会如预期一样表现出来。我们建议开发人员不要同时使用简要配置YAML文件和多个YAML文档同时使用。而是只是用他们其中一个。

### 类型安全的配置参数

使用@Value("${property}")注解来注入配置中的参数值有时候会显得非常笨重。特别是当你有多个参数的时候。或者是你的参数值是继承得来的，spring boot提供了额外的和配置参数打交道的方式。这个方式就是专门实例化某些bean来管理和验证这些参数。因为这些bean有一个特点就是与这些参数高度吻合。如下:

```
package com.example;

import java.net.InetAddress;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

import org.springframework.boot.context.properties.ConfigurationProperties;

@ConfigurationProperties("acme")
public class AcmeProperties {

	private boolean enabled;

	private InetAddress remoteAddress;

	private final Security security = new Security();

	public boolean isEnabled() { ... }

	public void setEnabled(boolean enabled) { ... }

	public InetAddress getRemoteAddress() { ... }

	public void setRemoteAddress(InetAddress remoteAddress) { ... }

	public Security getSecurity() { ... }

	public static class Security {

		private String username;

		private String password;

		private List<String> roles = new ArrayList<>(Collections.singleton("USER"));

		public String getUsername() { ... }

		public void setUsername(String username) { ... }

		public String getPassword() { ... }

		public void setPassword(String password) { ... }

		public List<String> getRoles() { ... }

		public void setRoles(List<String> roles) { ... }

	}
}
```

前面的POJO定义了下面的一些参数:

acom.enabled.默认值是false,
acme.remote-address,InetAddress 继承自String
acme.security.username,嵌套了一个Security类型。类型中的那么字段由配置参数的name属性决定。
acme.security.password.
acme.security.roles.字符串类型的集合。

> 。get和set方法通常都是强制性的。但是自从通过标准java bean属性描述器绑定属性以来，下面的set方法却可以省略：

```
1.地图,一旦他们初始化了之后。他们只需要get方法。但并不必须set方法。
2.集合或者时数组。
3.嵌套pojo.
```

> 某些朋友使用Lombok来添加自动添加get和set方法。请确保lombok在自动添加的时候不会附带生成一些特殊的构造函数。因为他们会被容器用来实例化对象。最后只有标准java bean属性会被使用。并且不支持静态属性注入。

你同样需要创建属性类来承接由@EnabledConfiguation注解带来的属性。

```
@Configuration
@EnableConfigurationProperties(AcmeProperties.class)
public class MyConfiguration {
}
```

当有@ConfigurationProperties注解的bean是由上面这种方式注册的时候。通常这个bean就叫做：<prefix>-<fqn>

下面的配置创建了一个常规的bean AcmeProperties.我们建议@ConfigurationProperties只用来配置环境中的参数。但是并不配置常规的bean.一定要记住@EnableConfigurationProperties注解会自动配置到你的应用中。这样每一个带有@ConfigurationProperties注解的bean都会从系统环境中配置。不需要配置@EnableConfigurationProperties(AcmeProperties.class)到你的配置类中。你只需要如下操作即可：

```
@Component
@ConfigurationProperties(prefix="acme")
public class AcmeProperties {

	// ... see the preceding example

}
```

上面的这种与yaml文件结合得非常好：

```
acme:
	remote-address: 192.168.1.1
	security:
		username: admin
		roles:
		  - USER
		  - ADMIN
```

你也可以通过下面得方式使用@ConfigurationProperties注解：

```
@Service
public class MyService {

	private final AcmeProperties properties;

	@Autowired
	public MyService(AcmeProperties properties) {
	    this.properties = properties;
	}

 	//...

	@PostConstruct
	public void openConnection() {
		Server server = new Server(this.properties.getRemoteAddress());
		// ...
	}

}
```

### 第三方配置

与使用@ConfigurationProperties一样的是。你也可以把他用在@Bean方法中。如果你想要绑定某些属性到第三方组件中得时候。这种方式就非常有用了。为了用应用环境中得参数配置某一个bean.你同样可以添加@ConfigurationProperties到你得配置类中。如下：

```
@ConfigurationProperties(prefix = "another")
@Bean
public AnotherComponent anotherComponent() {
	...
}
```

从上面可以看到。任何prefix = another的属性会被配置到AnotherComponentbean中。这就和前面的AcmeProperties类似。

### 轻松绑定

spring boot使用一些轻松的规则来绑定系统环境中的参数到有@ConfigurationProperties注解的bean中。因此bean中的名称和系统环境中的名称可以不相同。下面就是一个例子。他们使用了点号分隔符。context-path会被绑定到contextPath中。也会寻找雷同的应用环境参数(比如：PORT会被绑定到port)

```
@ConfigurationProperties(prefix="acme.my-project.person")
public class OwnerProperties {

	private String firstName;

	public String getFirstName() {
		return this.firstName;
	}

	public void setFirstName(String firstName) {
		this.firstName = firstName;
	}

}
```

了解下下面的例子:

```
acme.my-project.persion.first-name       //烤串式写法,
acme.myProject.person.firstName			 //标准驼峰写法
acme.my_project.person.first_name        //下划线写法,这种模式是标准模式的
ACME_MYPROJECT_PERSON_FIRSTNAME          //一般定义系统变量使用这种写法
```

> 前缀用法必须使用烤串式写法(小写，用-分隔)

下面是一些配置使用的写法:

name | 价格 |  数量  
香蕉 | $1 | 5 |
苹果 | $1 | 6 |
草莓 | $1 | 7 |
