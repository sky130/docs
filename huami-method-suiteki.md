# 华米方法

---

!> 该方法需要配置网络权限并且先检查网络环境避免报错,而且需要将关于网络操作的方法用线程运行

---

## 登录账号

> 先通过 **loginHuami()** 登录华米(ZeppLife/Zepp)账号
>
> 支持**小米账号**登录或**华米账号**(邮箱账号)登录

华米登录代码如下
``` java
    Suiteki suiteki = new Suiteki();//构建无参对象
    Suiteki.loginHuami("example@examlpe.com","examlpe123");//华米账号登录
    // loginHuami(String email,String password)
    // 传入参数 Email 和 Password 即可登录华米账号
```
或
``` java
    Suiteki suiteki = new Suiteki("example@example.com","example123");//构建带账号参数对象
    suiteki.loginHuami();//登录
```

---

小米登录代码如下
``` java
    Suiteki suiteki = new Suiteki();//构建无参对象
    suiteki.loginHuami("code");//登录
```
或
``` java
    Suiteki suiteki = new Suiteki("code");//构建带小米登录Code对象
    suiteki.loginHuami();//登录
```
还有更多方式
``` java
    Suiteki suiteki = new Suiteki();//构建无参对象
    suiteki.setEmail("example@example.com");//设置邮箱
    suiteki.setPassword("example123");//设置密码
    suiteki.setCode("code");//设置小米登录Code
    suiteki.loginHuami();//如果设置了邮箱密码则优先通过邮箱登录
    if(suiteki.isUserEmpty()){// isUserEmpty 只能检查账号密码或Code是否为空
        //空
    }else{
        //非空
    }
```

---

## Code 获取方式
> 先在**浏览器**中访问下面的链接
``` 
    https://account.xiaomi.com/fe/service/oauth2/authorize?skip_confirm=false&client_id=2882303761517383915&pt=0&scope=1+6000+16001+20000&redirect_uri=https%3A%2F%2Fhm.xiaomi.com%2Fwatch.do&_locale=zh_CN&response_type=code
```    
> 通过该链接登陆小米账号后，会**重定向**一个类似下面的链接
```
    https://hm.xiaomi.com/watch.do?code=C4_434BB7ADBA171F615DD9956881E21E7A
```
> 其中的参数 **code** 就是要获取的 **Code**
```
    C4_434BB7ADBA171F615DD9956881E21E7A
```
> 我们传入这个 Code 即可登录华米账号

## 验证登录状态
> 通过 **getResultCode()** 返回登录码

代码如下
``` java
    if(Suiteki.getResultCode().equals("200")){
        //登录成功
    }else{
        //登录失败 
    }
```

## 获取秘钥
> 当完成登录后，可以通过 **getHuamiToken()** 获取秘钥

代码如下
``` java
    suiteki.getHuamiToken();
    ArrayList<SuitekiObject> al = suiteki.getResultData();
    for(int i = 0; i < al.size(); i++){
        SuitekiObject sobj = al.get(i);
        String authkey = sobj.getAuthKey();//AuthKey的值
        String mac = sobj.getMac();//对应的Mac地址
        Log.d("test","authkey=" + authkey + "  " + "mac=" + mac);
    }
```
> 假设有两个以上手环，则打印数据为如下格式

``` log
    authkey=XXXXXXXXXXXX  mac=XX:XX:XX:XX:XX:XX
    authkey=XXXXXXXXXXXX  mac=XX:XX:XX:XX:XX:XX
    ···
```

> 如果只有一个手环，则只会打印一行数据
``` log
    authkey=XXXXXXXXXXXX  mac=XX:XX:XX:XX:XX:XX
```