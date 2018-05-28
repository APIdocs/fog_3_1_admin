# 用户管理 接口文档

## HOST 说明
* dev host: https://cnapitest.fogcloud.io
* production host: https://cnapi.fogcloud.io
* api prefix: /v3_1
* entirely api path: host + prefix + api

---
## api示例 接口
 **接口地址**
 >
 
 **请求示例**
 ```
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|

**返回参数**
```
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
  
 ---
## admin 用户登陆 接口(Token认证)
**接口地址**

> POST /v3_1/manage/login/
 
**请求参数示例**
 ```
{
  "username": "wxd@mxchip.com",
  "password": "fog123456"
 }

```

**请求参数说明**

| 参数 | 类型 | 必须 | 说明 |
| ---- | ---- | ---- | ---- |
|username|varchar|yes|用户名称，只支持邮箱|
|password|varchar|yes|登陆密码|

**返回参数**
```
{
    "meta": {
        "message": "Ok",
        "code": 0
    },
    "data": {
        "token": "901ea4a4dbc25e999615a0301918374d0e01132c",
        "user": {
            "id": 45,
            "email": "huanghq@mxchip.com",
            "groups": [
                {
                    "id": 3,
                    "name": "Fog"
                }
            ],
            "username": "h2",
            "is_staff": true,
            "is_superuser": true,
            "date_joined": "2018-04-09 10:22:28"
        }
    }
}
}
```

**返回参数说明**

|参数|类型|说明|
|:----:|:----:|:----:|
|token|varchar|登陆token, 在请求其他接口时，需在header中以格式：Authorization token 携带|
|groups|list|用户所属组|
|username|varchar|用户名称|
|is_staff|varchar|是否是admin用户|
|is_superuser|varchar|是否是超级用户|
|date_joined|datetime|用户注册时间|

---
## admin用户注销 接口(Token认证)
 **接口地址**
 > POST /manage/logout/
 
 **请求示例**
 ```
 POST /manage/logout/
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|

**返回参数**
```
{
    "meta": {
        "message": "Successfully logout",
        "code": 0
    },
    "data": {}
 }
```

---
## 重置密码获取验证码 接口

**接口地址**

> POST /v3_1/manage/verCode/

**接口请求示例**
```
{
  "username": "wxd@mxchip.com",
  "code_type": 1
}
```

**请求参数说明**

| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|username|varchar|yes|注册邮箱|
|code_type|int|yes|验证码类型，1(重置密码)|

**返回参数**
```
{
    "meta": {
        "message": "Ok",
        "code": 0
    },
    "data": {}
 }
```

## 重置密码 接口

**接口地址**
> POST /v3_1/manage/password/reset/

**请求示例**
```
{
  "username": "wxd@mxchip.com",
  "vercode": "087629",
  "password": "fog123456",
  "password2": "fog123456"
}
```

**请求参数说明**

| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|username|varchar|yes|登陆邮箱|
|vercode|varchar|yes|验证码|
|password|varchar|yes|重置密码参数|
|password|varchar|yes|重置密码参数2|

**返回参数**
```
{
  "meta": {
            "code": 0,
            "message"："重置密码成功！"
        },
   "data": {}
   }
 ```
 
--- 
## 新建权限组 接口(Token认证)
**接口地址**
> POST /v3_1/manage/newGroup/

**请求示例**
 ```
 POST /v3_1/manage/newGroup/
 
 {
  "name": "财务组"
  }
   
 ```
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|name|varchar|yes|新建组名称|

**返回参数**
```
{
  "meta": {
            "code": 0,
            "message": "ok"
            },
  "data": {
            "name": "财务组",
            "id": 3,
            }
 }
            
```
**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|id|int|组编号|
|name|varchar|组名称|

---
## 组列表 接口(Token认证)
 **接口地址**
 > GET /v3_1/manage/groupList/
 
 **请求示例**
 ```
 GET /v3_1/manage/groupList/
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data":[
        {
            "id": 5,
            "name": "财务组"
        },
        {
            "id": 2,
            "name": "Finance"
        }
    ]
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|id|int|组编号|
|name|varchar|组名称|

---
## 权限组下用户列表 接口(Token认证)
 **接口地址**
 > GET /v3_1/manage/groupUser/
 
 **请求示例**
 ```
 GET /v3_1/manage/groupUser/?group_id=1
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|group_id|int|yes|组编号|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": [
        {
            "id": 3,
            "email": "wxd@mxchip.com",
            "groups": [
                {
                    "id": 1,
                    "name": "Sales"
                },
                {
                    "id": 3,
                    "name": "Fog"
                },
                {
                    "id": 5,
                    "name": "财务组"
                }
            ],
            "username": "cfz",
            "is_staff": false,
            "is_superuser": true,
            "date_joined": "2018-01-10 16:56:23"
        },
        {
            "id": 36,
            "email": "adminyun@mxchip.com",
            "groups": [
                {
                    "id": 1,
                    "name": "Sales"
                }
            ],
            "username": "fogcloud",
            "is_staff": false,
            "is_superuser": false,
            "date_joined": "2018-03-02 16:52:36"
        }
    ]
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|groups|list|用户所属组|
|username|varchar|用户名称|
|is_staff|varchar|是否是admin用户|
|is_superuser|varchar|是否是超级用户|
|date_joined|datetime|用户注册时间|

---
## 权限组下的模块列表 接口(Token认证)
 **接口地址**
 > GET /v3_1/manage/groupModule/
 
 **请求示例**
 ```
 GET /v3_1/manage/groupModule/?group_id=1
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|group_id|int|yes|组编号|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": {
        "module_id": 1,
        "module_name": "权限管理",
        "module_ename": "user manage"
    }
}

```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|module_id|int|模块编号|
|module_name|varchar|模块名称|
|module_e_name|varchar|模块英语名称|

---