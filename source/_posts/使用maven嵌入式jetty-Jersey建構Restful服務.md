---
title: 使用maven嵌入式jetty+Jersey建構Restful服務
categories:
	- java
	- WebService
comments: true
date: 2019-03-23 11:57:34
tags: 
	- java
	- jetty
	- embeded
	- maven
	- jersey
	- restful
---
## 情境 ##
目前用嵌入式jetty練習Servlet，在學習過程中發現Restful 服務這個名詞，並發現這個Jersey這個實作服務．
這個筆記紀錄如何使用Jersey，在嵌入式jetty搭建Restful api服務．


<!-- more -->

## 環境 ##
1. jetty 9.4.15
2. Jersey 2.28
3. Java 1.8

## 步驟 ##


1. 在pom.xml設定相關要下載的套件
```xml
<!-- https://mvnrepository.com/artifact/org.eclipse.jetty/jetty-server -->
<dependency>
	<groupId>org.eclipse.jetty</groupId>
	<artifactId>jetty-server</artifactId>
	<version>9.4.15.v20190215</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.eclipse.jetty/jetty-servlet -->
<dependency>
	<groupId>org.eclipse.jetty</groupId>
	<artifactId>jetty-servlet</artifactId>
	<version>9.4.15.v20190215</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.glassfish.jersey.containers/jersey-container-servlet -->
<dependency>
	<groupId>org.glassfish.jersey.containers</groupId>
	<artifactId>jersey-container-servlet</artifactId>
	<version>2.28</version>
</dependency>
<dependency>
	<groupId>org.glassfish.jersey.inject</groupId>
	<artifactId>jersey-hk2</artifactId>
	<version>2.28</version>
</dependency>
```

2. 建立伺服器
```java
	Server server = new Server();
	ServerConnector http = new ServerConnector(server);
	http.setHost("localhost");
	http.setPort(8080);
	http.setIdleTimeout(30000);
	server.addConnector(http);
	
	// 配置靜態網頁Handler
	ServletContextHandler context = new ServletContextHandler(ServletContextHandler.NO_SESSIONS);
	context.setContextPath("/");
	context.setWelcomeFiles(new String[] { "index.html" });

	ServletHolder def = context.addServlet(DefaultServlet.class, "/");
	def.setInitParameter("resourceBase", "./http/");
	def.setInitParameter("dirAllowed", "false");
```


3. 設定Restful api相關配置
```java
	// api 提供的路徑
	ServletHolder apiHolder = context.addServlet(ServletContainer.class, "/api/*");
	apiHolder.setInitOrder(1);
	// 提供api的packagex路徑
	apiHolder.setInitParameter("jersey.config.server.provider.packages", 
				"idv.kaponcer.RoEAnalyze.model.api");
	/**
	* 也可以單獨載入類別
	* jerseyServlet.setInitParameter("jersey.config.server.provider.classnames",
    *           "UploadFileService;Packege.className");
	*/
	
	
	HandlerList handlers = new HandlerList();
	handlers.addHandler(context);

	server.setHandler(handlers);
```
## 備份筆記 #
```java
// 筆記備份,來源至底
	Server jettyServer = new Server();
	HttpConfiguration http_config = new HttpConfiguration();
	/**
	 *http_config可以对服务器进行配置，比如设置https,BufferSize等等
	 *        http_config.setSecureScheme("https");
	 *        http_config.setSecurePort(8443);
	 *        http_config.setOutputBufferSize(32768);
	 *        http_config.setRequestHeaderSize(8192);
	 *        http_config.setResponseHeaderSize(8192);
	 */
	http_config.setSendServerVersion(true);
	http_config.setSendDateHeader(false);
	
	/**
	 * 新建http连接来设置访问端口，超时时间等等。
	 */
	ServerConnector httpServer = new ServerConnector(jettyServer,
			new HttpConnectionFactory(http_config));
	httpServer.setPort(7012);
	httpServer.setIdleTimeout(120000);
	jettyServer.addConnector(httpServer);

	/**
	 * 设置整个web服务的根url，/ 表示 localhost:7012/  之后地址的是可访问的
	 */
	ServletContextHandler context = new ServletContextHandler(ServletContextHandler.SESSIONS);
	context.setContextPath("/");

	/**
	 * 添加动态servlet路径，处理我们自己写的动态的servlet
	 */
	ServletHolder jerseyServlet = context.addServlet(
			org.glassfish.jersey.servlet.ServletContainer.class, "/webapi/*");
	jerseyServlet.setInitOrder(1);
	// Tells the Jersey Servlet which REST api/class to load.设置动态servlt加载的包
	jerseyServlet.setInitParameter("jersey.config.server.provider.packages", "com.heu.cs.api");
	//也可单独设置加载某个类，
	 jerseyServlet.setInitParameter("jersey.config.server.provider.classnames",
			"UploadFileService;org.glassfish.jersey.media.multipart.MultiPartFeature");


	/**
	 * 添加默认的servlet路径，处理不在动态servlet路径中的地址，一般都是一些可供访问的静态html,css,js资源文件
	 */
	ServletHolder staticServlet = context.addServlet(DefaultServlet.class, "/static/*");
	staticServlet.setInitParameter("resourceBase", "src/main/resources");
	staticServlet.setInitParameter("pathInfoOnly", "true");


	/**
	 * Embedded Jetty还可以直接当作服务器，在上面部署已经发布的war包，这方面的资料国内挺多的，就不累述
	 * 
	 * 其次，在我们的项目中是没有用到web.xml文件来进行webappde的配置，因为上面的设置并不能使得服务器访问web.xml，
	 * 如果需要用到web.xml，则需要new一个WebAppContext,并对其进行配置，同时在下面的handlers中加上webAppContext
	 *  WebAppContext webAppContext = new WebAppContext();
	 *  设置描述符位置
	 *  webAppContext.setDescriptor("./web/WEB-INF/web.xml");
	 *  设置Web内容上下文路径
	 *  webAppContext.setResourceBase("./web");
	 *  设置上下文路径
	 *  webAppContext.setContextPath("/");
	 *  webAppContext.setParentLoaderPriority(true);
	 */
	
	HandlerCollection handlers = new HandlerCollection();
	// handlers.setHandlers(new Handler[]{context,webAppContext});
	handlers.setHandlers(new Handler[]{context});
	jettyServer.setHandler(handlers);
	try {
		jettyServer.start();
		jettyServer.join();
	} finally {
		jettyServer.destroy();
	}
```

## 來源 #
Jetty 官方文件 用來看基本的範例
(這是快照版本的說明，個人感覺比正式版好看一點，如果被官方砍掉了就只能看正式版的文件)
{% link Embedding-Jetty 
 https://www.eclipse.org/jetty/documentation/9.4.x/embedding-jetty.html %}


大陸的程序員撰寫的教學，關於嵌入式Jetty+Jersey Restful服務
{% link IDEA+Maven+Embedded Jetty+Jersey构建Restful服务并打包成jar包发布 
 https://www.jianshu.com/p/764fcdffc28a %}



