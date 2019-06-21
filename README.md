- [上传](#上传)
- [OA项目列表](#OA项目列表)
- [OA合同列表](#OA合同列表)
- [创建报告](#创建报告)
- [项目列表](#项目列表)
- [合同列表](#合同列表)
- [报告列表](#报告列表)
- [获取基本信息](#获取基本信息)
- [报告详情](#报告详情)
- [上传装箱资料](#上传装箱资料)
- [发送评论](#发送评论)
- [创建草稿箱](#创建草稿箱)
- [获取草稿箱](#获取草稿箱)
- [待复验合同](#待复验合同)
- [搜索报告](#搜索报告)
- [我的报告](#我的报告)

# 上传

- 接口地址：http://localhost/api/check/upload
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/upload

### 返回值

```
{
    "result": "success",
    "filename": ["1.jpg", "2.jpg"],
}
```


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
draft_id | false | Int | 草稿箱ID（需要删除的草稿箱ID）
old_rep_id | false | Int | 项目ID（需要设为旧报告的ID）
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

### style = 2 基本信息中锁定的Cell

有用的字段：

title:标题

content：内容

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

# 项目列表

- 接口地址：http://localhost/api/check/getProjects
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getProjects

### 返回值

```
[
    {
        "pro_id":"1",
        "pro_name":"俄罗斯Amylco刮刀备件",
        "pro_number":"MKCE18087",
        "pro_total":"2",
        "pro_type":"0"
    },
    {
        "pro_id":"2",
        "pro_name":"伊朗项目泵机封",
        "pro_number":"MKCE19085",
        "pro_total":"3",
        "pro_type":"0"
    }
]
```

# 合同列表

- 接口地址：http://localhost/api/check/getContracts
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getContracts?pro_id=1

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
pro_id | true | Int | 项目ID

### 返回值

```
[
    {
        "ct_id":"1",
        "pro_id":"1",
        "ct_name":"刮刀离心机备件采购",
        "ct_number":"MKCP18087-2",
        "ct_total":"2",
        "ct_review":"0"
    },
    {
        "ct_id":"2",
        "pro_id":"2",
        "ct_name":"刮刀离心机备件采购",
        "ct_number":"MKCP18087-2",
        "ct_total":"2",
        "ct_review":"0"
    }
]
```

# 报告列表

- 接口地址：http://localhost/api/check/getReport
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getReport?pro_id=1&ct_id=1&recheck=0

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
pro_id | true | Int | 项目ID
ct_id | true | Int | 合同ID
recheck | false | Int | 0所有报告；1待复验。默认为0。

### 返回值

```
// 所有报告
[
    {
        "id":"1",
        "pro_id":"1",
        "ct_id":"1",
        "supplier_id":"1",
        "project":"俄罗斯Amylco刮刀备件",
        "contract":"刮刀离心机备件采购",
        "supplier":"江苏赛德力制药机械制造有限公司",
        "title":"待复验项目",
        "cuser":"孟祥燕",
        "cuid":"1",
        "ctime":"2019年06月12日",
        "type":"1",
        "state":"0"
    }
]

// 待复验报告
[
    {
        "id":"1",
        "pro_id":"1",
        "ct_id":"1",
        "supplier_id":"1",
        "project":"伊朗项目泵机封",
        "contract":"离心泵机械密封采购",
        "supplier":"温州市康而达实业有限公司",
        "title":"hello world",
        "cuser":"孟祥燕",
        "cuid":"1",
        "ctime":"2019年06月17日",
        "type":"1",
        "state":"3"
    }
]
```


# 获取基本信息

- 接口地址：http://localhost/api/check/getBasicInfo
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getBasicInfo?pro_id=1&ct_id=1

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
pro_id | true | Int | 项目ID
ct_id | true | Int | 合同ID

### 返回值

```
{
    "project_name":"MKCE18087 俄罗斯Amylco刮刀备件",
    "contract_name":"MKCP18087-2 刮刀离心机备件采购",
    "supplier":"江苏赛德力制药机械制造有限公司"
}
```

# 报告详情

- 接口地址：http://localhost/api/check/getReportDetail
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getReportDetail?rep_id=1

返回Json格式信息


# 上传装箱资料

- 接口地址：http://localhost/api/check/uploadJJCPictures
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/uploadJJCPictures?rep_id=1&type=jjc&pictures=["picture1.jpg","picture2.jpg"]

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
rep_id | true | Int | 报告ID
type | true | String | jjc => 件重尺 zxd => 装箱单 other => 其他资料
pictures | true | String | 图片Json => ["picture1.jpg", "picture2.jpg"]

# 发送评论

- 接口地址：http://localhost/api/check/comment
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/comment?rep_id=1&comment=How are you?&cuid=1

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
rep_id | true | Int | 报告ID
comment | true | String | 评论内容
cuid | true | Int | 用户ID

# 创建草稿箱

- 接口地址：http://localhost/api/check/createDraft
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/createDraft

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
pro_id | true | Int | 项目ID
ct_id | true | Int | 合同ID
title | true | String | 草稿箱标题
uid | true | Int | 用户ID
technologyinfo | true | Int | JSON：技术要求
equipmentinfo | true | Int | JSON：随机备件

# 获取草稿箱

- 接口地址：http://localhost/api/check/getDrafts
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/getDrafts?uid=1

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
uid | true | Int | 当前用户ID

### 返回值

```

[
    {
        "id":"23",
        "pro_id":"146",
        "ct_id":"1366",
        "supplier_id":"39",
        "project":"伊朗项目泵机封",
        "contract":"MKCP19085-1 离心泵机械密封采购",
        "supplier":"温州市康而达实业有限公司",
        "title":"草稿箱",
        "cuser":"孟祥燕",
        "cuid":"2",
        "ctime":"2019年06月17日",
        "type":"0",
        "state":"0",
        "equipmentinfo":"[{"title":"法兰","style":12,"content":"型号","pictures":[],"check":false,"content2":"100"},{"title":"罐子","content":"型号","content2":"10","check":false,"pictures":[],"style":12}]",
        "technologyinfo":"[{"check":true,"content":"","pictures":[],"content2":"","style":3,"title":"真空"}]"
    }
]

```

# 待复验合同

- 接口地址：http://localhost/api/check/recheckContracts
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/recheckContracts

### 返回值

```
[
    {
        "ct_id":"1",
        "pro_id":"1",
        "ct_name":"离心泵机械密封采购",
        "ct_number":"MKCP19085-1",
        "ct_total":"5",     // 总报告数
        "ct_review":"0",
        "count":1   // 待复验报告数
    }
]
```

# 搜索报告

- 接口地址：http://localhost/api/check/search
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/search?key=关键词

### 返回值

```
[
    {
        "id":"1",
        "pro_id":"1",
        "ct_id":"1",
        "supplier_id":"1",
        "project":"伊朗项目泵机封",
        "contract":"离心泵机械密封采购",
        "supplier":"温州市康而达实业有限公司",
        "title":"123123123",
        "cuser":"孟祥燕",
        "cuid":"1",
        "ctime":"1560741889",
        "type":"1",
        "state":"3",
        "contract_name":"MKCP19085-1 离心泵机械密封采购"
    }
]
```

# 我的报告

- 接口地址：http://localhost/api/check/myReport
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/check/myReport?uid=1

### 返回值

```
[
    {
        "id":"16",
        "pro_id":"146",
        "ct_id":"1366",
        "supplier_id":"39",
        "project":"伊朗项目泵机封",
        "contract":"离心泵机械密封采购",
        "supplier":"温州市康而达实业有限公司",
        "title":"123123123",
        "cuser":"孟祥燕",
        "cuid":"2",
        "ctime":"1560741889",
        "type":"1",
        "state":"3",
        "time":"2019年06月17日"
    }
]
```
