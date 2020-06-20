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
<style>
    strong { 
        text-shadow: 0.5px 0.5px red;
    }
    .description {
        text-indent: 2em;  
    }
</style>


<div style=" border: 1px solid;"><!-- 下面要空一行不然會出錯 -->
<b style="font-size:32px"> <p id="catlog" style=" text-align: center;"> 目錄 </a> </b><br/>

- <a href="#descript">部屬描述檔</a>
- <a href="#structe">Web Project 結構</a>
- <a href="#servlet">Servlet</a>
    - <a href="#servletLearnMap"> Servlet學習地圖 </a> 
    - <a href="#doGet"> doGet </a>
    - <a href="#doPost"> doPost </a>
    - <a href="#doPut"> doPut </a>
    - <a href="#doDelete"> doDelete </a>
    - <a href="#doOption"> doOption </a>
-
</div>


<!-- more -->


- # <a id="descript" href="#catlog">部屬描述檔 </a> #
    
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




- # <a id="structe" href="#catlog">    Web Project 結構 </a> #
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


- # <a id="servlet" href="#catlog">Servlet</a> #
    ## <a id="servletLearnMap" href="#catlog"> Servlet學習地圖 </a> ##
    {% blockquote 圖1.1  Servlet類別關係圖  https://www.codejava.net/java-ee/servlet/uml-class-diagram-of-httpservlet-api source %}
        ![ServletClass](HttpServletAPIUMLdiagram.png)
    {% endblockquote %}

    <br/>

    {% blockquote 圖1.2 HttpServlet 類別圖 https://www.planttext.com/  writing from here %}
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
    <p class="description">
        下面介紹一些會依序介紹一些常用的方法．
    </p>

    ## <a id="doGet" href="#catlog"> doGet </a> ##

    <p class="description">
        用來處理HTTP GET請求的地方，也是我們最常用的兩個方法之一，通常我們會Overwrite這個方法．
    </p>

    ## <a id="doPost" href="#catlog"> doPost </a> ##

    <p class="description">
        用來處理HTTP Post請求的地方，也是我們最常用的兩個方法之一，通常我們會Overwrite這個方法．
    </p>

    ## <a id="doPut" href="#catlog"> doPut </a> ##

    <p class="description">
        用來處理HTTP Put請求的地方，通常我們會Overwrite這個方法．
    </p>

    ## <a id="doDelete" href="#catlog"> doDelete </a> ##

    <p class="description">
        用來處理HTTP Delete請求的地方，通常我們會Overwrite這個方法．
    </p>

    ## <a id="doOption" href="#catlog"> doOption </a> ##

    <p class="description">
        用來處理HTTP doOption請求的地方，通常我們會Overwrite這個方法．
    </p>
    <br/>

    {% blockquote 圖1.3 HttpServletRequest 類別圖  https://www.codejava.net/java-ee/servlet/uml-class-diagram-of-httpservlet-api source  %}
        ![ServletRequest](ServletRequest.png)
    {% endblockquote %}
    <!-- 
    ServletRequest <|-- HttpServletRequest
    ServletResponce <|-- HttpServletResponce
    interface ServletRequest {
        Object getAttribute(String name)
        Enumeration<String> getAttributeNames()
        void setCharacterEncoding(String env)
        int getContentLength()
        long getContentLengthLong()
        String getContentType()
        ServletInputStream getInputStream()
        String getParameter(String name)
        Enumeration<String> getParameterNames()
        String[] getParameterValues(String name)
        Map<String,String[]> getParameterMap()
    } 
    -->

    <p class="description">
        下面介紹一些會依序介紹一些常用的方法，
    </p>
    <br/>

    {% blockquote 圖1.4 HttpServletResponce 類別圖   https://www.codejava.net/java-ee/servlet/uml-class-diagram-of-httpservlet-api source  %}
        ![ServletResponce](ServletResponce.png)
    {% endblockquote %}
    <!-- 
    ServletRequest <|-- HttpServletRequest
    ServletResponce <|-- HttpServletResponce
    interface ServletRequest {
        Object getAttribute(String name)
        Enumeration<String> getAttributeNames()
        void setCharacterEncoding(String env)
        int getContentLength()
        long getContentLengthLong()
        String getContentType()
        ServletInputStream getInputStream()
        String getParameter(String name)
        Enumeration<String> getParameterNames()
        String[] getParameterValues(String name)
        Map<String,String[]> getParameterMap()
    } 
    -->

    <p class="description">
        下面介紹一些會依序介紹一些常用的方法，
    </p>
    <br/>

    
  
- # Filter #
- 