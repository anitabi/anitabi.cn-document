# 动画巡礼 API

## 根据 Bangumi 作品 id 获取对应巡礼地标信息

`GET` `https://api.anitabi.cn/bangumi/115908/lite`


返回数据结构结构
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

#### `bangumiLite` 作品对应巡礼信息 轻量版

 - `id` bangumi 作品 ID
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
 - `image` 地标对应截图
 - `ep` 集数
 - `s` 截图对应时间 单位秒
 - `geo[]` 地标对应 GPS 信息
