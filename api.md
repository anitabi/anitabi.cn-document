---
title: 🔧 开放 API
sidebar_position: 4
---

# 🔧 开放 API

## 基础 API 地址
 - 数据 API 基础地址 `https://api.anitabi.cn/`
 - 图片 API 基础地址 `https://image.anitabi.cn/`
> 请勿在任何场景下请求主域 `https://anitabi.cn/`，主域不确保任何 **资源地址** 以及 **数据结构** 的稳定

## 根据 Bangumi 作品 id 获取对应巡礼地标信息

`GET` `https://api.anitabi.cn/bangumi/${subjectID}/lite` [例](https://api.anitabi.cn/bangumi/115908/lite)


返回数据结构
```JSON
{
	"id": 115908,
	"cn": "吹响吧！上低音号",
	"title": "響け！ユーフォニアム",
	"city": "宇治市",
	"cover": "https://image.anitabi.cn/bangumi/115908.jpg?plan=h160",
	"color": "#02a7bd",
	"geo": [
		34.90646037778022,
		135.81221398475236
	],
	"zoom": 12.383488825333831,
	"modified": 1674702846652,
	"litePoints": [
		{
			"id": "qys7fu",
			"cn": "京都音乐厅",
			"name": "京都コンサートホール",
			"image": "https://image.anitabi.cn/points/115908/qys7fu.jpg?plan=h160",
			"ep": 1,
			"s": 1,
			"geo": [
				35.0503,
				135.7664
			]
		}
	],
	"pointsLength": 388,
	"imagesLength": 388
}
```
### 属性说明

#### `liteBangumi` 作品对应巡礼信息 轻量版

 - `id` bangumi 作品 `subjectID`
 - `cn` 作品中文译名
 - `title` 作品原名
 - `city` 巡礼地标主要所在城市，可能为空
 - `cover` 作品封面图
 - `color` 作品主色
 - `geo[]` 作品默认 GPS 坐标
 - `zoom` 作品默认放大等级
 - `modified` 数据最后更新时间戳
 - `litePoints[]` 前十个标志性地标信息
 - `pointsLength` 地标总数
 - `imagesLength` 含截图的地标数

#### `litePoints` 地标信息 轻量版

 - `id` 地标 ID
 - `cn` 地标中文译名
 - `name` 地标原名，默认为地标所属国家语言
 - `image` 地标对应截图缩略图
 - `ep` 集数
 - `s` 截图对应时间 单位秒
 - `geo[]` 地标对应 GPS 信息


## 通过截图缩略图地址获取标清截图
例如通过 [缩略图地址](https://image.anitabi.cn/points/115908/qys7fu.jpg?plan=h160)，获得更高分辨率截图。

可将 查询值 `?plan=h160` 替换为 `?plan=h360`

可获得适合在移动设备满宽度查看尺寸的 [截图地址](https://image.anitabi.cn/points/115908/qys7fu.jpg?plan=h360) 


## 通过截图缩略图地址获取完整尺寸截图
可将 查询值 `?plan=h160` 删除，即为 [完整尺寸截图](https://image.anitabi.cn/points/115908/qys7fu.jpg)。

> 不建议在 **任何展示界面** 上使用完整尺寸截图，大量请求完整尺寸截图会对服务器造成压力，且无法确保快速加载。

## 根据 bangumi 作品 ID 获得巡礼地图地址
```javascript
function getAnitabiSubjectURLById(id){
	return `https://anitabi.cn/map?bangumiId=${id}`
}
```


## 根据 Bangumi 作品 id 获取对应巡礼地标详情信息

`GET` `https://api.anitabi.cn/bangumi/${subjectID}/points/detail` [例](https://api.anitabi.cn/bangumi/126461/points/detail)

`QueryString` 
 - `haveImage=true` 筛选含图地标

Anitabi 的巡礼地标截图来着多种不同信息来源，使用此 API 获取地标截图信息时，建议在展示的地标截图信息旁 标注 `origin` 文字，以及实现 `originURL` 的跳转

遵循
署名、非商业性使用、相同方式共享 的
<a href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh-hans" target="_blank">CC BY-NC-SA 4.0</a>
协议共享

返回数据结构
```JSON
[
	{
		"id": "5qypywi9",
		"name": "第二箸別バス停前（箸別駅西側）",
		"image": "https://image.anitabi.cn/points/126461/5qypywi9.jpg?plan=h160",
		"ep": 1,
		"s": 282,
		"geo": [
			43.8578,
			141.5462
		],
		"origin": "Google Maps",
		"originURL": "https://www.google.com/maps/d/viewer?mid=1hkF1issn0oVQDeN4BIrBPp5b5Ek&ll=43.857864%2C141.546264&z=17"
	}
]
```
