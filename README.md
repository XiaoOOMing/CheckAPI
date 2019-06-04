- [OA项目列表](#OA项目列表)
- [OA合同列表](#OA合同列表)

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

### 返回值

```
// 存在满足条件的合同

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

```
