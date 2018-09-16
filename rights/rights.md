# 权限管理

## 新增权限

### 接口介绍

>uri: /rights
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
>resource_name 权限/资源名称 String
>value 权限值(如/project/add) String
>resource_type 资源类型： 1-资源，2-资源组 Integer
>parent_id 父权限编号  Integer
>rank 排序(控制后端中的显示顺序/非业务字段)   Integer


### 调用示例
```
{
  'resource_name': '项目管理',
  'value': 'proj_management' //后端有配置常量, 无需手动填写,
  'resource_type': 1,
  'parent_id': 0, // 0-表示顶级资源
  'rank': 0
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
 "msg": "不能重复添加权限"
}
```
---------------


## 删除权限

### 接口介绍

>uri: /rights
>method: delete
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
>id 权限编号  Integer


### 调用示例
```
{
  'id': 1,
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
-----------------


## 更改权限

### 接口介绍

>uri: /rights
>method: put
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
>id 权限编号  Integer
>resource_name 权限/资源名称 String
>value 权限值(如/project/add) String
>resource_type 资源类型： 1-资源，2-资源组 Integer
>parent_id 父权限编号  Integer
>rank 排序(控制后端中的显示顺序/非业务字段)   Integer


### 调用示例
```
{
  'id': 1,
  'resource_name': '项目管理',
  'value': 'proj_management' //后端有配置常量, 无需手动填写,
  'resource_type': 1,
  'parent_id': 0, // 0-表示顶级资源
  'rank': 0 
  
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
----------------


## 查看权限列表

### 接口介绍

>uri: /rights/list
>method: get
>返回数据格式: JSON

### 参数列表
>page 第几页 Integer


### 调用示例
```
{
  'page': 0 
}
```

### 成功返回
```
{
 "content": {
   result:[{"resource_name":  "用户管理", "resource_type": 1, "value":  "user_management", "parent_id": 1, "rank": 1}],
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
-------------


## 查看权限列表

### 接口介绍

>uri: /rights/<int:id>
>method: get
>返回数据格式: JSON

### 参数列表
>id  权限编号 Integer


### 调用示例
/rights/1

### 成功返回
```
{
 "content": {
   "resource_name":  "用户管理", "resource_type": 1, "value":  "user_management", "parent_id": 1, "rank": 1
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
---------


## 获取可编辑权限枚举值

### 接口介绍

>uri: /rights/editable/list
>method: get
>返回数据格式: JSON


### 调用示例
/rights/editable/list

### 成功返回
```
{
 "content": {
   "group": [1, 2, 3, 4, 5],
   "group_child_map": {
       "1": [],
       "2": [],
       "3": [],
       "4": [],
       "5": [6, 7],
   }
   "detail": {
      1: { "id": 1, "resource_name":  "项目管理", "resource_type": 1, "value":  "proj_management", "parent_id": 0, "rank": 1 }
      2: { "id": 2, "resource_name":  "员工管理", "resource_type": 1, "value":  "crew_management", "parent_id": 0, "rank": 1 }
      3: { "id": 3, "resource_name":  "模板管理", "resource_type": 1, "value":  "template_management", "parent_id": 0, "rank": 1 }
      4: { "id": 4, "resource_name":  "报表管理", "resource_type": 1, "value":  "charts_management", "parent_id": 0, "rank": 1 }
      5: { "id": 5, "resource_name":  "权限管理", "resource_type": 1, "value":  "rights_management", "parent_id": 0, "rank": 1 }
      6: { "id": 6, "resource_name":  "新增权限", "resource_type": 1, "value":  "rights_add", "parent_id": 5, "rank": 1 }
      7: { "id": 7, "resource_name":  "修改权限", "resource_type": 1, "value":  "rights_update", "parent_id": 5, "rank": 1 }
   }
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
-------


## 根据顶级权限编号获取相应的权限列表

### 接口介绍

>uri: /rights/uiElements/byParentId
>method: GET
>返回数据格式: JSON

### 参数列表
>parent_id 父资源编号 Integer


### 调用示例
```
{
  'parent_id': 0, // 0-表示顶级资源
}
```

### 成功返回
```
{
 "status": "ok",
 "content": [{'resource_id': 1, 'resource_name': 'xxx', 'value': 'crew_management'}]
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```