#百度天气预报接口介绍

百度提供天气预报查询接口API，可以根据经纬度/城市名查询天气情况，我们可以在微信公众平台开发中调用这一接口。

##接口说明
根据经纬度/城市名查询天气的结果

##接口示例
http://api.map.baidu.com/telematics/v3/weather?location=北京&output=json&ak=6tYzTvGZSOpYB5Oc2YGGOKt8

>百度ak申请地址：http://lbsyun.baidu.com/apiconsole/key

##接口参数说明
参数类型	参数名称	是否必须	具体描述
String	location	true	输入城市名或经纬度，城市名称如:北京或者131，经纬度格式为lng,lat坐标如: location=116.305145,39.982368;全国值为all,返回省会城市自治区，港澳台天气情况多城市天气预报中间”
String	output	false	输出的数据格式，默认为xml格式，当output设置为’json’时，输出的为json格式的数据;
String	coord_type	false	请求参数坐标类型，默认为gcj02经纬度坐标。允许的值为bd09ll、bd09mc、gcj02、wgs84。bd09ll表示百度经纬度坐标，bd09mc表示百度墨卡托坐标，gcj02表示经过国测局加密的坐标。wgs84表示gps获取的坐标。
String	ak	true	访问应用(ak) 需要在百度lbs开放平台申请
##返回结果
参数名称	含义	说明
currentCity	当前城市	返回城市名
status	返回结果状态信息	
date	当前时间	年-月-日
results	天气预报信息	白天可返回近期3天的天气情况（今天、明天、后天）、晚上可返回近期4天的天气情况（今天、明天、后天、大后天）
results.currentCity	当前城市	
results.weather_data	天气预报时间	
weather_data.dayPictureUrl	白天的天气预报图片url	
weather_data.nightPictureUrl	晚上的天气预报图片url	
weather_data.weather	天气状况	所有天气情况（”
weather_data.wind	风力	
weather_data.temperature	温度	
###返回JSON格式的数据
<code>
{
    "error": 0,
    "status": "success",
    "date": "2014-09-17",
    "results": [
        {
            "currentCity": "北京",
            "pm25": "153",
            "index": [
                {
                    "title": "穿衣",
                    "zs": "较舒适",
                    "tipt": "穿衣指数",
                    "des": "建议着薄外套或牛仔衫裤等服装。年老体弱者宜着夹克衫、薄毛衣等。昼夜温差较大，注意适当增减衣服。"
                },
                {
                    "title": "洗车",
                    "zs": "较适宜",
                    "tipt": "洗车指数",
                    "des": "较适宜洗车，未来一天无雨，风力较小，擦洗一新的汽车至少能保持一天。"
                },
                {
                    "title": "旅游",
                    "zs": "适宜",
                    "tipt": "旅游指数",
                    "des": "天气较好，但丝毫不会影响您出行的心情。温度适宜又有微风相伴，适宜旅游。"
                },
                {
                    "title": "感冒",
                    "zs": "少发",
                    "tipt": "感冒指数",
                    "des": "各项气象条件适宜，无明显降温过程，发生感冒机率较低。"
                },
                {
                    "title": "运动",
                    "zs": "较适宜",
                    "tipt": "运动指数",
                    "des": "天气较好，但考虑气温较低，推荐您进行室内运动，若户外适当增减衣物并注意防晒。"
                },
                {
                    "title": "紫外线强度",
                    "zs": "弱",
                    "tipt": "紫外线强度指数",
                    "des": "紫外线强度较弱，建议出门前涂擦SPF在12-15之间、PA+的防晒护肤品。"
                }
            ],
            "weather_data": [
                {
                    "date": "周三 09月17日 (实时：21℃)",
                    "dayPictureUrl": "http://api.map.baidu.com/images/weather/day/duoyun.png",
                    "nightPictureUrl": "http://api.map.baidu.com/images/weather/night/qing.png",
                    "weather": "多云转晴",
                    "wind": "微风",
                    "temperature": "23 ~ 12℃"
                },
                {
                    "date": "周四",
                    "dayPictureUrl": "http://api.map.baidu.com/images/weather/day/qing.png",
                    "nightPictureUrl": "http://api.map.baidu.com/images/weather/night/duoyun.png",
                    "weather": "晴转多云",
                    "wind": "微风",
                    "temperature": "25 ~ 15℃"
                },
                {
                    "date": "周五",
                    "dayPictureUrl": "http://api.map.baidu.com/images/weather/day/yin.png",
                    "nightPictureUrl": "http://api.map.baidu.com/images/weather/night/yin.png",
                    "weather": "阴",
                    "wind": "微风",
                    "temperature": "23 ~ 15℃"
                },
                {
                    "date": "周六",
                    "dayPictureUrl": "http://api.map.baidu.com/images/weather/day/qing.png",
                    "nightPictureUrl": "http://api.map.baidu.com/images/weather/night/qing.png",
                    "weather": "晴",
                    "wind": "微风",
                    "temperature": "29 ~ 16℃"
                }
            ]
        }
    ]
}
</code>
###返回XML格式的数据
<code>
<?xml version="1.0" encoding="utf-8"?>

<CityWeatherResponse> 
 <error>0</error> 
 <status>success</status> 
 <date>2014-09-17</date> 
 <results> 
 <currentCity>北京</currentCity> 
 <weather_data> 
 <date>周三 09月17日 (实时：21℃)</date> 
 <dayPictureUrl>http://api.map.baidu.com/images/weather/day/duoyun.png</dayPictureUrl> 
 <nightPictureUrl>http://api.map.baidu.com/images/weather/night/qing.png</nightPictureUrl> 
 <weather>多云转晴</weather> 
 <wind>微风</wind> 
 <temperature>23 ~ 12℃</temperature> 
 <date>周四</date> 
 <dayPictureUrl>http://api.map.baidu.com/images/weather/day/qing.png</dayPictureUrl> 
 <nightPictureUrl>http://api.map.baidu.com/images/weather/night/duoyun.png</nightPictureUrl> 
 <weather>晴转多云</weather> 
 <wind>微风</wind> 
 <temperature>25 ~ 15℃</temperature> 
 <date>周五</date> 
 <dayPictureUrl>http://api.map.baidu.com/images/weather/day/yin.png</dayPictureUrl> 
 <nightPictureUrl>http://api.map.baidu.com/images/weather/night/yin.png</nightPictureUrl> 
 <weather>阴</weather> 
 <wind>微风</wind> 
 <temperature>23 ~ 15℃</temperature> 
 <date>周六</date> 
 <dayPictureUrl>http://api.map.baidu.com/images/weather/day/qing.png</dayPictureUrl> 
 <nightPictureUrl>http://api.map.baidu.com/images/weather/night/qing.png</nightPictureUrl> 
 <weather>晴</weather> 
 <wind>微风</wind> 
 <temperature>29 ~ 16℃</temperature> 
 </weather_data> 
 <index> 
 <title>穿衣</title> 
 <zs>较舒适</zs> 
 <tipt>穿衣指数</tipt> 
 <des>建议着薄外套或牛仔衫裤等服装。年老体弱者宜着夹克衫、薄毛衣等。昼夜温差较大，注意适当增减衣服。</des> 
 <title>洗车</title> 
 <zs>较适宜</zs> 
 <tipt>洗车指数</tipt> 
 <des>较适宜洗车，未来一天无雨，风力较小，擦洗一新的汽车至少能保持一天。</des> 
 <title>旅游</title> 
 <zs>适宜</zs> 
 <tipt>旅游指数</tipt> 
 <des>天气较好，但丝毫不会影响您出行的心情。温度适宜又有微风相伴，适宜旅游。</des> 
 <title>感冒</title> 
 <zs>少发</zs> 
 <tipt>感冒指数</tipt> 
 <des>各项气象条件适宜，无明显降温过程，发生感冒机率较低。</des> 
 <title>运动</title> 
 <zs>较适宜</zs> 
 <tipt>运动指数</tipt> 
 <des>天气较好，但考虑气温较低，推荐您进行室内运动，若户外适当增减衣物并注意防晒。</des> 
 <title>紫外线强度</title> 
 <zs>弱</zs> 
 <tipt>紫外线强度指数</tipt> 
 <des>紫外线强度较弱，建议出门前涂擦SPF在12-15之间、PA+的防晒护肤品。</des> 
 </index> 
 <pm25>153</pm25> 
 </results> 
</CityWeatherResponse>

</code>
