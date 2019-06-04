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
basicimg | true | Json | 1.全景图片
facadeinfo | true | Json | 2.外观检查
facadeimg | true | Json | 2.外观检查图片
randominfo | true | Json | 3.随机资料
randodesc | true | Json | 3.随机资料描述
technologyinfo | true | Json | 4.技术要求
technologyimg | true | Json | 4.技术要求图片
equipmentinfo | true | Json | 5.随机备件
equipmentimg | true | Json | 5.随机备件图片
testinfo | true | Json | 6.现场测试
testresult | true | Json | 6.现场测试结果
testimg | true | Json | 6.现场测试图片
summary | true | Json | 7.总结
filejzc | true | Json | 7.件重尺
filezxd | true | Json | 7.装箱单
fileother | true | Json | 7.文件
signature | true | Json | 8.签名

