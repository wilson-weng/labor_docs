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
    "role": [{'id': 1, 'role_name': "超级管理员"}],
    "proj_rights_list": {
       company_list: [{'id': 1, 'company_name': 'xxx京东仓库'}],
       company_proj_map: {
           1: [{'proj_name': '50人xx项目', 'proj_id': 1}, {'proj_name': '50人xx项目', 'proj_id': 2}]   
           2: [{'proj_name': '50人xx项目', 'proj_id': 3}, {'proj_name': '50人xx项目', 'proj_id': 4}]   
       }
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
>password 密码 String

### 调用示例
```
{
  "phone": 18922101112,
  "password": "ascdf"
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

---

## 忘记密码(发送重设密码链接)

### 接口介绍

>uri: /manager/forget/psw
>method: GET
>返回数据格式: JSON

### 参数列表
> phone 电话号码 Long

### 调用示例
{
  "phone": 15122133551
}

### 成功返回
```
{
 "status": "ok",
 "content": {
   url: "https://mananger.hrms.cn/sys_user/change/psw?manager_id=1&req=1225333"
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

---

## 更改密码

### 接口介绍

>uri: /manager/<int:manager_id>
>method: PUT
>返回数据格式: JSON

### 参数列表
>manager_id 用户id Integer
>password 密码 String

### 调用示例
{
  "user_id": 1,
  "password": 1231
}

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



----

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
  'rights_ids': "1,2,3,4,5,6,7"
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

## 为对应用户项目权限

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
     {'proj_ids': [1,2,3,4]} 
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





