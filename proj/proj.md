# 项目管理

## 新建

### 接口介绍

>uri: /proj
>method: POST
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON



### 参数列表
>company_id: 所属公司编号
>proj_id 公司编号 Integer
>address 项目地址 String
>description 项目描述 String
>crew_num 所需人员数量 Integer
>start_date 开始时间 String
>end_date 结束时间 String
>category  项目品类 1-京东 2-淘宝 3-顺丰 Integer
>wage_mode 结算模式 1-计时 2-计件  Integer
>pic_url_list 项目图片地址列表 String

### 调用示例
```
{
  "company_id": 1,
  "proj_id": 1,
  "address": "上海虹桥",
  "descrption": "这是一个大项目",
  "crew_num": 200,
  "start_date": "2018-09-10",
  "end_date": "2018-07-10",
  "category": 1,
  "wage_mode": 1,
  "pic_url_list": "qiniu.com/asslguurlqq;qiniu.com/asslguurlqc"
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
>uri: /proj
>method: PUT
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表

>company_id: 所属公司编号
>proj_id 公司编号 Integer
>address 项目地址 String
>description 项目描述 String
>crew_num 所需人员数量 Integer
>start_date 开始时间 String
>end_date 结束时间 String
>category  项目品类 1-京东 2-淘宝 3-顺丰 Integer
>wage_mode 结算模式 1-计时 2-计件  Integer
>pic_url_list 项目图片地址列表 String

### 调用示例
```
{
  "company_id": 1
  "proj_id": 1,
  "address": "上海虹桥",
  "descrption": "这是一个大项目",
  "crew_num": 200,
  "start_date": "2018-09-10",
  "end_date": "2018-07-10",
  "category": 1,
  "wage_mode": 1,
  "pic_url_list": "qiniu.com/asslguurlqq;qiniu.com/asslguurlqc"
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
>uri: /proj/<int:proj_id>
>method: DELETE
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>proj_id 公司编号 Integer


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



## 公司列表

### 接口介绍
>uri: /proj
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
   result:[],
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
