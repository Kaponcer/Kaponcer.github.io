---
title: Java學習筆記(控制)
categories: Java
comments: true
date: 2019-02-17 19:16:56
tags:
 - java
 
---
+ #### 流程控制 ####

##### if-else、switch #####
if(條件式){
	條件式為真，要做的事情．
}else{
	條件式為否，要做的事情．
}

```java
int input = 10;
if(input>10){
	System.out.println("input >"+ input);
}else{
	System.out.println(input + " <= 10");
}
//else後面還可以再串接if條件式
if(input>10){
	System.out.println("input > 10);
}else if (input == 0){
	System.out.println("input = 10");
}else{
	System.out.println("input < 10" );
}

```








   - 類別(Class)、物件(Object)與方法(Method)在討論控制結構前，先來介紹類別(Class)、物件(Object)與方法(Method)．
舉例來說:
類別可以說是Car，物件可以說是Mazda 3 4D，方法可以說是"讓Car引擎發動、左右轉...等行為"
```java
public class Car {
	private 
    public void start(){        //引擎發動
       System.out.println("引擎發動");
   }  //start end

   public void turn(boolean direct){ //轉彎
       if(direct) System.out.println("向右轉");
       else  System.out.println("向左轉");
   }  //turn end

}   //Car class end


```





- #### 流程控制 ####