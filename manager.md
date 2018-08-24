# 系统用户管理(包含Bapp端用户)

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









