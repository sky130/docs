# 米家参数

!> 部分解释参考来源于[小米IOT设备规范v2](https://github.com/Mi-Home/miot-spec-doc/blob/master/%E5%B0%8F%E7%B1%B3IOT%E8%AE%BE%E5%A4%87%E8%A7%84%E8%8C%83v2.md)
!>
!> 由于项目特殊性, 并不会将规范中的内容完整搬过来, 你可以选择阅读原文

## Urn

URN表达式遵循URN语法规范(RFC2141)，6个字段，最后一个字段为可选：

  ```
  <URN> ::= "urn:"<namespace>":"<type>":"<name>":"<value>[":"<vendor-product>":"<version>]
  ```
  * urn

    第一个字段必须为urn，否则视为非法urn。

  * namespace

    如果是小米定义的规范为miot-spec-v2，蓝牙联盟定义的规范为bluetooth-spec。

  * type

    SpecificationType (类型，简写为: type)，只能是如下几个：

    * template
    * property
    * action
    * event
    * service
    * device

  * name

    有意义的单词或单词组合(小写字母)，多个单词用"-"间隔，比如：

    * temperature
    * current-temperature
    * device-name
    * battery-level

  * value

    16进制字符串，使用UUID前8个字符，如：

    * 00002A06
    * 00002A00

  * vendor-product

    厂家+产品代号，有意义的单词或单词组合(小写字母)，用"-"间隔，比如：

    * philips-moonlight
    * yeelink-c300
    * zhimi-vv
    * benz-c63

    ```
    注：这个字段只有在设备实例定义里出现。
    ```

  * version

    版本号，只能是数字，如:

    * 1
    * 2
    * 3

    ```
    注：这个字段只有在设备实例定义里出现。
    ```

## 实例ID

Instance ID, 简称iid, 用于指定某个实例, 用整数表示

在不同的设备实例中, 为了区分不同实例, ``特定iid``只会指向一个特定实例

并且一个``iid``在同一级是唯一的

在下文提到的 ``siid``, ``aiid``, ``piid`` 都属于``特定的iid``

## Service(服务)

在一个设备实例下, 会有许多不同的 ``Service``

例如

* Light
* Fan

``Service`` 是指在设备实例中代表的不同的功能板块

而在``Service``之下还有[Property](#Property(属性))和[Action](#Action(动作))两类

具体

例如``风扇灯``就是一种将``风扇``和``照明``两种功能结合起来的智能设备

为了方便区分和适配, 将其分成了两个服务

## Property(属性)


## Action(动作)


