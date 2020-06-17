---
title: Servlet&JSP 筆記
categories: 
    - Java
    - Web
comments: true
date: 2020-06-17 05:13:47
tags:
    - java
    - web
---
<div style=" border: 1px solid;">

 # <p id="catlog" style=" text-align: center;"> 目錄 </a> #
- <a href="#descript">部屬描述檔</a>
- <a href="#structe">Web Project 結構</a>
- <a href="#servlet">Servlet</a>
</div>


<!-- more -->


- <a id="descript" href="#catlog">    部屬描述檔 </a>
    
    用來Web container了解整個App的架構，下面是使用maven產生web project的web.xml
    ```xml
    <!DOCTYPE web-app PUBLIC
     "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
      "http://java.sun.com/dtd/web-app_2_3.dtd" >
    <web-app>
        <display-name>Archetype Created Web Application</display-name>
    </web-app>
    ```
    常見的web.xml內容包含如下
    ```xml
    <web-app>
        <!-- servlet的部分 -->
        <servlet>
            <servlet-name>HelloServlet</serlet-name>
            <servlet-class>idv.test.HelloServlet</servlet-class>
        </servlet>
        <servlet-mapping>
            <servlet-name>HelloServlet</servlet-name>
            <url-pattern>/hello</url-pattern>
        </servlet-mapping>
        <!-- servlet的部分 end -->
        <!-- 下面持續更新 -->
    </web-app>
    ```




- <a id="structe" href="#catlog">    Web Project 結構 </a>
    ```
    HelloProject
        WEB-INF ---------------------------------
            web.xml                             -
            lib                                 -
                extendsion.jar                  -
            classes                             - 應用程式內部資源
                idv                             -
                    test                        -
                        HelloServlet            -
        -----------------------------------------
        other
            otherFileOrDir                 
    ```


- <a id="servlet" href="#catlog">Servlet</a>
  
    {% blockquote 圖1.1 Servlet類別關係圖 %}
        ![ServletClass](ServletClass.png)
    {% endblockquote %}

    <!-- @startuml UML backup
    Servlet <|-- GenericServlet
    GenericServlet <|-- HttpServlet
    interface Servlet{
        + void init(ServletConfig config)
        + ServletConfig getServletConfig()
        + void service(ServletRequest req,ServletResponce res)
        + String getServletInfo()
        + void destroy()
    }
    class GenericServlet{}
    class HttpServlet{
        + HttpServlet()
        # Long getLastModified(HttpServletResponce res)
        # void doGet(HttpServletRequest req,HttpServletResponce res)
        # void doHead(HttpServletRequest req,HttpServletResponce res)
        # void doPost(HttpServletRequest req,HttpServletResponce res)
        # void doput(HttpServletRequest req,HttpServletResponce res)
        # void doDelete(HttpServletRequest req,HttpServletResponce res)
        # void doOption(HttpServletRequest req,HttpServletResponce res)
        # void doTrace(HttpServletRequest req,HttpServletResponce res)
        # void service(HttpServletRequest req,HttpServletResponce res)
        + void service(ServletRequest req,ServletResponce res)
   }@enduml
    -->

  
- 