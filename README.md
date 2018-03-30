> 让你在消费dubbo服务或者发布dubbo服务时可以脱离spring环境,同时也可以在无服务接口时进行消费,具体可参照**How2UsingExample**这个类

> 部分代码采用**scala**编写, 需要具备**scala**的一些知识, 没用到特别复杂的

#### 发布一个服务

* DubboProvider
* 利用dubbo的SPI机制在发布时可以将此信息额外上传到某个地方,然后这地方组装返回数据再装载到RuleHolder中,现在只是简单打印,现在**APrintExporterListener**只是简单的打印出接口信息

#### 消费一个服务

- classpath下存在接口鍥约
    * DubboProxy
- classpath下不存在接口鍥约
    * DubboConsumer
    
#### 如何组装RuleHolder

- key 组装
> 默认以 dubbo 接口名(包括包名),方法名,group,version是个来生成 key, 具体可以参数 RuleHolder#generateKey 这个方法

#### 使用场景
- 网关
    * 将http请求转成一个具体的 UniqueServiceDef 类实例, 其请求数据变成一个 key-value 的 map 进行调用 