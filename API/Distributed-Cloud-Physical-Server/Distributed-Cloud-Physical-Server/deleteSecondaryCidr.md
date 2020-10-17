# deleteSecondaryCidr


## Description
Delete secondary CIDR

## Request Method
DELETE

## Request Address
https://edcps.jdcloud-api.com/v1/regions/{regionId}/secondaryCidrs/{secondaryCidrId}

|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID, calling APIs (describeEdCPSRegions) to get regions supported by Distributed Cloud Physical Server|
|**secondaryCidrId**|String|True| |Secondary CIDR ID|

## Request Parameter
|Name|Type|Required or Not|Default Value|Description|
|---|---|---|---|---|
|**clientToken**|String|False| |Generated by the client to guarantee idempotence of request, and the length cannot exceed 36 characters;<br/><br>if multiple requests use the same clientToken, only the first request will be executed and the following requests will directly return the result of the first request<br/><br>|


## Return Parameter
|Name|Type|Description|
|---|---|---|
|**result**|[Result](deletesecondarycidr#result)| |
|**requestId**|String| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**success**|Boolean|Whether the deletion operation succeeded|

## Return Code
|Return Code|Description|
|---|---|
|**200**|OK|
|**400**|Bad request|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|