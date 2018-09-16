## 角色管理

## 新增角色

### 接口介绍

>uri: /rights/role
>method: POST
>content-type: application/x-www-form-urlencoded
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
>role_name 角色名称 String
>rank 排序(控制后端中的显示顺序/非业务字段)   Integer


### 调用示例
```
{
  'role_name': '超级管理员',
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
 "msg": "不能重复添加相同名称的角色"
}
```
-------


## 修改角色

### 接口介绍

>uri: /rights/role
>method: PUT
>content-type: application/x-www-form-urlencoded
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
>id 角色编号 Integer
>role_name 角色名称 String


### 调用示例
```
{
  'id': 1
  'role_name': '超级管理员2',
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
 "msg": "不能重复添加相同名称的角色"
}
```
-----


## 删除角色

### 接口介绍

>uri: /rights/role/<int:id>
>method: DELETE
>content-type: application/x-www-form-urlencoded
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
>id 角色编号 Integer


### 调用示例
```
{
  'id': 1
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
-----

## 角色列表

### 接口介绍

>uri: /rights/role/list
>method: GET
>返回数据格式: JSON

### 参数列表
>page 分页参数 Integer


### 调用示例
```
{
  'page': 1
}
```

### 成功返回
```
{
   "status": "ok",
   "content": [
      {"id": 1, "role_name": "超级管理员"},
      {"id": 2, "role_name": "超级管理员2"}
    ]
}
```

### 错误返回
```
{
 "status": "error",
 "msg": "system error"
}
```
---

## 角色详情

### 接口介绍

>uri: /rights/role/<int:role_id>
>method: GET
>返回数据格式: JSON

### 参数列表
> role_id Integer 角色编号


### 调用示例
```
{
  'role_id': 1
}
```

### 成功返回
```
{
   "status": "ok",
   "content": {
     "basic":  {"id": 1, "role_name": "超级管理员"},
     "rights_resource": [{'resource_id': 1, 'resource_name': 'xxx', 'value': 'crew_management'}]
   }
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

## 为对应角色分配权限

### 接口介绍

>uri: /rights/role/allocate
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
> role_id Integer 角色编号
> rights_ids 权限编号(逗号隔开)  String


### 调用示例
```
{
  'role_id': 1,
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

