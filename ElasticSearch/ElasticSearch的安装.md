好久没有更新博客了，之前春节一直在家，不怎么想写博客。因为之前的系统一直有在用 ElasticSearch (以下简称 ES)，但是 ES 相关不是我整合上去的，一直想了解一下 ES 的原理和工作方式，所以今天开始更新一下 ES 系列的文章。

​    先介绍一下 ES 这个软件，Elasticsearch 是一个基于 [Lucene](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2FLucene) 库的[搜索引擎](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%E6%90%9C%E7%B4%A2%E5%BC%95%E6%93%8E)。它提供了一个分布式、支持多租户的[全文搜索](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%E5%85%A8%E6%96%87%E6%AA%A2%E7%B4%A2)引擎，具有 [HTTP](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2FHTTP) Web 接口和无模式 [JSON](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2FJSON) 文档  。从上面的描述中，我们可以看出来，ES 是一个 HTTP Web 接口的搜索引擎。Elasticsearch 可以用于搜索各种文档。它提供可扩展的搜索，具有接近实时的搜索，并支持多租户。Elasticsearch 是分布式的，这意味着索引可以被分成分片，每个分片可以有 0 个或多个副本。每个节点托管一个或多个分片，并充当协调器将操作委托给正确的分片。再平衡和路由是自动完成的。“相关数据通常存储在同一个索引中，该索引由一个或多个主分片和零个或多个复制分片组成。一旦创建了索引，就不能更改主分片的数量。(维基百科)

​    看到这里，大家伙一定会奇怪，为什么要用 ES 进行搜索呢？数据库里面也可以搜索数据啊。这个主要是因为 ES 的速度更加快，具体为什么快，等我了解完源码和你们说一下。

ES 是使用 Java 语言开发的，所以电脑上必须要有 JDK。

首先我们去官网下载 ES、Logstash (用于往 ES 里添加数据，与 ES 的版本需要一致）、ElasticHD (可视化的界面)。写这篇文章的时候，ES 的最新版本是 7.6.0，我已经把三个包都传上去了，链接：https://pan.baidu.com/s/1LeFZci_pucgqSeHu8D8zRQ 提取码：ib9m。下载完成之后，我们把所有包都解压，如下图所示。

