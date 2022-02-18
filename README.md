
# 接口文档

## 分类服务

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/category/add`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求示例**：

```json
{
	"name": "",
	"parentId": 0
}
```


**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型     | schema       |
| ------------- | ------------------------- | ------ | -------- | ------------ | ------------ |
| Authorization | 格式：Bearer access_token | header | true     | string       |              |
| request       | 添加分类                  | body   | true     | 添加分类json | 添加分类json |

**schema属性说明**



**添加分类json**

| 参数名称 | 参数说明                     | in   | 是否必须 | 数据类型       | schema |
| -------- | ---------------------------- | ---- | -------- | -------------- | ------ |
| name     | 名称                         | body | false    | string         |        |
| parentId | 父类id,添加根目录分类时值为0 | body | false    | integer(int32) |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 删除分类

**接口描述**:需要accessToken，逻辑删除,需要管理员权限，若存在子类，则不允许删除

**接口地址**:`/category/delete/{id}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 分类id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 获取分类列表

**接口描述**:不分上下级，返回所有分类(已删除除外)

**接口地址**:`/category/list`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"id": 0,
			"name": "",
			"parentId": 0
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | array          | Category对象   |
| message  | 响应信息 | string         |                |



**schema属性说明**




**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**响应状态**:


| 状态码 | 说明         | schema                              |
| ------ | ------------ | ----------------------------------- |
| 200    | OK           | api响应json对象«List«Category对象»» |
| 401    | Unauthorized |                                     |
| 403    | Forbidden    |                                     |
| 404    | Not Found    |                                     |
## 分页获取分类

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/category/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 页码                      | query  | false    | integer  |        |
| size          | 每页数量                  | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"id": 0,
				"name": "",
				"parentId": 0
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                | schema              |
| -------- | -------- | ------------------- | ------------------- |
| code     | 响应码   | integer(int32)      | integer(int32)      |
| data     | 响应数据 | IPage«Category对象» | IPage«Category对象» |
| message  | 响应信息 | string              |                     |



**schema属性说明**




**IPage«Category对象»**

| 参数名称    | 参数说明 | 类型           | schema       |
| ----------- | -------- | -------------- | ------------ |
| current     |          | integer(int64) |              |
| pages       |          | integer(int64) |              |
| records     |          | array          | Category对象 |
| searchCount |          | boolean        |              |
| size        |          | integer(int64) |              |
| total       |          | integer(int64) |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**响应状态**:


| 状态码 | 说明         | schema                               |
| ------ | ------------ | ------------------------------------ |
| 200    | OK           | api响应json对象«IPage«Category对象»» |
| 401    | Unauthorized |                                      |
| 403    | Forbidden    |                                      |
| 404    | Not Found    |                                      |
## 获取分类树

**接口描述**:数据结构为树型结构，需要accessToken，需要管理员权限

**接口地址**:`/category/tree`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"children": [
				{
					"children": [
						{}
					],
					"id": 0,
					"name": "",
					"parentId": 0
				}
			],
			"id": 0,
			"name": "",
			"parentId": 0
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema          |
| -------- | -------- | -------------- | --------------- |
| code     | 响应码   | integer(int32) | integer(int32)  |
| data     | 响应数据 | array          | CategoryNodeDTO |
| message  | 响应信息 | string         |                 |



**schema属性说明**




**CategoryNodeDTO**

| 参数名称 | 参数说明 | 类型           | schema          |
| -------- | -------- | -------------- | --------------- |
| children | 子目录   | array          | CategoryNodeDTO |
| id       | id       | integer(int32) |                 |
| name     | 名称     | string         |                 |
| parentId | 父类id   | integer(int32) |                 |

**响应状态**:


| 状态码 | 说明         | schema                                 |
| ------ | ------------ | -------------------------------------- |
| 200    | OK           | api响应json对象«List«CategoryNodeDTO»» |
| 401    | Unauthorized |                                        |
| 403    | Forbidden    |                                        |
| 404    | Not Found    |                                        |
## 修改分类名

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/category/update`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 分类id                    | query  | false    | integer  |        |
| name          | 标签名                    | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
# 友链服务

## 删除友链


**接口描述**:


**接口地址**:`/friend/link/delete/{id}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 友链id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 获取友链列表


**接口描述**:


**接口地址**:`/friend/link/list`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"icon": "",
			"id": 0,
			"name": "",
			"url": ""
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema          |
| -------- | -------- | -------------- | --------------- |
| code     | 响应码   | integer(int32) | integer(int32)  |
| data     | 响应数据 | array          | FriendChain对象 |
| message  | 响应信息 | string         |                 |



**schema属性说明**




**FriendChain对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| icon     | 图标     | string         |        |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| url      | 链接     | string         |        |

**响应状态**:


| 状态码 | 说明         | schema                                 |
| ------ | ------------ | -------------------------------------- |
| 200    | OK           | api响应json对象«List«FriendChain对象»» |
| 401    | Unauthorized |                                        |
| 403    | Forbidden    |                                        |
| 404    | Not Found    |                                        |
## 分页获取友链列表


**接口描述**:


**接口地址**:`/friend/link/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 页码                      | query  | false    | integer  |        |
| size          | 每页数量                  | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"icon": "",
				"id": 0,
				"name": "",
				"url": ""
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                   | schema                 |
| -------- | -------- | ---------------------- | ---------------------- |
| code     | 响应码   | integer(int32)         | integer(int32)         |
| data     | 响应数据 | IPage«FriendChain对象» | IPage«FriendChain对象» |
| message  | 响应信息 | string                 |                        |



**schema属性说明**




**IPage«FriendChain对象»**

| 参数名称    | 参数说明 | 类型           | schema          |
| ----------- | -------- | -------------- | --------------- |
| current     |          | integer(int64) |                 |
| pages       |          | integer(int64) |                 |
| records     |          | array          | FriendChain对象 |
| searchCount |          | boolean        |                 |
| size        |          | integer(int64) |                 |
| total       |          | integer(int64) |                 |

**FriendChain对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| icon     | 图标     | string         |        |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| url      | 链接     | string         |        |

**响应状态**:


| 状态码 | 说明         | schema                                  |
| ------ | ------------ | --------------------------------------- |
| 200    | OK           | api响应json对象«IPage«FriendChain对象»» |
| 401    | Unauthorized |                                         |
| 403    | Forbidden    |                                         |
| 404    | Not Found    |                                         |
## 新增或更新友链

**接口描述**:id不为空时更新，需要accessToken，需要管理员权限

**接口地址**:`/friend/link/save`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
	"icon": "",
	"id": 0,
	"name": "",
	"url": ""
}
```


**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型        | schema          |
| ------------- | ------------------------- | ------ | -------- | --------------- | --------------- |
| Authorization | 格式：Bearer access_token | header | true     | string          |                 |
| friendLink    | 友链表                    | body   | true     | FriendChain对象 | FriendChain对象 |

**schema属性说明**



**FriendChain对象**

| 参数名称 | 参数说明 | in   | 是否必须 | 数据类型       | schema |
| -------- | -------- | ---- | -------- | -------------- | ------ |
| icon     | 图标     | body | false    | string         |        |
| id       | id       | body | false    | integer(int32) |        |
| name     | 名称     | body | false    | string         |        |
| url      | 链接     | body | false    | string         |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
# 客户端服务

## 删除客户端

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/client/delete/{id}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | id                        | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 分页获取客户端列表

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/client/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 页码                      | query  | false    | integer  |        |
| size          | 每页数量                  | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"accessTokenExpire": 0,
				"clientId": "",
				"clientSecret": "",
				"enableRefreshToken": 0,
				"id": 0,
				"refreshTokenExpire": 0
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型              | schema            |
| -------- | -------- | ----------------- | ----------------- |
| code     | 响应码   | integer(int32)    | integer(int32)    |
| data     | 响应数据 | IPage«Client对象» | IPage«Client对象» |
| message  | 响应信息 | string            |                   |



**schema属性说明**




**IPage«Client对象»**

| 参数名称    | 参数说明 | 类型           | schema     |
| ----------- | -------- | -------------- | ---------- |
| current     |          | integer(int64) |            |
| pages       |          | integer(int64) |            |
| records     |          | array          | Client对象 |
| searchCount |          | boolean        |            |
| size        |          | integer(int64) |            |
| total       |          | integer(int64) |            |

**Client对象**

| 参数名称           | 参数说明                         | 类型           | schema |
| ------------------ | -------------------------------- | -------------- | ------ |
| accessTokenExpire  | access_token有效时长             | integer(int64) |        |
| clientId           | 客户端id，客户端唯一标识         | string         |        |
| clientSecret       | 客户端秘钥                       | string         |        |
| enableRefreshToken | 是否启用refresh_token,1:是，0:否 | integer(int32) |        |
| id                 | id                               | integer(int32) |        |
| refreshTokenExpire | refresh_token有效时长            | integer(int64) |        |

**响应状态**:


| 状态码 | 说明         | schema                             |
| ------ | ------------ | ---------------------------------- |
| 200    | OK           | api响应json对象«IPage«Client对象»» |
| 401    | Unauthorized |                                    |
| 403    | Forbidden    |                                    |
| 404    | Not Found    |                                    |
## 新增或更新客户端,id为null时新增

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/client/save`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
	"accessTokenExpire": 0,
	"clientId": "",
	"clientSecret": "",
	"enableRefreshToken": 0,
	"id": 0,
	"refreshTokenExpire": 0
}
```


**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型   | schema     |
| ------------- | ------------------------- | ------ | -------- | ---------- | ---------- |
| Authorization | 格式：Bearer access_token | header | true     | string     |            |
| client        | 客户端表                  | body   | true     | Client对象 | Client对象 |

**schema属性说明**



**Client对象**

| 参数名称           | 参数说明                         | in   | 是否必须 | 数据类型       | schema |
| ------------------ | -------------------------------- | ---- | -------- | -------------- | ------ |
| accessTokenExpire  | access_token有效时长             | body | false    | integer(int64) |        |
| clientId           | 客户端id，客户端唯一标识         | body | false    | string         |        |
| clientSecret       | 客户端秘钥                       | body | false    | string         |        |
| enableRefreshToken | 是否启用refresh_token,1:是，0:否 | body | false    | integer(int32) |        |
| id                 | id                               | body | false    | integer(int32) |        |
| refreshTokenExpire | refresh_token有效时长            | body | false    | integer(int64) |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
# 文件存储服务

## 删除文件

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/file/delete`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| fullPath      | 文件全路径                | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 分页分类列表

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/file/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| marker        | marker标记                | query  | false    | string   |        |
| size          | 每页数量                  | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"currentMarker": "",
		"loadedAll": true,
		"nextMarker": "",
		"records": [
			{
				"date": "",
				"name": "",
				"path": "",
				"url": ""
			}
		],
		"size": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型              | schema            |
| -------- | -------- | ----------------- | ----------------- |
| code     | 响应码   | integer(int32)    | integer(int32)    |
| data     | 响应数据 | PageStorageObject | PageStorageObject |
| message  | 响应信息 | string            |                   |



**schema属性说明**




**PageStorageObject**

| 参数名称      | 参数说明 | 类型           | schema        |
| ------------- | -------- | -------------- | ------------- |
| currentMarker |          | string         |               |
| loadedAll     |          | boolean        |               |
| nextMarker    |          | string         |               |
| records       |          | array          | StorageObject |
| size          |          | integer(int32) |               |

**StorageObject**

| 参数名称 | 参数说明 | 类型              | schema |
| -------- | -------- | ----------------- | ------ |
| date     |          | string(date-time) |        |
| name     |          | string            |        |
| path     |          | string            |        |
| url      |          | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                             |
| ------ | ------------ | ---------------------------------- |
| 200    | OK           | api响应json对象«PageStorageObject» |
| 401    | Unauthorized |                                    |
| 403    | Forbidden    |                                    |
| 404    | Not Found    |                                    |
## 上传文件

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/file/upload`


**请求方式**：`POST`


**consumes**:`["multipart/form-data"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in       | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | -------- | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header   | true     | string   |        |
| file          | file                      | formData | true     | file     |        |

**响应示例**:

```json
{
	"code": 0,
	"data": "",
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | string         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema                  |
| ------ | ------------ | ----------------------- |
| 200    | OK           | api响应json对象«string» |
| 201    | Created      |                         |
| 401    | Unauthorized |                         |
| 403    | Forbidden    |                         |
| 404    | Not Found    |                         |
# 文章收藏服务
## 新增收藏

**接口描述**:需要accessToken

**接口地址**:`/article/collect/add`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 查询文章是否已收藏，1：是，0：否

**接口描述**:需要accessToken

**接口地址**:`/article/collect/collected/{articleId}`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": 0,
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | integer(int32) | integer(int32) |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema               |
| ------ | ------------ | -------------------- |
| 200    | OK           | api响应json对象«int» |
| 401    | Unauthorized |                      |
| 403    | Forbidden    |                      |
| 404    | Not Found    |                      |
## 删除收藏

**接口描述**:需要accessToken

**接口地址**:`/article/collect/delete`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 分页查询收藏文章

**接口描述**:需要accessToken

**接口地址**:`/article/collect/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 当前页，默认值：1         | query  | false    | integer  |        |
| size          | 每页数量，默认值为：5     | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"categoryId": 0,
				"categoryList": [
					{
						"id": 0,
						"name": "",
						"parentId": 0
					}
				],
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"next": {
					"categoryId": 0,
					"categoryName": "",
					"collectCount": 0,
					"commentCount": 0,
					"content": "",
					"cover": "",
					"htmlContent": "",
					"id": 0,
					"likeCount": 0,
					"original": 0,
					"publishTime": "",
					"reproduce": "",
					"status": 0,
					"summary": "",
					"title": "",
					"updateTime": "",
					"viewCount": 0
				},
				"original": 0,
				"previous": {
					"categoryId": 0,
					"categoryName": "",
					"collectCount": 0,
					"commentCount": 0,
					"content": "",
					"cover": "",
					"htmlContent": "",
					"id": 0,
					"likeCount": 0,
					"original": 0,
					"publishTime": "",
					"reproduce": "",
					"status": 0,
					"summary": "",
					"title": "",
					"updateTime": "",
					"viewCount": 0
				},
				"publishTime": "",
				"recommendScore": 0,
				"reproduce": "",
				"status": 0,
				"summary": "",
				"tagList": [
					{
						"deleted": 0,
						"id": 0,
						"name": ""
					}
				],
				"title": "",
				"updateTime": "",
				"user": {
					"admin": 0,
					"avatar": "",
					"birthday": "",
					"brief": "",
					"createTime": "",
					"email": "",
					"gender": 0,
					"id": 0,
					"mobile": 0,
					"nickname": "",
					"status": 0,
					"username": ""
				},
				"viewCount": 0
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                 | schema               |
| -------- | -------- | -------------------- | -------------------- |
| code     | 响应码   | integer(int32)       | integer(int32)       |
| data     | 响应数据 | IPage«ArticleVo对象» | IPage«ArticleVo对象» |
| message  | 响应信息 | string               |                      |



**schema属性说明**




**IPage«ArticleVo对象»**

| 参数名称    | 参数说明 | 类型           | schema        |
| ----------- | -------- | -------------- | ------------- |
| current     |          | integer(int64) |               |
| pages       |          | integer(int64) |               |
| records     |          | array          | ArticleVo对象 |
| searchCount |          | boolean        |               |
| size        |          | integer(int64) |               |
| total       |          | integer(int64) |               |

**ArticleVo对象**

| 参数名称       | 参数说明                                | 类型              | schema       |
| -------------- | --------------------------------------- | ----------------- | ------------ |
| categoryId     | 文章分类id                              | integer(int32)    |              |
| categoryList   | 分类列表,顺序:root node2 node3          | array             | Category对象 |
| categoryName   | 分类名称-冗余字段                       | string            |              |
| collectCount   | 收藏数-冗余字段                         | integer(int32)    |              |
| commentCount   | 评论数-冗余字段                         | integer(int32)    |              |
| content        | 文章内容                                | string            |              |
| cover          | 文章封面                                | string            |              |
| htmlContent    | 文章富文本内容                          | string            |              |
| id             | 文章id                                  | integer(int32)    |              |
| likeCount      | 点赞数-冗余字段                         | integer(int32)    |              |
| next           | 下一篇                                  | Article对象       | Article对象  |
| original       | 是否原创，1:是，0:否                    | integer(int32)    |              |
| previous       | 上一篇                                  | Article对象       | Article对象  |
| publishTime    | 发布时间                                | string(date-time) |              |
| recommendScore | 推荐分数                                | number(double)    |              |
| reproduce      | 转载地址                                | string            |              |
| status         | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |              |
| summary        | 文章摘要                                | string            |              |
| tagList        | 标签列表                                | array             | Tag对象      |
| title          | 文章标题                                | string            |              |
| updateTime     | 更新时间                                | string(date-time) |              |
| user           | 作者                                    | User对象          | User对象     |
| viewCount      | 文章浏览次数                            | integer(int32)    |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                                |
| ------ | ------------ | ------------------------------------- |
| 200    | OK           | api响应json对象«IPage«ArticleVo对象»» |
| 401    | Unauthorized |                                       |
| 403    | Forbidden    |                                       |
| 404    | Not Found    |                                       |
# 文章服务


## 文章归档分页查询

**接口描述**:按年月归档，月份文章计数

**接口地址**:`/article/archives/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                   | in     | 是否必须 | 数据类型 | schema |
| ------------- | -------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token  | header | true     | string   |        |
| current       | 当前页,非必传，默认为:1    | query  | false    | integer  |        |
| size          | 每页数量,非必传，默认为:12 | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"articleCount": 0,
				"yearMonth": ""
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                         | schema                       |
| -------- | -------- | ---------------------------- | ---------------------------- |
| code     | 响应码   | integer(int32)               | integer(int32)               |
| data     | 响应数据 | IPage«ArticleArchivesVo对象» | IPage«ArticleArchivesVo对象» |
| message  | 响应信息 | string                       |                              |



**schema属性说明**




**IPage«ArticleArchivesVo对象»**

| 参数名称    | 参数说明 | 类型           | schema                |
| ----------- | -------- | -------------- | --------------------- |
| current     |          | integer(int64) |                       |
| pages       |          | integer(int64) |                       |
| records     |          | array          | ArticleArchivesVo对象 |
| searchCount |          | boolean        |                       |
| size        |          | integer(int64) |                       |
| total       |          | integer(int64) |                       |

**ArticleArchivesVo对象**

| 参数名称     | 参数说明         | 类型           | schema |
| ------------ | ---------------- | -------------- | ------ |
| articleCount | 数量             | integer(int64) |        |
| yearMonth    | 年月,格式yyyy-mm | string         |        |

**响应状态**:


| 状态码 | 说明         | schema                                        |
| ------ | ------------ | --------------------------------------------- |
| 200    | OK           | api响应json对象«IPage«ArticleArchivesVo对象»» |
| 401    | Unauthorized |                                               |
| 403    | Forbidden    |                                               |
| 404    | Not Found    |                                               |
## 文章分类统计

**接口描述**:按分类计数文章数

**接口地址**:`/article/category/statistic`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"articleCount": 0,
			"id": 0,
			"name": "",
			"parentId": 0
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema                  |
| -------- | -------- | -------------- | ----------------------- |
| code     | 响应码   | integer(int32) | integer(int32)          |
| data     | 响应数据 | array          | ArticleCategoriesVo对象 |
| message  | 响应信息 | string         |                         |



**schema属性说明**




**ArticleCategoriesVo对象**

| 参数名称     | 参数说明     | 类型           | schema |
| ------------ | ------------ | -------------- | ------ |
| articleCount | 分类文章数量 | integer(int32) |        |
| id           | id           | integer(int32) |        |
| name         | 名称         | string         |        |
| parentId     | 父类id       | integer(int32) |        |

**响应状态**:


| 状态码 | 说明         | schema                                         |
| ------ | ------------ | ---------------------------------------------- |
| 200    | OK           | api响应json对象«List«ArticleCategoriesVo对象»» |
| 401    | Unauthorized |                                                |
| 403    | Forbidden    |                                                |
| 404    | Not Found    |                                                |
## 已发布文章总数


**接口描述**:


**接口地址**:`/article/count`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": 0,
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | integer(int32) | integer(int32) |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema               |
| ------ | ------------ | -------------------- |
| 200    | OK           | api响应json对象«int» |
| 401    | Unauthorized |                      |
| 403    | Forbidden    |                      |
| 404    | Not Found    |                      |
## 删除文章

**接口描述**:逻辑删除，需要accessToken，需要管理员权限

**接口地址**:`/article/delete/{id}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 后台管理，获取文章详情信息

**接口描述**:需要accessToken,用于后台文章管理，比列表返回的多一个文章内容，文章分类列表

**接口地址**:`/article/detail/{id}`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"categoryId": 0,
		"categoryList": [
			{
				"id": 0,
				"name": "",
				"parentId": 0
			}
		],
		"categoryName": "",
		"collectCount": 0,
		"commentCount": 0,
		"content": "",
		"cover": "",
		"htmlContent": "",
		"id": 0,
		"likeCount": 0,
		"next": {
			"categoryId": 0,
			"categoryName": "",
			"collectCount": 0,
			"commentCount": 0,
			"content": "",
			"cover": "",
			"htmlContent": "",
			"id": 0,
			"likeCount": 0,
			"original": 0,
			"publishTime": "",
			"reproduce": "",
			"status": 0,
			"summary": "",
			"title": "",
			"updateTime": "",
			"viewCount": 0
		},
		"original": 0,
		"previous": {
			"categoryId": 0,
			"categoryName": "",
			"collectCount": 0,
			"commentCount": 0,
			"content": "",
			"cover": "",
			"htmlContent": "",
			"id": 0,
			"likeCount": 0,
			"original": 0,
			"publishTime": "",
			"reproduce": "",
			"status": 0,
			"summary": "",
			"title": "",
			"updateTime": "",
			"viewCount": 0
		},
		"publishTime": "",
		"recommendScore": 0,
		"reproduce": "",
		"status": 0,
		"summary": "",
		"tagList": [
			{
				"deleted": 0,
				"id": 0,
				"name": ""
			}
		],
		"title": "",
		"updateTime": "",
		"user": {
			"admin": 0,
			"avatar": "",
			"birthday": "",
			"brief": "",
			"createTime": "",
			"email": "",
			"gender": 0,
			"id": 0,
			"mobile": 0,
			"nickname": "",
			"status": 0,
			"username": ""
		},
		"viewCount": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | ArticleVo对象  | ArticleVo对象  |
| message  | 响应信息 | string         |                |



**schema属性说明**




**ArticleVo对象**

| 参数名称       | 参数说明                                | 类型              | schema       |
| -------------- | --------------------------------------- | ----------------- | ------------ |
| categoryId     | 文章分类id                              | integer(int32)    |              |
| categoryList   | 分类列表,顺序:root node2 node3          | array             | Category对象 |
| categoryName   | 分类名称-冗余字段                       | string            |              |
| collectCount   | 收藏数-冗余字段                         | integer(int32)    |              |
| commentCount   | 评论数-冗余字段                         | integer(int32)    |              |
| content        | 文章内容                                | string            |              |
| cover          | 文章封面                                | string            |              |
| htmlContent    | 文章富文本内容                          | string            |              |
| id             | 文章id                                  | integer(int32)    |              |
| likeCount      | 点赞数-冗余字段                         | integer(int32)    |              |
| next           | 下一篇                                  | Article对象       | Article对象  |
| original       | 是否原创，1:是，0:否                    | integer(int32)    |              |
| previous       | 上一篇                                  | Article对象       | Article对象  |
| publishTime    | 发布时间                                | string(date-time) |              |
| recommendScore | 推荐分数                                | number(double)    |              |
| reproduce      | 转载地址                                | string            |              |
| status         | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |              |
| summary        | 文章摘要                                | string            |              |
| tagList        | 标签列表                                | array             | Tag对象      |
| title          | 文章标题                                | string            |              |
| updateTime     | 更新时间                                | string(date-time) |              |
| user           | 作者                                    | User对象          | User对象     |
| viewCount      | 文章浏览次数                            | integer(int32)    |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                         |
| ------ | ------------ | ------------------------------ |
| 200    | OK           | api响应json对象«ArticleVo对象» |
| 401    | Unauthorized |                                |
| 403    | Forbidden    |                                |
| 404    | Not Found    |                                |
## 丢弃文章(回收站)

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/article/discard/{id}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 新增浏览次数

**接口描述**:20分钟内ip或用户浏览计数

**接口地址**:`/article/increment_view/{id}`


**请求方式**：`PUT`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 相关文章

**接口描述**:根据分类查询，分类为空则根据标签查询

**接口地址**:`/article/interrelated/list`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |
| limit         | 数量                      | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"categoryId": 0,
			"categoryList": [
				{
					"id": 0,
					"name": "",
					"parentId": 0
				}
			],
			"categoryName": "",
			"collectCount": 0,
			"commentCount": 0,
			"content": "",
			"cover": "",
			"htmlContent": "",
			"id": 0,
			"likeCount": 0,
			"next": {
				"categoryId": 0,
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"original": 0,
				"publishTime": "",
				"reproduce": "",
				"status": 0,
				"summary": "",
				"title": "",
				"updateTime": "",
				"viewCount": 0
			},
			"original": 0,
			"previous": {
				"categoryId": 0,
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"original": 0,
				"publishTime": "",
				"reproduce": "",
				"status": 0,
				"summary": "",
				"title": "",
				"updateTime": "",
				"viewCount": 0
			},
			"publishTime": "",
			"recommendScore": 0,
			"reproduce": "",
			"status": 0,
			"summary": "",
			"tagList": [
				{
					"deleted": 0,
					"id": 0,
					"name": ""
				}
			],
			"title": "",
			"updateTime": "",
			"user": {
				"admin": 0,
				"avatar": "",
				"birthday": "",
				"brief": "",
				"createTime": "",
				"email": "",
				"gender": 0,
				"id": 0,
				"mobile": 0,
				"nickname": "",
				"status": 0,
				"username": ""
			},
			"viewCount": 0
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | array          | ArticleVo对象  |
| message  | 响应信息 | string         |                |



**schema属性说明**




**ArticleVo对象**

| 参数名称       | 参数说明                                | 类型              | schema       |
| -------------- | --------------------------------------- | ----------------- | ------------ |
| categoryId     | 文章分类id                              | integer(int32)    |              |
| categoryList   | 分类列表,顺序:root node2 node3          | array             | Category对象 |
| categoryName   | 分类名称-冗余字段                       | string            |              |
| collectCount   | 收藏数-冗余字段                         | integer(int32)    |              |
| commentCount   | 评论数-冗余字段                         | integer(int32)    |              |
| content        | 文章内容                                | string            |              |
| cover          | 文章封面                                | string            |              |
| htmlContent    | 文章富文本内容                          | string            |              |
| id             | 文章id                                  | integer(int32)    |              |
| likeCount      | 点赞数-冗余字段                         | integer(int32)    |              |
| next           | 下一篇                                  | Article对象       | Article对象  |
| original       | 是否原创，1:是，0:否                    | integer(int32)    |              |
| previous       | 上一篇                                  | Article对象       | Article对象  |
| publishTime    | 发布时间                                | string(date-time) |              |
| recommendScore | 推荐分数                                | number(double)    |              |
| reproduce      | 转载地址                                | string            |              |
| status         | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |              |
| summary        | 文章摘要                                | string            |              |
| tagList        | 标签列表                                | array             | Tag对象      |
| title          | 文章标题                                | string            |              |
| updateTime     | 更新时间                                | string(date-time) |              |
| user           | 作者                                    | User对象          | User对象     |
| viewCount      | 文章浏览次数                            | integer(int32)    |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                               |
| ------ | ------------ | ------------------------------------ |
| 200    | OK           | api响应json对象«List«ArticleVo对象»» |
| 401    | Unauthorized |                                      |
| 403    | Forbidden    |                                      |
| 404    | Not Found    |                                      |
## 后台管理分页获取文章

**接口描述**:可以查询所有状态的文章，用于后台管理，需要accessToken，需要管理员权限

**接口地址**:`/article/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                                                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | --------------------------------------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token                                 | header | true     | string   |        |
| current       | 当前页                                                    | query  | false    | integer  |        |
| size          | 每页数量                                                  | query  | false    | integer  |        |
| status        | 文章状态,非必传，不传查全部；0:已发布，1:未发布，2:回收站 | query  | false    | integer  |        |
| categoryId    | 分类id，非必传                                            | query  | false    | integer  |        |
| tagId         | 标签id，非必传                                            | query  | false    | integer  |        |
| yearMonth     | 年月,非必传                                               | query  | false    | string   |        |
| title         | 标题关键字，可空                                          | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"categoryId": 0,
				"categoryList": [
					{
						"id": 0,
						"name": "",
						"parentId": 0
					}
				],
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"next": {
					"categoryId": 0,
					"categoryName": "",
					"collectCount": 0,
					"commentCount": 0,
					"content": "",
					"cover": "",
					"htmlContent": "",
					"id": 0,
					"likeCount": 0,
					"original": 0,
					"publishTime": "",
					"reproduce": "",
					"status": 0,
					"summary": "",
					"title": "",
					"updateTime": "",
					"viewCount": 0
				},
				"original": 0,
				"previous": {
					"categoryId": 0,
					"categoryName": "",
					"collectCount": 0,
					"commentCount": 0,
					"content": "",
					"cover": "",
					"htmlContent": "",
					"id": 0,
					"likeCount": 0,
					"original": 0,
					"publishTime": "",
					"reproduce": "",
					"status": 0,
					"summary": "",
					"title": "",
					"updateTime": "",
					"viewCount": 0
				},
				"publishTime": "",
				"recommendScore": 0,
				"reproduce": "",
				"status": 0,
				"summary": "",
				"tagList": [
					{
						"deleted": 0,
						"id": 0,
						"name": ""
					}
				],
				"title": "",
				"updateTime": "",
				"user": {
					"admin": 0,
					"avatar": "",
					"birthday": "",
					"brief": "",
					"createTime": "",
					"email": "",
					"gender": 0,
					"id": 0,
					"mobile": 0,
					"nickname": "",
					"status": 0,
					"username": ""
				},
				"viewCount": 0
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                 | schema               |
| -------- | -------- | -------------------- | -------------------- |
| code     | 响应码   | integer(int32)       | integer(int32)       |
| data     | 响应数据 | IPage«ArticleVo对象» | IPage«ArticleVo对象» |
| message  | 响应信息 | string               |                      |



**schema属性说明**




**IPage«ArticleVo对象»**

| 参数名称    | 参数说明 | 类型           | schema        |
| ----------- | -------- | -------------- | ------------- |
| current     |          | integer(int64) |               |
| pages       |          | integer(int64) |               |
| records     |          | array          | ArticleVo对象 |
| searchCount |          | boolean        |               |
| size        |          | integer(int64) |               |
| total       |          | integer(int64) |               |

**ArticleVo对象**

| 参数名称       | 参数说明                                | 类型              | schema       |
| -------------- | --------------------------------------- | ----------------- | ------------ |
| categoryId     | 文章分类id                              | integer(int32)    |              |
| categoryList   | 分类列表,顺序:root node2 node3          | array             | Category对象 |
| categoryName   | 分类名称-冗余字段                       | string            |              |
| collectCount   | 收藏数-冗余字段                         | integer(int32)    |              |
| commentCount   | 评论数-冗余字段                         | integer(int32)    |              |
| content        | 文章内容                                | string            |              |
| cover          | 文章封面                                | string            |              |
| htmlContent    | 文章富文本内容                          | string            |              |
| id             | 文章id                                  | integer(int32)    |              |
| likeCount      | 点赞数-冗余字段                         | integer(int32)    |              |
| next           | 下一篇                                  | Article对象       | Article对象  |
| original       | 是否原创，1:是，0:否                    | integer(int32)    |              |
| previous       | 上一篇                                  | Article对象       | Article对象  |
| publishTime    | 发布时间                                | string(date-time) |              |
| recommendScore | 推荐分数                                | number(double)    |              |
| reproduce      | 转载地址                                | string            |              |
| status         | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |              |
| summary        | 文章摘要                                | string            |              |
| tagList        | 标签列表                                | array             | Tag对象      |
| title          | 文章标题                                | string            |              |
| updateTime     | 更新时间                                | string(date-time) |              |
| user           | 作者                                    | User对象          | User对象     |
| viewCount      | 文章浏览次数                            | integer(int32)    |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                                |
| ------ | ------------ | ------------------------------------- |
| 200    | OK           | api响应json对象«IPage«ArticleVo对象»» |
| 401    | Unauthorized |                                       |
| 403    | Forbidden    |                                       |
| 404    | Not Found    |                                       |
## 分页获取文章(已发布)

**接口描述**:用于前台页面展示,默认按发布时间倒序排序

**接口地址**:`/article/published/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                                                     | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------------------------------------------ | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token                                    | header | true     | string   |        |
| current       | 当前页，默认值：1                                            | query  | false    | integer  |        |
| size          | 每页数量，默认值为：5                                        | query  | false    | integer  |        |
| categoryId    | 分类id，非必传                                               | query  | false    | integer  |        |
| tagId         | 标签id，非必传                                               | query  | false    | integer  |        |
| yearMonth     | 年月,非必传,格式:yyyy-mm                                     | query  | false    | string   |        |
| title         | 标题关键字，非必传                                           | query  | false    | string   |        |
| orderBy       | 排序字段，倒序，非必传，默认:publish_time;可选项：发布时间:publish_time、热度:hot | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"categoryId": 0,
				"categoryList": [
					{
						"id": 0,
						"name": "",
						"parentId": 0
					}
				],
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"next": {
					"categoryId": 0,
					"categoryName": "",
					"collectCount": 0,
					"commentCount": 0,
					"content": "",
					"cover": "",
					"htmlContent": "",
					"id": 0,
					"likeCount": 0,
					"original": 0,
					"publishTime": "",
					"reproduce": "",
					"status": 0,
					"summary": "",
					"title": "",
					"updateTime": "",
					"viewCount": 0
				},
				"original": 0,
				"previous": {
					"categoryId": 0,
					"categoryName": "",
					"collectCount": 0,
					"commentCount": 0,
					"content": "",
					"cover": "",
					"htmlContent": "",
					"id": 0,
					"likeCount": 0,
					"original": 0,
					"publishTime": "",
					"reproduce": "",
					"status": 0,
					"summary": "",
					"title": "",
					"updateTime": "",
					"viewCount": 0
				},
				"publishTime": "",
				"recommendScore": 0,
				"reproduce": "",
				"status": 0,
				"summary": "",
				"tagList": [
					{
						"deleted": 0,
						"id": 0,
						"name": ""
					}
				],
				"title": "",
				"updateTime": "",
				"user": {
					"admin": 0,
					"avatar": "",
					"birthday": "",
					"brief": "",
					"createTime": "",
					"email": "",
					"gender": 0,
					"id": 0,
					"mobile": 0,
					"nickname": "",
					"status": 0,
					"username": ""
				},
				"viewCount": 0
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                 | schema               |
| -------- | -------- | -------------------- | -------------------- |
| code     | 响应码   | integer(int32)       | integer(int32)       |
| data     | 响应数据 | IPage«ArticleVo对象» | IPage«ArticleVo对象» |
| message  | 响应信息 | string               |                      |



**schema属性说明**




**IPage«ArticleVo对象»**

| 参数名称    | 参数说明 | 类型           | schema        |
| ----------- | -------- | -------------- | ------------- |
| current     |          | integer(int64) |               |
| pages       |          | integer(int64) |               |
| records     |          | array          | ArticleVo对象 |
| searchCount |          | boolean        |               |
| size        |          | integer(int64) |               |
| total       |          | integer(int64) |               |

**ArticleVo对象**

| 参数名称       | 参数说明                                | 类型              | schema       |
| -------------- | --------------------------------------- | ----------------- | ------------ |
| categoryId     | 文章分类id                              | integer(int32)    |              |
| categoryList   | 分类列表,顺序:root node2 node3          | array             | Category对象 |
| categoryName   | 分类名称-冗余字段                       | string            |              |
| collectCount   | 收藏数-冗余字段                         | integer(int32)    |              |
| commentCount   | 评论数-冗余字段                         | integer(int32)    |              |
| content        | 文章内容                                | string            |              |
| cover          | 文章封面                                | string            |              |
| htmlContent    | 文章富文本内容                          | string            |              |
| id             | 文章id                                  | integer(int32)    |              |
| likeCount      | 点赞数-冗余字段                         | integer(int32)    |              |
| next           | 下一篇                                  | Article对象       | Article对象  |
| original       | 是否原创，1:是，0:否                    | integer(int32)    |              |
| previous       | 上一篇                                  | Article对象       | Article对象  |
| publishTime    | 发布时间                                | string(date-time) |              |
| recommendScore | 推荐分数                                | number(double)    |              |
| reproduce      | 转载地址                                | string            |              |
| status         | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |              |
| summary        | 文章摘要                                | string            |              |
| tagList        | 标签列表                                | array             | Tag对象      |
| title          | 文章标题                                | string            |              |
| updateTime     | 更新时间                                | string(date-time) |              |
| user           | 作者                                    | User对象          | User对象     |
| viewCount      | 文章浏览次数                            | integer(int32)    |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                                |
| ------ | ------------ | ------------------------------------- |
| 200    | OK           | api响应json对象«IPage«ArticleVo对象»» |
| 401    | Unauthorized |                                       |
| 403    | Forbidden    |                                       |
| 404    | Not Found    |                                       |
## 从推荐列表中删除

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/article/recommend/delete/{articleId}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 获取文章推荐列表

**接口描述**:按分数排序

**接口地址**:`/article/recommend/list`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"categoryId": 0,
			"categoryList": [
				{
					"id": 0,
					"name": "",
					"parentId": 0
				}
			],
			"categoryName": "",
			"collectCount": 0,
			"commentCount": 0,
			"content": "",
			"cover": "",
			"htmlContent": "",
			"id": 0,
			"likeCount": 0,
			"next": {
				"categoryId": 0,
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"original": 0,
				"publishTime": "",
				"reproduce": "",
				"status": 0,
				"summary": "",
				"title": "",
				"updateTime": "",
				"viewCount": 0
			},
			"original": 0,
			"previous": {
				"categoryId": 0,
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"original": 0,
				"publishTime": "",
				"reproduce": "",
				"status": 0,
				"summary": "",
				"title": "",
				"updateTime": "",
				"viewCount": 0
			},
			"publishTime": "",
			"recommendScore": 0,
			"reproduce": "",
			"status": 0,
			"summary": "",
			"tagList": [
				{
					"deleted": 0,
					"id": 0,
					"name": ""
				}
			],
			"title": "",
			"updateTime": "",
			"user": {
				"admin": 0,
				"avatar": "",
				"birthday": "",
				"brief": "",
				"createTime": "",
				"email": "",
				"gender": 0,
				"id": 0,
				"mobile": 0,
				"nickname": "",
				"status": 0,
				"username": ""
			},
			"viewCount": 0
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | array          | ArticleVo对象  |
| message  | 响应信息 | string         |                |



**schema属性说明**




**ArticleVo对象**

| 参数名称       | 参数说明                                | 类型              | schema       |
| -------------- | --------------------------------------- | ----------------- | ------------ |
| categoryId     | 文章分类id                              | integer(int32)    |              |
| categoryList   | 分类列表,顺序:root node2 node3          | array             | Category对象 |
| categoryName   | 分类名称-冗余字段                       | string            |              |
| collectCount   | 收藏数-冗余字段                         | integer(int32)    |              |
| commentCount   | 评论数-冗余字段                         | integer(int32)    |              |
| content        | 文章内容                                | string            |              |
| cover          | 文章封面                                | string            |              |
| htmlContent    | 文章富文本内容                          | string            |              |
| id             | 文章id                                  | integer(int32)    |              |
| likeCount      | 点赞数-冗余字段                         | integer(int32)    |              |
| next           | 下一篇                                  | Article对象       | Article对象  |
| original       | 是否原创，1:是，0:否                    | integer(int32)    |              |
| previous       | 上一篇                                  | Article对象       | Article对象  |
| publishTime    | 发布时间                                | string(date-time) |              |
| recommendScore | 推荐分数                                | number(double)    |              |
| reproduce      | 转载地址                                | string            |              |
| status         | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |              |
| summary        | 文章摘要                                | string            |              |
| tagList        | 标签列表                                | array             | Tag对象      |
| title          | 文章标题                                | string            |              |
| updateTime     | 更新时间                                | string(date-time) |              |
| user           | 作者                                    | User对象          | User对象     |
| viewCount      | 文章浏览次数                            | integer(int32)    |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                               |
| ------ | ------------ | ------------------------------------ |
| 200    | OK           | api响应json对象«List«ArticleVo对象»» |
| 401    | Unauthorized |                                      |
| 403    | Forbidden    |                                      |
| 404    | Not Found    |                                      |
## 添加到推荐，如果已存在则更新

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/article/recommend/save`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |
| score         | 分数，分数越高越排前面    | query  | false    | number   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 保存文章

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/article/save`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
	"categoryId": 0,
	"content": "",
	"cover": "",
	"htmlContent": "",
	"id": 0,
	"original": 0,
	"reproduce": "",
	"status": 0,
	"summary": "",
	"tagIds": [],
	"title": ""
}
```


**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型     | schema       |
| ------------- | ------------------------- | ------ | -------- | ------------ | ------------ |
| Authorization | 格式：Bearer access_token | header | true     | string       |              |
| request       | 文章请求体                | body   | true     | 文章请求json | 文章请求json |

**schema属性说明**



**文章请求json**

| 参数名称    | 参数说明             | in   | 是否必须 | 数据类型       | schema |
| ----------- | -------------------- | ---- | -------- | -------------- | ------ |
| categoryId  | 文章分类id           | body | false    | integer(int32) |        |
| content     | 文章内容             | body | false    | string         |        |
| cover       | 文章封面             | body | false    | string         |        |
| htmlContent | 文章内容             | body | false    | string         |        |
| id          | 文章id，编辑时不可空 | body | false    | integer(int32) |        |
| original    | 是否原创，1:是，0:否 | body | false    | integer(int32) |        |
| reproduce   | 转载地址，转载非空   | body | false    | string         |        |
| status      | 状态，0:发布，1:保存 | body | false    | integer(int32) |        |
| summary     | 文章摘要             | body | false    | string         |        |
| tagIds      | 文章标签id列表       | body | false    | array          |        |
| title       | 文章标题             | body | false    | string         |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 修改文章发布或保存状态

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/article/status/update`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                                | in     | 是否必须 | 数据类型 | schema |
| ------------- | --------------------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token               | header | true     | string   |        |
| articleId     | 文章id                                  | query  | false    | integer  |        |
| status        | 文章状态，0为正常，1为待发布，2为回收站 | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 文章标签统计

**接口描述**:按标签计数文章数

**接口地址**:`/article/tag/statistic`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"articleCount": 0,
			"deleted": 0,
			"id": 0,
			"name": ""
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema                     |
| -------- | -------- | -------------- | -------------------------- |
| code     | 响应码   | integer(int32) | integer(int32)             |
| data     | 响应数据 | array          | ArticleTagStatisticsVo对象 |
| message  | 响应信息 | string         |                            |



**schema属性说明**




**ArticleTagStatisticsVo对象**

| 参数名称     | 参数说明              | 类型           | schema |
| ------------ | --------------------- | -------------- | ------ |
| articleCount | 分类文章数量          | integer(int32) |        |
| deleted      | 是否已删除,1:是，0:否 | integer(int32) |        |
| id           | id                    | integer(int32) |        |
| name         | 标签名                | string         |        |

**响应状态**:


| 状态码 | 说明         | schema                                            |
| ------ | ------------ | ------------------------------------------------- |
| 200    | OK           | api响应json对象«List«ArticleTagStatisticsVo对象»» |
| 401    | Unauthorized |                                                   |
| 403    | Forbidden    |                                                   |
| 404    | Not Found    |                                                   |
## 获取文章详情信息

**接口描述**:比列表返回的多一个文章内容，文章分类列表

**接口地址**:`/article/view/{id}`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"categoryId": 0,
		"categoryList": [
			{
				"id": 0,
				"name": "",
				"parentId": 0
			}
		],
		"categoryName": "",
		"collectCount": 0,
		"commentCount": 0,
		"content": "",
		"cover": "",
		"htmlContent": "",
		"id": 0,
		"likeCount": 0,
		"next": {
			"categoryId": 0,
			"categoryName": "",
			"collectCount": 0,
			"commentCount": 0,
			"content": "",
			"cover": "",
			"htmlContent": "",
			"id": 0,
			"likeCount": 0,
			"original": 0,
			"publishTime": "",
			"reproduce": "",
			"status": 0,
			"summary": "",
			"title": "",
			"updateTime": "",
			"viewCount": 0
		},
		"original": 0,
		"previous": {
			"categoryId": 0,
			"categoryName": "",
			"collectCount": 0,
			"commentCount": 0,
			"content": "",
			"cover": "",
			"htmlContent": "",
			"id": 0,
			"likeCount": 0,
			"original": 0,
			"publishTime": "",
			"reproduce": "",
			"status": 0,
			"summary": "",
			"title": "",
			"updateTime": "",
			"viewCount": 0
		},
		"publishTime": "",
		"recommendScore": 0,
		"reproduce": "",
		"status": 0,
		"summary": "",
		"tagList": [
			{
				"deleted": 0,
				"id": 0,
				"name": ""
			}
		],
		"title": "",
		"updateTime": "",
		"user": {
			"admin": 0,
			"avatar": "",
			"birthday": "",
			"brief": "",
			"createTime": "",
			"email": "",
			"gender": 0,
			"id": 0,
			"mobile": 0,
			"nickname": "",
			"status": 0,
			"username": ""
		},
		"viewCount": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | ArticleVo对象  | ArticleVo对象  |
| message  | 响应信息 | string         |                |



**schema属性说明**




**ArticleVo对象**

| 参数名称       | 参数说明                                | 类型              | schema       |
| -------------- | --------------------------------------- | ----------------- | ------------ |
| categoryId     | 文章分类id                              | integer(int32)    |              |
| categoryList   | 分类列表,顺序:root node2 node3          | array             | Category对象 |
| categoryName   | 分类名称-冗余字段                       | string            |              |
| collectCount   | 收藏数-冗余字段                         | integer(int32)    |              |
| commentCount   | 评论数-冗余字段                         | integer(int32)    |              |
| content        | 文章内容                                | string            |              |
| cover          | 文章封面                                | string            |              |
| htmlContent    | 文章富文本内容                          | string            |              |
| id             | 文章id                                  | integer(int32)    |              |
| likeCount      | 点赞数-冗余字段                         | integer(int32)    |              |
| next           | 下一篇                                  | Article对象       | Article对象  |
| original       | 是否原创，1:是，0:否                    | integer(int32)    |              |
| previous       | 上一篇                                  | Article对象       | Article对象  |
| publishTime    | 发布时间                                | string(date-time) |              |
| recommendScore | 推荐分数                                | number(double)    |              |
| reproduce      | 转载地址                                | string            |              |
| status         | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |              |
| summary        | 文章摘要                                | string            |              |
| tagList        | 标签列表                                | array             | Tag对象      |
| title          | 文章标题                                | string            |              |
| updateTime     | 更新时间                                | string(date-time) |              |
| user           | 作者                                    | User对象          | User对象     |
| viewCount      | 文章浏览次数                            | integer(int32)    |              |

**Category对象**

| 参数名称 | 参数说明 | 类型           | schema |
| -------- | -------- | -------------- | ------ |
| id       | id       | integer(int32) |        |
| name     | 名称     | string         |        |
| parentId | 父类id   | integer(int32) |        |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                         |
| ------ | ------------ | ------------------------------ |
| 200    | OK           | api响应json对象«ArticleVo对象» |
| 401    | Unauthorized |                                |
| 403    | Forbidden    |                                |
| 404    | Not Found    |                                |
# 文章点赞服务

## 文章点赞


**接口描述**:


**接口地址**:`/article/like/add`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 取消文章点赞


**接口描述**:


**接口地址**:`/article/like/cancel`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 查询文章是否已点赞

**接口描述**:1：是，0：否

**接口地址**:`/article/like/liked/{articleId}`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": 0,
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | integer(int32) | integer(int32) |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema               |
| ------ | ------------ | -------------------- |
| 200    | OK           | api响应json对象«int» |
| 401    | Unauthorized |                      |
| 403    | Forbidden    |                      |
| 404    | Not Found    |                      |
# 文章评论回复服务

## 新增文章评论回复

**接口描述**:需要accessToken

**接口地址**:`/article/reply/add`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |
| commentId     | 评论id                    | query  | false    | integer  |        |
| toUserId      | 被回复者id                | query  | false    | integer  |        |
| content       | 回复内容                  | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 删除回复

**接口描述**:逻辑删除，需要accessToken,管理员或回复者可删除

**接口地址**:`/article/reply/delete`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| replyId       | 回复id                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
# 文章评论服务

## 新增文章评论

**接口描述**:需要accessToken

**接口地址**:`/article/comment/add`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| articleId     | 文章id                    | query  | false    | integer  |        |
| content       | 评论内容                  | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 删除文章评论

**接口描述**:逻辑删除，需要accessToken,管理员或评论发表者可删除

**接口地址**:`/article/comment/delete`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| commentId     | 评论id                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 最新文章评论列表

**接口描述**:包括文章信息和评论者信息

**接口地址**:`/article/comment/latest`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| limit         | 数量限制,默认值:5         | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"article": {
				"categoryId": 0,
				"categoryName": "",
				"collectCount": 0,
				"commentCount": 0,
				"content": "",
				"cover": "",
				"htmlContent": "",
				"id": 0,
				"likeCount": 0,
				"original": 0,
				"publishTime": "",
				"reproduce": "",
				"status": 0,
				"summary": "",
				"title": "",
				"updateTime": "",
				"viewCount": 0
			},
			"commentTime": "",
			"content": "",
			"fromUser": {
				"admin": 0,
				"avatar": "",
				"birthday": "",
				"brief": "",
				"createTime": "",
				"email": "",
				"gender": 0,
				"id": 0,
				"mobile": 0,
				"nickname": "",
				"status": 0,
				"username": ""
			},
			"id": 0,
			"replyList": [
				{
					"content": "",
					"fromUser": {
						"admin": 0,
						"avatar": "",
						"birthday": "",
						"brief": "",
						"createTime": "",
						"email": "",
						"gender": 0,
						"id": 0,
						"mobile": 0,
						"nickname": "",
						"status": 0,
						"username": ""
					},
					"id": 0,
					"replyTime": "",
					"toUser": {
						"admin": 0,
						"avatar": "",
						"birthday": "",
						"brief": "",
						"createTime": "",
						"email": "",
						"gender": 0,
						"id": 0,
						"mobile": 0,
						"nickname": "",
						"status": 0,
						"username": ""
					}
				}
			]
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema           |
| -------- | -------- | -------------- | ---------------- |
| code     | 响应码   | integer(int32) | integer(int32)   |
| data     | 响应数据 | array          | ArticleCommentVo |
| message  | 响应信息 | string         |                  |



**schema属性说明**




**ArticleCommentVo**

| 参数名称    | 参数说明     | 类型              | schema         |
| ----------- | ------------ | ----------------- | -------------- |
| article     | 文章         | Article对象       | Article对象    |
| commentTime | 评论时间     | string(date-time) |                |
| content     | 评论内容     | string            |                |
| fromUser    | 评论者id     | User对象          | User对象       |
| id          | id           | integer(int32)    |                |
| replyList   | 评论回复列表 | array             | ArticleReplyVo |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**ArticleReplyVo**

| 参数名称  | 参数说明 | 类型              | schema   |
| --------- | -------- | ----------------- | -------- |
| content   | 回复内容 | string            |          |
| fromUser  | 评论者   | User对象          | User对象 |
| id        | id       | integer(int32)    |          |
| replyTime | 回复时间 | string(date-time) |          |
| toUser    | 被评论者 | User对象          | User对象 |

**响应状态**:


| 状态码 | 说明         | schema                                  |
| ------ | ------------ | --------------------------------------- |
| 200    | OK           | api响应json对象«List«ArticleCommentVo»» |
| 401    | Unauthorized |                                         |
| 403    | Forbidden    |                                         |
| 404    | Not Found    |                                         |
## 分页获取文章评论及回复列表

**接口描述**:包括评论者和回复者信息

**接口地址**:`/article/comment/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 页码                      | query  | false    | integer  |        |
| size          | 每页数量                  | query  | false    | integer  |        |
| articleId     | 文章id                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"article": {
					"categoryId": 0,
					"categoryName": "",
					"collectCount": 0,
					"commentCount": 0,
					"content": "",
					"cover": "",
					"htmlContent": "",
					"id": 0,
					"likeCount": 0,
					"original": 0,
					"publishTime": "",
					"reproduce": "",
					"status": 0,
					"summary": "",
					"title": "",
					"updateTime": "",
					"viewCount": 0
				},
				"commentTime": "",
				"content": "",
				"fromUser": {
					"admin": 0,
					"avatar": "",
					"birthday": "",
					"brief": "",
					"createTime": "",
					"email": "",
					"gender": 0,
					"id": 0,
					"mobile": 0,
					"nickname": "",
					"status": 0,
					"username": ""
				},
				"id": 0,
				"replyList": [
					{
						"content": "",
						"fromUser": {
							"admin": 0,
							"avatar": "",
							"birthday": "",
							"brief": "",
							"createTime": "",
							"email": "",
							"gender": 0,
							"id": 0,
							"mobile": 0,
							"nickname": "",
							"status": 0,
							"username": ""
						},
						"id": 0,
						"replyTime": "",
						"toUser": {
							"admin": 0,
							"avatar": "",
							"birthday": "",
							"brief": "",
							"createTime": "",
							"email": "",
							"gender": 0,
							"id": 0,
							"mobile": 0,
							"nickname": "",
							"status": 0,
							"username": ""
						}
					}
				]
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                    | schema                  |
| -------- | -------- | ----------------------- | ----------------------- |
| code     | 响应码   | integer(int32)          | integer(int32)          |
| data     | 响应数据 | IPage«ArticleCommentVo» | IPage«ArticleCommentVo» |
| message  | 响应信息 | string                  |                         |



**schema属性说明**




**IPage«ArticleCommentVo»**

| 参数名称    | 参数说明 | 类型           | schema           |
| ----------- | -------- | -------------- | ---------------- |
| current     |          | integer(int64) |                  |
| pages       |          | integer(int64) |                  |
| records     |          | array          | ArticleCommentVo |
| searchCount |          | boolean        |                  |
| size        |          | integer(int64) |                  |
| total       |          | integer(int64) |                  |

**ArticleCommentVo**

| 参数名称    | 参数说明     | 类型              | schema         |
| ----------- | ------------ | ----------------- | -------------- |
| article     | 文章         | Article对象       | Article对象    |
| commentTime | 评论时间     | string(date-time) |                |
| content     | 评论内容     | string            |                |
| fromUser    | 评论者id     | User对象          | User对象       |
| id          | id           | integer(int32)    |                |
| replyList   | 评论回复列表 | array             | ArticleReplyVo |

**Article对象**

| 参数名称     | 参数说明                                | 类型              | schema |
| ------------ | --------------------------------------- | ----------------- | ------ |
| categoryId   | 文章分类id                              | integer(int32)    |        |
| categoryName | 分类名称-冗余字段                       | string            |        |
| collectCount | 收藏数-冗余字段                         | integer(int32)    |        |
| commentCount | 评论数-冗余字段                         | integer(int32)    |        |
| content      | 文章内容                                | string            |        |
| cover        | 文章封面                                | string            |        |
| htmlContent  | 文章富文本内容                          | string            |        |
| id           | 文章id                                  | integer(int32)    |        |
| likeCount    | 点赞数-冗余字段                         | integer(int32)    |        |
| original     | 是否原创，1:是，0:否                    | integer(int32)    |        |
| publishTime  | 发布时间                                | string(date-time) |        |
| reproduce    | 转载地址                                | string            |        |
| status       | 文章状态：0为正常，1为待发布，2为回收站 | integer(int32)    |        |
| summary      | 文章摘要                                | string            |        |
| title        | 文章标题                                | string            |        |
| updateTime   | 更新时间                                | string(date-time) |        |
| viewCount    | 文章浏览次数                            | integer(int32)    |        |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**ArticleReplyVo**

| 参数名称  | 参数说明 | 类型              | schema   |
| --------- | -------- | ----------------- | -------- |
| content   | 回复内容 | string            |          |
| fromUser  | 评论者   | User对象          | User对象 |
| id        | id       | integer(int32)    |          |
| replyTime | 回复时间 | string(date-time) |          |
| toUser    | 被评论者 | User对象          | User对象 |

**响应状态**:


| 状态码 | 说明         | schema                                   |
| ------ | ------------ | ---------------------------------------- |
| 200    | OK           | api响应json对象«IPage«ArticleCommentVo»» |
| 401    | Unauthorized |                                          |
| 403    | Forbidden    |                                          |
| 404    | Not Found    |                                          |
# 标签服务

## 添加标签

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/tag/add`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| tagName       | tagName                   | query  | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 删除标签

**接口描述**:需要accessToken,需要管理员权限，逻辑删除

**接口地址**:`/tag/delete/{id}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 标签id                    | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 获取标签列表

**接口描述**:不需要accessToken

**接口地址**:`/tag/list`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| tagName       | 标签名关键字，可空        | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"deleted": 0,
			"id": 0,
			"name": ""
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | array          | Tag对象        |
| message  | 响应信息 | string         |                |



**schema属性说明**




**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**响应状态**:


| 状态码 | 说明         | schema                         |
| ------ | ------------ | ------------------------------ |
| 200    | OK           | api响应json对象«List«Tag对象»» |
| 401    | Unauthorized |                                |
| 403    | Forbidden    |                                |
| 404    | Not Found    |                                |
## 分页查询标签

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/tag/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 当前页                    | query  | false    | integer  |        |
| size          | 每页数量                  | query  | false    | integer  |        |
| tagName       | 标签名关键字，可空        | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"deleted": 0,
				"id": 0,
				"name": ""
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | IPage«Tag对象» | IPage«Tag对象» |
| message  | 响应信息 | string         |                |



**schema属性说明**




**IPage«Tag对象»**

| 参数名称    | 参数说明 | 类型           | schema  |
| ----------- | -------- | -------------- | ------- |
| current     |          | integer(int64) |         |
| pages       |          | integer(int64) |         |
| records     |          | array          | Tag对象 |
| searchCount |          | boolean        |         |
| size        |          | integer(int64) |         |
| total       |          | integer(int64) |         |

**Tag对象**

| 参数名称 | 参数说明              | 类型           | schema |
| -------- | --------------------- | -------------- | ------ |
| deleted  | 是否已删除,1:是，0:否 | integer(int32) |        |
| id       | id                    | integer(int32) |        |
| name     | 标签名                | string         |        |

**响应状态**:


| 状态码 | 说明         | schema                          |
| ------ | ------------ | ------------------------------- |
| 200    | OK           | api响应json对象«IPage«Tag对象»» |
| 401    | Unauthorized |                                 |
| 403    | Forbidden    |                                 |
| 404    | Not Found    |                                 |
## 修改标签名

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/tag/update`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | 标签id                    | query  | false    | integer  |        |
| name          | 标签名                    | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
# 用户服务

## 更新用户头像

**接口描述**:文件只限bmp,gif,jpeg,jpeg,png,webp格式

**接口地址**:`/user/avatar/update`


**请求方式**：`POST`


**consumes**:`["multipart/form-data"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in       | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | -------- | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header   | true     | string   |        |
| file          | 头像图片文件              | formData | false    | file     |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## code绑定邮箱

**接口描述**:不需要accessToken，code有效2小时

**接口地址**:`/user/email/bind`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| code          | 邮箱链接中的code          | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 发送验证链接到邮箱

**接口描述**:需要accessToken

**接口地址**:`/user/email/validate`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| email         | 邮箱                      | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 获取用户信息

**接口描述**:需要传accessToken

**接口地址**:`/user/info`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema                  |
| ------ | ------------ | ----------------------- |
| 200    | OK           | api响应json对象«object» |
| 401    | Unauthorized |                         |
| 403    | Forbidden    |                         |
| 404    | Not Found    |                         |
## 绑定手机号

**接口描述**:需要传accessToken，只用于原手机为空的情况下

**接口地址**:`/user/mobile/bind`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| mobile        | 手机号                    | query  | false    | integer  |        |
| code          | 验证码                    | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 更换手机号步骤二，绑定新手机号

**接口描述**:需要传accessToken

**接口地址**:`/user/mobile/rebind`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| mobile        | 手机号                    | query  | false    | integer  |        |
| code          | 验证码                    | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 更换手机号步骤一，验证原手机号

**接口描述**:需要传accessToken

**接口地址**:`/user/mobile/validate`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| mobile        | 手机号                    | query  | false    | integer  |        |
| code          | code                      | query  | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 分页获取用户信息，用于后台管理

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/user/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 页码                      | query  | false    | integer  |        |
| size          | 每页数量                  | query  | false    | integer  |        |
| username      | 用户名                    | query  | false    | string   |        |
| nickname      | 昵称                      | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"admin": 0,
				"avatar": "",
				"birthday": "",
				"brief": "",
				"createTime": "",
				"email": "",
				"gender": 0,
				"id": 0,
				"mobile": 0,
				"nickname": "",
				"status": 0,
				"username": ""
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型            | schema          |
| -------- | -------- | --------------- | --------------- |
| code     | 响应码   | integer(int32)  | integer(int32)  |
| data     | 响应数据 | IPage«User对象» | IPage«User对象» |
| message  | 响应信息 | string          |                 |



**schema属性说明**




**IPage«User对象»**

| 参数名称    | 参数说明 | 类型           | schema   |
| ----------- | -------- | -------------- | -------- |
| current     |          | integer(int64) |          |
| pages       |          | integer(int64) |          |
| records     |          | array          | User对象 |
| searchCount |          | boolean        |          |
| size        |          | integer(int64) |          |
| total       |          | integer(int64) |          |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**响应状态**:


| 状态码 | 说明         | schema                           |
| ------ | ------------ | -------------------------------- |
| 200    | OK           | api响应json对象«IPage«User对象»» |
| 401    | Unauthorized |                                  |
| 403    | Forbidden    |                                  |
| 404    | Not Found    |                                  |
## 重置密码

**接口描述**:不需要传accessToken,需要验证手机号

**接口地址**:`/user/password/reset`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| mobile        | 手机号                    | query  | false    | integer  |        |
| code          | 验证码                    | query  | false    | string   |        |
| password      | 密码                      | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 修改密码

**接口描述**:需要传accessToken,密码至少6位数

**接口地址**:`/user/password/update`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| oldPassword   | 原密码                    | query  | false    | string   |        |
| newPassword   | 新密码                    | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 用户注册

**接口描述**:不需要传accessToken

**接口地址**:`/user/register`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
	"code": "",
	"mobile": 0,
	"password": "",
	"username": ""
}
```


**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型       | schema         |
| ------------- | ------------------------- | ------ | -------- | -------------- | -------------- |
| Authorization | 格式：Bearer access_token | header | true     | string         |                |
| request       | 用户注册                  | body   | true     | 用户注册请json | 用户注册请json |

**schema属性说明**



**用户注册请json**

| 参数名称 | 参数说明                                             | in   | 是否必须 | 数据类型       | schema |
| -------- | ---------------------------------------------------- | ---- | -------- | -------------- | ------ |
| code     | 验证码                                               | body | false    | string         |        |
| mobile   | 手机号                                               | body | false    | integer(int64) |        |
| password | 密码                                                 | body | false    | string         |        |
| username | 用户名只能字母开头，允许2-16字节，允许字母数字下划线 | body | false    | string         |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 修改用户状态,用于禁用、锁定用户等操作

**接口描述**:需要accessToken，需要管理员权限

**接口地址**:`/user/status/update`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                            | in     | 是否必须 | 数据类型 | schema |
| ------------- | ----------------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token           | header | true     | string   |        |
| userId        | 用户id                              | query  | false    | integer  |        |
| status        | 状态,0:正常，1:锁定，2:禁用，3:过期 | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 更新用户基本信息

**接口描述**:需要传accessToken，请求的json中id字段必传，更新不为null的项

**接口地址**:`/user/update`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
	"birthday": "",
	"brief": "",
	"gender": 0,
	"nickname": "",
	"userId": 0
}
```


**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型     | schema       |
| ------------- | ------------------------- | ------ | -------- | ------------ | ------------ |
| Authorization | 格式：Bearer access_token | header | true     | string       |              |
| request       | 用户更新                  | body   | true     | 用户更新json | 用户更新json |

**schema属性说明**



**用户更新json**

| 参数名称 | 参数说明                    | in       | 是否必须 | 数据类型       | schema |
| -------- | --------------------------- | -------- | -------- | -------------- | ------ |
| birthday | 生日                        | body     | false    | string(date)   |        |
| brief    | 简介                        | 个性签名 | body     | false          | string |
| gender   | 性别，1：男，0：女，默认为1 | body     | false    | integer(int32) |        |
| nickname | 昵称                        | body     | false    | string         |        |
| userId   | 用户id                      | body     | false    | integer(int32) |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 绑定用户名

**接口描述**:需要传accessToken，只用于原用户名为空的情况下

**接口地址**:`/user/username/bind`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| username      | 用户名                    | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
# 留言服务

## 新增留言

**接口描述**:需要accessToken

**接口地址**:`/leave/message/add`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| content       | 留言内容                  | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
## 删除留言或留言回复

**接口描述**:需要accessToken，本人和管理员可删除

**接口地址**:`/leave/message/delete/{id}`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| id            | id                        | path   | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 最新留言列表

**接口描述**:包括留言者

**接口地址**:`/leave/message/latest`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| limit         | 数量限制,默认值:5         | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": [
		{
			"content": "",
			"createTime": "",
			"fromUser": {
				"admin": 0,
				"avatar": "",
				"birthday": "",
				"brief": "",
				"createTime": "",
				"email": "",
				"gender": 0,
				"id": 0,
				"mobile": 0,
				"nickname": "",
				"status": 0,
				"username": ""
			},
			"id": 0,
			"replyList": [
				{
					"content": "",
					"createTime": "",
					"fromUser": {
						"admin": 0,
						"avatar": "",
						"birthday": "",
						"brief": "",
						"createTime": "",
						"email": "",
						"gender": 0,
						"id": 0,
						"mobile": 0,
						"nickname": "",
						"status": 0,
						"username": ""
					},
					"id": 0,
					"toUser": {
						"admin": 0,
						"avatar": "",
						"birthday": "",
						"brief": "",
						"createTime": "",
						"email": "",
						"gender": 0,
						"id": 0,
						"mobile": 0,
						"nickname": "",
						"status": 0,
						"username": ""
					}
				}
			]
		}
	],
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema             |
| -------- | -------- | -------------- | ------------------ |
| code     | 响应码   | integer(int32) | integer(int32)     |
| data     | 响应数据 | array          | LeaveMessageVo对象 |
| message  | 响应信息 | string         |                    |



**schema属性说明**




**LeaveMessageVo对象**

| 参数名称   | 参数说明 | 类型              | schema                  |
| ---------- | -------- | ----------------- | ----------------------- |
| content    | 内容     | string            |                         |
| createTime | 时间     | string(date-time) |                         |
| fromUser   | 留言者   | User对象          | User对象                |
| id         | id       | integer(int32)    |                         |
| replyList  | 回复列表 | array             | LeaveMessageReplyVo对象 |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**LeaveMessageReplyVo对象**

| 参数名称   | 参数说明 | 类型              | schema   |
| ---------- | -------- | ----------------- | -------- |
| content    | 内容     | string            |          |
| createTime | 时间     | string(date-time) |          |
| fromUser   | 回复者   | User对象          | User对象 |
| id         | id       | integer(int32)    |          |
| toUser     | 被回复者 | User对象          | User对象 |

**响应状态**:


| 状态码 | 说明         | schema                                    |
| ------ | ------------ | ----------------------------------------- |
| 200    | OK           | api响应json对象«List«LeaveMessageVo对象»» |
| 401    | Unauthorized |                                           |
| 403    | Forbidden    |                                           |
| 404    | Not Found    |                                           |
## 分页获取留言及回复列表

**接口描述**:包括留言者和回复者信息

**接口地址**:`/leave/message/page`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| current       | 页码                      | query  | false    | integer  |        |
| size          | 每页数量                  | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"current": 0,
		"pages": 0,
		"records": [
			{
				"content": "",
				"createTime": "",
				"fromUser": {
					"admin": 0,
					"avatar": "",
					"birthday": "",
					"brief": "",
					"createTime": "",
					"email": "",
					"gender": 0,
					"id": 0,
					"mobile": 0,
					"nickname": "",
					"status": 0,
					"username": ""
				},
				"id": 0,
				"replyList": [
					{
						"content": "",
						"createTime": "",
						"fromUser": {
							"admin": 0,
							"avatar": "",
							"birthday": "",
							"brief": "",
							"createTime": "",
							"email": "",
							"gender": 0,
							"id": 0,
							"mobile": 0,
							"nickname": "",
							"status": 0,
							"username": ""
						},
						"id": 0,
						"toUser": {
							"admin": 0,
							"avatar": "",
							"birthday": "",
							"brief": "",
							"createTime": "",
							"email": "",
							"gender": 0,
							"id": 0,
							"mobile": 0,
							"nickname": "",
							"status": 0,
							"username": ""
						}
					}
				]
			}
		],
		"searchCount": true,
		"size": 0,
		"total": 0
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型                      | schema                    |
| -------- | -------- | ------------------------- | ------------------------- |
| code     | 响应码   | integer(int32)            | integer(int32)            |
| data     | 响应数据 | IPage«LeaveMessageVo对象» | IPage«LeaveMessageVo对象» |
| message  | 响应信息 | string                    |                           |



**schema属性说明**




**IPage«LeaveMessageVo对象»**

| 参数名称    | 参数说明 | 类型           | schema             |
| ----------- | -------- | -------------- | ------------------ |
| current     |          | integer(int64) |                    |
| pages       |          | integer(int64) |                    |
| records     |          | array          | LeaveMessageVo对象 |
| searchCount |          | boolean        |                    |
| size        |          | integer(int64) |                    |
| total       |          | integer(int64) |                    |

**LeaveMessageVo对象**

| 参数名称   | 参数说明 | 类型              | schema                  |
| ---------- | -------- | ----------------- | ----------------------- |
| content    | 内容     | string            |                         |
| createTime | 时间     | string(date-time) |                         |
| fromUser   | 留言者   | User对象          | User对象                |
| id         | id       | integer(int32)    |                         |
| replyList  | 回复列表 | array             | LeaveMessageReplyVo对象 |

**User对象**

| 参数名称   | 参数说明                                 | 类型              | schema |
| ---------- | ---------------------------------------- | ----------------- | ------ |
| admin      | 是否管理员，1：是，0：否                 | integer(int32)    |        |
| avatar     | 用户头像                                 | string            |        |
| birthday   | 生日                                     | string(date)      |        |
| brief      | 简介                                     | 个性签名          | string |
| createTime | 创建时间                                 | string(date-time) |        |
| email      | 电子邮箱                                 | string            |        |
| gender     | 性别，1：男，0：女，默认为1              | integer(int32)    |        |
| id         | 用户id                                   | integer(int32)    |        |
| mobile     | 手机号                                   | integer(int64)    |        |
| nickname   | 昵称                                     | string            |        |
| status     | 状态，0：正常，1：锁定，2：禁用，3：过期 | integer(int32)    |        |
| username   | 用户名                                   | string            |        |

**LeaveMessageReplyVo对象**

| 参数名称   | 参数说明 | 类型              | schema   |
| ---------- | -------- | ----------------- | -------- |
| content    | 内容     | string            |          |
| createTime | 时间     | string(date-time) |          |
| fromUser   | 回复者   | User对象          | User对象 |
| id         | id       | integer(int32)    |          |
| toUser     | 被回复者 | User对象          | User对象 |

**响应状态**:


| 状态码 | 说明         | schema                                     |
| ------ | ------------ | ------------------------------------------ |
| 200    | OK           | api响应json对象«IPage«LeaveMessageVo对象»» |
| 401    | Unauthorized |                                            |
| 403    | Forbidden    |                                            |
| 404    | Not Found    |                                            |
## 留言回复

**接口描述**:需要accessToken

**接口地址**:`/leave/message/reply`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| pid           | 父id                      | query  | false    | integer  |        |
| toUserId      | 被回复者id                | query  | false    | integer  |        |
| content       | 回复内容                  | query  | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
# 短信验证码服务

## 发送短信验证码

**接口描述**:验证码有效时5分钟;同一手机号每天只能发10次;同一ip每天只能发10次;同一手机号限流120s一次

**接口地址**:`/sms/send`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明                  | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------------------- | ------ | -------- | -------- | ------ |
| Authorization | 格式：Bearer access_token | header | true     | string   |        |
| mobile        | 手机号                    | query  | false    | integer  |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 201    | Created      |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
| 404    | Not Found    |                 |
# 认证服务

## 账号密码登录

**接口描述**:账号可以是用户名或手机号

**接口地址**:`/account/login`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明         | in     | 是否必须 | 数据类型 | schema |
| ------------- | ---------------- | ------ | -------- | -------- | ------ |
| username      | 用户名或手机号   | query  | false    | string   |        |
| password      | 密码             | query  | false    | string   |        |
| Authorization | 客户端认证请求头 | header | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"access_token": "",
		"refresh_token": "",
		"token_type": ""
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | AccessTokenDTO | AccessTokenDTO |
| message  | 响应信息 | string         |                |



**schema属性说明**




**AccessTokenDTO**

| 参数名称      | 参数说明         | 类型   | schema |
| ------------- | ---------------- | ------ | ------ |
| access_token  | access_token     | string |        |
| refresh_token | refresh_token    | string |        |
| token_type    | token类型:Bearer | string |        |

**响应状态**:


| 状态码 | 说明         | schema                          |
| ------ | ------------ | ------------------------------- |
| 200    | OK           | api响应json对象«AccessTokenDTO» |
| 201    | Created      |                                 |
| 401    | Unauthorized |                                 |
| 403    | Forbidden    |                                 |
| 404    | Not Found    |                                 |
## 用户登出


**接口描述**:


**接口地址**:`/logout`


**请求方式**：`DELETE`


**consumes**:``


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明      | in     | 是否必须 | 数据类型 | schema |
| ------------- | ------------- | ------ | -------- | -------- | ------ |
| access_token  | access_token  | query  | false    | string   |        |
| Authorization | Authorization | header | true     | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | object         |                |
| message  | 响应信息 | string         |                |





**响应状态**:


| 状态码 | 说明         | schema          |
| ------ | ------------ | --------------- |
| 200    | OK           | api响应json对象 |
| 204    | No Content   |                 |
| 401    | Unauthorized |                 |
| 403    | Forbidden    |                 |
## 手机号验证码登录

**接口描述**:验证码调用发送验证码接口获取

**接口地址**:`/mobile/login`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明         | in     | 是否必须 | 数据类型 | schema |
| ------------- | ---------------- | ------ | -------- | -------- | ------ |
| mobile        | 手机号           | query  | false    | integer  |        |
| code          | 手机号验证码     | query  | false    | string   |        |
| Authorization | 客户端认证请求头 | header | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"access_token": "",
		"refresh_token": "",
		"token_type": ""
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | AccessTokenDTO | AccessTokenDTO |
| message  | 响应信息 | string         |                |



**schema属性说明**




**AccessTokenDTO**

| 参数名称      | 参数说明         | 类型   | schema |
| ------------- | ---------------- | ------ | ------ |
| access_token  | access_token     | string |        |
| refresh_token | refresh_token    | string |        |
| token_type    | token类型:Bearer | string |        |

**响应状态**:


| 状态码 | 说明         | schema                          |
| ------ | ------------ | ------------------------------- |
| 200    | OK           | api响应json对象«AccessTokenDTO» |
| 201    | Created      |                                 |
| 401    | Unauthorized |                                 |
| 403    | Forbidden    |                                 |
| 404    | Not Found    |                                 |
## 第三方登录

**接口描述**:不需要accessToken

**接口地址**:`/oauth`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明         | in     | 是否必须 | 数据类型 | schema |
| ------------- | ---------------- | ------ | -------- | -------- | ------ |
| type          | 认证类型         | query  | false    | integer  |        |
| code          | 第三方授权码     | query  | false    | string   |        |
| Authorization | 客户端认证请求头 | header | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"access_token": "",
		"refresh_token": "",
		"token_type": ""
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | AccessTokenDTO | AccessTokenDTO |
| message  | 响应信息 | string         |                |



**schema属性说明**




**AccessTokenDTO**

| 参数名称      | 参数说明         | 类型   | schema |
| ------------- | ---------------- | ------ | ------ |
| access_token  | access_token     | string |        |
| refresh_token | refresh_token    | string |        |
| token_type    | token类型:Bearer | string |        |

**响应状态**:


| 状态码 | 说明         | schema                          |
| ------ | ------------ | ------------------------------- |
| 200    | OK           | api响应json对象«AccessTokenDTO» |
| 201    | Created      |                                 |
| 401    | Unauthorized |                                 |
| 403    | Forbidden    |                                 |
| 404    | Not Found    |                                 |
## 刷新accessToken


**接口描述**:


**接口地址**:`/refresh_access_token`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称      | 参数说明         | in     | 是否必须 | 数据类型 | schema |
| ------------- | ---------------- | ------ | -------- | -------- | ------ |
| refresh_token | refresh_token    | query  | false    | string   |        |
| Authorization | 客户端认证请求头 | header | false    | string   |        |

**响应示例**:

```json
{
	"code": 0,
	"data": {
		"access_token": "",
		"refresh_token": "",
		"token_type": ""
	},
	"message": ""
}
```

**响应参数**:


| 参数名称 | 参数说明 | 类型           | schema         |
| -------- | -------- | -------------- | -------------- |
| code     | 响应码   | integer(int32) | integer(int32) |
| data     | 响应数据 | AccessTokenDTO | AccessTokenDTO |
| message  | 响应信息 | string         |                |



**schema属性说明**




**AccessTokenDTO**

| 参数名称      | 参数说明         | 类型   | schema |
| ------------- | ---------------- | ------ | ------ |
| access_token  | access_token     | string |        |
| refresh_token | refresh_token    | string |        |
| token_type    | token类型:Bearer | string |        |

**响应状态**:


| 状态码 | 说明         | schema                          |
| ------ | ------------ | ------------------------------- |
| 200    | OK           | api响应json对象«AccessTokenDTO» |
| 201    | Created      |                                 |
| 401    | Unauthorized |                                 |
| 403    | Forbidden    |                                 |
| 404    | Not Found    |                                 |
