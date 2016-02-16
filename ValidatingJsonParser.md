# This page talks about Validating quick-json parser usage

# quick-json Validating parser Usage #

quick json validating parser can be used whenever json has to be validated at every level to see if the format is expected or not. Keys/Values, Sub-Json, Array and its elements can be validated.

What/When/Where needs to be validated ? All this information is expected to be passed to the parser during initialization.

Below is the sample way of initializing and working with validating parser.

```
 JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();

//initialize parser with the json validation configuration file stream
 parser.initialize(xml_stream));
			
//configure parser for validating
 parser.setValidating(true);

//parse input json string with validating parser instance
 Map jsonData=parser.parseJson(inputJsonString);

```


**E.g.1**

**Input JSON String**

```
sample={
"key":"value",
"key1":"value1",
"key2":234234234
}
```

Validation configuration for the above JSON string would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="sample">
		<KeyValues>
			<KeyValue name="default" valueType="STRING_LITERAL"/>
			<KeyValue name="key2" valueType="INTEGER"/>
		</KeyValues>
	</json-heirarchy>
	
</json-config>
```


**root** configuration is for validating the root level, this is mandatory to validate the root level is JSON/JSON\_ARRAY

**sample** configuration is for the key/value pairs under sample json string. As per the above configuration, **default** configuration is applicable for all the key/value pairs whenever there is no specific validation configured for keys. In this case **key2** requirement is to have separate validation configuration. so overriding the default one.

**Validation data types**

|JSON | validates for JSON presence|
|:----|:---------------------------|
|JSON\_ARRAY | validates for JSON\_ARRAY presence|
|STRING\_LITERAL | validates for double quoted string presence|
|STRING | Validates for simple string with alphanumeric data|
|INTEGER | Validates for number data, doesnt allow double type of values|
|DOUBLE | Validates for number data, allows double type of values|
|BOOLEAN | Validates for boolean value (true or false)|
|NULL | Validates for null         |



**E.g.2**

**Input JSON String**

```
sample={
"key":"value",
"key1":["value1",234234.32,adfasdf],
"key2":234234234
}
```

Validation Configuration for the above json string would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="sample">
		<KeyValues>
			<KeyValue name="default" valueType="STRING_LITERAL"/>
			<KeyValue name="key1" valueType="JSON_ARRAY"/>
			<KeyValue name="key2" valueType="INTEGER"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="sample/key1">
		<KeyValues>
			<KeyValue name="default" valueType="STRING_LITERAL"/>
			<KeyValue index="1" valueType="DOUBLE"/>
			<KeyValue index="2" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>	
	
</json-config>
```



**E.g.3**

```
sample={
"key":"value",
"key1":[{
	subjsonkey:subjsonvalue,
	subjsonkey1:subjsonvalue1
},234234.32,adfasdf],
"key2":234234234
}
```

Validation Configuration for the above JSON would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="sample">
		<KeyValues>
			<KeyValue name="default" valueType="STRING_LITERAL"/>
			<KeyValue name="key1" valueType="JSON_ARRAY"/>
			<KeyValue name="key2" valueType="INTEGER"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="sample/key1">
		<KeyValues>
			<KeyValue index="0" valueType="JSON"/>
			<KeyValue index="1" valueType="DOUBLE"/>
			<KeyValue index="2" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="sample/key1[0]">
		<KeyValues>
			<KeyValue name="default" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>	
</json-config>
```


**E.g.4**
```
{
"key":"value",
"key1":[{
	subjsonkey:subjsonvalue,
	subjsonkey1:subjsonvalue1
},234234.32,adfasdf],
"key2":234234234
}
```

In this case, JSON block is not assigned with any name. so default name would be root.Validation configuration for the above JSON would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON"/>
			<KeyValue name="key1" valueType="JSON_ARRAY"/>
			<KeyValue name="key2" valueType="INTEGER"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="root/key1">
		<KeyValues>
			<KeyValue index="0" valueType="JSON"/>
			<KeyValue index="1" valueType="DOUBLE"/>
			<KeyValue index="2" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root/key1[0]">
		<KeyValues>
			<KeyValue name="default" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>	
</json-config>
```

**E.g.5**

```
{
"key":"value",
"key1":[234234.32,adfasdf],
"key2":[arrayvalue,arrayvalue1,arrayvalue2]
}
```

Validation Configuration for the above JSON would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON"/>
			<KeyValue name="key1" valueType="JSON_ARRAY"/>
			<KeyValue name="key2" valueType="JSON_ARRAY"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="root/key1">
		<KeyValues>
			<KeyValue index="0" valueType="DOUBLE"/>
			<KeyValue index="1" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="root/key2">
		<KeyValues>
			<KeyValue index="0" valueType="STRING"/>
			<KeyValue index="1" valueType="STRING"/>
			<KeyValue index="2" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>	
	
</json-config>
```


**E.g.6**

```
[{
"key":"value",
"key1":[234234.32,adfasdf],
"key2":[arrayvalue,arrayvalue1,arrayvalue2]
},
"Rajesh Putta",
"Example String Value"]
```

Validation configuration for the above json would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON_ARRAY"/>
			<KeyValue index="0" valueType="JSON"/>
			<KeyValue index="1" valueType="STRING_LITERAL"/>
			<KeyValue index="2" valueType="STRING_LITERAL"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="root[0]">
		<KeyValues>
			<KeyValue index="key1" valueType="JSON_ARRAY"/>
			<KeyValue index="key2" valueType="JSON_ARRAY"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[0]/key1">
		<KeyValues>
			<KeyValue index="0" valueType="DOUBLE"/>
			<KeyValue index="1" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[0]/key2">
		<KeyValues>
			<KeyValue name="default" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>	
		
</json-config>
```



**E.g.7**

```
[{
"key":"value",
"key1":[234234.32,adfasdf],
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

Validation Configuration for the above json would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON_ARRAY"/>
			<KeyValue index="0" valueType="JSON"/>
			<KeyValue index="1" valueType="JSON"/>
			<KeyValue index="2" valueType="STRING_LITERAL"/>
			<KeyValue index="3" valueType="DOUBLE"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="root[0]">
		<KeyValues>
			<KeyValue index="key1" valueType="JSON_ARRAY"/>
			<KeyValue index="key2" valueType="JSON_ARRAY"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[1]">
		<KeyValues>
			<KeyValue index="key" valueType="JSON"/>
		</KeyValues>
	</json-heirarchy>	
	
	<json-heirarchy path="root[0]/key1">
		<KeyValues>
			<KeyValue index="0" valueType="DOUBLE"/>
			<KeyValue index="1" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[0]/key2">
		<KeyValues>
			<KeyValue name="default" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[1]/key">
		<KeyValues>
			<KeyValue name="default" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>	
</json-config>
```


**E.g.8**

boolean and null values presence and validation,

```
[{
"key":"value",
"key1":[234234.32,	true ],
"key2":[arrayvalue,arrayvalue1,arrayvalue2]
},
{
"key":{
	subjsonkey:subjsonvalue
	}
},
null,
234234.23]
```


Validation configuration for the above json would be,

```
<json-config>
	<json-heirarchy path="root">
		<KeyValues>
			<KeyValue name="ROOT" valueType="JSON_ARRAY"/>
			<KeyValue index="0" valueType="JSON"/>
			<KeyValue index="1" valueType="JSON"/>
			<KeyValue index="2" valueType="NULL"/>
			<KeyValue index="3" valueType="DOUBLE"/>
		</KeyValues>
	</json-heirarchy>

	<json-heirarchy path="root[0]">
		<KeyValues>
			<KeyValue index="key1" valueType="JSON_ARRAY"/>
			<KeyValue index="key2" valueType="JSON_ARRAY"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[1]">
		<KeyValues>
			<KeyValue index="key" valueType="JSON"/>
		</KeyValues>
	</json-heirarchy>	
	
	<json-heirarchy path="root[0]/key1">
		<KeyValues>
			<KeyValue index="0" valueType="DOUBLE"/>
			<KeyValue index="1" valueType="BOOLEAN"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[0]/key2">
		<KeyValues>
			<KeyValue name="default" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>
	
	<json-heirarchy path="root[1]/key">
		<KeyValues>
			<KeyValue name="default" valueType="STRING"/>
		</KeyValues>
	</json-heirarchy>	
</json-config>
```