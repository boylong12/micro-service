# micro-service
spring-cloud 微服务组件demo

<table>
<tbody><tr>
<td>**工程名**</td>  <td>**描述**</td>  <td>**端口**</td>
</tr>
<tr>
<td>eureka-server</td>  <td>服务发现与注册中心</td>  <td>7070</td>
</tr>
<tr>
<td>ribbon</td>  <td>负载均衡器</td>  <td>7071</td>
</tr>
<tr>
<td>config-server</td>  <td>配置管理中心</td>  <td>7072</td>
</tr>
<tr>
<td>zuul</td>  <td>动态路由器</td>  <td>7073</td>
</tr>
<tr>
<td>service-A</td>  <td>A服务，用来测试服务间调用与路由</td>  <td>7074</td>
</tr>
<tr>
<td>service-B</td>  <td>B服务，整合Mybatis、PageHelper、Redis，整合接口限速方案，可选google Guava RateLimiter与自实现</td>  <td>7075</td>
</tr>
<tr>
<td>service-B2</td>  <td>B2服务，与B服务serviceId相同，用来测试负载均衡和容错</td>  <td>7076</td>
</tr>
<tr>
<td>hystrix-ribbon</td>  <td>负载均衡器的容错测试</td>  <td>7077</td>
</tr>
<tr>
<td>feign</td>  <td>声明式、模板化的HTTP客户端，可用来做负载均衡，较轻量</td>  <td>7078</td>
</tr>
<tr>
<td>hystrix-feign</td>  <td>feign的容错测试</td>  <td>7079</td>
</tr>
<tr>
<td>hystrix-dashboard</td>  <td>hystrix可视化监控台</td>  <td>7080</td>
</tr>
<tr>
<td>turbine</td>  <td>集群下hystrix可视化监控台</td>  <td>7081</td>
</tr>
<tr>
<td>sleuth</td>  <td>服务链路追踪</td>  <td>7082</td>
</tr>
<tr>
<td>service-admin</td>  <td>spring boot admin监控台</td>  <td>7088</td>
</tr>
</tbody></table>

开发环境：JDK1.7 + maven 
<br/>说明：最好还是用1.8版本的JDK，后面高版本都是在1.8下面迭代的，注意修改pom文件中的Java.version

<br/><properties>
<br/>    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
<br/>    <java.version>1.7</java.version>
<br/>  </properties>

<br/>有关项目启动和配置的说明：
<br/>1、最先启动的是eureka-server，并且你需要在整个测试过程中保持它的启动状态，因为它是注册中心，大多数服务必须依赖于它才能实现必要的功能。 
<br/>2、如果你想测试配置中心，可以先启动config-server，再启动service-A，按照规则来获取config-server的配置信息。 
<br/>3、如果你想测试负载均衡，则需启动ribbon、service-B、service-B2工程，在ribbon中配置自己需要的负载均衡策略，配置方法见：http://blog.csdn.net/rickiyeat/article/details/64918756 
<br/>4、如果你想测试路由，则需启动zuul工程，另外需保证service-B、service-B2、service-A其中一个或者多个工程处于启动状态，按照zuul工程的配置文件来进行相应的操作。 
<br/>5、如果你想查看spring boot admin监控台，则需启动service-admin、service-B工程，注意，spring boot admin工程需至少运行于JDK8环境。 
<br/>6、如果你想测试熔断功能，则需启动hystrix-ribbon与ribbon或者feign与hystrix-feign工程。 
<br/>7、如果你想查看断路器的监控台，请启动hystrix-dashboard（单机）和turbine（集群）工程，使用方法代码注释有写。 
<br/>8、如果你想知道服务之间的调用情况，启动sleuth、service-B2、service-A。 
<br/>9、另外还有需要咨询或者项目疑难问题的的请加我的qq，页面左方。
