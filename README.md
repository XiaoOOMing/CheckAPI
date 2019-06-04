- [OA项目列表](#OA项目列表)
- [OA合同列表](#OA合同列表)
- [创建报告](#创建报告)

# OA项目列表

- 接口地址：http://localhost/api/check/getProjectData
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getProjectData
http://localhost/api/check/getProjectData?pro_id=1

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
saletype | false | Int | 0（默认）项目。1 采购
pro_id | false | Int | 项目ID。如果填写则查询单个项目

### 返回值

```
// 项目列表
[
	{
		"pro_id”:”1”,
		"pro_number":"MKCE19085",
		"pro_name”:”离心泵”,
		"pro_type":"0",
		"cstime":"1559554319",
		"entry":"7"
	},
	{
		"pro_id”:”2”,
		"pro_number":"MKCE19085",
		"pro_name”:”分离机”,
		"pro_type":"0",
		"cstime":"1559554319",
		"entry":"7"
	},
]

// 输入ID，查询单个项目信息（如果有）

{
	"pro_id”:”1”,
	"pro_number":"MKCE19085",
	"pro_name”:”离心泵”,
	"pro_type":"0",
	"cstime":"1559554319",
	"entry":"7"
}

// 输入ID，查询单个项目信息（没有查到）

[]
```

# OA合同列表

- 接口地址：http://localhost/api/check/getContractData
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getContractData?pro_id=1

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
pro_id | true | Int | 项目ID
ct_id | false | Int | 指定合同ID

### 返回值

```
// 合同列表

[
	{
		"pro_id”:"1",
		"ct_id”:"1",
		"supplier_id”:"1",
		"number”:"1",
		"num_attr”:"1",
		"buytype":"0",
		"ct_name":"刮刀离心机备件采购",
		"supplier":"江苏械制造公司",
		"ct_number":"MKCP18087-2"
	},
	{
		"pro_id”:"2",
		"ct_id”:"2",
		"supplier_id”:"1",
		"number”:"1",
		"num_attr”:"1",
		"buytype":"0",
		"ct_name":"刮刀离心机备件采购",
		"supplier":"江苏械制造公司",
		"ct_number":"MKCP18087-2"
	}
]

// 不存在合同

[]

// 指定合同

{
	"pro_id”:"1",
	"ct_id”:"1",
	"supplier_id”:"1",
	"number”:"1",
	"num_attr”:"1",
	"buytype":"0",
	"ct_name":"刮刀离心机备件采购",
	"supplier":"江苏械制造公司",
	"ct_number":"MKCP18087-2"
}

```

# 创建报告

- 接口地址：http://localhost/api/check/createReport
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/createReport

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
pro_id | true | Int | 项目ID
ct_id | true | Int | 指定合同ID
title | true | String | 报告标题
uid | true | Int | 用户ID
type | true | Int | 0草稿 1报告
state | true | Int | 0正常报告 1已复验 2旧报告 3待复验
basicinfo | true | Json | 1.基本信息
facadeinfo | true | Json | 2.外观检查
randominfo | true | Json | 3.随机资料
technologyinfo | true | Json | 4.技术要求
equipmentinfo | true | Json | 5.随机备件
testinfo | true | Json | 6.现场测试
summary | true | Json | 7.总结
signature | true | Json | 8.签名

# Json对照表

模型：["title": item.title, "content": item.content, "check": item.check, "pictures": item.pictures, "content2": item.content2, "style": item.style]

说明：

### style = 3 判断Cell

有用的字段：
check：true ✅，false ❌
title：标题

### style = 6 输入Cell

有用的字段：
title：标题
content：占位文字
content2: 实际内容

### style = 8 图片Cell

有用的字段：
title：标题
pictures：图片数组

### style = 1 点击弹出选择框Cell（答案保存在本地）

有用的字段：
title：标题
content：选择的内容（默认为：请选择）

### style = 10 输入区域Cell （TextArea）

有用的字段：
title：占位文字
content：实际内容

### style = 12 随机备件页添加的Cell

有用的字段：
title：备件名称
content：备件型号
content2:  数量

### style = 14 展示时间的Cell

有用的字段：
title：标题
content：内容（时间）
