# deleteHttpHeader


## Description
Delete httpHeader

## Request Method
PUT

## Request Address
https://cdn.jdcloud-api.com/v1/domain/{domain}/httpHeader

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**domain**|String|True| |User Domain|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**headerType**|String|True| |header type [resp,req]|
|**headerName**|String|True| |header name|


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|Object| |
|**requestId**|String| |


## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
