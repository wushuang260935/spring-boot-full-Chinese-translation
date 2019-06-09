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

	name | 价格 |  数量  
	-|-|-
	香蕉  | $1 | 5 |
	苹果  | $1 | 6 |
	草莓  | $1 | 7 |



	名称 | 描述 
	-|-
	spring-boot-starter | 核心starter,包括自动配置支持，日志和YAML



 
 
