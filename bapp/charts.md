# 报表模块


## 报表列表

### 接口介绍

>uri: /charts
>method: GET
>返回数据格式: JSON


### 参数列表
> proj_id 项目编号 Integer 0表示全部项目
> data_type 数据类型,逗号隔开  // 0-表示所有 1-收支, 2-平均人效, 3-人员流失率

### 调用示例
```
{
  "proj_id": 1,
  "data_type": "1, 2, 3"
}
```

### 成功返回
```
{
 "status": "ok",
 "content": [
  {
    "style": "bar", //图标样式 bar-柱状图/条形图 pie-饼图 table-表格
    "data_type": 1, 
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
      "data_type": 2,
      "charts_name": "平均人效",
      "style": "bar",
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
       "data_type": 3, 
       "charts_name": "人员流失率",
       "style": "bar",
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