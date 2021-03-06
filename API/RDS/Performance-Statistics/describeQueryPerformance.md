# describeQueryPerformance


## Description
Obtain the information of performance statistics of SQL execution, such as slow SQL, etc. based on user-defined query conditions. Based on this information, users can find and optimize performance bottlenecks related to SQL execution. <br>- Support SQL Server Only

## Request method
POST

## Request address
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/performance:describeQueryPerformance

|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**regionId**|String|True| |Region code, with range detailed in [Regions and Availability Zone Comparison Table](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS instance ID, which uniquely identifies an RDS instance|

## Request parameter
|Name|Type|Required or not|Default value|Description|
|---|---|---|---|---|
|**queryType**|String|True| |Query Type, Return Results of Fields From High to Low for Different Query Types. <br>support the following types: <br>ExecutionCount: Number of executions<br>LastRows: Number of rows returned last time<br>ElapsedTime: Average execution time<br>CPUTime: Average CPU time<br>LogicalReads: Average logical read<br>LogicalWrites: Average logical write<br>PhysicalReads: Average physical read<br>|
|**threshold**|Integer|False| |Return only records whose query condition is larger than or equal to threshold and the default is 0|
|**pageNumber**|Integer|False| |The default of the number of the data displayed is 1 and the value range is [-1,1000]. When pageNumber is -1, return all data page numbers; when the total number of pages is exceeded, display the last page.|
|**pageSize**|Integer|False| |The default of the number of data displayed per page is 50 and the value range is [1,100]. It can only be a multiple of 10 used for the API to query the list.|


## Response parameter
|Name|Type|Description|
|---|---|---|
|**result**|[Result](describequeryperformance#result)| |

### <div id="result">Result</div>
|Name|Type|Description|
|---|---|---|
|**queryPerformanceResult**|[QueryPerformanceResult[]](describequeryperformance#queryperformanceresult)|Search Performance Statistics Result Set|
|**totalCount**|Integer|Total Number of Records|
|**pageNumber**|Integer|The Page Number of the Current Data|
|**pageSize**|Integer|The Number of Data Displayed Per Page|
### <div id="queryperformanceresult">QueryPerformanceResult</div>
|Name|Type|Description|
|---|---|---|
|**sql**|String|Sql Statement|
|**lastExecutionTime**|String|Last execution time, format: YYYY-MM-DD hh:mm:ss|
|**elapsedTime**|Integer|Average Execution Time, Unit: Milliseconds (ms)|
|**executionCount**|Integer|Number of Executions|
|**workerTime**|Integer|Average CPU Usage Time, Unit: Milliseconds (ms)|
|**logicalReads**|Integer|Average Logical Reads|
|**logicalWrites**|Integer|Average Logical Writes|
|**physicalReads**|Integer|Average Physical Reads|
|**lastRows**|Integer|Number of Records in Last Return|

## Response code
|Return code|Description|
|---|---|
|**200**|OK|

## Request Example
POST
```
public void testDescribeQueryPerformance() {
    DescribeQueryPerformanceRequest request = new DescribeQueryPerformanceRequest();
    request.setRegionId("cn-north-1");
    request.setInstanceId("sqlserver-83uqv7avy4");
    request.setQueryType("LogicalReads");
    request.setPageSize(10);
    request.setPageNumber(1);
    DescribeQueryPerformanceResponse response = rdsClient.describeQueryPerformance(request);
    System.out.println(new Gson().toJson(response));
}

```

## Return Example
```
{
    "requestId": "bpaohu1t9up4ide0a9g4pwcoinp86hwn", 
    "result": {
        "pageNumber": 1, 
        "pageSize": 10, 
        "queryPerformanceResult": [
            {
                "elapsedTime": 1, 
                "executionCount": 7, 
                "lastExecutionTime": "2020-01-08 14:35:51.440", 
                "lastRows": 3, 
                "logicalReads": 43, 
                "logicalWrites": 0, 
                "physicalReads": 0, 
                "sql": "select 1", 
                "workerTime": 1
            }
        ], 
        "totalCount": 1
    }
}
```
