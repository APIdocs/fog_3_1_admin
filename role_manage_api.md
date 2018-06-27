# 角色管理 接口文档

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
|:----|:----|:----|:----|

**返回参数**
```
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----|:----|:----|

---
## 客户列表 接口
 **接口地址**
 > GET /manage/role/customer/
 
 **请求示例**
 ```
 1. GET /manage/role/customer/?page=2&list_type=assign
 2. GET /manage/role/customer/?page=1&list_type=all
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----|:----|:----|:----|
|page|int|no|页码|
|page_size|int|no|每页数量|
|list_type|varchar|yes|请求类型，assign(可分配客户), all(全部客户)|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": {
        "count": 31,
        "page_size": 10,
        "next": true,
        "previous": true,
        "results": [
            {
                "id": 40,
                "username": "Hamasaki",
                "email": "",
                "is_active": true,
                "date_joined": "2018-03-23 10:19:32"，
                "principal":[
                              {"user__username": "fkk",
                              "user_id":3
                              }
                           ]
            }...
}
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----|:----|:----|
|id|int|客户ID|
|username|varcahr|客户名称|
|email|varcar|客户邮箱|
|is_active|bool|客户是否激活|
|date_joined|datetime|客户注册时间|
|user_username|varchar|客户负责人名称|
|user_id|int|客户负责人编号|

---
## 销售人员列表 接口
 **接口地址**
 > GET /manage/role/sales/
 
 **请求示例**
 ```
GET /manage/role/sales/?page=2
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----|:----|:----|:----|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": {
        "count": 18,
        "page_size": 10,
        "next": null,
        "previous": true,
        "results": [
            {
                "id": 59,
                "username": "mimi1",
                "email": "2733677680@qq.com",
                "is_active": true,
                "is_staff": true,
                "date_joined": "2018-06-11 10:20:49",
                "groups": [
                    3
                ]，
                "customer":[
                {"customer__username":"h",
                "customer_id": 4
                }
            }...
  }
```

**返回参数说明**

| 参数 | 类型 |说明 |
|:----|:----|:----|
|id|int|销售ID|
|username|varcahr|销售名称|
|email|varcar|销售邮箱|
|is_active|bool|销售是否激活|
|is_staff|bool|销售是否是admin用户|
|date_joined|datetime|客户注册时间|
|groups|list|销售所属组|
|customer__username|varchar|客户名称|
|customer_id|varchar|客户编号|

---
## 客户分配 接口
 **接口地址**
 > POST /manage/role/customerAssign/
 
 **请求示例**
 ```
 {
     "user_id": 1,
     "customer_id": [49,2]
  }
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----|:----|:----|:----|
|user_id|int|yes|销售用户编号|
|customer_id|list|yes|客户用户编号|

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
## 删除销售下的客户 接口
 **接口地址**
 > DELETE /manage/role/customerManage/[customer_id]/
 
 **请求示例**
 ```
 DELETE /manage/role/customerManage/17/
 
 {
   "user_id": 3
 }
 ```
 
 **请求参数说明**
 
| 参数 | 类型 | 必须 | 说明 |
|:----|:----|:----|:----|
|user_id|int|yes|销售的用户ID|

**返回参数**
```
{
    "meta": {
        "message": "ok",
        "code": 0
    },
    "data": {}
}
```

