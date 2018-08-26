# 项目管理

## 新建

### 接口介绍

>uri: /proj
>method: POST
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON



### 参数列表
>company_id: 所属公司编号
>proj_name 公司编号 Integer
>address 项目地址 String
>description 项目描述 String
>crew_num 所需人员数量 Integer
>category  项目品类 1-京东 2-淘宝 3-顺丰 Integer
>pic_url_list 项目图片地址列表 String

### 调用示例
```
{
  "company_id": 1,
  "proj_name": "",
  "address": "上海虹桥",
  "descrption": "这是一个大项目",
  "crew_num": 200,
  "category": 1,
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
>proj_id 项目编号 Integer
>company_id 所属公司编号 Integer
>proj_name 公司编号 Integer
>address 项目地址 String
>description 项目描述 String
>crew_num 所需人员数量 Integer
>category  项目品类 1-京东 2-淘宝 3-顺丰 Integer
>wage_mode 结算模式 1-计时 2-计件  Integer
>pic_url_list 项目图片地址列表 String

### 调用示例
```
{
  "company_id": 1
  "proj_id": 1,
  "proj_name": "",
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



## 项目列表

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
   result:[{"company_id": 1, "company_name: "明星人力资源公司", "address": "浦东南路", "proj_name": "",
    "crew_num": 100, "description": "", "work_crew_num": 90, "current_month_income": 480001331, "message_count": 6}],
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


## 更改项目状态


### 接口介绍
>uri: /proj/status
>method: PUT
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>proj_id 项目编号 Integer
>proj_status 项目状态 0-招工(未开始),1-进行中,2-已结束, 3-异常 Integer 

### 调用示例
```
{
  "proj_id": 1,
  "proj_status": 1
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