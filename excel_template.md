# excel模板管理

## 项目报名

### 模板下载

>uri: /excel_template/download
>method: GET
>返回数据格式: JSON


### 参数列表
>process 流程 1-工作记录模板,2-赔付记录模板,3-员工信息模板
>proj_id 项目编号


### 调用示例
```
{
 "proj_id": "项目编号",
 "process": 1
}
```

### 成功返回(模板会下载到浏览器)
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
