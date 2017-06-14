# 2017 会展 接口文档（v2.2）

[TOC]

## 首页
### 首页接口

| 类型 | type |
| :-- | :-: |
| 大会新闻 | 1 |
| 大会日程 | 2 |
| 地图导航 | 3 |
| 会议服务 | 4 |
| 嘉宾服务 | 5 |
| 嘉宾通讯录 | 6 |
| 嘉宾点评 | 7 |
| 大会资料 | 8 |
| 服务调度 | 9 |
| 工作通讯录 | 10 |
| 服务签到 | 11 |
| 全部服务 | 0 |

#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式
```
{
    "resultcode":"resultcode",
    "qrcodeurl":"‘我的’界面中APP二维码",
    "banner": [
        {
            "id": "新闻id",
            "title": "导航title.",
            "url": "导航详情",
            "imgurl": "图片地址"
        }
    ],
    "notice": [
        {
            "id": "新闻id",
            "type": "通知类型",
            "title": "http://www.google.com"
        }
    ],
    "feature": [
        {
            "type": "1",
            "title": "工作通讯录"
        },
        {
            "type": "2",
            "title": "服务签到"
        }
    ]
}
```

### 全部服务

#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode":"resultcode",
    "feature": [
        {
            "type": "1",
            "title": "工作通讯录"
        }
    ]
}
```
## 日程相关
### 大会日程/个人行程

#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| id | String | 日期id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode":"resultcode",
    "datebar": [
        {
            "id":"1001"
            "time": "3月11日",
            "week": "星期三",
            "current": true
        }
    ],
    "schedule": [
        {
            "enable": true,
            "time": "上午8:00",
            "meeting": [
                {
                    "id": "1001",
                    "time": "8:30-13:30",
                    "title": "会议名称",
                    "location": "会议地点",
                    "enable": true
                }
            ]
        }
    ]
}
```
* current ： 是否为当前日期
* enable ： 是否为已过时

### 会议详情

#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| id | String | 会议id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode":"resultcode",
    "title": "会议标题",
    "introduction": "会议简介",
    "time": "2017-01-01 上午8:30-上午10:30",
    "location": "会议地点",
    "longitude": "”经度“",
    "latitude": "”纬度“",
    "host": "”主持人“",
    "attention": false,
    "issue": {
        "id": "id.",
        "title": "议题名称"
    },
    "guest": [
        {
            "name": "嘉宾名",
            "url": "头像url",
            "introduction": "简介"
        }
    ]
}
```
* attention ：是否关注

### 议题详情

#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| id | String | 议题id |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode":"resultcode",
    "title": "议题标题",
    "introduction": "议题简介",
    "time": "2017-01-01 上午8:30-上午10:30",
    "host": "”主持人“",
    "guest": [
        {
            "name": "嘉宾名",
            "url": "头像url",
            "introduction": "简介"
        }
    ]
}
```

### 行程详情

#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| id | String | 行程id |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode":"resultcode",
    "title": "行程简介标题",
    "introduction": "行程简介标",
    "date": "2017-01-01 星球一",
    "starttime": "”上午8:30“",
    "endtime": "”下午8:30“",
    "location": "”地点“"
}
```

### 搜索日程
#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| keywords | String | 关键字 |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode":"resultcode",
    "schedule": [
        {
            "time": "上午8:00",
            "meeting": [
                {
                    "id": "1001",
                    "time": "8:30-13:30",
                    "title": "会议名称",
                    "location": "会议地点",
                    "type":"大会日程为1，个人行程为2"
                }
            ]
        }
    ]
}
```
## 新闻相关
### 大会新闻
#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| type | String | 新闻分类 |
| page | String | 分页 |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode":"resultcode",
    "newstpye": [
        {
            "id": "分类id.",
            "title": "分类名称"
        }
    ],
    "banner": [
        {
            "id": "新闻id",
            "url": "新闻详情url",
            "imageurl": "图片url",
            "title": "title"
        }
    ],
    "news": [
        {
            "id": "新闻id",
            "url": "新闻详情url",
            "imageurl": "图片url",
            "title": "标题",
            "introduction": "简介",
            "time": "2017.01.01 15：30",
            "attentionnum": "关注人数"
        }
    ]
}
```


## 通知相关
### 通知中心
#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| page | String | 请求页数 |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode": "resultcode",
    "notice": [
        {
            "id": "通知id",
            "title": "标题",
            "type": "通知类型",
            "time": "2017.01.01 15:30"
        }
    ]
}
```
### 通知详情
#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| id | String | 通知id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "title": "标题",
    "time": "2017.01.01 13:13",
    "detail": "详情"
}
```

## 大会资料
### 大会资料
#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "folder": [
        {
            "title": "文件夹名称",
            "file": [
                {
                    "url": "下载地址",
                    "title": "名称"
                }
            ]
        }
    ],
    "file": [
        {
            "url": "下载地址",
            "title": "名称"
        }
    ]
}
```


## 服务相关
### 会议服务
#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "service": [
        {
            "title": "服务名称",
            "phonenum": [
                {
                    "num": "电话名称"
                }
            ]
        }
    ]
}
```
## 通讯录相关
### 通讯录
#### 请求格式

| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| deptId | String | 部门id,最外层为”“|
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "depts": [
        {
            "obey_dept_id": "所属部门id",
            "dept_id": "部门id",
            "dept_name": "部门名字",
            "dept_pic": "部门头像地址"
        }
    ],
    "users": [
        {
            "obey_dept_id": "所属部门id",
            "user_id": "用户id",
            "user_name": "用户名字",
            "user_pic": "用户头像地址"
        }
    ]
}
```

### 通讯录搜索
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| type | String | 嘉宾通讯录为1，工作人员通讯录为2 |
| keyword | String | 关键字 |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode": "resultcode",
    "people": {
        "id": "id",
        "name": "名称",
        "imgurl": "中国头像",
        "type":"嘉宾为1工作人员为2"
        "dept": "所属部门"
    }
}
```
### 通讯录创建群组
#### 请求格式

```
{
    "userIds": "uid1,uid2,uid3所选人员id",
    "userId": "用户id",
    "groupId": "群组id",
    "groupName": "群组名称",
    "deptIds": "1,2,3所包含的部门的id"
}
```
#### 返回格式

```
{
    "resultcode": "resultcode"
}
```

### 嘉宾/工作人员个人详情
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| type | String | 嘉宾通讯录为1，工作人员通讯录为2 |
| id | String | 人员id |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode": "resultcode",
    "name": "姓名",
    "id": "用户id",
    "phonenum": "电话",
    "group": "代表团",
    "imageurl": "头像地址",
    "company": "单位",
    "duty": "职务",
    "hotel": "酒店信息",
    "roomnum": "房间号",
    "sex": "性别",
    "mark": "补充字段"
}
```
## 点评相关
### 嘉宾点评
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| page | String | 分页，每次15条 |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode": "resultcode",
    "commentary": [
        {
            "id": "点评id",
            "name": "名称",
            "promulgatorid": "发布者id",
            "imageurl": "头像",
            "time": "1小时前",
            "content": "内容",
            "image": [
                {
                    "imageurl": "原图地址",
                    "thumbnailUrl": "缩略图地址"
                }
            ],
            "review": [
                {
                    "fromname": "嘉宾A",
                    "fromid": "嘉宾AId",
                    "toname": "嘉宾B",
                    "toid": "嘉宾BId",
                    "content": "回复内容"
                }
            ]
        }
    ]
}
```


### 嘉宾点评-评论/回复
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| commentaryid | String | 评论项id |
| toid | String | 被回复的人的id，无此项则为普通评论，否则为回复某人 |
| content | String | 评论内容 |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode": "resultcode"
}
```

### 嘉宾点评-写点评
#### 请求格式

```
{
    "userid": "userid",
    "language": " language",
    "content": "点评内容",
    "image": [
        {
            "name": "图片名",
            "image": "图片base64"
        }
    ]
}
```
#### 返回格式
```
{
    "resultcode": "resultcode"
}
```

## 嘉宾服务
### 嘉宾服务（嘉宾登录）
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| type | String | 角色类型 |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode": "resultcode",
    "hotel": {
        "name": "酒店名称.",
        "room": "房间号",
        "location": "中国酒店地址",
        "longitude": "经度",
        "latitude": "纬度",
        "phonenum": "电话"
    },
    "service": [
        {
            "id": "服务人员id",
            "name": "服务人员姓名",
            "imageurl": "服务人员头像",
            "phonenum": "联系方式",
            "group": "代表团",
            "mark": "补充字段"
        }
    ]
}
```

### 嘉宾服务（服务人员登录）
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| type | String | 角色类型 |
| language | String | 语言类型 |

#### 返回格式


```
{
    "resultcode": "resultcode",
    "guest": [
        {
            "id": "嘉宾id",
            "name": "嘉宾姓名",
            "imageurl": "嘉宾头像",
            "phonenum": "联系方式",
            "group": "代表团",
            "qrcode": "二维码url"
        }
    ]
}
```

### 服务调度
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |
| type | String | 1：服务调度（不包含自建群组） 2：群组会话（包含自建群组） |

#### 返回格式


```
{
    "resultcode": "resultcode",
    "group": [
        {
            "id": "群组id",
            "name": "群组名称",
            "imageurl": "群组头像"
        }
    ]
}
```
###服务签到（公共任务列表）
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "tuli": [
        {
            "imgurl": "图片地址",
            "name": "图例名称"
        }
    ],
    "group": [
        {
            "id": "嘉宾id",
            "name": "嘉宾姓名",
            "schedule": [
                {
                    "id": "行程id",
                    "type": "行程类型，1为公共行程，2为个人行程",
                    "name": "行程名",
                    "imgurl": "图片地址",
                    "status": "签到状态，1为已签，2为未签"
                }
            ]
        }
    ]
}
```

###服务签到（个人行程列表）
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| guestid | String | 嘉宾用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "schedule": [
        {
            "id": "行程id",
            "type": "行程类型，1为公共行程，2为个人行程",
            "name": "行程名",
            "imgurl": "图片地址",
            "status": "签到状态，1为已签，2为未签"
        }
    ]
}
```


###服务签到（单独签到）
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| guestid | String | 嘉宾id |
| scheduleid | String | 行程id |
| scheduletype | String | 行程类别 |
| language | String | 语言类型 |


```
{
    "userid": "用户id",
    "language": "1",
    "guestid": "123",
    "scheduleid": "123",
    "scheduletype": "行程类型,1为公共,2为个人"

}
```

#### 返回格式

```
{
    "resultcode": "resultcode",
}
```

###服务签到（批量签到）
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| guestidlist | 数组 | 嘉宾id列表 |
| scheduleidlist| 数组 | 行程id列表 |
| language | String | 语言类型 |

```
{
    "userid": "用户id",
    "language": "1",
    "guestidlist": [
        {
            "guestid": "123"
        }
    ],
    "scheduleidlist": [
        {
            "scheduleid": "123",
            "scheduletype": "行程类型,1为公共,2为个人"
        }
    ]
}
```

#### 返回格式

```
{
    "resultcode": "resultcode",
}
```

##登录相关

#### 请求格式
待定
#### 返回格式

```
{
    "resultcode": "resultcode",
    "userid": "userid",
    "username": "用户名",
    "usertype": "角色类型",
    "dept": "所属部门",
    "phonenum": "联系方式",
    "imageurl": "个人头像",
    "rongtoken": "融云token",
    "token": "时效token",
    "refreshtoken": "刷新token",
    "group": [
        {
            "id": "群组id",
            "name": "群组名字",
            "imageurl": "联系人头像"
        }
    ],
    "contactor": [
        {
            "id": "联系人id",
            "name": "联系人姓名",
            "imageurl": "联系人头像"
        }
    ]
}
```

## 个人资料相关
### 个人资料
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "username": "用户名",
    "phonenum": "联系方式",
    "imageurl": "个人头像",
    "sex": "性别",
    "dept": "单位",
    "duty": "职位",
    "email": "邮箱",
    "group": "代表团"
}
```

### 修改个人资料
#### 请求格式
```
{
    "userid": "userid",
    "username": "用户名",
    "phonenum": "联系方式",
    "imageurl": "图片base64",
    "sex": "性别",
    "dept": "单位",
    "duty": "职位",
    "email": "邮箱",
    "group": "代表团"
}
```
#### 返回格式

```
{
    "resultcode": "resultcode"
}
```

##设置界面

### 联系我们
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "url": "联系我们h5页面地址"
}
```
### 关于我们
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |

#### 返回格式

```
{
    "resultcode": "resultcode",
    "url": "关于我们h5页面地址"
}
```
### 检查更新
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| type | String | 系统类型 IOS 为1 Android 为 2 |
| language | String | 语言类型 |



#### 返回格式

```
{
    "resultcode": "resultcode",
    "version": "最新版本号",
    "url": "下载地址"
}
```

### 会话列表
#### 请求格式

```
{
    "userid": "userid",
    "language": "language",
    "userlist": [
        {
            "userid": "userid"
        }
    ]
}
```

#### 返回格式（群组列表一并返回）


```
{
    "userlist": [
        {
            "id": "id",
            "name": "名称",
            "imageurl": "头像"
        }
    ]
}
```

### 室外导航
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| language | String | 语言类型 |
#### 返回格式

```
[
    {
        "typeName": "酒店、会场",
        "locationList": [
            {
                "locationName": "酒店1号",
                "longtitude": "经度",
                "atitude": "纬度"
            }
        ]
    }
]
```
### 室内导航 图片导航
#### 请求格式
| 请求参数 | 类型 | 意义 |
| --- | --- | --- |
| userid | String | 用户id |
| type | String | 导航图片类型（ 酒店/宴会厅） |
| language | String | 语言类型 |
#### 返回格式

```
[
    {
        "typeName": "会场一",
        "picturs": [
            {
                "pictureUrl": "urlString",
                "pictureName":"L1"
            },
            {
                "pictureUrl": "urlString",
                "pictureName":"L2"
            }
        ]
    },
    {
        "typeName": "会场二",
        "picturs": [
            {
                "pictureUrl": "urlString",
                "pictureName":"L1"
            },
            {
                "pictureUrl": "urlString",
                "pictureName":"L2"
            }
        ]
    }
]
```
## 更新日志

* v1.1 <font color="ff0000">首页banner增加详情url</font>
* v1.2 <font color="ff0000">检查更新增加系统类型判断</font>
* v1.3 <font color="ff0000">服务签到拆分为公共签到列表和个人签到列表</font>
* v1.4 <font color="ff0000">大会资料接口修改</font>
* v1.5 <font color="ff0000">大会点评增加缩略图字段</font>
* v1.6 <font color="ff0000">大会点评增加点评发布者id(promulgatorid)字段</font>
* v1.7 <font color="ff0000">修改签到部分请求，增加行程类型字段</font>
* v1.8 <font color="ff0000">大会资料接口修改</font>
* v1.9 <font color="ff0000">新增会话列表请求接口，群组列表需一并返回</font>
* v2.0 <font color="ff0000">新增室外导航接口</font>
* v2.1 <font color="ff0000">服务调度接口增加type字段，会话列表接口修改</font>
* v2.2 <font color="ff0000">新增室内导航接口(图片类型室内导航，不显示地图，只显示场地平面图片);大会点评增加分页请求</font>



