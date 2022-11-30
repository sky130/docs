# 全部方法

## 通过华米接口(Huami/Zepp)获取
> 先通过 **loginHuami()** 登录华米(ZeppLife/Zepp)账号
>
> 支持小米账号登录或华米账号(邮箱账号)登录
登录代码如下
``` java
    loginHuami("example@examlpe.com","exmalpe123");//华米账号登录
    // loginHuami(String email,String password)
    // 传入参数 Email 和 Password 即可登录华米账号
    loginHuami("code");//小米账号登录
    //传入小米账号返回的 Code 参数 即可登录华米账号
```
其中 Code 的获取方式如下
> 先在浏览器中访问下面的链接
``` 
    https://account.xiaomi.com/fe/service/oauth2/authorize?skip_confirm=false&client_id=2882303761517383915&pt=0&scope=1+6000+16001+20000&redirect_uri=https%3A%2F%2Fhm.xiaomi.com%2Fwatch.do&_locale=zh_CN&response_type=code
```    
> 通过该链接登陆小米账号后，会重定向一个类似下面的链接
```
    https://hm.xiaomi.com/watch.do?code=C4_434BB7ADBA171F615DD9956881E21E7A
```
> 其中的参数 code 就是要获取的 Code
```
    C4_434BB7ADBA171F615DD9956881E21E7A
```
> 我们传入这个 Code 即可登录华米账号