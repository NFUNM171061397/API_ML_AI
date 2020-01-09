# API_ML_AI

## 产品要求
| 发布时间 | 2019-12-05 |
| ------  | -------:   |
| 文档名称 |  旅行轨迹    |
| 文档状态 |  进行中     |
| 文档撰写者 |  张柳燕     |
| 产品设计师  |  张柳燕    |
|  产品开发者 |  张柳燕    |
| 产品测试员|  张柳燕    |

## 价值主张设计（一句话版本）
旅行轨迹APP为用户提供了照片打卡与发现电影好去处这两大功能，能够通过用户上传的照片进行旅行打卡，在地图上生成专属地图，以及为广大电影爱好者提供影片地标识别，推荐旅行好去处，是一款适合旅游和电影爱好者的软件。


## 价值主张设计（一分钟版本）
### 1.加值宣言
* 旅行轨迹APP是一款针对于旅行爱好者的软件，拥有照片打卡与地标识别这两大核心功能。
* 作为旅游爱好者想要通过打卡的方式来记录自己的旅行轨迹，那么可以通过用户上传的照片，进行照片信息的读取，再根据经纬度通过百度地图API获取位置，实现照片打卡功能。（重要）
* 用户在影视/图片中看到心仪的景点，则可上传图片（影片截图），软件将通过调用百度——地标识别API，反馈给用户有关该图片中的地标名称。识别地标名称与查询相应的信息，帮助用户解决不知道图片中出现的地标名称的问题，提供图片地标查询的功能。（重要）
* 用户想要旅游又不知道去哪里好，可以根据用户浏览记录来为用户推荐景点，也可以根据用户所在位置推荐周边景点。（次重要-暂不做）


### 2.核心价值（最小可行性产品）
1. 照片打卡：对用户上传的照片进行信息读取，通过逆地理解析API获取照片经纬度，再通过调用静态地图API，根据经纬度获取地图位置。
2. 地标识别：用户从手机相册上传图片/拍摄照片，返回图中的地标名称与详细资料。

### 3.核心价值与用户痛点
* 用户想要一款可以通过打卡的方式来记录自己旅行的app。
* 用户想要知道图片中的地标名称与信息，但是没有办法知道。
* 用户想要去旅游，但不知道去哪里好。
* 用户想知道自己周边有什么好玩的景点。
* 用户想要查看相册中某次旅行的照片，但是相册没有分类。

### 4.人工概率性与用户痛点
* 用户上传的图片清晰度过低，无法识别
* 用户拍照时没有开启GPS定位
* 用户在室内拍照时，GPS信号弱，定位不准确

### 5.需求列表与人工智能API加值

| 问题 | 结果| 人工智能API| 重要程度|
| ------  | ------- |----|----|
| 用户想要快速知道图片中的地标名称是什么？ |  上传图片，即能识别该地标名称  |地标识别API|非常重要|
| 用户想要一款有趣的旅行记录app |  上传照片，实现地图打卡，生成专属于你的旅行轨迹  |逆地理解析API、静态地图API|非常重要|
| 用户想要发现世界上更多美好的景点？ | 推荐系统通过浏览记录智能筛选您可能感兴趣的内容    |智能推荐|次重要|
| 用户想要发现自己周边的景点？ | 推荐系统通过用户定位智能推荐周边好去处    |智能推荐|次重要|

## 二、产品设计
* 产品架构图
![产品架构](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/产品架构.png)

* 载入页面-介绍产品的三大核心功能
![载入界面](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/载入界面.jpeg)

* 拍照打卡模块
![拍照打卡](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/拍照打卡.jpeg)
![拍照打卡2](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/拍照打卡2.jpeg)

* 地标识别模块
![地标识别](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/地标识别.jpeg)
![地标识别](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/地标识别2.jpeg)

* 附近去处模块（暂不做）
![附近去处](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/附近去处.jpeg)

* 个人页面
![个人模块](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/个人模块.jpeg)

### 1.交互及界面设计（详见上文图片/原型）
* 拍照打卡模块：静态地图API
* 地标识别模块：地标识别API、智能推荐
### 2.信息设计（详见上文图片/原型）
* 返回的地标建筑详细资料：地标识别API+百度百科资料
* 返回的照片打卡地图：静态地图API
### 3.[产品原型文档]( http://nfunm171061397.gitee.io/api_ml_ai)
### 4.口头操作说明（详见上文图片/原型，20*20ppt）

## 三、API调用
### 1.使用水平
[拍照打卡模块实践](http://nfunm171061397.gitee.io/photo_python)
[地标识别模块实践](http://nfunm171061397.gitee.io/build_python)
[利用地标识别+百科，搞定名胜古迹识别](https://www.csdn.net/article/a/2019-07-04/15977007)
总结：都是当前可实现的技术。

### 2.使用比较分析
### 地标识别API
#### 1.百度AI-地标识别API
* [接口文档](https://ai.baidu.com/ai-doc/IMAGERECOGNITION/Kk3bcxbxj)
* 接口描述：该请求用于识别地标，即对于输入的一张图片（可正常解码，且长宽比适宜），输出图片中的地标识别结果。
* 接口地址： https://aip.baidubce.com/rest/2.0/image-classify/v1/landmark
* 请求方式：POST
* 请求实例：
```python
# encoding:utf-8

import requests
import base64

'''
地标识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v1/landmark"
# 二进制方式打开图片文件
f = open('[本地文件]', 'rb')
img = base64.b64encode(f.read())

params = {"image":img}
access_token = '[调用鉴权接口获取的token]'
request_url = request_url + "?access_token=" + access_token
headers = {'content-type': 'application/x-www-form-urlencoded'}
response = requests.post(request_url, data=params, headers=headers)
if response:
    print (response.json())
```
* 输出示例1
```python
{"log_id": 3450013152046070669, "result": {"landmark": "狮身人面像"}}
```
 * 输出示例2
```python
{'log_id': 1157600868256087579, 'result': {'landmark': '埃菲尔铁塔'}}
```
* 输出结果
![百度ai](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/百度识别结果.png)
 
#### 2.微软-计算机影像api
* 识别名人和地标：名人和地标模型是特定于域的模型的示例。名人模型识别功能可识别 20 万商业、政治、体育和娱乐界名人。地标模型识别功能可识别全世界 9000 个自然和人工地标。特定于域的模型是计算机影像 API 内不断发展的功能。
* 代码示例：
```python
computervision_client = ComputerVisionClient(endpoint, CognitiveServicesCredentials(subscription_key))
remote_image_url = "https://raw.githubusercontent.com/Azure-Samples/cognitive-services-sample-data-files/master/ComputerVision/Images/landmark.jpg"

# Call API with content type (landmarks) and URL
detect_domain_results_landmarks = computervision_client.analyze_image_by_domain("landmarks", remote_image_url)
print()

print("Landmarks in the remote image:")
if len(detect_domain_results_landmarks.result["landmarks"]) == 0:
    print("No landmarks detected.")
else:
    for landmark in detect_domain_results_landmarks.result["landmarks"]:
        print(landmark["name"])
```
* 输出结果：
![微软](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/输出结果2.png)

#### 两家API对比
![百度](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/百度.png)
* 百度AI适用于企业用户使用，调用量无限制，免费调用量一次性共3000次，超过部分的价格为1.8元/千次。它支持识别12万中外著名地标、景点，广泛应用于拍照识图、图片分类等场景。

![微软](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/微软价格.png)
* 微软认知服务中，计算机视觉API目前支持两个特定领域的模型识别：名人和地标。免费调用量一次性共5000次，超过部分的价格有三个范围：0-1 百万个事务 — 每 1,000 个事务 ¥ 9.54；1-5 百万个事务 — 每 1,000 个事务 ¥ 6.36；5百万 + 个事务 — 每 1,000 个事务 ¥4.13。地标识别功能可识别全世界9000个自然和人工地标。

* 总结：就两家的调用价格来看，百度AI的价格优惠非常多，性价比高。再从收录的地标来看，百度AI高达12万，远远多于微软9000的收录。对于一款旅行app来说，能够成功识别图片中的地标，这对用户来说非常的重要。因此我选择百度AI中的地标识别，这是最适合于本产品的API。

### 逆地理解析API
#### 1.百度地图-逆地理解析API
* 全球逆地理编码服务（又名Geocoder）是一类Web API接口服务；
* 服务介绍：用户可通过该功能，将位置坐标解析成对应的行政区划数据以及周边高权重地标地点分布情况，整体描述坐标所在的位置。
* 服务地址： http://api.map.baidu.com/geocoder/v2/
* 请求方式：GET
* json示例：
http://api.map.baidu.com/geocoder/v2/?ak=E4805d16520de693a3fe707cdc962045&callback=renderReverse&location=39.983424,116.322987&output=json&pois=1
* xml示例：
http://api.map.baidu.com/geocoder/v2/?ak=E4805d16520de693a3fe707cdc962045&callback=renderReverse&location=39.983424,116.322987&output=xml&pois=1
* 示例可参见上文1.使用水平


#### 2.高德地图-逆地理解析API
* 逆地理编码：将经纬度转换为详细结构化的地址，且返回附近周边的POI、AOI信息。
* 例如：116.480881,39.989410 转换地址描述后：北京市朝阳区阜通东大街6号
* URL： https://restapi.amap.com/v3/geocode/regeo?parameters
* 请求方式：GET
* 代码示例：
```python
import requests
key_1 = 'you key'
def geo(location):
    """获取逆地理编码"""
    url = 'https://restapi.amap.com/v3/geocode/regeo?parameters'
    params = {
        'key' : key_1,
        'location' : '116.481488,39.990464',
        'output' : 'json'
    }
    response = requests.get(url,params=params)
    data = response.json()
    return data
```
* 返回示例：
```python
{'status': '1',
 'regeocode': {'addressComponent': {'city': [],
   'province': '北京市',
   'adcode': '110105',
   'district': '朝阳区',
   'towncode': '110105026000',
   'streetNumber': {'number': '6号',
    'location': '116.482005,39.9900561',
    'direction': '东南',
    'distance': '63.2126',
    'street': '阜通东大街'},
   'country': '中国',
   'township': '望京街道',
   'businessAreas': [{'location': '116.470293,39.996171',
     'name': '望京',
     'id': '110105'},
    {'location': '116.494356,39.971563', 'name': '酒仙桥', 'id': '110105'},
    {'location': '116.492891,39.981321', 'name': '大山子', 'id': '110105'}],
   'building': {'name': '方恒国际中心B座', 'type': '商务住宅;楼宇;商务写字楼'},
   'neighborhood': {'name': '方恒国际中心', 'type': '商务住宅;楼宇;商住两用楼宇'},
   'citycode': '010'},
  'formatted_address': '北京市朝阳区望京街道方恒国际中心B座方恒国际中心'},
 'info': 'OK',
 'infocode': '10000'}
```
#### 3.腾讯地图-逆地理解析API
* 接口描述：本接口提供由坐标到坐标所在位置的文字描述的转换。输入坐标返回地理位置信息和附近poi列表。目前应用于物流、出行、O2O、社交等场景。服务响应速度快、稳定，支撑亿级调用
* URL： https://apis.map.qq.com/ws/geocoder/v1/?location= 
* 请求方式：GET
* 调用示例：//GET请求示例，注意参数值要进行URL编码
https://apis.map.qq.com/ws/geocoder/v1/?location=39.984154,116.307490&key=OB4BZ-D4W3U-B7VVO-4PJWW-6TKDJ-WPB77&get_poi=1
* 具体的参数介绍：http://lbs.qq.com/webservice_v1/guide-gcoder.html

### 静态地图API
#### 1.百度地图-静态图API
* 服务地址：http://api.map.baidu.com/staticimage/v2
* 高分屏设备，从低清图切换至高清图示例：
低清图url:
```python
 <img style="margin:20px" width="280" height="140" src="http://api.map.baidu.com/staticimage/v2?ak=E4805d16520de693a3fe707cdc962045&width=280&height=140&zoom=1"/>
 ```
示例效果：在iphone4（ios系统）中显示一张280*140，缩放级别为10的北京市地图
![百度低清图](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/百度低清图.png)
高清图url:
```python
<img style="margin:20px" width="280" height="140" src="http://api.map.baidu.com/staticimage/v2?ak=E4805d16520de693a3fe707cdc962045&width=280&height=140&zoom=11&scale=2"/>
```
示例效果：在iphone 4（ios系统）显示一张560*280，缩放级别为11的北京市高清地图
![百度高清图](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/百度高清图.png)

#### 2.高德地图-静态地图API
* 服务介绍：静态地图服务通过返回一张地图图片响应HTTP请求，使用户能够将高德地图以图片形式嵌入自己的网页中。用户可以指定请求的地图位置、图片大小、以及在地图上添加覆盖物，如标签、标注、折线、多边形。
* 示例：
```python
https://restapi.amap.com/v3/staticmap?location=116.481485,39.990464&zoom=10&size=750*300&markers=mid,,A:116.481485,39.990464&key=<用户的key>
```
![高德示例](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/高德示例.png)


#### 3.腾讯地图-静态地图API
* 大小限制：静态图支持返回的图片尺寸：宽度介于50到1680像素之间，高度介于50到1200像素之间。超过该尺寸范围将不返回图片。
* 调用示例：
```python
https://apis.map.qq.com/ws/staticmap/v2/
?center=39.8802147,116.415794
&zoom=10
&size=600*300
&maptype=roadmap
&markers=size:large|color:0xFFCCFF|label:k|39.8802147,116.415794
&key=OB4BZ-D4W3U-B7VVO-4PJWW-6TKDJ-WPB77
```
* 调用结果：
![腾讯调用结果](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/腾讯调用结果.png)


#### 配额限制说明
* 百度地图
![百度逆地理](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/百度逆地理.png)
![百度静态图](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/百度静态图.png)
* 高德地图
![高德地图](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/高德地图.png)
* 腾讯地图
![腾讯地图](https://gitee.com/NFUNM171061397/API_ML_AI/blob/master/image/腾讯地图.png)

#### 三家API对比
百度之前的优点就是没有调用次数限制，这点比腾讯的10000/天好多了。但是现在都有次数限定了，所以高德的性价比比较高。
在逆地理编码API中，用经纬度查询实际地理位置时，百度地图只能精确到小数点后第2位，只能够定位到某个区，但是高德地图，能够精确到小数点后第4位。


### 3.使用后风险报告



### 4.加分项
使用复杂度：用了2个以上机器学习与人工智能的API之输入及输出




