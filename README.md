# [Spring AI Alibaba](https://sca.aliyun.com/ai/)

[中文版本](./README-zh.md)

An AI application framework for Java developers built on top of Spring AI that provides seamless integration with Alibaba Cloud QWen LLM services and cloud-native infrastructures.

## Build the code
1. Clone the master branch
2. ``` cd spring-ai-alibaba```
3. Run ``` mvn spring-javaformat:apply```
4. Run ``` mvn clean package```
 
## Get Started

Please refer to [quick start](https://sca.aliyun.com/ai/get-started/) for how to quickly add generative AI to your Spring Boot applications.

Overall, it takes only two steps to turn your Spring Boot application into an intelligent agent:

> Because Spring AI Alibaba is developed based on Spring Boot 3.x, it requires JDK version 17 and above.

1. Add 'spring-ai-alibaba-starter' dependency to your project.

	```xml
	<dependency>
		<groupId>com.alibaba.cloud.ai</groupId>
		<artifactId>spring-ai-alibaba-starter</artifactId>
		<version>1.0.0-M3.2</version>
	</dependency>
	```

	> NOTICE: Since spring-ai related packages haven't been published to the central repo yet, it's needed to add the following maven repository to your project in order to successfully resolve artifacts like  spring-ai-core.
	>
	> ```xml
	> <repositories>
	> 	<repository>
	> 		<id>spring-milestones</id>
	> 		<name>Spring Milestones</name>
	> 		<url>https://repo.spring.io/milestone</url>
	> 		<snapshots>
	> 			<enabled>false</enabled>
	> 		</snapshots>
	> 	</repository>
	> </repositories>
	> ```
	> Addendum: If the mirrorOf tag in your local Maven settings. xml is configured with the wildcard *, please modify it according to the following example.
	> ```xml
	> <mirror>
	>   <id>xxxx</id>
	>   <mirrorOf>*,!spring-milestones</mirrorOf>
	>   <name>xxxx</name>
	>   <url>xxxx</url>
	> </mirror>
	> ```

2. Inject `ChatClient`

	```java
	@RestController
	public class ChatController {

		private final ChatClient chatClient;

		public ChatController(ChatClient.Builder builder) {
			this.chatClient = builder.build();
		}

		@GetMapping("/chat")
		public String chat(String input) {
			return this.chatClient.prompt()
					.user(input)
					.call()
					.content();
		}
	}
	```

## Examples

More examples can be found at [spring-ai-alibaba-examples](./spring-ai-alibaba-examples).

* Hello World
* Chat Model
* Multi Model
* Function Calling
* Structured Output
* Prompt
* RAG
* Flight Booking Playground, an advanced example showcasing usage of prompt template, function calling, chat memory and rag at the same time.

## Core Features

Spring AI Alibaba provides the following features, read the [documentation](https://sca.aliyun.com/ai) on our website for more details of how to use these features.

* Support for Alibaba Cloud QWen Model and Dashscope Model service.
* Support high-level AI agent abstraction -- ChatClient.
* Support various Model types like Chat, Text to Image, Audio Transcription, Text to Speech.
* Both synchronous and stream API options are supported.
* Mapping of AI Model output to POJOs.
* Portable API across Vector Store providers.
* Function calling.
* Spring Boot Auto Configuration and Starters.
* RAG (Retrieval-Augmented Generation) support: DocumentReader, Splitter, Embedding, VectorStore, and Retriever.
* Support conversation with ChatMemory

## Roadmap

Spring AI Alibaba aims to reduce the complexity of building ai native java applications, from development, evaluation to deployment and observability. In order to achieve that, we provide both open-source framework and ecosystem integrations around it, below are the features that we plan to support in the near future:
* Prompt Template Management
* Event Driven AI Application
* Support of more Vector Databases
* Function Deployment
* Observability
* AI proxy support: prompt filtering, rate limit, multiple Model, etc.
* Development Tools

![ai-native-architecture](./docs/imgs/spring-ai-alibaba-arch.png)

## References
* [Spring AI](https://docs.spring.io/spring-ai/reference/index.html)
* [Spring AI Alibaba](https://sca.aliyun.com/docs/ai/overview/)
* [Alibaba Cloud Dashscope Model Service Platform (阿里云百炼模型服务及应用开发平台)](https://help.aliyun.com/zh/model-studio/getting-started/what-is-model-studio/)

## Contact Us
* Dingtalk Group (钉钉群), search `64485010179` and join.
* Wechat Group (微信公众号), scan the QR code below and follow us.

<img src="./docs/imgs/wechat-account.png" style="width:260px;"/>
