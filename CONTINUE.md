
#### 连接到influxDB

springboot可以自动配置一个influxDB实例。如果类路径(classpath)中提供了influxdb-java客户端的话。springboot就会自动设置一个url:

```
spring.influx.url = https://172.0.0.1:8086
```

如果还需要用户民和密码的话，我们可以依次这样设置spring.influx.user和spring.influx.password

influxDB依赖okHttp.如果需要让InfluxDb后台运行。需要注册一个InfluxDbOkHttpClientBuilderProvider类。

## 缓存

spring框架对于“向应用中提价缓存”也提供了支持。在框架的内核中就有一些抽象类了:抽象类中有操作缓存的方法。这样可以减少对有用缓存的执行数量。spring框架对缓存的操作也非常的透明。因为没有使用任何反向映射机制。

只要在spring boot应用中使用了@EnableCaching注解。springboot就会自动配置缓存的基础属性。(可以通过查看“[参考文献](https://docs.spring.io/spring/docs/5.2.4.RELEASE/spring-framework-reference/integration.html#cache)”获取更多缓存知识)


在你的应用中添加缓存是一件非常简单的事项：

```
import org.springframework.cache.annotation.Cacheable;
import org.springframework.cache.stereotype.Component;

@Component
public class MathService{
	@Cacheable("piDecimals")
	public int computePiDecimal(int i){
		//...
	}
}
```

上面这个例子表明了在一个有很大的开销的方法上使用缓存的好处（Pi还有Decimal级别，肯定需要大量的计算)。在执行computePiDecimal方法之前。抽象函数会根据参数中的i到缓存序列中查询是否有相匹配的值。如果找到了的话。就会直接返回而不会执行方法。如果没有找到的话，那么方法会被执行。但是执行完成了之后，在方法返回之前，就会更新缓存内容。

```
你也可以使用标准的JSR-107缓存注解(也就是@CacheResult).但是，我们强烈地建议你必要混用spring缓存和J缓存的注解。
```

如果你没有添加任何具体的缓存库。springboot会在内存中自动配置一个简单的缓存容器。就是线程安全的concurrent map.但它是懒加载的。只有需要缓存的时候，它才开始创建。建议这种简单的容器不应该在生产环境中使用。但是它可以供你练习，作为你了解springboot缓存特性的工具。

当你决定好使用某一个缓存容器的时候。在使用它之前请确保完全指导怎么配置这个容器。因为几乎所有的缓存容器都要求你充分配置好将要使用的每个缓存。只有一些默认的缓存配置，可以在spring.cache.cache-names属性中。