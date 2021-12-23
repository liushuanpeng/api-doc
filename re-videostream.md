
# re-videostream 模块接口定义

* [视频流RE请求](#upload)
  
    + [接口描述](#upload.interafceDesc)
    + [请求URL](#upload.requestUrl)
    + [请求方法](#upload.requestMethod)
    + [支持协议](#upload.requestProtocol)
    + [字符编码](#upload.requestEncode)
    + [建议超时时间](#upload.requestTimeout)
    + [请求参数](#upload.requestParameters)
    * [返回参数](#upload.responseParameters)

* [视频流关闭请求](#close)
  
    + [接口描述](#close.interfaceDesc)
    + [请求URL](#close.requestUrl)
    + [请求方法](#close.requestMethod)
    + [支持协议](#close.requestProtocol)
    + [字符编码](#close.requestEncode)
    + [建议超时时间](#close.requestTimeout)
    + [请求参数](#close.requestParameters)
    + [返回参数](#close.responseParameters)
* [视频流内部请求](#innerReq)
  
    + [视频流中的音频流](#demo.requestUploadV4)
    + [视频流中内部合并](#demo.requestUploadV4)
    + [视频流中内部结束](#demo.requestUploadV4)
    + [请求AE](#demo.responseUploadV4)
    + [请求图片BE](#demo.callbackV4)


## <span id = "upload">视频流RE请求</span>

### <span id = "upload.interafceDesc">接口描述</span>

该接口用于主接口模块请求RE模块请求使用。

### <span id = "upload.requestUrl">请求URL：</span>
| 接口类型 | URI | 接口功能|
| --- | --- | --- |
| V2 | `/v3/saas/anti_fraud/videostream` | V2请求接口|
| V2 | `/v3/saas/anti_fraud/finish_videostream` | V2结束接口|
| V2 | `/v3/saas/anti_fraud/query_videostream` | V2查询接口（暂时不对外暴露）|
| V4 | `/videostream/v4` | V4请求接口|
| V4 | `/finish_videostream/v4` | V4结束接口|

线上测试地址uri，和上述接口uri请求参数完全一致，主要用于对接一些来不及测试，但是对接客户比较着急的功能

| 接口类型 | URI | 接口功能|
| --- | --- | --- |
| V2 | `/v3/saas/anti_fraud/videostream/test` | V2线上测试请求接口|
| V2 | `/v3/saas/anti_fraud/finish_videostream/test` | V2线上测试结束接口|
| V2 | `/v3/saas/anti_fraud/query_videostream/test` | V2线上测试查询接口（暂时不对外暴露）|
| V4 | `/videostream/v4/test` | V4线上测试请求接口|
| V4 | `/finish_videostream/v4/test` | V4线上测试结束接口|

RE内部uri

| 接口类型 | URI | 接口功能|
| --- | --- | --- |
| V1 | `/saas/v1/antifraud/merge_image_audio_result` | [流结束合并流最终结果](#innerMergeResult.interafceDesc)|
| V1 | `/saas/v1/antifraud/inner_finish_info` | [发送结束请求给正在处理的流的机器](#innerMergeResult.interafceDesc) |

### <span id = "upload.requestMethod">请求方法：</span>

`POST` 

### <span id = "upload.requestProtocol">支持协议</span>

`HTTP`

### <span id = "upload.requestEncode">字符编码：</span>

`UTF-8`

### <span id = "upload.requestTimeout">建议超时时间：</span>

1s

### <span id = "upload.requestParameters">请求参数：</span>
在http头中会加入一些参数，re需要解析，详细如下：

header key | header value
---|---
m_request_id   | 请求唯一标识
m_service_id   | 客户产品标识
m_organization | 公司标识



见接口文档地址：

接口类型 | uri | 文档地址
---|---|---
V2 | /v3/saas/anti_fraud/videostream |xxxxx
V4 | /videostream/v4 |https://github.com/ishumei/api-doc/blob/main/V4/%E6%99%BA%E8%83%BD%E8%A7%86%E9%A2%91%E6%B5%81%E8%AF%86%E5%88%AB%E4%BA%A7%E5%93%81API%E6%96%87%E6%A1%A3.md

### <span id = "upload.responseParameters">返回参数</span>

见接口文档地址：
接口类型 | uri | 文档地址
---|---|---
V2 | /v3/saas/anti_fraud/videostream |xxxxx
V4 | /videostream/v4 |https://github.com/ishumei/api-doc/blob/main/V4/%E6%99%BA%E8%83%BD%E8%A7%86%E9%A2%91%E6%B5%81%E8%AF%86%E5%88%AB%E4%BA%A7%E5%93%81API%E6%96%87%E6%A1%A3.md

## <span id = "close">视频流关闭接口</span>

### <span id = "close.interfaceDesc">接口描述</span>

该接口用于客户端通知服务端某个视频流已关闭。

### <span id = "close.requestUrl">请求参数：</span>

见接口文档地址：
接口类型 | uri | 文档地址
---|---|---
V2 | /v3/saas/anti_fraud/finish_videostream |xxxxx
V4 | /finish_videostream/v4|https://github.com/ishumei/api-doc/blob/main/V4/%E6%99%BA%E8%83%BD%E8%A7%86%E9%A2%91%E6%B5%81%E8%AF%86%E5%88%AB%E4%BA%A7%E5%93%81API%E6%96%87%E6%A1%A3.md

### <span id = "close.responseParameters">返回参数</span>

见接口文档地址：
接口类型 | uri | 文档地址
---|---|---
V2 | /v3/saas/anti_fraud/finish_videostream |xxxxx
V4 | /finish_videostream/v4|https://github.com/ishumei/api-doc/blob/main/V4/%E6%99%BA%E8%83%BD%E8%A7%86%E9%A2%91%E6%B5%81%E8%AF%86%E5%88%AB%E4%BA%A7%E5%93%81API%E6%96%87%E6%A1%A3.md


## <span id = "inner.requestUri">内部接口uri请求</span>

### <span id = "inner.interfaceDesc">接口描述</span>

### <span id = "innerVSAudioInterFace.interafceDesc">视频流中的音频流请求：</span>
##### 请求接口uri：
/v2/saas/anti_fraud/audiostream_videostream

##### 请求类型：http

#####  请求参数：
请求head
header key | header value
---|---
m_request_id   | 请求唯一标识
m_service_id   | 客户产品标识
m_organization | 公司标识
请求body
```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```
#####  返回参数：
```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```

### <span id = "innerMergeResult.interafceDesc">内部合并uri：</span>

##### 请求接口uri：
/saas/v1/antifraud/merge_image_audio_result

##### 请求类型：http

#####  请求参数：

#####  返回参数：

### <span id = "innerFinishResult.interafceDesc">内部结束uri：</span>
##### 请求接口uri：
/saas/v1/antifraud/inner_finish_info

##### 请求类型：http

#####  请求参数：

```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```

#####  返回参数：
```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```

### <span id = "ReqAE.interafceDesc">请求AE：</span>

##### 请求类型：thirft

#####  请求参数：

```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```

#####  返回参数：
```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```

### <span id = "ReqAE.interafceDesc">请求截帧图片BE：</span>

##### 请求类型：thirft

#####  请求参数：

```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```

#####  返回参数：
```json
{
    "accessKey": "*********",
    "appId": "defaulttest",
    "eventId": "VIDEOSTREAM",
    "imgType": "POLITICS_VIOLENCE_BAN_PORN_MINOR_AD_SPAM_LOGO_STAR",
    "imgBusinessType": "SCREEN_SCENCE_QR_FACE_QUALITY_MINOR_LOGO_BEAUTY_FACECOMPARE",
}
```

















