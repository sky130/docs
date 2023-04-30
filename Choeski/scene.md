# 情景配置

---

> 下面是一个简洁的情景配置文件
>
> **请注意**,为了方便理解,我会添加注释,而JSON并**无注释**

``` json
{
  "name": "森林",//场景名
  "description": "把你的密码藏进森林",//场景描述,最好是一个有含义的短句
  "data": [//播放数据
    {
      "audioName": "鸟鸣.mp3", //音频名,只有在线性音频时启用
      "duration": 0, //播放间隔,只有在点状音频时启用
      "isLineAudio": true, //用于判断是否是线性音频
      "isPointAudio": false, //用于判断是否是点状音频
      "names": [], //音频名,只有在点状音频时启用
      "volume": 1.0//音量大小
    }
    {
    "audioName": "",
      "duration": 4049, //播放间隔,只有在点性音频时启用
      "isLineAudio": false, //用于判断是否是线性音频
      "isPointAudio": true, //用于判断是否是点状音频
      "names": [ //音频名,只有在点状音频时启用
        "庄稼地1.mp3",
        "庄稼地2.mp3",
        "庄稼地3.mp3",
        "庄稼地4.mp3",
        "庄稼地5.mp3"
      ],
      "volume": 1.0//音量大小
    }
  ]
}
```

上面的文件已经包含了绝大多数情况的用法,下面的表格才是全部用法

| 属性名 | 数据类型 | 说明 |
| ------ | -------- | ---- |
| duration | Int | 音频时长，单位为秒 |
| startPlayTime | Int? | 音频播放的开始时间，单位为秒，可空 |
| totalEndTime | Int? | 音频结束的时间，单位为秒，可空 |
| audioName | String? | 音频名称，可空 |
| names | List<String>? | 音频名称列表，可空 |
| isLineAudio | Boolean? | 是否为线性音频，可空 |
| isPointAudio | Boolean? | 是否为点状音频，可空 |F
| configVolume | Double? | 配置音量，范围为0-1，可空 |
| frequency | Int? | 音频频率，单位为Hz，可空 |
| pitch | Double? | 音高，可空 |
| speed | Double? | 播放速度，可空 |
| isRawRes | Boolean? | 是否为原始资源，可空 |
| volume | Double | 音量，范围为0-1 |

---
So, enjoy it~