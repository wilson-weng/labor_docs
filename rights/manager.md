# 系统用户管理(包含Bapp端用户)

## 创建用户

### 接口介绍

>uri: /manager
>method: POST
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>user_name 账户名称 String
>phone 电话号码 Long
>email 邮箱 String

### 调用示例
```
{
  "user_name": "王小明",
  "phone": 18922101112,
  "email": "188551133@qq.com",
}
```

### 成功返回
```
{
 "status": "ok"
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```

-------

## 用户列表

### 接口介绍

>uri: /manager
>method: GET
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>page 分页参数 Integer

### 调用示例
```
{
  "page": 1,
}
```

### 成功返回
```
{
 "status": "ok",
 "content": [{"user_name": "王小明",     
              "phone": 15809875551,
              "email": "164606991@qq.com",
              "user_status": 1}]
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```

-------


## 查看用户详情

### 接口介绍

>uri: /manager/<int:id>
>method: GET
>返回数据格式: JSON

### 参数列表
>id 账户编号 Integer

### 调用示例
```
{
  "id": 1
}
```

### 成功返回
```
{
 "status": "ok",
 "content": {
    "basic": {
       "user_name": "王小明",     
       "phone": 15809875551,
       "email": "164606991@qq.com",
       "user_status": 1
    },
    "roles": [{'id': 1, 'role_name': "超级管理员"}],
    "proj_rights": {
       company_rights: [1, 2], // 公司级别权限 [0]拥有所有公司所有项目的权限
       proj_rights: [ // 项目级别权限, 表示该用户拥有指定项目的权限
         {company_id: 3, proj_id: 3},
         {company_id: 3, proj_id: 4},
       ]
    }
 
 }
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```

-------


## 更新用户基础信息

### 接口介绍

>uri: /manager
>method: PUT
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>id 账户编号 Integer
>user_name 账户名称 String
>phone 电话号码 Long
>email 邮箱 String
>user_status 用户状态 1-恢复正常，2-注销 Integer

### 调用示例
```
{
  "id": 1,
  "user_name": "王小明",
  "phone": 18922101112,
  "email": "188551133@qq.com",
  "user_status": 1, // 用户状态1-恢复正常，2-注销,拥有此接口后就不需要单独开发一个删除用户的接口了
}
```

### 成功返回
```
{
 "status": "ok"
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```

-------

## 登陆

### 接口介绍

>uri: /manager/login
>method: POST
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>phone 电话号码 Long
>code 验证码 String

### 调用示例
```
{
  "phone": 18922101112,
  "code": "871131"
}
```

### 成功返回
```
{
 "status": "ok",
 "content": {
   "user_base_info": {
      "user_id": 1,
      "user_name": "王鹏", 
      "phone": 16791910012
   },
   "token": "asdefxlfeqqzxx"
 }
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```

----
## 发送短信验证码

### 接口介绍

>uri: /manager/login/code/send
>method: POST
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>phone 电话号码 Long

### 调用示例
```
{
  "phone": 18922101112
}
```

### 成功返回
```
{
 "status": "ok"
}
```

### 错误返回
```
{
 "status": "error",
 "msg": "你的号码已经封号"
}
```

-----
## 为对应用户分配角色

### 接口介绍

>uri: /manager/role/allocate
>content-type: application/x-www-form-urlencoded
>method: POST
>返回数据格式: JSON
>headers: 
```
{
    'mimetype': 'multipart/form-data',
    'enctype': 'multipart/form-data',
    'X-Requested-With': 'XMLHttpRequest'
}
```

### 参数列表
> manage_id Integer 角色编号
> role_ids 权限编号(逗号隔开)  String


### 调用示例
```
{
  'manage_id': 1,
  'role_ids': "1,2,3,4,5,6,7"
}
```

### 成功返回
```
{
   "status": "ok"
}
```

### 错误返回
```
{
 "status": "error",
 "msg": "system error"
}
```



----

## 为对应用户分配项目权限

### 接口介绍

>uri: /manager/proj/allocate
>content-type: application/x-www-form-urlencoded
>method: POST
>返回数据格式: JSON
>headers: 
```
{
    'mimetype': 'multipart/form-data',
    'enctype': 'multipart/form-data',
    'X-Requested-With': 'XMLHttpRequest'
}
```

### 参数列表
> manage_id Integer 角色编号
> proj_map 项目权限列表(json 字符串)  String


### 调用示例
####  分配指定项目的权限
```
{
  'manage_id': 1,
  'proj_map': "
     {'proj_ids': [1,2,3,4]} 
  "
}
```

####  分配指定公司所有项目的权限
```
{
  'manage_id': 1,
  'proj_map': "
     {'company_ids': [1,2,3,4]} 
  "
}
```

####  分配所有项目的权限
```
{
  'manage_id': 1,
  'proj_map': "
     {'company_id': [0]} 
  "
}
```


### 成功返回
```
{
   "status": "ok"
}
```

### 错误返回
```
{
 "status": "error",
 "msg": "system error"
}
```





