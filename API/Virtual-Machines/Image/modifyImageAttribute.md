# modifyImageAttribute


## Description
Modify the image information, including name and description; Only allow your personal private image to be operated.


## Request method
POST

## Request address
https://vm.jdcloud-api.com/v1/regions/{regionId}/images/{imageId}:modifyImageAttribute

|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**imageId**|String|True| |Image ID|

## Request parameter
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**name**|String|False| |Name, <a href="http://docs.jdcloud.com/virtual-machines/api/general_parameters">Refer to the public parameter specification </a>.|
|**description**|String|False| |Description, <a href="http://docs.jdcloud.com/virtual-machines/api/general_parameters">Refer to the public parameter specification</a>.|


## Response parameter
None


## Response code
|Return code|Description|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|
