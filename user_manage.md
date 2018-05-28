# 用户管理 接口文档

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
  
## admin 用户登陆 接口
**接口地址**

> POST /v3_1/manage/login/(Token认证)
 
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

## 获取验证码 接口

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
 
 ## api 接口
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
  
        
  

