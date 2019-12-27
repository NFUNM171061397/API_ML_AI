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
### 加值宣言
旅行轨迹APP是一款针对于旅行爱好者的软件，拥有照片打卡与地标识别这两大核心功能。作为旅游爱好者想要通过打卡的方式来记录自己的旅行轨迹，那么可以通过用户上传的照片，进行照片信息的读取，再根据经纬度通过百度地图API获取位置，实现照片打卡功能。用户在影视/图片中看到心仪的景点，则可上传图片（影片截图），软件将通过调用百度——地标识别API，反馈给用户有关该图片中的地标名称。用户想要旅游又不知道去哪里好，可以根据用户浏览记录来为用户推荐景点，也可以根据用户所在位置推荐周边景点。识别地标名称与查询相应的信息，帮助用户解决不知道图片中出现的地标名称的问题，提供图片地标查询的功能。


### 核心价值（最小可行性产品）
1. 照片打卡：对用户上传的照片进行信息读取，获取照片经纬度，再通过调用高德地图API-静态地图，根据经纬度获取地图位置。
2. 地标识别：用户从手机相册上传图片/拍摄照片，返回图中的地标名称。
3. 智能推荐：可以根据用户浏览记录来为用户推荐景点，也可以根据用户所在位置推荐周边景点。


### 核心价值与用户痛点
* 用户想要一款可以通过打卡的方式来记录自己的旅行。
* 用户想要知道图片中的地标名称与信息，但是没有办法知道。
* 用户想要去旅游，但不知道去哪里好。
* 用户想知道自己周边有什么好玩的景点。
* 用户想要查看相册中某次旅行的照片，但是相册没有分类。

### 人工概率性与用户痛点
* 用户上传的图片清晰度过低，无法识别
* 用户拍照时没有开启GPS定位
* 用户在室内拍照时，GPS信号弱，定位不准确

### 需求列表与人工智能API加值

| 问题 | 结果|
| ------  | -------:   |
| 用户想要快速知道图片中的地标名称是什么？ |  上传图片至本产品，通过百度-地标识别API，即能查到该地标名称  |
| 用户想了解更多有关该地标的信息有什么？ |  该产品提供查询界面，可以查到该地标/影片的详细信息  |
| 用户想要发现世界上更多美好的景点？ | 推荐系统通过历史记录智能筛选您可能感兴趣的内容    |




## 二、产品设计
![产品原型](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/9101577203297_.pic.jpg)
![产品原型](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/9111577203329_.pic.jpg)
![产品原型](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/9121577203354_.pic.jpg)
![产品原型](https://gitee.com/NFUNM171061397/API_ML_AI/raw/master/image/9131577203400_.pic.jpg)


## 三、API调用
### 地标识别API
1.百度AI-地标识别API
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
2.聚合数据-地标识别API
* 接口地址：http://apis.juhe.cn/landmarkDetect/index
* 返回格式：json
* 请求方式：http post
* 接口备注：该请求用于识别地标，即对于输入的一张图片（可正常解码，且长宽比适宜），输出图片中的地标识别结果
* [请求实例](http://apis.juhe.cn/landmarkDetect/index)
* JSON返回数据：
```python
{
    "reason": "success",
    "result": "东方明珠",
    "error_code": 0
}
```

3.阿里云-景点识别
* 调用地址：http(s)://location.market.alicloudapi.com/landmark
* 请求方式：POST
* 返回类型：JSON
* 请求实例：
```python
import urllib, urllib2, sys
import ssl


host = 'https://location.market.alicloudapi.com'
path = '/landmark'
method = 'POST'
appcode = '你自己的AppCode'
querys = ''
bodys = {}
url = host + path

bodys['src'] = '''图片base64编码'''
post_data = urllib.urlencode(bodys)
request = urllib2.Request(url, post_data)
request.add_header('Authorization', 'APPCODE ' + appcode)
//根据API的要求，定义相对应的Content-Type
request.add_header('Content-Type', 'application/x-www-form-urlencoded; charset=UTF-8')
ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE
response = urllib2.urlopen(request, context=ctx)
content = response.read()
if (content):
    print(content)
 ```
 * 输出示例1——成功
 ```python
  "status": 200,
  "msg": [
    {
      "description": "中央电视指挥部大楼",
      "score": 0.34413087,
      "boundingPoly": {
        "vertices": [
          {
            "x": 221,
            "y": 64
          },
          {
            "x": 720,
            "y": 64
          },
          {
            "x": 720,
            "y": 608
          },
          {
            "x": 221,
            "y": 608
          }
        ]
      },
      "locations": [
        {
          "latLng": {
            "latitude": 39.913505296604,
            "longitude": 116.456537
          }
        }
      ]
    }
  ]
}
 ```
* 输出示例2——失败
 ```python
 {
  "status": 500
}
 ```
 
4.微软-计算机影像api
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
