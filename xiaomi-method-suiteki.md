# 小米方法

---
!> 该方法无需配置网络权限, 但需要配置完整的文件读写权限, SDK>=30 的**需要配置外部访问Data权限**
!> 配置权限可以参考我[这篇博客](https://sky233.ml/android11-data/)或看开发文档

---

> 小米方法是通过读取**小米运动健康**和**小米穿戴**的Log文件获取AuthKey
> 小米运动健康支持获取AuthKey,Mac,DeviceName
> 小米穿戴支持获取AuthKey, 其他的未来会适配


## 获取秘钥列表
代码如下
``` java  
    Suiteki suiteki = new Suiteki;
    suiteki.setLog(Log);//设置Log内容
    ArrayList<SuitekiObject> al = suiteki.getAuthKeyList();
    for(int i = 0; i < al.size(); i++){
        SuitekiObject sobj = al.get(i);
        String authkey = sobj.getAuthKey();//AuthKey的值
        String mac = sobj.getMac();//对应的Mac地址
        String name = sobj.getDeviceName();//对应的DeviceName名字
        Log.d("test","authkey=" + authkey + "  " + "mac=" + mac + "  " + "name=" + name);
    }
        Log.d("test",al[i]);
```
打印结果
``` log
    authkey=xxxxxxxxxxx  mac=xx:xx:xx:xx:xx  name=xxx.xxx.xxx
    ...
```

> 返回的DeviceName可以转换为手环的型号名字
> 例如**hmpace.motion.v6nfc**可以转换为**小米手环6 NFC**
> 实现这个功能需要用**SuitekiUtils.getModelName(String model)**

## 获取Data读写权限

!> 仅支持Android8~12的设备,Android13的设备需要其他方法

> 先引进**SuitekiUtils**

``` java
    SuitekiUtils.startFor(this,1);//申请权限
```

> 回调保存权限

``` java
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == 1 && data.getData() != null) {
            getContentResolver().takePersistableUriPermission(data.getData(), data.getFlags() & (
                    Intent.FLAG_GRANT_READ_URI_PERMISSION | Intent.FLAG_GRANT_WRITE_URI_PERMISSION));//回调保存权限
        }
    }
```

> 读取Log文件

``` java
    String str = SuitekiUtils.getLog(this,SuitekiUtils.MI_HEALTH_PATH);
```