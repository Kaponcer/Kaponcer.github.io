---
title: Java學習筆記(基本語法)
categories: Java
comments: true
date: 2019-02-12 19:07:49
tags:
 - java
 - 未完全
---

+ # 筆者序 #
　　本文件是以學習筆記的概念為基礎，用於自我的複習紀錄，不過也開放各位的概念指證．畢竟學習過程中難免會出現觀念錯誤的問題．也感謝各位的觀念指證．


+ # 安裝JDK #
    1. 在Oracle網站中找自己系統的JDK{% link 下載位置 http://www.oracle.com/technetwork/java/javase/downloads/index.html %}
    2. 設定 PATH windows10 =>本機=>右鍵內容=>進階系統設定=>進階=>環境變數 設定
    
+ # 第一個程式Hello World #
    
    {% codeblock lang:java %}
    //Hello World =>Java的單行註解方式
    public class HelloWorld{
        /** 
            程式的預設的進入點，
            必須是public static，
            另外這是Java的多行註解方式．
        */
        public static void main(String args[]){
            // 在console輸出Hello World
            System.out.println("Hello World");
        }//main-end
     }//HelloWorld class-end
     {% endcodeblock %}
    
+ # 基本型別與變數宣告 #
    

    
| 型別類別 | 資料型態 | 位元組數(byte)   | 資料範圍(range)       | 初始值(非預設值)    |
| :------: | :------: | :--------------: | :-------------------: | :-------: |
| 字元 | char(Unicode) | 2 | '\u0000'~'\uFFFF' 0~65535 | '\u0000' |
| 整數 | byte | 1 | -128 ~ 127 | 0 |
| | short | 2 | -32768 ~ 32767 | 0 |
| | int | 4 | $-2^{31}$ ~ $2^{31}$-1 | 0 |
| | long | 8 | $-2^{63}$ ~ $2^{63}$-1 | 0L |
| 浮點數 | float | 4 | -3.4E+38 ~ 1.4E-45 | 0.0F|
| | double | 8 | -1.7E+308 ~ 4.9E-324 | 0.0D |
| 布林 | boolean | 1 | true or false | false |


{% codeblock lang:java %}
        // 數值資料範圍
        public class DataRange{
            public static void main(String[]args){
                System.out.println("byte range: " + Byte.MIN_VALUE + " ~ " + Byte.MAX_VALUE);
                System.out.println("short range: " + Short.MIN_VALUE + " ~ " + Short.MAX_VALUE);
                System.out.println("int range: " + Integer.MIN_VALUE + " ~ " + Integer.MAX_VALUE); 
                System.out.println("long range: " + Long.MIN_VALUE + " ~ " + Long.MAX_VALUE);  
                System.out.println("float range: " + Float.MIN_VALUE + " ~ " + Float.MAX_VALUE); 
                System.out.println("double range: " + Double.MIN_VALUE + " ~ " + Double.MAX_VALUE);
            }//main-end
        }//class-end
{% endcodeblock %}

<!--- more --->

+ # 存取修飾字元(Modifier)存取權限 #
    
| 存取修飾字元 | 同一class中 | 同一Package中 | 子類別 | 不同Package |
| :------- | :------: | :----------: | :----------: | :-------: |
| private | yes | no | no | no |
| default | yes | yes | no | no |
| protected | yes | yes | yes | (yes) 繼承才能使用|
| public | yes | yes | yes | yes |

 除了**內部類別（Inner class）**外，一般外部類別只能使用default 或 public 的存取權限
 
+ # 變數宣告 #
 規則：變數名稱的第一個字元必須是英文字母，底線［_］或［$］其中之一
```java
/**
[存取修飾字元] [型別] [變數名稱];
[存取修飾字元] [型別] [變數名稱] = [值]; */
public int test;
public int num = 10; 
```
+ # final #
規則：同變數宣告一樣，不過在中間加了final關鍵字，指的是這個變數只能設定一次，起始值即是最終值．
```java
/**
[存取修飾字元] final [型別] [變數名稱] = [值]; */
public final int num = 10;
```

+ # 靜態[static] #
對於一些類別中的物件裡，目的在於"分享該物件"，而這時候就可以使用static修飾字了
```java
public static int sum = 0;
//使用final static 時變數名稱第一個字元必須為大寫
public final static int PI = 3.1416;
//此System的console靜態方法不需要實體化System就可以使用．
 Console console = System.console();
//全程式裡面共享唯一一個的PI值.
double PI = Math.PI;
```
靜態的部分牽扯到跨類別問題，這裡只簡單講解一下．詳細請參考{% link 良葛格Java學習筆記"關於靜態" https://openhome.cc/Gossip/Java/Static.html %}


+ # 運算子 #
  - ### 算術運算子 ###
  
| 運算子 | 名稱 | 運算子種類 | 備註 |
| :------: | :------ | :------ | :------ |
| + | 正號 | 單元 ||
| | 加法 | 雙元 ||
| - | 負號 | 單元 ||
| | 減法 | 雙元 ||
| * | 乘法 | 雙元 ||
| / | 除法 | 雙元 ||
| % | 餘數 | 雙元 | 浮點數也可使用 |
| ++ | 遞增 | 雙元 ||
| - - | 遞減 | 雙元 ||

   遞增(++)與遞減(--)的範例 
```java
int a = 0;
int b = 0;
b = a++ - a++ + ++a ;
System.out.println("a = "+ a +" b = " + b);
/** 解法
=>b = a(++) - a(++) + (++)a
=>b = a(0+1) - a(1+1) + (2+1)a  ,a=3
=>b = 0      - 1      +      3 
=> a = 3, b=2
**/
int c = 0;
int d = 0;
d = c-- - c-- + --c ;
System.out.println("c = " + c + " d = "+ d );
/** 解法
=>d = c(--) - c(--) + (--)c
=>d = c(-1) - c(-2) + (-3)c , c =-3 
=>d = 0     - -1    +     -3
=>c = -3 , d = -2;
**/
int e = 0;
int f = 0;
f = --e - e-- + --e ;
System.out.println("e = " + e + " f = "+ f );
/** 解法
=>f = (--)e - e(--) + (--)e
=>f = (-1)e - e(-2) + (-3)e   ,e=-3
=>f =     -1-(-1)   +     -3 ,f=-3

**/
```
 - ### 關係運算子 ###
 
| 運算子 | 說明 | 範例 |
| :------: | :------ | :------ |
| == | 等於 | a==b |
| != | 不等於 | a!=b |
| > | 大於 | a>b |
| < | 小於 | a>b |
| >= | 大於等於 | a>=b |
| <= | 小於等於 | a>=b |
  
 - ### 邏輯運算子 ### 
<table><tbody><th>運算子</th><th>說明</th><th>範例</th><tr><td>&</td><td>AND</td><td>a&b</td></tr><tr><td>|</td><td>OR</td><td>a|b</td></tr><tr><td>!</td><td>NOT</td><td>!a</td></tr><tr><td colspan="3">(短路)Short-circuit Operator </td></tr><tr><td>&&</td><td>AND</td><td>a&&b</td></tr><tr><td>||</td><td>OR</td><td>a||b</td></tr></tbody></table>

   & and && 與 | and ||的分別 
   程式小技巧，這點十分重要，因為在程式中邏輯判斷十分常見到，如果在邏輯運算中需要執行算數運算時，保險一點建議使用非short-circuit的邏輯運算子


```java
int x = 0,y=1;
System.out.println("(x>y)&(++x>y)=>"+Boolean.toString((x>y)&(++x>y)));
System.out.println("before x = 0,y = 1,after x = "+x+", y = "+y);
x=0;
y=1;
System.out.println("(x>y)&(++x>y)=>"+Boolean.toString((x>y)&&(++x>y)));
System.out.println("before x = 0,y = 1,after x = "+x+", y = "+y);
x=0;
y=1;
System.out.println("(x<y)|(++x==y)=>"+Boolean.toString((x<y)|(++x==y)));
System.out.println("before x = 0,y = 1,after x = "+x+", y = "+y);
x=0;
y=1;
System.out.println("(x<y)||(++x==y)=>"+Boolean.toString((x<y)||(++x==y)));
System.out.println("before x = 0,y = 1,after x = "+x+", y = "+y);
```

 - ### 位元運算子，位移運算子 ### 
  //先記錄,晚點再看,20190217
<table><tbody><th>運算子</th><th>說明</th><th>範例</th><tr><td>&</td><td>AND</td><td>a&b</td></tr><tr><td>|</td><td>OR</td><td>a|b</td></tr><tr><td>^</td><td>XOR</td><td>a^b</td></tr><tr><td>~</td><td>補數</td><td>a ~ b</td></tr><tr><td>>></td><td>位元右移</td><td>a>>b</td></tr><tr><td><<</td><td>位元左移</td><td>a<<b</td></tr><tr><td>>>></td><td>邏輯右移</td><td>a>>>b</td></tr></tbody></table>
 //先記錄,晚點再看,20190217
 
 - ### 指定運算子 ### 
<table><tbody><th>運算子</th><th>說明</th><th>範例</th><tr><td>=</td><td>基本指定</td><td>a=b</td></tr><tr><td>+=</td><td>加法指定</td><td>a+=b  => a=a+b</td></tr><tr><td>-=</td><td>減法指定</td><td>a+=b  => a=a-b</td></tr><tr><td>*=</td><td>乘法指定</td><td>a*=b  => a=a * b</td></tr><tr><td>/=</td><td>除法指定</td><td>a/=b  => a=a / b</td></tr><tr><td>%=</td><td>餘數指定</td><td>a%=b  => a=a % b</td></tr><tr><td>&=</td><td>AND指定</td><td>a&=b => a=a & b</td></tr><tr><td>|=</td><td>OR指定</td><td>a|=b => a=a | b</td></tr><tr><td>^=</td><td>XOR指定</td><td>a^=b => a=a ^ b</td></tr><tr><td>>>=</td><td>位元右移指定</td><td>a>>=b => a=a>>b</td></tr><tr><td><<=</td><td>位元左移指定</td><td>a<<=b => a=a<<b</td></tr><tr><td>>>>=</td><td>邏輯右移指定</td><td>a>>>=b => a=a>>>b</td></tr></tbody></table>

 - ### 三元運算子 ### 
 三元基本上可以說是if-else條件的簡化版
 變數 = (boolean exp) ? true-value : false-value
```java
int x=0;
if (x==0){
    x+=1;
}else{
    x-=1;
}
//等同於
x = (x==0) ? x+1 : x-1 ;
```

 
 
 
 
 
 