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


