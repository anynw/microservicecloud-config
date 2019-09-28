springcloud配置中心
1、在配置客户端eureka地址的时候，去拉取github上最新的配置，服务端没有问题，客户端却一直取不到eureka.client.server-url.defaultZone
百度上很多人都遇到了这个问题，因配置各有千秋，具体原因并没有找到，源码中明明有defaultZone相关配置。
有兴趣的网友可以自行研究下EurekaClientConfigBean这个类。
	1.1、本人理解：serviceUrl是一个map集合key是defaultZone，value是后面配置的地址。在获取可用的zone的时候，如果我们没有配置region，那么会获取自定义的
		defaultZone，可用逗号分隔多个。而真正获取serviceUrls的是getEurekaServerServiceUrls的方法，判空，遍历循环，封装，返回等操作，，，
解决方法：去掉defaultZone，注意配置文件的中属性之间的逗号。
2、客户端没有配置相关端口。
