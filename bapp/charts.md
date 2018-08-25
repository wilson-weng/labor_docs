# 报表模块


## 报表列表

### 接口介绍

>uri: /charts
>method: GET
>返回数据格式: JSON


### 参数列表
> proj_id 项目编号 Integer 0表示全部项目
> chart_id chart编号,逗号隔开,可同时获取多种数据  // 0-表示所有 1-收支, 2-平均人效, 3-人员流失率

### 调用示例
```
{
  "proj_id": 1,
  "chart_id": "1, 2, 3"
}
```

### 成功返回
```
{
 "status": "ok",
 "content": [
  {
    "chart_id": 1, 
    "chart_name": "项目收支月度报表",
    "meta_data": {
       "total_income": 190555, //元
       "salary": 121000
    },
    "options": {
          legend: {
              data: ['应收', '工资', '利润'],
              left: 'center',
              bottom: '30px',
              z: 100
          },

          xAxis: {
              type: 'category',
              boundaryGap: false,
              data: ['2018-01', '2018-02', '2018-03', '2018-04', '2018-05', '2018-06', '2018-07'],
          },
          yAxis: {
              x: 'center',
              type: 'value',
              axisLabel: {
                  formatter: (value, index) => {
                      if (value >= 10000 && value < 10000000) {
                          value = value / 10000 + "万";
                      } else if (value >= 10000000) {
                          value = value / 10000000 + "千万";
                      }
                      return value;
                  }
              },
          },
          grid: {
              containLabel: true
          },
          series: [{
              name: '应收',
              type: 'line',
              smooth: true,
              data: [0, 1000, 65000, 70900, 100000, 150000, 620000]
          }, {
              name: '工资',
              type: 'line',
              smooth: true,
              data: [500, 800, 30000, 50000, 89000, 112000, 489000]
          }, {
              name: '利润',
              type: 'bar',
              smooth: true,
              data: [-500, 200, 35000, 20900, 11000, 38000, 131000]
          }]
      }
  },
  {
      "chart_id": 2,
      "chart_name": "每周项目人效达成情况",
      "options": {
          legend: {
              data: ['人效达成'],
              left: 'center',
              bottom: '30px',
              z: 100
          },

          xAxis: {
              type: 'category',
              boundaryGap: false,
              data: ['week20', 'week21', 'week22', 'week23',],
          },
          yAxis: {
              x: 'center',
              type: 'value',
              axisLabel: {
                  show: true,
                  interval: 'auto',
                  formatter: '{value}%'
              },
          },
          grid: {
              containLabel: true
          },
          series: [{
              name: '人效达成',
              type: 'line',
              smooth: true,
              data: [0, 20, 56, 77]
          }]
      }
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
