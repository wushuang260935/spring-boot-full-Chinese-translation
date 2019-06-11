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

很多spring boot支持的库会使用缓存来提供效率。比如：模板引擎为了避免重复编译同一个文件，会在在编译的时候缓存模板，Spring MVC和http也会有缓存。虽然缓存在生产模式很有用。但是在开发阶段却是相反的。然而，spring-boot-devtools默认就带了禁用缓存的功能。缓存通常会配置在application.properties文件上。比如:thy
