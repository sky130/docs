# 参数变量
---

?> 以下参数并不**全面**，如果无法解决问题，可以查看开发Demo代码

## 请求接口链接
| 请求接口链接     |             链接(String)              |
| ---------------- | :-----------------------------------: |
| URL_INTERNATIONL | https://international.v1.hitokoto.cn/ |
| URL_NATIONL      |        https://v1.hitokoto.cn/        |
| URL_DEFAULT      |        https://v1.hitokoto.cn/        |

## 请求一言类型
| 请求一言类型    | 类型(String) |
| --------------- | :----------: |
| TYPE_ANIMATION  |      a       |
| TYPE_COMICS     |      b       |
| TYPE_GAME       |      c       |
| TYPE_LITERATURE |      d       |
| TYPE_ORIGINAL   |      e       |
| TYPE_INTERNET   |      f       |
| TYPE_OTHER      |      g       |
| TYPE_VIDEO      |      h       |
| TYPE_POEM       |      i       |
| TYPE_NETEASE    |      j       |
| TYPE_PHILOSOPHY |      k       |
| TYPE_JOKE       |      l       |
| TYPE_DEFAULT    |      a       |


## 返回一言类型
| 返回一言类型 | 类型(int) |
| ------------ | :-------: |
| ID           |     0     |
| UUID         |     1     |
| HITOKOTO     |     2     |
| FROM         |     4     |
| FROM_WHO     |     5     |
| CREATOR      |     6     |
| CREATOR_UID  |     7     |
| REVIEWER     |     8     |
| COMMIT_FROM  |     9     |
| CREATED_AT   |    10     |
| LENGTH       |    11     |

## 结果类型
| 结果类型     | 类型(String) |
| ------------ | :----------: |
| RESULT_OK    |     200      |
| RESULT_BAD   |     400      |
| RESULT_ERROR |      -1      |

## 通用设置类型
| 通用设置类型 | 类型(int) |
| ------------ | :-------: |
| URL          |     0     |
| TYPE         |     3     |
| CHARSET      |     6     |
| MIN_LENGTH   |     9     |
| MAX_LENGTH   |     7     |
| TOKEN        |     8     |
| COMMENT      |    10     |
| SCORE        |    11     |

## 请求参数
| 请求参数           | 参数(String) |
| ------------------ | :----------: |
| CHARSET_DEFAULT    |    UTF-8     |
| LENGTH_MAX_DEFAULT |      0       |
| LENGTH_MIN_DEFAULT |      0       |



## 登录参数
| 登录参数     | 参数(int) |
| ------------ | :-------: |
| LOGIN_STATUS |     0     |
| LOGIN_NAME   |     1     |
| LOGIN_EMAIL  |     2     |
| LOGIN_ID     |     3     |
| LOGIN_TOKEN  |     4     |


## 用户喜欢参数 
| 用户喜欢参数        | 参数(int) |
| ------------------- | :-------: |
| LIKE_LIMIT_DEFAULT  |    20     |
| LIKE_OFFSET_DEFAULT |     0     |

## 用户提交历史参数
| 用户提交历史参数 | 参数(int) |
| ---------------- | :-------: |
| HISTORY_DEFAULT  |     0     |
| HISTORY_ALL      |     0     |
| HISTORY_PENDING  |     1     |
| HISTORY_REFUSE   |     2     |
| HISTORY_ACCEPT   |     3     |

## 设置参数 
| 设置参数                  | 参数(int) |
| ------------------------- | :-------: |
| SETTING_GLOBAL            |     0     |
| SETTING_HITOKOTO_APPENDED |     1     |
| SETTING_HITOKOTO_REVIEWED |     2     |
| SETTING_POLL_CREATED      |     3     |
| SETTING_POLL_RESULT       |     4     |
| SETTING_POLL_DAILY_REPORT |     5     |

## 提交新一言参数
| 提交新一言参数  | 参数(int) |
| --------------- | :-------: |
| SUMMARY_TOTAL   |     1     |
| SUMMARY_PENDING |     2     |
| SUMMARY_REFUSE  |     3     |
| SUMMARY_ACCEPT  |     4     |

