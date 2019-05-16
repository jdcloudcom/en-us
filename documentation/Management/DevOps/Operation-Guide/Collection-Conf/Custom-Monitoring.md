# Custom Metric Monitoring

Custom metric monitoring includes customized script and stand-alone machine program http output. In which,

Customized script: users can customize scripts and define data to be output according to the conventional format in the scripts

Stand-alone machine program http output: If you want to obtain output results of program, you can output results according to the conventional format specification, then obtain output data by means of submitting http request to the native machine.

## Operation Guide

**(1) Customize script monitoring**

​     Customized script implements specific monitoring contents and methods completely according to the monitoring script developed by users. The scripts shall meet the following requirements:

- Users need to designate the path of the script

- There is no limit to script language, as long as the monitoring machine can parse and execute it, e.g., shell, python, ruby, etc.

- Parser shall be designated in the script, and grant $account with read and execution permissions, so that it shall notice when scripting

- Monitoring system is not responsible for script distribution temporarily

- The exit status code must be 0 after script execution


​     The plug-in will catch the stdout output of scripts. The script output must conform to the specified specifications, in the format below:

```sh
[tags:k1:v1,k2:v2]

$ItemName:$ItemValue[,type:$type][,desc:%desc][,classify:%classify]
```

 In which, 
 tags: Please fill in the tag of the monitoring item, with the configuration in form of key:value. key can be named with English letters, numbers, "、_" (underlines), "." (period in English) and "-" (line-through in English).

$ItemName: The name of the monitoring item supports English letters, numbers, underlines (_) and periods in English (.) and cannot begin with a number. $ItemValue is recognized as the double type. However, "$itemValue" will be recognized as the string type and only the latest value can be stored by default

type: Please fill in the data type expected to be acquired by the user in the type field, and three types are supported by agent by default, including gauge, counter and counterQps,

- gauge: which do not process the value by default
- counter: newValue - lastValue
- counterQps: (newValue - lastValue) / cycle

desc: This field can be used for describing information of the monitoring item and will be sent to the alarm only

classify: Type of character string, used for indicating type of monitoring item produced  


```sh
   E.g. (without tag):

    \#!/bin/bash -

    echo "nginx_timeout:998.0,desc: Normal, classify:latency"
    echo "nginx_pv:10000,desc: Unreachable database by ping, classify:traffic"

  If acquisition configuration is exec_demo, the monitoring items generated by monitoring script above are:
    Name:exec_demo.nginx_timeout
    Value:998.0
    
    Name:exec_demo.nginx_pv
    Value:10000.0  
```

```sh
 E.g. (with tag)

   \#!/bin/bash -

    echo "tags:idc:majuqiao,version:1.0"
    echo "nginx_timeout:998.0,classify:latency"
    echo "nginx_pv:10000,classify:traffic"
    echo "tags:idc:majuqiao,version:2.0"
    echo "nginx_err:78"

  E.g., acquisition configuration is exec_demo, the monitoring items generated by monitoring script above are:
    Name:exec_demo.nginx_timeout
    Tags:idc:majuqiao,version:1.0
    Value:998.0
       
    Name:exec_demo.nginx_pv
    Tags:idc:majuqiao,version:1.0
    Value:10000.0  
    
    Name:exec_demo.nginx_err
    Tags:idc:majuqiao,version:2.0
    Value:78  
```

Format of generated monitoring indicators: $name.$outputMetric

**(2) Stand-alone machine http output monitoring script**

The purpose of stand-alone machine HTTP output monitoring is to submit http requests to the native machine, check returned output results. Users designate http port + http monitoring access path of current machine, wherein the output format shall meet the specified monitoring output format, then monitoring items will be acquired automatically.

```sh
Specific rules include:

[tags:k1:v1,k2:v2]

     $ItemName:$ItemValue[,type:$type]
```

 ​     Of which, $type is gauge, counter, counterQps by default

 ​     Of which, $ItemValue is double type, in the case of "$itemValue", it is string type and only can store latest value by default

 ​   Format of generated monitoring indicators: $name.$outputMetric

**Examples**

E.g., we have an alarm sending module — hawkeye-sender, which implements a http interface/stat, explore indicators of successful alarm number, failed alarm number, internal accumulated queue length, with listen port of 4322.
curl 127.0.0.1:4322/stat
Output Contents:

```
mail_cnt:12
mail_queue_size:1
sms_cnt:12
sms_queue_size:2
```

Monitoring configuration is shown as below:

```json
{
	"method": "http",
	"para": {
		"port": "4322",
		"target": "/stat"
	},
	"cycle": 10
}
```
