# 网络请求
> 在Zeroc中, 你可以发送get/post请求, 而这些的请求方法相单简单, 你只需要定义好URL就可发送请求。

---

# 定义URL

定义一个URL只需要使用**var**变量声明一个链接即可
示例如下:

```
var url = https://example.com/
```

# GET请求

发送get请求只需要使用**url**方法
示例如下:

```
var url = https://example.com/
url url | get
// 结果返回
print result
```

!> 变量名可以和方法名一样