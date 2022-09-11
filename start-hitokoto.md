# 快速配置

> 一个用Java + okhttp写的一言Hitokoto类库,方便调用接口
> 目前基本已经完工

---

### 在build.gradle中引进
``` java
  dependencies {
    ...
    implementation('ml.sky233.suiteki:hitokoto:1.0.0')   
    implementation('com.squareup.okhttp3:okhttp:4.9.1')
}
```

### 在Java文件中引进
``` java
    ...
    import static ml.sky233.hitokoto.Hitokoto.*;
    import ml.sky233.hitokoto.HitokotoUtils;
    ...
```

完成上面的步骤后,你可以在你的项目中使用 **Hitokoto-Utils-Java** 了
