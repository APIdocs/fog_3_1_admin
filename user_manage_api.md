# 用户管理 接口文档

## HOST 说明
* dev host: https://cnapitest.fogcloud.io
* production host: https://cnapi.fogcloud.io
* api prefix: /v3_1
* entirely api path: host + prefix + api

---
## Token 说明
* Token认证标识 表示请求该接口必须携带token
* 携带token方法：设置headers: Authorization : token klk4terlg....

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

> POST /manage/login/
 
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
|password2|varchar|yes|重置密码参数2|

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
> POST /v3_1/manage/group/

**请求示例**
 ```
 POST /v3_1/manage/group/
 
 {
  "name": "财务组",
  "modules": [1,2,3]
  }
   
 ```
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|name|varchar|yes|新建组名称|
|modules|list|yes|新建组下模块|

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
            "hash_name": "lkfjkl3r4jtlferkglefjl3jr3l45j3lklxnfdjd"
            }
 }
            
```
**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|id|int|组编号|
|name|varchar|组名称|
|hash_name|varchar|组名称的hash值|


--- 
## 删除权限组 接口(Token认证)
**接口地址**
> DELETE /v3_1/manage/group/

**请求示例**
 ```
 DELETE /v3_1/manage/group/?group_id=13
 ```
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|group_id|varchar|yes|删除组编号|

**返回参数**
```
{
  "meta": {
            "code": 0,
            "message": "ok"
            }
 }
            
```
**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|


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
## 组下添加用户 接口
 **接口地址**
 > POST /manage/newUser/
 
 **请求示例**
 ```
{
	"email": "Hellokitty@gmail.com",
	"username": "HelloKitty",
	"is_superuser": 1,
	"groups": [1]
}
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|email|varchar|yes|用户登陆邮箱|
|username|varchar|yes|用户名|
|is_superuser|bool|no|是否设置为超级用户|
|groups|list|yes|用户拥有的权限组|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": {
        "id": 50,
        "email": "Hellokitty@gmail.com",
        "groups": [
            {
                "id": 1,
                "name": "Sales",
                "hash_name": "d0edfb6e8c55c8742a83f0f192886e0e15fa0347"
            }
        ],
        "username": "HelloKitty",
        "is_staff": true,
        "is_superuser": true,
        "date_joined": "2018-05-31 16:14:23"
    }
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|id|int|用户id|
|email|varchar|用户邮箱|
|username|varchar|用户名称|
|is_staff|varchar|是否是admin用户|
|is_superuser|varchar|是否是超级用户|
|data_joined|datetime|注册时间|

---
## 组下删除用户 接口
 **接口地址**
 > DELETE /manage/newUser/
 
 **请求示例**
 ```
DELETE /manage/newUser/?user_id=62&group_id=1
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|user_id|int|yes|删除的用户ID|
|group_id|int|yes|用户所属组id|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    }
 }
```
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
## 模块列表 接口(Token认证)
 **接口说明**
 * 获取所有的模块列表
 
 **接口地址**
 > GET /manage/moduleList/
 
 **请求示例**
 ```
 GET /manage/moduleList/
 ```

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": [
        {
            "id": 2,
            "name": "配额管理"
        },
        {
            "id": 1,
            "name": "客户管理"
     }
    ]
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|id|int|模块ID|
|name|varchar|模块名称|


## admin用户列表 接口(Token认证)
 **接口地址**
 > GET /manage/userList/
 
**请求示例**
 ```
 GET /manage/userList/?group_id=1
 ```
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|group_id|int|yes|组id|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": [
        {
            "id": 8,
            "email": "fog@mxchip.com",
            "groups": [],
            "username": "admin",
            "is_staff": true,
            "is_superuser": true,
            "date_joined": "2018-01-12 14:42:39",
            "last_login": "2018-01-12 14:43:17"
        }
    ]
}
```

## 添加用户到组 接口
 **接口地址**
 > PUT /manage/groupUser/
 
 **请求示例**
 ```
 {
	"groups": [1],
	"users": [48]
}
 
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|users|list|yes|添加到组的用户列表|
|groups|list|yes|添加用户的组|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    }
}
```

---
## 更新组信息 接口
 **接口地址**
 > PUT /manage/group/
 
 **请求示例**
 ```
 {
 	"group_id": 1,
	"name": "Sales Group",
	"modules": [1,3]
}
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|group_id|int|yes|组编号|
|name|varchar|no|更新组名称|
|modules|list|no|更新模块列表|

**返回参数**
```
{
	"meta": {
		"code":0,
		"message":"ok"
		},
	"data":{}
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|

---
## 获取组详情 接口
 **接口地址**
 > GET /manage/group/
 
 **请求示例**
 ```
 GET /manage/group/?group_id=1
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
        "modules": [
            {
                "module_id": 2,
                "module_name": "配额管理"
            }
        ],
        "id": 1,
        "name": "Sales Group"
    }
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|id|int|组编号|
|name|varchar|组名称|
|modules|list|组模块列表|
|module_id|int|模块编号|
|module_name|varchar|模块名称|

---
## 获取用户详情 接口
 **接口地址**
 > GET manage/newUser/
 
 **请求示例**
 ```
 GET /manage/newUser/?user_id=53
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|user_id|int|yes|用户编号|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": {
        "id": 53,
        "username": "hamasaki",
        "email": "12321@qq.com",
        "is_staff": true,
        "is_superuser": true,
        "date_joined": "2018-06-07 13:38:38",
        "groups": [
            {
                "id": 1,
                "name": "Sales Group"
            }
        ],
        "last_login": null,
        "modules": [
            {
                "module_id": 2,
                "module__name": "配额管理"
            }
        ]
    }
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|
|id|int|用户编号|
|username|varchar|用户名称|
|email|varchar|用户邮箱|
|is_superuser|bool|是否超级用户|
|date_joined|datetime|用户注册时间|
|last_login|datetime|用户最后登陆时间|
|groups|list|用户所有组列表|


---
## 更新用户信息 接口
 **接口地址**
 > PUT /manage/newUser/
 
 **请求示例**
 ```
 {
 	"user_id": 53,
	"username": "wangxingd",
	"email": "wxd@mxchip.com",
	"is_superuser": 1,
	"groups": [1,2]
}
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----:|:----:|:----:|:----:|
|user_id|int|yes|用户ID|
|username|varchar|no|用户名称|
|email|varchar|no|用户邮箱|
|is_superuser|varchar|no|是否超级管理员|
|groups|list|no|用户组列表|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    }
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----:|:----:|:----:|

