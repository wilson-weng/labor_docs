# 公司管理

## 新建

### 接口介绍

>uri: /company
>method: POST
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON



### 参数列表
>company_name 公司名称 String
>address 公司地址 String
>memo 备注 String

### 调用示例
```
{
 "company_name": "xxx劳务公司",
 "memo": "此公司"
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
---

## 修改


### 接口介绍
>uri: /company
>method: PUT
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>company_id 公司编号 Integer
>company_name 公司名称 String
>address 公司地址 String
>memo 备注 String


### 调用示例
```
{
 "company_id": 1,
 "company_name": "xxx劳务公司",
 "memo": "此公司"
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
---

## 删除

### 接口介绍
>uri: /company/<int:company_id>
>method: DELETE
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>company_id 公司编号 Integer


### 调用示例


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
## 公司列表

### 接口介绍
>uri: /company
>method: GET
>返回数据格式: JSON

### 参数列表
>page 第几页 Integer

### 调用示例
{
  "page": 1
}

### 成功返回
```
{
 "content": {
   result:[{
               "id": 1,
               "address": "xxx",
               "company_name": "xxx",
               "memo": "",
               "create_time": "2018-08-11 11:10"
            }],
   total_page: 10,
   page:1
 },
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
--- 
## 公司详情


### 接口介绍
>uri: /company/<int:company_id>
>method: GET
>返回数据格式: JSON

### 参数列表
>company_id 公司编号 Integer
>company_name 公司名称 String
>address 公司地址 String
>memo 备注 String


### 调用示例


### 成功返回
```
{
 "status": "ok",
 "content": {
    "id": 1,
    "address": "xxx",
    "company_name": "xxx",
    "memo": "",
    "create_time": "2018-08-11 11:10"
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

------
## 公司列表

### 接口介绍
>uri: /company
>method: GET
>返回数据格式: JSON

### 参数列表
>page 第几页 Integer

### 调用示例
{
  "page": 1
}

### 成功返回
```
{
 "content": {
   result:[{
               "id": 1,
               "address": "xxx",
               "company_name": "xxx",
               "memo": "",
               "create_time": "2018-08-11 11:10"
            }],
   total_page: 10,
   page:1
 },
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


--- 
## 公司详情


### 接口介绍
>uri: /company/proj/list
>method: GET
>返回数据格式: JSON

### 参数列表
>company_id 公司编号 Integer


### 调用示例


### 成功返回
```
{
  "status": "ok",
  "content": ['proj_id': 1, 'proj_name': 'xxx项目']
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```