# 简单示例

---

## 刷新句子
``` java
    HitokotoUtils.set(URL, URL_DEFAULT);//默认为国内路线
    HitokotoUtils.set(TYPE, TYPE_DEFAULT);//默认类型为动画
    HitokotoUtils.set(CHARSET, CHARSET_DEFAULT);//默认编码UTF-8,尽量不要修改
    HitokotoUtils.set(MIN_LENGTH, LENGTH_MIN_DEFAULT);//默认为0
    HitokotoUtils.set(MAX_LENGTH, LENGTH_MAX_DEFAULT);//默认为30
    //以上内容非必须添加,可以直接调用getHitokoto(),所有参数均为默认
    String[] str = HitokotoUtils.getHitokoto();//返回的是数组类型(bushi
    System.out.print(str[HITOKOTO]);//打印句子
```
**打印结果**
``` log
    若汝无介意，愿作耳边墙。 思君无情拒，唯吾孤自哀。希愿回心意，眷恋越星海。欲采栀子花，赠予手心中。
```

---

## 喜欢句子
``` java
    String uuid = "c8b35bc2-bbb9-4b3f-a1ed-2b3e355bee37";
    HitokotoUtils.set(UUID,uuid);
    //如果你之前有调用过getHitokoto(),则可以忽略上面,如果无法判断
    //可以使用 HitokotoUtils.get(UUID)看看是否为""
    //调用此方法时必须登录或通过 HitokotoUtils.set(TOKEN,token)设置令牌
    System.out.print(HitokotoUtils.like());
```
**打印结果**
``` log
    200
```
**正常结果均为200,错误信息可以上官网查看**

**此方法可以把like改为unlike,可以取消喜欢句子**


---

#### 登录账号
``` java
    String email = "example@example.com", password = "example123";
    String[] str = HitokotoUtils.login(email,password);
    if (str[LOGIN_STATUS].equals(RESULT_OK)) System.out.print(str[LOGIN_TOKEN]);//打印令牌
```
**打印结果**
``` log
    Z6C9FE7nxzmBaup7V76SlIsyUA0BVTxhIY6gMEyl
```

---
## 刷新令牌
``` java
    if (HitokotoUtils.refreshToken().equals(RESULT_OK)){
        System.out.print(HitokotoUtils.getToken);//刷新成功并打印令牌
    }
```

**打印结果**
``` log
    Z6C9FE7nxzmBaup7V76SlIsyUA0BVTxhIY6gMEyl
```
---

## 喜欢列表
``` java
    if (HitokotoUtils.getLike(LIKE_OFFSET_DEFAULT,LIKE_LIMIT_DEFAULT).equal(RESULT_OK)){
        System.out.print(HitokotoUtils.getLikeString());//刷新成功并打印列表
    }
```
**打印结果**
需要自己解析Json,可以使用配套的Eson(EasyJson)进行[解析](#展示列表)

``` json
    {
    "statistics": {
        "total": 21
    },
    "collection": [
        {
            "uuid": "c8b35bc2-bbb9-4b3f-a1ed-2b3e355bee37",
            "hitokoto": "若汝无介意，愿作耳边墙。 思君无情拒，唯吾孤自哀。希愿回心意，眷恋越星海。欲采栀子花，赠予手心中。",
            "type": "e",
            "from": "原创",
            "from_who": "Sky233",
            "creator": "sky233",
            "creator_uid": 11171,
            "reviewer": 1,
            "commit_from": "web",
            "operated_at": "2022-08-12T08:17:13.000000Z",
            "created_at": "1641130378"
        },
        {
            "uuid": "85e0bd7a-0fab-4719-9b56-21a34776b2f1",
            "hitokoto": "满招损，谦受益。",
            "type": "g",
            "from": "尚书·大禹谟",
            "from_who": null,
            "creator": "小强",
            "creator_uid": 11,
            "reviewer": 0,
            "commit_from": "web",
            "operated_at": "2022-08-12T08:14:09.000000Z",
            "created_at": "1472435170"
        }
    ]
}
```
---
## 添加句子
``` java
    HitokotoUtils.set(TYPE,TYPE_DEFAULT);
    HitokotoUtils.set(HITOKOTO,"TEST");
    HitokotoUtils.set(FROM,"TEST");
    HitokotoUtils.set(FROM_WHO,"TEST");
    System.out.print(HitokotoUtils.addHitokoto());
```

**打印结果**
``` log
    200
```

---
## 通知设置

``` java
    String str[] = HitokotoUtils.getSetting();//获取设置配置，在设置前必须调用，否则报错
    if (str[0].equals("200")) {//判断是否获取配置，避免报错
        HitokotoUtils.setNotification(SETTING_GLOBAL, true);//全局通知
        HitokotoUtils.setNotification(SETTING_HITOKOTO_APPENDED, true);//一言提交通知
        HitokotoUtils.setNotification(SETTING_HITOKOTO_REVIEWED, true);//一言审核通知
        HitokotoUtils.setNotification(SETTING_POLL_CREATED, true);//投票创建通知
        HitokotoUtils.setNotification(SETTING_POLL_RESULT, true);//投票结果通知
        HitokotoUtils.setNotification(SETTING_POLL_DAILY_REPORT, true);//审核员每日报告
        System.out.print(HitokotoUtils.putSetting());//设置
    }
```

**打印结果**
``` log
    200
```

---
## 展示列表

> 示例将使用Eson(EasyJson)和[喜欢列表的Json](#喜欢列表)来演示

``` java
    ...
    import ml.sky233.hitokoto.EsonUtils;
    ...
```

!> **LIKE_OFFSET_DEFAULT**默认为0 | **LIKE_LIMIT_DEFAULT**默认为20,不能小于20大于200

``` java
    if (HitokotoUtils.getUserLike(LIKE_OFFSET_DEFAULT, LIKE_LIMIT_DEFAULT).equals("200")) {//判断是否获取，避免报错
        Object object = HitokotoUtils.getJsonObject();//获取Eson对象
        int length = EsonUtils.getArrayLength(object);//获取句子数量
        String[] hitokoto = new String[length];//分类
        String[] uuid = new String[length];
        String[] from_who = new String[length];
        for (int a = 0; length > a; a++) {
            Object obj = EsonUtils.getArrayObject(object, a);
            hitokoto[a] = EsonUtils.getObjectText(obj, "hitokoto");
            uuid[a] = EsonUtils.getObjectText(obj, "uuid");
            from_who[a] = EsonUtils.getObjectText(obj, "from_who");
        }
        System.out.print(String.valueOf(hitokoto));
        System.out.print(String.valueOf(uuid));
        System.out.print(String.valueOf(form_who));
    }
```

**打印结果**
``` log
    [若汝无介意，愿作耳边墙。 思君无情拒，唯吾孤自哀。希愿回心意，眷恋越星海。欲采栀子花，赠予手心中。,满招损，谦受益。]
    [c8b35bc2-bbb9-4b3f-a1ed-2b3e355bee37,85e0bd7a-0fab-4719-9b56-21a34776b2f1]
    [Sky233,null]
```
