# 报表模块


## 报表列表

### 接口介绍

>uri: /charts
>method: GET
>返回数据格式: JSON


### 参数列表
> proj_id 项目编号 Integer 0表示全部项目

### 调用示例
```
{
  "proj_id": 1
}
```

### 成功返回
```
{
 "status": "ok",
 "content": [
  {
    "charts_name": "收支",
    "total_income": 190555, //元
    "salary": 121000
    "data_set": [
       {"month:""2018-01-01": num:0},
       {"month:""2018-02-01": num:1000},
       {"month:""2018-03-01": num:60000},
       {"month:""2018-04-01": num:79900},
       {"month:""2018-05-01": num:90000},
       {"month:""2018-06-01": num:100020}
    ]
  },
  {
      "charts_name": "平均人效",
      "data_set": [
        {"week:"W1", num:0, "success_rate": 0.282},
        {"week:"W2", num:1000, "success_rate": 0.282},
        {"week:"W3", num:60000, "success_rate": 0.282},
        {"week:"W4", num:79900, "success_rate": 0.282},
        {"week:"W5", num:90000, "success_rate": 0.282},
        {"week:"W6", num:100020, "success_rate": 0.282}
      ]
   },
   {
       "charts_name": "人员流失率",
       "data_set": [
            {"week:"W1", num:0, "leave_rate": 0.282},
            {"week:"W2", num:1000, "leave_rate": 0.282},
            {"week:"W3", num:60000, "leave_rate": 0.282},
            {"week:"W4", num:79900, "leave_rate": 0.282},
            {"week:"W5", num:90000, "leave_rate": 0.282},
            {"week:"W6", num:100020, "leave_rate": 0.282}
       ]
   }
 ]
}
```

### 错误返回
```
{
 "status": "error",
 "msg": ""
}
```