# 赔付管理

## 导入赔付数据

### 接口介绍

>uri: /fine/import
>method: POST
>content-type: application/x-www-form-urlencoded
>headers: 
```
{
    'mimetype': 'multipart/form-data',
    'enctype': 'multipart/form-data',
    'X-Requested-With': 'XMLHttpRequest'
}
```
>返回数据格式: JSON

### 参数列表

>proj_id 项目编号 Integer
>file 文件 file
>import_mode 导入模式 Integer 0-正常导入, 1-覆盖导入


### 调用示例
```
export function submitForm(formData) {
    return fetch(`${Url.FINE_DATA_IMPORT}`, {
        method: 'post',
        headers:{
            'mimetype': 'multipart/form-data',
            'enctype': 'multipart/form-data',
            'X-Requested-With': 'XMLHttpRequest'
        },
        body: formData
    })
      .then(response => response.json())
      .then(json => {
          return json;
      });

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
 "msg": "人员信息冲突....."
}
```
---

## 结算列表

### 接口介绍
>uri: /fine
>method: GET
>返回数据格式: JSON

### 参数列表
>page 第几页 Integer 
>start_date 开始日期 String
>end_date 结束日期 String
>proj_id 项目编号 Integer
>supplier_name 供应商


### 调用示例
{
  "page": 1,
  "start_date": "2018-09-01",
  "end_date": "2018-09-11",
  "supplier_name": "xxx",
  "proj_id": 1
}

### 成功返回
```
{
 "content": {
   result:[{"date": "2018-09-11", "real_name": "张三", "phone": 18909810913, "fine_reason": "打坏东西", "fine_amount": 180}]
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


## 赔付导出

### 接口介绍
>uri: /fine
>method: GET
>返回数据格式: JSON

### 参数列表
>page 第几页 Integer
>start_date 开始日期 String
>end_date 结束日期 String
>proj_id 项目编号 Integer


### 调用示例
{
  "page": 1,
  "start_date": "2018-09-01",
  "end_date": "2018-09-11",
  "proj_id": 1
}

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