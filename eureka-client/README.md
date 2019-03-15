eureka-client 模块为 Eureka-Client 的功能实现：

com.netflix.appinfo 包：Eureka-Client 的应用配置。此处的应用指的就是上文提到的 Application Provider，Application Consumer。
com.netflix.discovery 包：Eureka-Client 的注册与发现相关功能。

com.netflix.discovery.DiscoveryClient 类：注册发现客户端实现类。
Guice (pronounced ‘juice’) is a lightweight dependency injection framework for Java 6 and above, brought to you by Google.

com.netflix.discovery.converters 包：Eureka 内部传输数据编解码转换器，支持 XML / JSON 格式。

com.netflix.discovery.endpoint 包：目前该包正在重构，和下文的 com.netflix.discovery.shared.dns 和 com.netflix.discovery.shared.resolver 用途相近。
com.netflix.disvoery.provider 包：目前仅有 DiscoveryJerseyProvider 类。该类声明自定义的 Jersey 请求和响应的序列化和反序列化实现。
com.netflix.disvoery.providers 包：目前仅有 DefaultEurekaClientConfigProvider 类。该类实现 javax.inject.Provider 接口，设置 EurekaClientConfig ( Eureka 客户端配置 ) 的生成工厂。感兴趣的同学，可以点击《Google-Guice入门介绍》搜索 Provider 关键字。
com.netflix.discovery.shared 包：Eureka-Client 和 Eureka-Server 注册发现相关的共享重用的代码。下文你会看到，Eureka-Server 通过 eureka-core 模块实现，eureka-core 依赖 eureka-client。粗一看，我们会感觉 What ？Eureka-Server 代码依赖 Eureka-Client 代码！？这个和 Eureka-Server 多节点注册信息 P2P 同步的实现有关。一个 Eureka-Server 收到 Eureka-Client 注册请求后，Eureka-Server 会自己模拟 Eureka-Client 发送注册请求到其它的 Eureka-Server，因此部分实现代码就使用到了这个包，在 《Eureka 源码解析 —— Eureka-Server 集群同步》 详细解析。

com.netflix.discovery.shared.transport 包：Eureka-Client 对 Eureka-Server RESTful 的 HTTP 客户端，基于 Jersey Client 实现。Jersey 在下文「2.1 eureka-client-jersey2」详细解析。
com.netflix.discovery.shared.dns 包 ：DNS 解析器。
com.netflix.discovery.shared.resolver 包：Eureka Endpoint 解析器。在 《Eureka 源码解析 —— EndPoint 与 解析器》 有详细解析。
com.netflix.discovery.util 包 ：工具类。