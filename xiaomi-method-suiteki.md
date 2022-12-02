# 小米方法

---

## 设置Log内容
代码如下
``` java  
    Suiteki.setLog(Log);
```
## 获取秘钥列表
代码如下
``` java
    String[] keys = Suiteki.getAuthKeyList();
    for(int i = 0;i < keys.length;i++)
        Log.d("test",keys[i]);
```
打印结果
``` log
    xxxxxxxxxxxxxx
    xxxxxxxxxxxxxx
```