# This page talks about Validating quick-json parser usage - with JSON based validation configuration

# quick-json Validating parser Usage - with JSON based validation configuration #

quick json validating parser can be used whenever json has to be validated at every level to see if the format is expected or not. Keys/Values, Sub-Json, Array and its elements can be validated.

What/When/Where needs to be validated ? All this information is expected to be passed to the parser during initialization.

Below is the sample way of initializing and working with validating parser with JSON based validation configuration.

```
JsonParserFactory factory=JsonParserFactory.getInstance();

JSONParser parser=factory.newJsonParser(ValidationConfigType.JSON);
			
parser.initializeWithJson(json_based_validation_config_stream);
			
parser.setValidating(true);

//parse input json string with validating parser instance
Map jsonData=parser.parseJson(inputJsonString);

```

**E.g.1**

```
[{
"key":"value",
"key1":[234234.32,true ],
"key2":[arrayvalue,arrayvalue1,arrayvalue2]
},
{
"key":{
	subjsonkey:subjsonvalue
	}
},
"Rajesh Putta",
234234.23]
```

Below would be the JSON based validation configuration,

```
{
	"root":{
		"ROOT":{valueType:"JSON_ARRAY"},
		"0":{valueType:"JSON"},
		"1":{valueType:"JSON"},
		"2":{valueType:"STRING_LITERAL"},
		"3":{valueType:"DOUBLE"}
	},
	"root[0]":{
		"key1":{valueType:"JSON_ARRAY"},
		"key2":{valueType:"JSON_ARRAY"}
	},
	"root[1]":{
		"key":{valueType:"JSON"}
	},
	"root[0]/key1":{
		"0":{valueType:"DOUBLE"},
		"1":{valueType:"BOOLEAN"}
	},
	"root[0]/key2":{
		"default":{valueType:"STRING"}
	},
	"root[1]/key":{
		"default":{valueType:"STRING"}
	},
}
```