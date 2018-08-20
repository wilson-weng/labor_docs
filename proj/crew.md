# 项目人员管理

## 项目报名

### 接口介绍

>uri: /proj/crew
>method: POST
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON


### 参数列表
>real_name 公司名称 String
>id_card_num 身份证号码 String
>phone 电话 Long
>proj_id 项目编号 Integer
>id_card_front_pic 身份证正面照 String


### 调用示例
```
{
 "real_name": "王小丫",
 "id_card_num": "510113199510167509",
 "phone": 18810922511,
 "proj_id: 1,
 "id_card_front_pic", "qiniu.com/abxazggqqp"
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

## 项目人员导入

### 接口介绍

>uri: /crew/import
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
>project_id 项目编号 Integer
>file 文件 file
>import_mode 导入模式 Integer 0-正常导入, 1-覆盖导入


### 调用示例
```
export function submitForm(formData) {
    return fetch(`${Url.PROJ_CREW_IMPORT}`, {
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

## 项目人员删除

### 接口介绍
>uri: /proj/crew
>method: DELETE
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
> proj_id 项目编号 Integer
> crew_id 人员编号 Integer


### 调用示例
{
  "proj_id": 1,
  "crew_id": 2
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

## 项目人员列表(支持搜索)
>uri: /proj/crew
>method: GET
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>page  具体页 Integer
>search_str 搜索字符串  String
>proj_id 项目编号 Integer
>search_type 搜索方式1-员工姓名 2-员工电话

### 调用示例
```
{
  "page": 1,
  "search_str": "张员外",
  "search_type": 1,
  "proj_id": 1
}
```


### 成功返回
```
{
 "content": {
   result:[{"real_name": "张三", "phone": 16133131011, "entry_date": "2018-09113", "total_work_day": 30}],
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


## 项目人员导出(excel会被自动下载到浏览器)
>uri: /proj/crew/export
>method: GET
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>page  具体页 Integer
>search_str 搜索字符串  String
>search_type 搜索方式1-员工姓名 2-员工电话 Integer
>proj_id 项目人员编号  Integer

### 调用示例
```
{
  "page": 1,
  "search_str": "张员外",
  "search_type": 1,
  "proj_id": 1
}
```


### 成功返回
```
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

## 员工详情

### 接口介绍
>uri: /proj/crew
>method: GET

>返回数据格式: JSON

### 参数列表
>crew_id 员工编号 Integer
>proj_id 项目编号 Integer


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

## 指定项目员工离职

### 接口介绍
>uri: /proj/crew/leave
>method: PUT
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>crew_id 员工编号 Integer
>proj_id 项目编号 Integer


### 调用示例
{
   "crew_id": 1,
   "proj_id": 2
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
 "msg": "无权限操作此员工"
}
```


---

## 当前项目员工审核

### 接口介绍
>uri: /proj/crew/verify
>method: PUT
>content-type: application/x-www-form-urlencoded
>返回数据格式: JSON

### 参数列表
>crew_id 员工编号 Integer
>proj_id 项目编号  Integer
>verify_status 1-审核通过, 2-审核驳回

### 调用示例
{ 
  "proj_id": 1,
  "crew_id": 2,
  "verify_status": 1
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
 "msg": "无权限操作此员工"
}
```


