# createLiveDomainPrefecthTask


## Description
Create live prewarm task

## Request Method
POST

## Request Address
https://cdn.jdcloud-api.com/v1/task:createLivePrefetchTask


## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**urlList**|String[]|True| |Prewarm URL|
|**prefetchTime**|Integer|True| |Prewarm Duration|
|**action**|String|True| |Operation type only can be one of [start,stop]|


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
