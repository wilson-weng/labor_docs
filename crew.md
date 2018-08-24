# 人员管理(这里与项目无关, 只管理人员的基础信息)


## 员工列表

### 接口介绍
>uri: /crew
>调用方式: GET
>返回数据格式: JSON

### 参数列表
>page 第几页 Integer
>proj_id 项目编号 Integer

### 调用示例
{
  "page": 1,
  "proj_id": 1
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


--

## 员工详情

### 接口介绍
>uri: /crew/detail
>method: GET

>返回数据格式: JSON

### 参数列表
>crew_id 员工编号 Integer


### 调用示例
{
 "crew_id": 1,
 "proj_id": 2
}

### 成功返回
```
{
 "status": "ok",
 "content": {
    "base_data": {
      "real_name": "唐海伦",
      "current_proj_name": "上海3CA电脑办公仓1号库",
      "current_proj_id": 1,
      "entry_date": "2018-09-01",
      "start_date": "2018-09-01",
      "work_status": "1" //当前工作状态 0-报名，1-工作中,2-工作结束,3-已离职
    },
    "income_data": [
      {"date": "2018.7.8", "work_hours": 18.9, "settlement_amount": 189}
    ],
    "fine_data" [
      {}
    ]
 }
}
```

### 错误返回
```
{
 "status": "error",
 "msg": "无权限查看此员工"
}
```
---