# 快速配置

> 一个可以获取小米手环的AuthKey的类库

---

## 在build.gradle中引进
``` java
  dependencies {
    ...
    implementation('ml.sky233.suiteki:Suiteki:1.1.0')   
    implementation('com.squareup.okhttp3:okhttp:4.9.1')
}
```

## 在Java文件中引进
``` java
    ...
    import ml.sky233.Suiteki;
    import ml.sky233.SuitekiObject;
    ...
```

## 构建一个Suiteki对象

!> 正常开发时不一定需要事先配置账号密码,可以稍后配置

``` java
    Suiteki suiteki = new Suiteki();//不带账号参数的构建对象
    Suiteki suiteki_huami = new Suiteki("example@exmaple.com","exmaple123");//带有华米账号的构建对象
    Suiteki suiteki_xiaomi = new Suiteki("code");//带有小米登录Code的构建对象
```

## 获取Demo
> [点我下载](https://github.com/sky130/Suiteki-app)

###### 完成上面的步骤后,你可以在你的项目中使用 **Suiteki-Lib** 了
