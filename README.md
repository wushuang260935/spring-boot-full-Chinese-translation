# spring-boot-full-Chinese-translation
spring boot全文档中文版翻译,本文档很长，github中只能显示部分

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

属性源 | 写法 | 列表  
-|-|-
属性文件 | 驼峰写法,烤串写法,下划线写法 | 标准列表写法使用[]或者逗号分隔 |
YAML文件 | 驼峰写法,烤串写法,下划线写法 | 标准列表写法或者逗号分隔 |
环境变量文件 | 全大写格式使用下划线分隔 | 变量名中如果包含数字，那么数字的前后方应该用_链接:MY_ACME_1_OTHER = my.acme[1].other |
系统属性 | 驼峰写法,烤串写法,下划线写法 | 标准列表写法使用[]或者逗号分隔 |

当你想绑定某些之到一个map集合中的时候。如果键中包含的字符不只是26个字符，也不只是数字，或者下划线的话，你需要用中括号把他们阔起来。这样能够保留他们的整体性。如果没有括号的保护，不是字母表中的字符或者数字或者下划线的字符会被自动移除。如下:

```
acme:
  map:
    "[/key1]": value1
    "[/key2]": value2
    /key3: value3
```

上面的属性中进入map的键是: /key1,/key2,key3

### 合并复杂类型

当某一个列表在不同的配置环境中有不同的配置。当我们从某一个配置环境跳转到另一个配置环境中的时候。我们就需要对原来的配置进行重载。
例如: 假设MyPojo类有两个属性name和description。两个属性的默认值是null.下面的配置类种需要一个MyPojo列表:

```
@ConfigurationProperties("acme")
public class AcmeProperties {

	private final List<MyPojo> list = new ArrayList<>();

	public List<MyPojo> getList() {
		return this.list;
	}

}
```

如果我们的配置文件中是这样的:

```
acme:
  list:
    - name: my name
      description: my description
---
spring:
  profiles: dev
acme:
  list:
    - name: my another name
```

上面的配置中假设dev模式未开启.那么list种就会默认加载name = my name的MyPojo类。但是如果dev模式开启了。那么当加载的时候,list种就会加载dev中的两个值。key1.name=dev name 1 key1.description = my description 1和key2.name = dev name 2 key2.description = dev description 2

> 上面的合并规则适合所有的属性资源而不仅仅是YAML文件。

### 属性转换

如果你的应用中有一些第三方属性。并且这些属性需要配置到你的@ConfigurationProperties中。那么spring boot就会尝试强制性的转换这些属性。把他们变成你配置类中需要的类型。并且spring boot还支持由你来自定义强制转换逻辑。你只需要实现ConversionService接口。或者你也可以通过返回一个CustomEditorConfigurer bean来自定义属性强制转换器。

> 由于这些bean这应用的早期就需要了。因此你最好限制你的自定义ConversionService中的依赖引用。基本上,你在这个service中引用的所有依赖都不会在应用创建的时候初始化。

#### 转换间隙

spring boot正在努力地支持间隙策略。如果你的应用中有一个java.time.Duration属性。那么下面的应用格式就可以使用:

> 常规的long型。它是你的Duration属性的默认类型。
> 标准ISO-8601格式
>键值对

```
@ConfigurationProperties("app.system")
public class AppSystemProperties{

	@Duration(ChronoUnit.SECONDS)
	private Duration sessionTimeOut = Duration.ofSeconds(30);
	
	private Duration readTimeout = Duration.ofMills(1000);
	
	public Duration getSessionTimeout(){
		return this.sessionTimeout;
	}
	
	public void setSessionTimeout(Duration sessionTimeout){
		this.sessionTimeout = sessionTimeout;
	}
 
 	public Duration getReadTimeout(){
 		return this.readTimeout;
 	}
 	
 	public void setReadTimeout(Duration readTimout){
 		this.readTimeout = readTimeout;
 	}
}
```

为了指定一个30秒便会过期的会话。你可以使用30,PT30S,30s三种类型。

#### 转换数据尺寸

spring框架有一个DataSize值，它允许你配置字节格式的数据。和上面的同样:

```
@ConfigurationProperties("app.io")
public class AppIoProperties {

	@DataSizeUnit(DataUnit.MEGABYTES)
	private DataSize bufferSize = DataSize.ofMegabytes(2);

	private DataSize sizeThreshold = DataSize.ofBytes(512);

	public DataSize getBufferSize() {
		return this.bufferSize;
	}

	public void setBufferSize(DataSize bufferSize) {
		this.bufferSize = bufferSize;
	}

	public DataSize getSizeThreshold() {
		return this.sizeThreshold;
	}

	public void setSizeThreshold(DataSize sizeThreshold) {
		this.sizeThreshold = sizeThreshold;
	}

}
```

你可以在配置文件中配置:10,10MB,256,256B

### 配置属性的验证

不管配置了@ConfigurationProperties的类是否配置了@Validation注解.spring boot都会尝试去验证它。你可以使用JSR-303 javax.validation 直接限制你的配置类上的注解。请确保有一个JSR-303实例在你的类路径中。示例如下:

```
@ConfigurationProperties(prefix="acme")
@Validated
public class AcmeProperties {

	@NotNull
	private InetAddress remoteAddress;

	// ... getters and setters

}
```

> 如果某一个配置类中带有@Validated注解。那么要触发这个类的验证的另一个方法就是：使用一个有@Bean注解到某一个方法中。这个方法用来创建前面说的配置类对象。

尽管对配置中的属性进行赋值的时候会做验证。但是还是我们最好把@Valid注解这个配置类中。因为这样能够保证在没有属性被找到的时候配置类的验证仍然能够触发。下面的例子基于上一个例子而来:

```
@ConfigurationProperties(prefix="acme")
@Validated
public class AcmeProperties {

	@NotNull
	private InetAddress remoteAddress;

	@Valid
	private final Security security = new Security();

	// ... getters and setters

	public static class Security {

		@NotEmpty
		public String username;

		// ... getters and setters

	}

}
```

上面的例子中，对于AcmeProperties来说@Valid本来可以不用加，因为自己已经有了@NotEmpty了，但是为了保证能够触发对Security的验证。最好还是加上

你也可以添加自定义的验证器。只需要使用@Bean注解创建出你的自定义验证器对象。但是@Bean的注解需要被定义为static。配置类是在应用的生命周期的很早的阶段被创建的。因此声明一个静态的@Bean方法,可以允许应用在还没有实例化@Configuration类的时候就可以创建出对象了。这样做可以避免早期实例化过程中产生的问题。

> spring-boot-actuator模块中有一个观测点。这个观测点可以暴露所有的@ConfigurationProperties的bean。使用浏览器访问/actuator/configprops或者具有相同工能的JMX观测点。

#### @ConfiguraztionProperties VS @Value

@Value配置文件是一个核心的容器特性。但是他并不像@COnfigurationProperties一样提供“类型安全”特性。下面的表格总结了这两个配置 的不同特性:

特性 | @ConfigurationProperties | @Value  
-|-|-
轻松绑定 | YES | NO
原数据支持 | YES | NO
SpEL评估 | NO | YES

如果你为你的组件定义了一系列属性键。我们建议你把他们定义在某一个POJO中。并且使用@ConfigurationProperties。你同样应该意识到。自从@Value并不支持轻松绑定之后，如果你想要使用环境参数来赋值。它就不是一个好的选项。最后。当你使用@Value注解写SpEL表达式的时候。这些表达式不会从应用配置文件中获取。

## 精简配置

spring 的精简配置 提供了这样的一种方式: 把你的部分应用配置分离出来。让这部分在特定的环境下才能够使用。任何@Component或者@Configuration都可以被标识为@Profile。以此来限制它的加载环境。如下所示:

```
@Configuration
@Profile("production")
public class ProductionCOnfiguration{
}
```

你可以使用一个spring.profiles.active(这是一个环境属性)来指定哪些精简配置会被加载。你也可以把spring.profiles.active定义在很多地方。比如:application.properties.
```
spring.profiles.active=dev,hsqldb
```
你也可以在启动应用的时候以命令行的形式指定哪些精简配置会被启动:
```
--spring.profiles.active=dev,hsqldb
```

### 添加活跃的精简配置

与其他配置一样,spring.profiles.active会遵循下面的顺序:最高的PropertySource(属性源)是最高顺序,这就意味着你可以在application.properties文件中指定某一个精简配置。但是你却可以通过命令行的指定方式来覆盖之前application.properties的值。

有时候，我们希望替换部分的精简配置而不是全部。那么这时候我们就使用spring.profiles.include.这个属性被用来无条件加载精简配置。SpringApplication也有一个API来设置额外精简配置。就是SpringApplication.setAdditionalProfiels()。

举一个例子：当含有下面的配置的应用在使用命令行启动的时候:--spring.profiels.active=prod,那么proddb和prodmq也会被加载:

```
my.property:fromyamlfile
spring.profiles:prod
spring.profiels.include:
- proddb
- prodmq
````

> 请注意spring.profiels也可以使用YAML文件来定义。

### 以编程方式设置精简配置

在你的应用启动之前,你可以通过调用SpringApplication.setAdditionalProfiels()方法来设置精简配置。还有一种方式就是实例化COnfigurableEnvironment接口。

### “特定的精简配置”配置文件

application.properties(application.yml)和@ConfigurationProperties的文件中都可以由“特定的精简配置”变量。
```

## 日志

spring boot使用 commons Loggings来打印所有的国际化日志。但同时也开放了底层的接口。spring boot日志的默认配置由java.Util.Logging,Log4j2,Logback提供。这几个都是默认使用控制台打印日志。

如果你使用spring boot starters。使用的日志工具是logback

> java有很多日志框架,上面的日志框架看起来很混淆.实际上你不需要调整你的日志依赖。spring boot默认的配置已经非常好了。

### 日志格式

默认的日志格式是从spring boot resemble中来的。如下:

```
2014-03-05 10:57:51.112  INFO 45469 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet Engine: Apache Tomcat/7.0.52
2014-03-05 10:57:51.253  INFO 45469 --- [ost-startStop-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2014-03-05 10:57:51.253  INFO 45469 --- [ost-startStop-1] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 1358 ms
2014-03-05 10:57:51.698  INFO 45469 --- [ost-startStop-1] o.s.b.c.e.ServletRegistrationBean        : Mapping servlet: 'dispatcherServlet' to [/]
2014-03-05 10:57:51.702  INFO 45469 --- [ost-startStop-1] o.s.b.c.embedded.FilterRegistrationBean  : Mapping filter: 'hiddenHttpMethodFilter' to: [/*]
```

下面的项会被打印出来:

> 日期和时间: 精确到毫秒并且以排序
> 日志级别： ERROR,WARN,INFO,DEBUG,TRACE
> 进程ID
> ---分隔符来区别出真正的日志开头
> 线程名:线程名使用中括号括起来
> 日志名:实际上就是打印这条日志的类名称
> 最后就是日志消息:

logback没有FATAL级别。只有ERROR级别.

### 控制台输出

默认地，日志配置会在每一条日志写入日志文件之后再把他们返回给控制台。默认地,ERROR级别,WARN级别,INFO级别的日志会被打印。你也可以打印DEBUG级别的日志。只需要再命令行后面加一个:

> java -jar myapp.jar --debug  当然你也可以在application.properties文件中配置:debug=true

当使用debug模式的时候，一系列的核心日志器(内置容器,hibernate,spring boot)会打印更多的信息,但是启用debug模式并不打印所有的DEBUG级别的日志。

你可以使用--trace标志来启用trace模式.这样就能打印trace级别的日志了。(有trace级别的日志有：内置容器,hibernate schema生成器,所有的spring portfolio)

#### 彩色打印

如果你的终端支持ANSI,就可以使用彩色打印，彩色打印的好处就是提高代码的可读性。你可以设置spring.output.ansi.enabled属性。并不常用的颜色编码可以通知%clr转换器配置。%clr(%5p)

下面是一个使用彩色打印的例子:

特性 | @ConfigurationProperties | @Value  
-|-|-
轻松绑定 | YES | NO
原数据支持 | YES | NO
SpEL评估 | NO | YES

额外地,你可以指定你想要的颜色和格式.并且把他们配置在转换器上。比如：想要把文本内容变为黄色的，你可以这样:
> %clr(%d{yyyy-MM-dd HH:mm:ss}){yellow}
除了黄色你还可以:
.blue
.cyan
.faint
.green
.magenta
.red
.yellow

### 文件日志打印

默认地:spring boot只会打印日志到控制台上而不会写到日志文件中。如果你除了打印到控制台之外还想要打印到日志文件中。你需要设置logging.file或者logging.path属性

当日志文件达到10M的时候就会被轮换掉，从新生成新的日志我呢见.由于默认的控制台输出,ERROR级别,WARN级别,和INFO级别的消息会记录在日志文件中。使用logging.file.max-size属性可以修改你的日志文件大小。如果有了logging.file.max-history属性的值，在这个值之前生成的日志文件会被删除掉.否则所有日志文件就会被一直保存。

> 日志系统会在应用的生命周期的早期阶段加载。这样就导致了:属性文件中有日志的相关配置的话,但是却使用@PropertySource注解加载属性文件.这时候日志属性还没有加载进来。

> 日志属性是独立于整个日志架构之外的。这样，具体的配置关键字比如说:logback.configuationFile才不会被spring boot纳入管理体系中。

### 日志级别

spring 环境中可以通过设置logging.level.<logger-name>=<level>来设置日志系统中的日志级别.level就是前面的那几个。TRACE,DEBUG,INFO,WARN,ERROR,FATAL,OFF,root层级的日志级别可以通过logging.level.root来配置。下面的例子展示了一些必要的日志设置:

> logging.level.root = WARN
> logging.level.org.springframework.web=DEBUG
> logging.level.org.hibernate = ERROR

### 日志群组

我们一般会把有关联的日志器配置集中到一起，这样他们便于集体调整，比如说:你可能会修改与tomcat相关的日志的级别。但是你可能不记得与tomcat日志相关的依赖包了。为了解决这个问题，spring boot允许你在spring 环境中定义日志群组。下面就是一个例子:

> logging.group.tomcat=org.apache.catalina,org.apache.cyota,org.apache.tomcat

一旦定义,你就可以修改所有的日志级别了，只需要做如下修改:

> logging.level.tomcat=TRACE

spring boot包含以下预定义日志群组。而且这些群组是不受spring 容器管理的:

> web=org.springframework.core.codec,org.springframework.http,org.springframework.web
> sql=or.springframework.jdbc.core,org.hibernate.SQL

### 自定义日志配置

把你需要的依赖引入到类路径上就能够启用其内部的日志系统。而且你也可以把自定义的日志配置文件配置到类路径中达到定制日志配置的效果。最后你还可以使用spring环境的logging.config来配置日志。

使用org.springframework.boot.logging.LoggingSystem系统属性来强制spring boot使用你指定的日志体系。org.springframework.boot.logging.LogginfSystem的值应该实现LoggingSystem接口的类的全称.当然你也可以通过把它置为空来禁用所有的spring boot日志配置。

> 从日志在应用上下文创建之前就加载的那个时候开始，通过spring的@PropertySource和@Configuration注解所在的配置文件来控制日志就是不可能的了。所以唯一能够控制系统日志属性的方法就是通过系统参数。

根据经典的应用,你需要下列日志的依赖:

日志系统|定制文件
-|-
Logback|logback-spring.xml,logback-spring.groovy,logback.xml,logback.groovy
log4j2|log4j2-spring.xml,log4j2.xml
JDK|logging.properties

>如果条件允许的话，我们建议你使用带有*-spring.xml的配置文件来配置你的日志，比如:使用logback-spring.xml而不是logback.xml.如果你使用标准配置路径。spring不能够完全地加载系统初始项。

>我们现在已知java Util logging有加载问题:如果从运行jar包中执行的话。这个包会出现问题。因此我们建议你规避它。

为了帮助你自定以日志。有很多的日志参数从spring 环境中转换到了系统配置中。如下面所示:

spring环境|系统参数|描述
-|-|-
logging.exception-conversion-word|LOG_EXCEPTION_CONVERSION_WORD|当发生日志异常的时候需要转换的文字
logging.file|LOG_FILE|如果你使用了这个参数,它会被用作默认的日志配置文件。
logging.file.max-size|LOG_FILE_MAX_SIZE|最大的日志文件大小，但是前提是启用了logging.file。并且只支持默认的logback设置
logging.path|LOG_PATH|如果你使用了这个参数，它会被用作默认的日志配置。
logging.pattern.console|CONSOLE_LOG_PATTERN|设置打印在控制台中的日志格式,只支持默认的logback设置
logging.pattern.dateformat|LOG_DATEFORMAT_PATTERN|只支持默认的logbak设置。日志时间格式设置
logging.pattern.file|FILE_LOG_PATTERN|前提是logging.file启用。支支持默认的logbak设置。日志文件中的日志格式
logging.pattern.level|LOG_LEVEL_PATTERN|只支持more你的logback设置。这个参数会根据日志级别来确定日志格式
PID|PID|当前线程的ID

你也可以通过logback,log4j2,java Util logging来仔细地了解日志系统的各个环节。

> 如果你想在日志参数中使用占位符，你应该使用spring boot语法而不是下划线语法。可以明确的是：如果你是用logback.你应该使用":"冒号作为分隔符.而不是使用-

> 通过重载LOG_LEVEL_PATTERN或者是logback中的logging.pattern.level的值你就可以添加MDC 和其他的ad-hoc内容到日志内容中。比如:如果你用:logging.pattern.level=user:%X{user} %5p 那么默认的日志格式就会包含当前日志的操作用户的MDC内容。如下所示:

```
2015-09-30 12:30:04.031 user:someone INFO 22174 --- [  nio-8080-exec-0] demo.Controller
Handling authenticated request
```

### logback扩展

spring boot包含了很多的logback扩展,这些扩展可以帮助你补充最新的日志配置属性。你可以把这些扩展放到你的logback-spring.xml中:

> 因为标准logback.xml配置文件在很早期的时候就被加载了。所以你不能再这里面添加扩展，因为应用现在还不具备识别这些扩展的能力。因此你只能选择加到logback-spring.xml中或者定义一个logging.config属性。

> 扩展还有一个局限性就是它不能和logback的配置扫描一起使用。如果你这样做，就会出现下面的配置文件错误:

```
ERROR in ch.qos.logback.core.joran.spi.Interpreter@4:71 - no applicable action for [springProperty], current ElementPath is [[configuration][springProperty]]
ERROR in ch.qos.logback.core.joran.spi.Interpreter@4:71 - no applicable action for [springProfile], current ElementPath is [[configuration][springProfile]]
```

#### 详细的简要配置

<springProfiles>标签允许你根据当前spring简要配置来引入或者排除一些配置.springprofiles标签有一个name属性。它可以指定哪一个简要配置接受下面的参数.springprofile既可以接收简要配置的名称也可以接收简要配置表达式.如:production&eu-central|eu-west.示例如下:

```
<springprofile name="staging">
	<!-- configuration to be enabled when the "staging" profile is active-->
</springprofile>
<springprofile name="dev|staging">
	<!-- configuration to be enabled when the "staging" or dev profile is active>
</springfile>
<springprofile name="!production">
	<!-- configuration to be enabled when production profile is not active>
</springfile>
```

#### 环境属性

<springProperties>标签允许你暴露出spring环境中的logback配置。如果你想从你的application.properties中获取logback的相关配置值得时候，这个暴露得方式就会非常有用了。这个标签和<property>有点类似。springProperties中得scope属性还可以规定取值范围。source属性指定从这个源中获取值。还有默认值defaultvalue,示例如下:

```
<springProperties scope="context" name="fluentHost" source="myapp.fluentd.host" default="localhost"/>
<appender name="FLUENT" class="ch.qos.loback.more.appenders.DataFluentAppender">	 
	<remoteHost>${fluentHost}</remoteHost>
	...
</appender>


```

## 国际化

spring boot支持信息本地化，这样可以满足应用的不用语言需求。默认地，spring boot会去类路径中的最顶层寻找messages配置(也就是本地化信息的相关配置)。
就像其他属性一样。我们使用spring.messages来配置我们的信息属性。

```
spring.messages.basename=messages,config.i18n.messages
spring.messages.fallback-to-system-locale=false
```

> spring.messages.basename支持逗号分隔

## JSON

spring boot 支持下面的json工具：

> Gson
> Jackson
> JSON-B

其中默认使用的是Jackson

### Jackson

默认配置就是使用的Jackson并且Jackson是spring-boot-starter-json的一部分。如果你的应用的类路径中有Jackson。那么spring boot会自动装配ObjectMapper.

### Gson

Gson也是自动装配的一部分。如果你的应用的类路径中有Gson。那么Gson对象会自动配置。你可以使用spring.gson.*来对Gson进行自定义配置。如果你还想控制Gson的更多属性。可以使用一个或者多个GsonBuilderCustomizer类。

### JSON-B

和前面的都很类似。如果类路径中有jsonb。那么Jsonb类就会被创建。


## spring boot扩展web应用


### 扩展spring web MVC框架

spring boot非常适合web应用开发。通过使用内置的tomcat/jetty/undertow/netty.你可以创建一个自包含的HTTP服务。大多数web应用使用spring-boot-starter-web实现快速开发。你也可以通过使用spring-boot-starter-webflux来创建一个响应式web应用。

#### spring web MVC框架

简称springMVC,允许你创建特殊的@Controller和@RestController类来处理	HTTP请求。

####  springMVC自动配置

spring boot为springMVC提供了自动装配。下面是自动装配提供的一些例子:

> 内含了ContentNegotatingViewResolver,BeanNameViewResolver,MessageCodesResolver.
> 提供对静态资源的服务。包括对index.html,Webjars的服务都可以。
> Convertor,GenericConverter,HttpMessageConverters,Formatter的自动注册
> 支持自定义favicon
> 自动使用了ConfiguableWebBindingInitializer

如果你在保留spring boot MVC特性的同时还想额外的MVC配置。（比如拦截器(interceptor,格式化(formatters),视图控制器view controller等等).你可以添加你自己的WebMvcConfigurer类型的配置类(@Configuration class)但是不能使用@EnableWebMvc。如果你使用了@EnableWebMvc那么spring boot MVC的特性就不会使用。如果你想要添加你自定义的RequestMappingHandlerMapping,RequestMappingHandlerAdapter,或者是ExceptionHandlerExceptionResolver,你可以这样做:实例化一个WebMvcRegistrationsAdapter来提供上述组件。

#### HttpMessageConverters

SpringMVC使用HttpMessageConverter接口来转换http请求和响应。对于一些默认值开箱即用。比如说:对象可以很轻松地转换为JSON或者XML。(默认使用UTF-8格式)

如果你想自定义转换器。你可以使用HttpMessageConverters这个类。例子如下:

```
import org.springframework.boot.autoconfigure.http.HttpMessageConverters;
import org.springframework.context.annotation.*;
import org.springframework.http.converter.*;

@Configuration
public class MyConfiguration{
 @Bean
 public HttpMessageConverters customConverters(){
 	HttpMessageConverter<?> addtional = ...;
 	HttpMessageConverter<?> another = ...;
 	
 	return new HttpMessageConverters(addtional,another);
 }
}
```

上面的例子中，你可以把任何你想添加的HttpMessageConverter都放到里面去。

#### 自定义JSON序列化和额反序列化算法

如果你使用Jackson来序列化和反序列化数据。那么你有可能想要自定义自己的序列化和反序列化类。spring boot 提供了一个@jsonComponent注解来注册这个序列化/反序列化类。

所有在应用上下文(ApplicationContext)的@jsonComponent都会被自动注册并且服务Jackson格式。

当然spring boot中处理Jackson有标准的序列化工具：JsonObjectSerializer,jsonObjectDeserializer。

#### 消息编码解析器MessageCodesResolver

SpringMVC有一个针对错误的策略:spring boot会把已绑定的错误信息交给MessageCodesResolver处理。并生成带有一定格式的错误信息。只需要配置spring.mvc.message-codes-resolver.format属性的PREFIX_ERROR_CODE或者配置POSTFIX_ERROR_CODE.

#### 静态资源

springboot默认对应用根路径/static或者/public或者/META-INF/resource路径提供静态资源支持。springboot使用ResourceHttpRequestHandler来处理静态资源请求。这个handler是从springMVC中来的。你可以通过添加你自己的WebMvcConfigurer来修改他本身的相关操作。这里面最重要的就是修改addResourceHandlers方法。
你也可以配置自定义静态路径:

>spring.mvc.static-path-pattern=/resources/*8

你也可以使用 这个:

> spring.resources.static-locations。默认使用的是/也就是根路径

以上除了传统的静态资源以外，还有一种情况就是给Webjar提供静态资源。WebJar中静态资源一般在路径/webjars/**中。

>webjar中不能使用src/main/webapp路径。虽然他是一个标准的web路径。但是它只能在普通jar包中使用。

对于那些高级的springMVC资源处理特性。springboot同样支持。比如缓存。

#### 欢迎页面

springboot同时支持静态和模板页面。首先会在配置的静态资源路径中寻找index.html页面。如果没有找到。那么就会找index模板。如果都没有找到。那么就会走正常的index请求。

#### 自定义Favicon

spring boot会在静态资源路径和应用根目录中寻找favicon.ico。 	

#### 路径匹配和内容过滤

SpringMVC能够把到来的HTTP请求集合到请求处理器中。怎么做到的呢，就是通过检验请求路径，把它们一个个都分类到相应的匹配期中。举个例子：我们经常用的getMapping注解就具有给到来的请求分类的能力。

 默认地，springboot会禁用后缀匹配。也就是说类似于"/springboot.json"不会匹配到getMapping("/springboot")请求处理器中。这种匹配方式过去被称作最佳springMVC应用实践。应为这种匹配方式可以用来过滤那些请求头不正确的请求。而以前我们需要确保我们受理的请求是符合我们规范的。但是现在呢。我们觉得内容协商会更加靠谱一些。

现在我们有了其他的方式来检验到来的请求是否配置了正确的请求头。那就是在请求路径后面加上一段查询参数。比如:"/springboot?format=json"会被配置成匹配到请求getMapping("/springboot")中。

```
spring.mvc.contentnegotation.favor-parameter=true

# 我们可以改变参数名称。（默认的名称是format)：spring.mvc.contentnegotation.parameter-name=format

#我们也可以自定义一个后缀文件名:spring.mvc.contentnegotation.media-types.markdown=markdown

```

但是如果你仍然喜欢使用后缀来过滤相关请求。那么就需要设置下面的配置:

```
spring.mvc.contentnegotation.favor-path-extension=true
spring.mvc.pathmatch.use-suffix-pattern=true
```

另外，相对于开放所有的后缀格式。使用自己定义的后缀格式会更加安全:

```
spring.mvc.contentnegotation.favor-path-extension=true
spring.mvc.pathmatch.use-registered-suffix-pattern=true

你也可以使用下面的配置来注册额外的文件后缀/格式
spring.mvc.contentnegotation.media-types.adoc=text/asciidoc
```

#### 可配置网络绑定加载器(ConfigurableWebBindingInitializer)

对于某些特殊的HTTP请求，springMVC使用WebBindingInitializer来加载网络信息绑定器(WebDataBinder).如果你创建了自己的ConfigurableWebBindingInitializer，那么springboot就会自动配置到spring MVC中

#### 模板引擎

与REST web service一样，你同样可以使用springmvc来处理动态网页内容。springmvc支持很多的模板技术。包括thymeleaf,freemarker,jsps,以及包括springmvc自己和其他的一些引擎。

springboot提供下列引擎的自动装配支持

> freemarker
> groovy
> thymeleaf
> mustache

请尽量避免使用JSPs,目前所知，使用JSPs和内置servlet结合使用时会有很多的限制。

如果使用这些引擎的时候使用的是默认配置，那么你的静态模板会自动从/src/main/resources/templates路径中获取

你在运行你的应用的时候需要注意一个细节。IntelliJ IDEA 对于类路径(classpath)的排序有所不同。相比于使用maven或者graddle或者直接jar包启动你的应用，直接使用IDE中的main方法来启动项目会导致不同的类路径排序。这种差异可能会导致springboot找不到类路径的模板。如果发生了这种问题，需要调整IDE中的类路径排序。把相关模板资源置为首位。另外，你可以配置模板前缀(比如templates)，这样可以搜索所有包含这个前缀的目录：classpath*:/templates/.

#### 错误处理

默认地，springboot以敏感的方式为所有的错误提供了一个/error映射器。它在servlet容器中被注册成了一个全域错误页面。对于非浏览器客户端，页面会返回一个HTTP状态码，异常信息，以及一个包含错误详情的json格式的响应。而对于，浏览器客户端，会返回一个白色页面的视图，视图中包含一些简单的信息。(如果你想自定义这个视图，可以添加一个解析到error的视图).为了完全覆盖默认的错误处理流程，你可以实例化ErrorController并且用@bean注解来注册这个实例。你也可以实例化一个ErrorAttributes对象。这个对象只会覆盖错误内容，但是会使用原来的错误处理机制。

基础错误控制器(BasicErrorController)可以用作自定义错误控制器的基础类。这对于你想要添加一个新类型处理器非常有用(我们默认的处理类型是text/html，那么我们可以自定义一个错误类）。因此，扩展BasicErrorController,添加一个有@RequestMapping注解(注解中需要使用produces属性)的方法。在方法中创建你定义的错误类。

如果是为你的处理错误的controller返回特殊的JSON内容，你可以自定义一个类(注解成@ControllerAdvice)来自定义JSON文档。例子如下:

```
@ControllerAdvice(basePackageClasses	= AcmeController.class)
public class AcmeControllerAdvice extends ResponseEntityExceptionHandler {
 @ExceptionHandler(YourException.class)
 @ResponseBody
 ResponseEntity<?> handleControllerException(HttpServletRequest request,Throwable ex){
  HttpStatus status = getStatus(request); 
  return new ResponseEntity<>(new CustomErrorType(status.value(),ex.getMessage()),status);
 }
 
 private HttpStatus getStatus(HttpServletRequest request){
  Integer statusCode = (Integer) request.getAttribute("javax.servlet.error.status_code");
  if(statusCode == null){
 	return HttpStatus.INTERAL_SERVER_ERROR; 
  } 
  return HttpStatus.valueOf(statusCode);
 }
}
```

接下来。你的错误信息会被定义在相同路径中的AcmeController抛出来。格式就是一个CustomErrorType的json。而不是ErrorAttributes。

##### 自定义错误页面

如果你需要自定义一个特定错误码的页面。你可以在/error路径中添加一个页面。自定义页面可以是静态页面也可以是动态页面(可以使用模板引擎)。但是文件名称可以是那个特定的错误码也可以是错误集。例如404错误如下:

```
sr/
	main/
		java/
		resources/
			public/
				error/
					404.html
```

5xx错误如下:

```
src/
	main/
		java/
		resource/
			templates/
				error/
					5xx.ftl
```

对于其他比较复杂的映射。你同样可以实例化一个实现了ErrorViewResolver接口的类来处理。例子如下:

```
public class MyErrorViewResolver implements ErrorViewResolver {
	@Override
	public ModelAndView resolveErrorView(HttpServletRequest request,HttpStatus status,Map<String,Object> model){
		return ...
	}
}
```

你也可以使用常规的springmvc特性，比如@ExceptionHandler方法和@ControllerAdvice类。ErrorController就会处理任何未处理的错误。

##### 非springmvc映射错误页面

对于非springmvc应用，你可以使用ErrorPageRegister接口来直接注册ErrorPages对象.这个抽象类会直接和内置servlet容器工作。例子如下:

```
@Bean 
public ErrorPageResiger errorPageRegister{
	return new MyErrorPageRegistrar();
}

private static class MyErrorRegistrar implements ErrorPageRegistrar{
	
	@Override
	public void registerErrorPages(ErrorPageRegistry registry){
		registry.addErrorPages(new ErrorPage(HttpStatus.BAD_REQUEST,"/400"));
	}
}
```

如果你注册了一个会被过滤器处理的ErrorPage类。(这种情况在非springmvc中非常常见).那么这个过滤器需要被注册成为错误分发器。例子如下:

```
@Bean
public FilterRegistrationBean myFilter{
	FilterRegistrationBean registration = new FilterRegistration();
	registration.setFilter(new MyFilter());
	...
	registration.setDispatcherTypes(EnumSet.allOf(DispatcherType.class));
	return registration;
}
```

请注意默认的FilterRegistrationBean没有包含ERROR分发器。

请注意: 当被部署到一个servlet容器中时。springboot使用它本身的错误页面过滤器来映射此错误请求到对应的错误页面。只有当请求的响应还没有被提交时，请求才会被映射到指定的错误页面上。我们了解到。WebSphere服务器8.0及后续版本会在servlet方法执行成功过后提交响应。你可以通过设置com.ibm.ws.webcontainer.invokeFlushAfterService 为false来禁用提交。

#### spring HATEOAS风格

。。。。

#### 跨源共享(CORS)支持

大多数浏览器都实现了跨源共享从而实现跨域。springmvc4.2以后开始支持跨源共享。在你的springboot应用中把与跨源共享有关的注解@CrossOrigin加到你的controller方法上就可以了并不需要其他特别的配置。

通过注册一个自定义了方法addCorsMappings(CorsRegistry)的bean WebMvcConfigurer，我们可以实现全局跨域共享。例子如下:

```
@Configuration(proxyBeanMethod = false)
public class MyConfiguration {
	@Bean
	public WebMvcConfigurer(){
		@Override
		public void addCorsMappings(CorsRegistry registry){
			registry.addMapping("/api/**");		
		}	
	}
}
```

### spring webflux 框架

在spring framework5.0中出现了一个叫做webflux的新式响应式web框架。与springmvc不一样的是。webflux是高度异步和无阻赛式的。webflux通过响应式计划[reactor project](https://projectreactor.io/)实现了它的响应式管道。webflux有两种风格:函数式和注解式。注解式与springmvc非常类似。如下:

```
	@RestController
	@RequestMapping("/users")
	public class MyController{
		@GetMaping("/{user}")
		public <Mono> getUser(@PathVariable Long user){
			
		}
	}
```

'webflux.cn',如下所示，函数式变体就是把每一个请求一个个分割起来配置：

```

	@Configuration(proxyBeanMethods = false)
	public class RouteConfiguration {
		@Bean
		public RouterFunction<serverResponse> monoRouterFunction(UserHandler userHandler){
			return route(GET("/{user}").and(accept(APPLICATION_JSON)),userHandler::getUser)
				  .andRoute(GET("/{user}/customers").and(accept(APPLICATION_JSON)),userHandler::getUserCustomers)
				  .andRoute(DELETE("/{user}").and(accept(APPLICATION_JSON)),userHandler::deleteUser);
		}
	}
	
	@Component
	public class UserHandler {
		public Mono<serverResponse> getUser(ServerRequest request){
			//...
		}
		public Mono<ServerResponse> getUserCustomers(ServerRequest request){
			//...
		}
		public Mono<ServerResponse> deleteUser<ServerRequest request){
			//...
		}
	}
```

WebFlux属于springframework的一部分。详情请看[参考信息](https://docs.spring.io/spring/docs/5.2.1.RELEASE/spring-framework-reference/web-reactive.html#webflux-fn)

> 你可以定义很多的函数式变体(RouterFunction)来模块化路由器。另外，如果你需要调整优先级别，这些函数式变体是可以排序的。

你可以添加spring-boot-starter-webflux启动器来开始你的webflux之旅。

> 如果你同时添加spring-boot-starter-webflux和spring-boot-starter-web到你的应用中。那么就会导致springboot自动配置springmvc而不是webflux.
> 但是这种行为是无法避免的。因为很多开发人员需要在springmvc应用中使用webflux启动器中的响应式webclient.
>为了解决这个问题。你可以在springApplication中这样设置:SpringApplication.setWebApplicationType(WebApplication.REACTIVE).

#### webflux自动配置

springboot为webflux提供的自动配置可以在大多数应用中工作的很好。

springboot的自动配置会把下面的属性加在spring默认配置的最上面:

> 为HttpMessageReader和HttpMessageWriter的实例配置codecs
> 提供静态资源的支持，包括对webjar的支持

如果你想在保持webflux属性的同时也想添加额外的webflux配置。你可以这样做:添加一个自定义的WebFluxConfigurer类。把它设置为@Configuration类。但是不能设置为@EnableWebFlux

当然，如果你想完全控制spring webflux,那么你在把WebFluxConfigurer类设置为@Configuration类之后，就添加@EnableWebFlux吧

#### 带有HTTP Codecs的HttpMessageReaders和HttpMessageWriters 

webflux使用HttpMessageReaders和HttpMessageWriters接口来转换HTTP的请求和响应。他们会被配置成带有CodecConfigurer接口信息的请求和响应。带有CodecConfigurer接口信息的请求和响应有这样的一种特点:会通过查看你的classpath的库来配置一些敏感信息。

springboot也为codecs提供了专门的application.properties中配置:spring.codec.*.并且，你也可以通过使用CodecCustomizer实例来配置更多的自定义属性。举个例子:有一个spring.jackson.*的属性是给jackson的codec配置的。

如果你需要添加和自定义codecs.你可以创建一个自定义的CodecCustomizer接口的实例。下面就是一个例子:

```
import org.springframework.boot.web.codec.CodecCustomizer;

@Configuration(proxyBeanMethods = false)
public class MyConfiguration {
	@Bean
	public CodecCustomizer myCodecCustomizer(){
		return codecConfigurer->{
			//...
		};
	} 
}
```

#### 静态内容

默认地,springboot从一个在classpath中名叫/static（/public or /resources or /META-INF/resource)的目录中提供静态服务。因此如果你使用的是webflux.那么就需要使用ResourceWebHandler来修改这种默认设置。方法就是添加你自己的WebFluxCOnfigurer实例并覆盖addResourceHandlers方法。

默认地,静态资源资源会被自动匹配成/**(爷就是默认根目录下),但是这也是可以改的:通过设置spring.webflux.static-path-pattern属性。示例如下:

> spring.webflux.static-path-pattern=/resources/**

这样你就可以把webflux的静态资源目录变成/resources。

当然这里还有另一个办法。那就是设置spring.resources.static-locations属性来改变静态目录。并且，你可以把这个属性的值设置成多个静态目录。设置好这个值之后，默认的欢迎页面就会去你设置的目录或者多个目录中寻找。如果静态目录中有一个index.html。那么它就会成为主页。

除了上面列出来的“标准”静态目录之外。有一个特殊的地方就是webjar的静态内容：如果一个jar文件被打包成了webjar。那么它里面的资源目录就是/webjars/**。

> webflux应用并不严格依赖servlet API。所以他不能被打包成war文件。因此它不能使用src/main/webapp目录。


#### 模板引擎

与REST web services一样。webflux同样也可以处理动态html内容。因为webflux同样支持模板引擎。包括：thymeleaf,freemarker,mustache.

另外，springboot也对下面的模板引擎提供了自动配置：

> freemarker,thymeleaf,mustache

当你使用他们中任意一个的默认配置的时候。你的模板会自动从src/mairesources/templates中获取。


#### 错误处理

springboot提供了一个叫做WebExceptionHandler的接口来敏感地处理各种错误。如果你的应用中有WebExceptionHandler的接口实例。那么这个实例在请求的处理过程中，它是排在webflux处理器(handlers)的前面的。如果请求的发送方是一个服务器。它就会返回一个带有错误详情，HTTP状态，以及这个错误的消息(exception message)的json。如果请求的发送方式一个浏览器。他就会把错误详情，HTTP状态，错误消息(exception message)做成一个HTML返回回来。当然，这个错误页面我们是可以自定义的。那么怎么实现呢

首先： 我们可以添加一个叫做"ErrorAttributes"的bean。(这个与我们传统的做法有区别。传统上，我们会替换或者添加一个更加美观的错误内容上去）

然后我们需要改变一下错误处理的流程:实现spring boot原生的ErrorWebExceptionHandler接口 并注册成实例。或者直接使用更高级AbstractErrorWebExceptionHandler抽象类。这个类比较符合webflux的风格。下面是一个例子:

```
public class CustomErrorWebExceptionHandler extends AbstractErrorWebExcetpionHandler{
	//define constructor here
	
	
	
	@Override
	protected RouterFunction<serverResponse> getRoutingFunction(ErrorAttributes errorAttributes){
		return RouterFunctions.route(aPredicate,aHandler)
						   .andRoute(anotherPredicate,anotherHandler);
	}
}
```

其实我们还提供了一个简单的处理实例，那就是：DefaultErrorWebExceptionHandler。你可以直接使用它


#### 自定义错误页面

针对某一个特定的错误码，如果你想返回自定义的错误页面的话，可以添加一个/error的文件夹，错误页面可以是静态页面，也可以嵌有模板引擎，只是页面的名称必须是错误码或者是错误码模糊匹配(比如5xx.mustache可以模糊匹配500等错误)

```
	src/
		main/
			java/
			resources/
			public/
			error/
				404.html
```

如果是模糊匹配的话就需要像这样:

```
	src/
		main/
			java/
			resources/
				templates/
					error/
						5xx.mustache
```

### web过滤器

webflux提供了一个WebFilter接口(这里的WebFilter是用来国旅request response exchange的，和mvc的不一样).它的实例如果存在于应用上下文中的话，就会自动去国旅每一个exchange.

webflux之间的顺序是很重要的，因此我们提供了@Order注解或者直接实现ordered接口来进行排序。

当然如果你没有自定义顺序，那么可以参考下面的表格来判断过滤器的顺序:

web Filter | order
-|-
MetricsWebFilter | Ordered.HIGHEST_PRECEDENCE + 1
WebFilterChainProxy(Spring Security) | -100
HttpTraceWebFilter | Orded.LOWEST_PRECEDENCE - 10;

### JAX-RS 和 Jersey

如果你更喜欢JAX-RS编码模型。那么除了springmvc之外，你还可以使用JAX-RS和Jersey中任何一个得实例。因为他们使用是开箱得。CXF要求你把Servlet和Filter注册成为bean.springboot也对jesery提供了支持。也就是说，jesery有一个启动器(starter)

你的项目中除了要有spring-boot-starter-jersey之外。还需要有一个实现ResourceConfig接口的bean。因为需要用它来加载一些端点。

```
	@Component
	public class JerseyConfig extends ResourceConfig{
		public JerseyConfig(){
			register(Endpoint.class);
		}
	}
```

```
	jersey在支持扫描可执行项目方面能力非常有限。 比如：它不能在可执行jar包中或者WEB-INF/classes中扫描端点。因此为了解决这个问题，我们就需要这样：我们的项目中不能使用"包"级方法。并且端点必须使用“注册”级方法单独注册。例子如下所示:
```

更进一步地自定义，你可以随意地注册多个实现了ResourceConfigCustomizer接口的bean。所有注册的端点(endpoints)应该被同时标记为@GET等类型的HTTP自愿注解和@Component注解。例子如下:

```
	@Component
	@Path("/hello")
	public class Endpoint{
		@GET
		public String Message(){
			return "hello";
		}
	}	
```

从端点(Endpoint)成为spring组件之后。它的生命周期就会被spring管理了。所以在端点里面可以使用@Autowired来注入它需要的依赖。以及使用@Value注解来注入我们已经有的配置。默认地，Jesery会被注册和映射到/*路径。那么如果想要修改它的映射路径。就需要在你的ResourceConfig接口实例中添加@ApplicationPath。


通常情况下，Jersey会被设置为一种servlet。这个servlet属于ServletRegistrationBean类型。它通常被叫做JeseryServletRegistration.

这个servlet一般是懒加载。但是修改的话就需要设置spring.jersey.servlet.load-on-startup.

如果你要覆盖或者他们的话，新建一个名称一模一样的实体就行。

过滤器也可以代替servlet，只需要设置:spring.jersey.type=filter.

过滤器(Filter)有顺序注解@Order.你也可以设置顺序:spring.jersey.filter.order.

不管是filter还是servlet。我们都可以通过使用spring.jersey.init.*的方式来来指定一系列的属性。这些属性用来提供它们的构造函数参数。


### 内置servlet容器支持

springboot提供了对某些容器的支持。tomcat,jetty,undertow。他们都有对应的启动器。我们只需要引用就可以了。他们的默认端口都是8080


### Servlets,Filters 和 Listeners

当内置容器的时候。你可以从servlet 实例中中注册他们。或者通过@Bean组件注册，也或者通过扫描servlet组件注册。	

#### 注册servlet Filter Listener

任何标题所示的实例，如果他们是一个bean，那么他们就会被拉入内置容器中。

默认地，如果上下文中只包含一个servlet(它被映射到/)。相比于多个servlet的情况。一个servlet的名称就是路径前缀，然后就成了这样:"servletName/"

如果你还想对他们进一步控制。可以使用ServletRegistrationBean,FilterRegistrationBean,ServletListenerRegistrationBean实例来进行完整控制。

通常情况下过滤器(filter)无序不会出现安全问题。但是如果你需要排序的话，就需要添加@Order注解或者实现Ordered接口。

但是请注意。如果这个Filter是由添加@Bean的方法生成的。那么这个方法上面不能添加@Order。那怎么办呢？(这里待实验，纯翻译不准确)


### servlet上下文加载机制

内置的servlet容器并不会直接之星servlet3.0+的接口或者是org.springframework.web.webapplicationInitliazer接口。

唯独onStartup方法可以操作ServletContext.甚至有时候onStartup方法可以成为操作WebApplicationInitalizer的适配器。


#### 扫描Servlets,Filters和Listeners

当我们使用内置容器时。可以通过使用@ServletComponentScan来自动注册那些注有@WebServlet,@WebFilter,@WebListener的类。	

> @ServletComponentScan在独立容器中是没有效果的，因为独立容器使用的是内置的查找机制来注册相关信息。


### ServletWebServerApplicationContext

在servlet生命周期期间，springboot会使用一种不同类型的ApplicationContext来给内置servlet容器提供支持。ServletWebServerApplicationContext就是一种特殊的WebApplicationContext。它的特点就是它可以通过“查询一个单例ServletWebServerFactory类型的bean”这个动作来重启。

需要注意的是。像：TomcatServletWebServerFactory,JettyServletWebServerFactory,UndertowServletWebServerFactory是springboot自动配置上去的。

> 通常情况下，你不需要关心这些实体类。他们大多数都是自动配置的，

### 自定义内置servlet容器

一般的servlet容器可以通过spring 环境(Environment)属性来配置。这些配置属性一般情况下可以在你的application.properties文件中配置。下面是一些常见的配置属性:

> 网络设置:server.port(用来配置监听的端口号),server.address(用来绑定接口地址).

> 会话设置:server.servlet.session.persistent(用来设置会话是否永不过期),server.servlet.session.timeout(会话过期时间).server.servlet.session.store-dir(会话中保存的本地信息).server.servlet.session.cookie.*(会话cookie设置)

> 错误管理:server.error.path(错误页面路径)

> [SSL](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/html/howto.html#howto-configure-ssl)

> 
[HTTP Compression](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/html/howto.html#how-to-enable-http-response-compression)


#### 应用控制内置容器属性

如果你想要使用应用来配置你的容器(有时候会有这种需求，程序来控制容器的一些属性).可以注册一个实现了WebServerFactoryCustomizer接口的bean。这个接口可以操作ConfigurableServletWebServerFactory.因为这个factory里面包含了很多属性的setter方法。举个例子:

```
import org.springframework.boot.web.server.WebServerFactoryCustomizer;
import org.springframework.boot.web.servlet.server.ConfigurableServletWebServerFactory;
import org.springframework.stereotype.Component;

@Component
public class CustomizationBean implements WebServletWebServerFactoryCustomizer<ConfigurableServletWebServerFactory>{
	@Override
	public void Customize(ConfigurableServletWebServerFactory server){
		server.setPort(9000);
	}
}

```

类似的还有TomcatServletWebServerFactory,JettyWebServerFactory,UndertowWebServerFactory.


#### 直接自定义ConfigurableServletWebServerFactory

如果前面介绍的解决方案仍然无法满足你的需求。那干脆自己实现ConfigurableServletWebSearverFactory接口.下面是一个简单的例子:

```

	@Bean
	public ConfigurableServletWebServerFactory webServerFactory(){
		xxxServletWebServerFactory factory = new xxxServletWebServerFactory();
		factory.setPort(8080);
		factory.setSessionTimeout(10,TimeUnit.MINUTES);
		factory.addErrorPages(new ErrorPage(HttpStatus.NOT_FOUND,"/notfound.html"));
		return factory;
	}
```

我们可以参考TomcatServletWebServerFactory,UndertowServletWebServerFactory,JettyServletWebServerFactory的实现方式，定义很多protected级别的set方法，他们就是我们操作这些factory的工具。


### 对JSP的限制

当我们使用内置servlet容器启动springboot应用时。下面是一些对JSP支持的限制:

> 再jetty和tomcat中，可以支持JSP打成war包，或者可执行war包。或者直接把编译程序放到jetty和tomcat中运行。但是可运行jar包不支持JSP。

> Undertow不支持jsp

> error.jsp不会覆盖默认的错误处理视图。


### 内置的响应式服务支持

springboot提供了下面的响应式服务支持: reactor Netty,Tomcat,Jetty,Undertow,这几个响应式服务中间件也有他们对应的starter


### 响应式服务资源配置

当我们自动配置一个Reactor jetty或者jetty服务的时候。springboot会生成他们对应的资源工厂:ReactorResourceFactory,JettyResourceFactory.这些工厂的作用就是生成一些HTTP资源供这些服务器使用。

reactor jetty和jetty客户端之间会选择性地共享某些http资源,但这是有条件的:

> 客户端和服务之间必须使用的是同一种技术

> 客户端的实例须由springboot的自动配置工具WebClient.Builder创建

开发人员如果自定义了一个ReactorResourceFactory或者JettyResourceFactory的话。就可以用他们来覆盖Jetty和Netty自己的资源配置。而且是客户端和服务同时覆盖。

详情请看[WebClient Runtime section](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/html/spring-boot-features.html#boot-features-webclient-runtime)



## RSocket

RSocket是用于字节流传输中的二进制协议，它允许对称交互模块之间在一条单连接上传输异步消息。

spring-messageing模块提供了对RSocket的请求者和响应者的支持。详情请了解[RSocket section](https://docs.spring.io/spring/docs/5.2.2.RELEASE/spring-framework-reference/web-reactive.html#rsocket-spring)

### RSocket自动配置策略

springboot为RSocketStrategies提供了自动配置。RSocketStrategies为加密和解密RSocket载体所需的所有组件提供了支持。	如下:

> 带有jackson的[CBOR](https://cbor.io/)编码

> 带有jackson的json 编码
s
spring-boot-starter-rsocket提供了这两种编码的依赖。可以参考[Jackson support section](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/html/spring-boot-features.html#boot-features-json-jackson)章节了解更多知识。

开发人员可以通过注册一个实现了RSocketStrategiesCustomizer接口的bean来自定义RSocketStrategries组件。

请注意为了调整编码器的顺序，@Order注解很重要。

### RSocket服务自动配置

springboot也为RSocket服务提供了自动配置。相应的依赖也是在spring-boot-starter-rsocket中。

springboot允许从Webflux服务的WebSocket中暴露RSocket。也可以建立一个独立的RSocket服务。

对于Webflux应用来说。只有当下面的属性匹配了之后，RSocket服务才会嵌入Web服务中。

```
	spring.rsocket.server.mapping-path=/rsocket # 定义了一个匹配路径
	spring.rsocket.server.transport=websocket #
```

> 我们只能在Reactor netty服务中嵌入Rsocket.其他的不行

另外需要说明的是: RSocket TCP或者websocket server会作为一个独立的内置服务而启动。因此除非特殊要求，我们唯一需要配置的就是服务端口号:

```
	spring.rsocket.server.port=9898 #唯一强制要求配置的属性
	spring.rsocket.server.transport=tcp #这里也可以设置其他协议
```

### spring 消息 RSocket支持

springboot将会为spring message组件自动配置

也就是说springboot会创建一个RSocketMessageHandler的bean来处理应用中的RSocket请求。


### 请求带有RSocketRequester的RSocket服务

一旦RSocket管道在客户端和服务端之间建立。任何一端都可以发送到或者接收另一端消息。

作为一个服务器(指的是RSocket 服务),在任何一个属于RSocket的controller(带有@Controller注解)的处理方法(handler method)中,你都可以向它里面注入RSocketRequester实例。

作为一个客户端,就需要事先主动和服务器建立一个RSocket连接。建立连接可以借助RSocketRequester.Builder的功能。而且Builder的相关属性由springboot自动配置


## 安全(Security)

如果你的类路径中有springSecurity.说明你的应用受springSecurity保护，springboot依赖于springSecurity的内容协商机制来决定是使用httpBasic呢还是formLogin.

如果要给应用加入方法级别的安全措施，可以添加@EnableGlobalMethodSecurity,@EnableGlobalMethodSecurity需要带上你想要的设定。详情请看[Spring Security Reference Guide](https://docs.spring.io/spring-security/site/docs/5.2.1.RELEASE/reference/htmlsingle/#jc-method)

默认的UserDetailsService有一个用户,用户名是"usear",密码是随机的，在应用启动的时候会打印在INFO级别的日志信息中:

> Using generated security password； asdkfla-asdlkfalk-asdfls

> 如果你调整了你的日志配置，请保证org.springframework.boot.autoconfigure.security策略被设置为INFO级别，否则密码打印不出来

修改username和password: spring.security.user.name,spring.security.user.password

下面是一些基本的特性:

> 一个保存在内存中的UserDeatilsService(或者webflux的ReactiveUserDetailsService)实例

> 基于表单或者基于HTTP的安全机制(这得看请求的accept是个什么类型)

> 为发布授权事件而创建的DefaultAuthenticationPublisher(这玩意可以自定义)


### MVC Security

默认的安全配置主要是在SecurityAutoConfiguration和UserDetailsServiceConfiguration中.

SecurityAutoConfiguration引入了SpringBootWebSecurityConfiguration来处理web安全问题，引入了UserDetailsServiceAutoConfiguration来处理认证问题。

如果我们需要完全关闭默认的 web application security配置。或者是我们想组合多个spring安全组件（比如说组合OAuth2组件).我们就需要添加一个叫做WebSecurityConfigurerAdapter

如果我们需要关闭UserDetailsService配置,我们需要添加一个我们自己实现了UserDetailsService和AuthenticationProvider(AuthenticationManager也可以)接口的bean。

权限规则也是可以修改的，我们只需要自定义一个实现了WebSecurityConfigurerAdapter接口的实例就可以。

对于监控端点(actuator endpoints)和静态资源(static Resources)来说,springboot提供了一些很简便的方法来修改他们的权限规则。EndPointRequest类被用来创建RequestMatcher对象。RequestMatcher对象主要依赖于management.endpoint.web.base-path属性。

PathRequest类也被用来创建RequestMatcher对象。但是它创建的RequestMatcher对象主要是用来匹配常用的本地资源。


### Webflux	Security

与springmvc应用类似,添加安全机制的相关依赖就是:spring-boot-starter-security.

默认的安全配置在ReactiveSecurityAutoConfiguration,UserDetailsServiceAutoConfiguration中.

ReactiveSecurityAutoConfiguration引入了WebFluxSecurityConfiguration来处理Web安全问题，并引入UserDetailsServiceAutoConfiguration来处理认证问题。

同样的，如果你想要完全关闭默认的security配置。	创建一个实现了WebFilterChainProxy接口的bean。如果想要关闭UserDetailsService配置添加一个自己的实现了ReactiveUserDetailsService接口或者是实现了ReactiveAuthenticationManager接口的bean。

同样的，权限规则的修改需要创建一个SecurityWebFilterChain的bean。

同样的对于监控端点(actuator endpoints)和静态资源.springboot也提供了一些简便的方法来修改他们的权限规则。也就是EndPointRequest和PathRequest

下面的例子展示出怎么通过自定义配置来改变权限规则:

```
	@Bean SecurityWebFilterChain springSecurityFilterChain(serverHttpSecurity http){
		return http
			.authorizeExchange()
			.matchers(PathRequest.toStaticResources().atCommonLocations())
			.permitAll()
			.pathMatchers("/foo","/bar")
			.authenticated()
			.and()
			.formLogin()
			.and()
			.build();
	}
```


### OAuth2

OAuth2是受spring支持的一种广泛使用的认证框架，详情请看[OAuth2](https://oauth.net/2/)


#### OAuth2客户端

如果你的类路径(classpath)中有spring-security-oauth2-client.再加上自动配置的帮助，你就可以轻松地建立一个OAuth2/openID连接客户端。

自动配置的参数来源于OAuth2ClientProperties类。这个类在servlet和响应式应用中都可以使用。

你可以注册多个OAuth2客户端并且给他们添加前缀:如下所示:

```
	spring.security.oauth2.client.registration.my-client-1.client-id=abcd
	spring.security.oauth2.client.registration.my-client-1.client-secret=password
	spring.security.oauth2.client.registration.my-client-1.client-name=Client for user scope
	spring.security.oauth2.client.registration.my-client-1.provider=我的某一个provider
	spring.security.oauth2.client.registration.my-client-1.scope=usear
	spring.security.oauth2.client.registration.my-client-1.redirect-uri=我的重定向地址
	spring.security.oauth2.client.registration.my-client-1.client-authentication-method=basic
	spring.security.oauth2.client.registration.my-client-1.authorization-grant-type=授权级别码
	//第二个客户端
	spring.security.oauth2.client.registration.my-client-1.client-id=abcd
	spring.security.oauth2.client.registration.my-client-1.client-secret=password
	spring.security.oauth2.client.registration.my-client-1.client-name=Client for user scope
	spring.security.oauth2.client.registration.my-client-1.provider=我的某一个provider
	spring.security.oauth2.client.registration.my-client-1.scope=usear
	spring.security.oauth2.client.registration.my-client-1.redirect-uri=我的重定向地址
	spring.security.oauth2.client.registration.my-client-1.client-authentication-method=basic
	spring.security.oauth2.client.registration.my-client-1.authorization-grant-type=授权级别码
	//第三个客户端
	....
```

这块由于没学习过，因此暂不翻译



## springboot搭配sql 数据库

spring框架为sql 数据库提供了大量的支持。从直接的jdbc支持(比如JdbcTemplate),到完整的ORM框架支持(比如hibernate),详情请看[spring data](https://spring.io/projects/spring-data)


### 配置一个数据源

java的"javax.sql.DataSource"接口提供了一个标准的数据库连接方法。一般地，Datasource依赖一个有一定规范的URL来获取数据库的连接.关于例子可以参考这:[how to](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/html/howto.html#howto-configure-a-datasource)


#### 内置数据源支持

如果使用内存数据库的话开发起来会非常方便。基本上内存数据库不提供持久化，因此数据只存在于应用运行期间.例子可以参考这:[how to initializ a database](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/html/howto.html#howto-database-initialization)

springboot可以自动配置内置的H2,HSQL,Derby数据库。而不必提供任何URL。只需要引入他们对应的依赖就可以。

>	如果你在测试中使用这些特性。你可能会发现你的多个应用使用的是同一个数据库。因此如果你还是想一个应用一个数据库的话，你应该设置spring.datasource.generate-unique-name=true

举例：下面是一个标准的依赖:

```
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-data-jpa</artifactId>
	</dependency>
	<dependency>
		<groupId>org.hsqldb</groupId>
		<artifactId>hsqldb</artifactId>
		<scope>runtime</scope>
	</dependency>
```

> 上面的例子中因为内置数据库需要spring.jdbc中的某些依赖才能自动配置，后来我们把这些依赖放到了spring-boot-starter-data-jpa中

> 如果出于什么原因，你确实给内置数据库配置了URL，请确保数据库的自动关闭为禁用，H2:DB_CLOSE_ON_EXIT=FALSE,HSQL:确保没有shutdown=true。确保他们被禁用是为了让springboot来控制他们的关闭。



#### 连接到产品数据库

产品数据库也可以通过数据连接池来自动配置。springboot使用下面的算法来下选择哪一个实例被使用:

> 如果有HikariCP连接池的话，我们优先使用HikariCP

> 然后是tomcat连接池

> 然后是Commons DBCP2连接池

如果你使用spring-boot-starter-jdbc 或者 spring-boot-starter-data-jpa，你就可以自动获取HikariCP的自动配置

> 如果你想修改我们的算法的话，就设置spring.datasource.type。

> 连接池随时都可以手动设置。如果你引入了你自己的DataSource，那么就不会出现自动配置啦

手动配置数据源可以通过spring.datasource.*;示例如下:

```
	spring.datasource.url=jdbc:mysql://localhost/test
	spring.datasource.username=dbuser
	spring.datasource.password=dbpass
	spring.datasource.driver-class-name=com.mysql.jdbc.Driver
```

手动配置数据源的时候至少要指定spring.datasource.url的值。否则的话springboot就认为是自动配置

> 其实spring.datasource.driver-class-name不用配置，因为现在大多数的数据库springboot可以通过url自动识别

>当springboot准备创建数据源的时候，我们需要验证driver是否可用。因此加载驱动类是第一步工作，因此如果你设置了driver-class-name的话，需要确保它可被加载进虚拟机。


对于更多关于数据源的参数可以参考DataSourceProperties类。这个类甚至加了连接池的前缀:spring.datasource.hikari.*,spring.datasource.tomcat.*,...

下面是这个类的一些参数:

```
	spring.datasource.tomcat.max-wait=10000
	spring.datasource.tomcat.max-active=50
	spring.datasource.tomcat.test-on-borrow=true
```

#### 连接到JNDI数据源

也许你的数据源需要从应用服务中获取。那么:spring.datasource.jndi-name就可以代替spring.datasource.url和spring.datasource.username和spring.datasource.password属性了。举例如下:

```
spring.datasource.jndi-name=java:jboss/datasource/customers
```

### 使用JdbcTemplate

spring的JdbcTemplate和NamedParameterJdbcTemplate类都是可以自动配置的。你可以直接@Autowired他们。

```
	import org.springframework.beans.factory.annotation.Autowired;
	import org.springframework.jdbc.core.JdbcTemplate;
	import org.springframework.stereotype.Component;
	
	@Component
	public class MyBean{
	
		private final JdbcTemplate jdbcTemplate;
		
		@Autowired
		public MyBean(JdbcTemplate jdbcTemplate){
			this.jdbcTemplate = jdbcTemplate;
		}
	}
}
```


使用spring.jdbc.template.*来自定义他们中的某些属性。


### JPA和springdata JPA

java 持久化 API是一种标准的对象关系映射技术，我们只需要引入spring-boot-starter-jpa依赖就可以开始了,它对下面的关键技术提供了支持:hibernate,spring data jpa,spring orms

这里就不深入JPA和 data JPA了。有需要可以查资料

#### 实体类

一般情况下，JPA实体类被配置成了persistence.xml文件中。但是有了springboot之后就没有必要了，而是使用实体扫描Entity Scanning.因为一般主入口类层级以下的包都会被扫描(因为入口类一般都有@EnableAutoConfiguration或者干脆是@SpringBootApplication。

并且带有@Entity,@Embeddable,@MappedSuperclass都会被扫描:

```
	import java.io.Serializable;
	import javax.persistence.*;
	
	@Entity
	public class City implements Serializable{
	
		@Id
		@GeneratedValue
		private Long id;
		
		@Column(nullable = false)
		private String name;
		
		@Column(nullable = false)
		private String state;
		
		protected City(){}
		
		public City(String name,String state){
			this.name = name;
			this.state = state;
		}
		
		public String getName(){
			return this.name
		}
		
		public String getState(){
			return this.state;
		}
	}
```


#### springdata JPA库

[spring data JPA](https://spring.io/projects/spring-data-jpa)库是一系列接口，这些接口定义了获取数据的方式。JPA查询会从你的方法名中自动创建。比如说:你创建了一个CityReposity接口。定义了一个findAllByState(String state)方法。主要用来查询某一个州的所有城市信息.请注意方法名 find All By State。有了这些关键字就可以自动创建查询语句。

当然，还有更为简便的方式，就是使用@Query注解

spring data的库基本上都是从Repository和CrudRepository接口中扩展出来的。举例如下:

```
	import org.springframework.data.domain.*;
	import org.springframework.data.repository.*;
	
	public interface CityRepository extends Repository<City,Long>{
		Page<City> findAll(Pageable pagealbe);
		City findByNameAndStateAllIgnoringCase(String name,String state);
	}
```

Spring Data JPA 支持三种启动模式: default,deferred,lazy。设置deferred和lazy启动:spring.data.jpa.repositories.bootstrap-mode=lazy.

当使用lazy模式的时候。自动配置:EntityManagerFactoryBuilder就会使用上下文中的AsyncTaskExecutor接口的实例。但是如果上下文有多个Executor的实例。就会使用applicationTaskExecutor。

















