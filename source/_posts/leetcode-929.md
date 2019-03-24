---
title: 'leetcode#929'
categories: 
 - leetcode
 - easy
 - 929. Unique Email Addresses
comments: true
date: 2019-03-07 10:45:29
tags:
 - leetcode
 - 929
 - Unique Email Addresses
 - easy
---

問題:
找出有多少不同組信箱地址.規則如下:
1. 接在@之後為網域地址，如：@leet.code.com 與 @leetcode.com不同，.則代表在不同網段之下
2. 接在@之前則為使用者名稱，可以任意加上多少.，如：kapo.ncer 等同於 kaponcer 等同於 k.a.p.o.n.c.e.r
3. 使用者名稱可以再加上+號，＋號之後到@之前都是使用者個人分類，如：kaponcer+leetcode 等同於 kapncer 等同於 kaponcer+gg

Example 1:
{% blockquote %}
Input: ["test.email+alex@leetcode.com","test.e.mail+bob.cathy@leetcode.com","testemail+david@lee.tcode.com"]
Output: 2
Explanation: "testemail@leetcode.com" and "testemail@lee.tcode.com" actually receive mails
{% endblockquote %}

Note:

    1 <= emails[i].length <= 100
    1 <= emails.length <= 100
    Each emails[i] contains exactly one '@' character.

<!-- more -->


```java
class Solution {
    public int numUniqueEmails(String[] emails) {
        // 準備存放email的地方
        Set<String> emailSet = new HashSet<String>();
        // 將每個輸入的email逐一取出判斷
        for(String email:emails){
            // 該email的使用者名稱
            String userName = email.substring(0, email.indexOf("@"));
            // 該使用者的網域名稱
            String domainName = email.substring(email.indexOf("@"));
            //將使用者名稱之後的加號都刪掉
            if(email.indexOf("+")>=0)
              userName = userName.substring(0,email.indexOf("+"));
            //去除點號
            String trueUserName="";
            for(String str :userName.split("\\.")){
                trueUserName+=str;
            }
            //end 去除點號
            //全組來一起再放入emailSet 中
            emailSet.add(trueUserName+domainName);
        }
        
        return emailSet.size();
    }
}
```