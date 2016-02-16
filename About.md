# quick-json Parser #

Quick JSON Parser is a simple and flexible parser for parsing input JSON string and return a Map of key/value pairs. This supports name association as well with every JSON block. This parser supports validating/non-validating versions. Validating parser version is a strict parser and it does parsing based upon pre-configured validation rules. Non-Validating parser verifies the standards of json while parsing and will not validate keys/values and will not apply any custom validations at all.

**e.g.**

```
 samplejson = {
   "key1": "value1",
   "key2": "value2",
   "key3": "value3"
}
```

Now Map generated out of the above mentioned JSON String will look like,

A map with one key as 'samplejson' and its value as another map of key/value pairs. i.e. it will be very easy for the developers to look up for a specific key within json hierarchy.


This parser supports input JSON string of following notation as well...

```
 samplejson = {
   key1: "value1",
   key2: "value2",
   key3: "value3"
}
```

**or**

```
 samplejson = {
   key1: value1,
   key2: value2,
   key3: value3
}
```

Value can be looked up by just parsing the above JSON string using parsing API as follows,

```
 JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();
 Map jsonData=parser.parse(inputJsonString);

 //lookup the key 'key2' under Json Block 'samplejson'
 String value=jsonData.get("samplejson").get("key2");
```

simple example of json string,

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

### quick-json features ###

# Compliant with JSON specification (RFC4627) <br><br>
# High-Performance JSON parser  <br><br>
# Supports Flexible/Configurable parsing approach  <br><br>
# Configurable validation of key/value pairs of any JSON Heirarchy  <br><br>
# Easy to use  # Very Less foot print <br><br>
# Raises developer friendly and easy to trace exceptions <br><br>
# Pluggable Custom Validation support - Keys/Values can be validated by configuring custom   validators as and when encountered <br><br>
# Validating and Non-Validating parser support <br><br>
# Support for two types of configuration (JSON/XML) for using quick-json validating parser <br><br>
# Require JDK 1.5 # No dependency on external libraries <br><br>
# Support for Json Generation through object serialization <br><br>
# Support for collection type selection during parsing process <br><br>


<h1>quick-json Non-Validating parser Usage</h1>

quick-json Non-Validating parser supports parsing of different formats of json strings which are compliant with JSON spec. Parser throws developer friendly exceptions in case of there is any syntax/semantic issues.<br>
<br>
<b>E.g.</b>

<pre><code> samplejson = {<br>
   "key1": value1,<br>
   "key_2": "value2",<br>
   key3: value3,<br>
   key4:234234234,<br>
   key5:234234.233<br>
}<br>
</code></pre>

Value can be looked up by just parsing the above JSON string using parsing API as follows,<br>
<br>
<pre><code> JsonParserFactory factory=JsonParserFactory.getInstance();<br>
 JsonParser parser=factory.newJsonParser();<br>
 Map jsonData=parser.parseJson(inputJsonString);<br>
<br>
 //lookup the key 'key_2' under Json Block 'samplejson'<br>
 String value=jsonData.get("samplejson").get("key_2");<br>
</code></pre>



<pre><code>{<br>
"employees": [<br>
{ "firstName":"Rajesh" , "lastName":"Putta" }, <br>
{ "firstName":"Rajesh" , "lastName":"P" }, <br>
{ "firstName":"first name" , "lastName":"last name" }<br>
]<br>
}<br>
</code></pre>


Value can be looked up by just parsing the above JSON string using parsing API as follows,<br>
<br>
<pre><code> JsonParserFactory factory=JsonParserFactory.getInstance();<br>
 JsonParser parser=factory.newJsonParser();<br>
 Map jsonData=parser.parseJson(inputJsonString);<br>
<br>
Map rootJson=jsonData.get("root");<br>
 List al=rootJson.get("employees");<br>
 String fName=((Map)al.get(0)).get("firstName");<br>
 String lName=((Map)al.get(0)).get("lastName");<br>
</code></pre>

<br><br>

<h1>quick-json Validating parser Usage</h1>

quick json validating parser can be used whenever json has to be validated at every level to see if the format is expected or not. Keys/Values, Sub-Json, Array and its elements can be validated.<br>
<br>
What/When/Where needs to be validated ? All this information is expected to be passed to the parser during initialization.<br>
<br>
Below is the sample way of initializing and working with validating parser.<br>
<br>
<pre><code> JsonParserFactory factory=JsonParserFactory.getInstance();<br>
 JsonParser parser=factory.newJsonParser();<br>
<br>
//initialize parser with the json validation configuration file stream<br>
 parser.initialize(xml_stream));<br>
			<br>
//configure parser for validating<br>
 parser.setValidating(true);<br>
<br>
//parse input json string with validating parser instance<br>
 Map jsonData=parser.parseJson(inputJsonString);<br>
<br>
</code></pre>


<b>E.g.1</b>

<b>Input JSON String</b>

<pre><code>sample={<br>
"key":"value",<br>
"key1":"value1",<br>
"key2":234234234<br>
}<br>
</code></pre>

Validation configuration for the above JSON string would be,<br>
<br>
<pre><code>&lt;json-config&gt;<br>
	&lt;json-heirarchy path="root"&gt;<br>
		&lt;KeyValues&gt;<br>
			&lt;KeyValue name="ROOT" valueType="JSON"/&gt;<br>
		&lt;/KeyValues&gt;<br>
	&lt;/json-heirarchy&gt;<br>
<br>
	&lt;json-heirarchy path="sample"&gt;<br>
		&lt;KeyValues&gt;<br>
			&lt;KeyValue name="default" valueType="STRING_LITERAL"/&gt;<br>
			&lt;KeyValue name="key2" valueType="INTEGER"/&gt;<br>
		&lt;/KeyValues&gt;<br>
	&lt;/json-heirarchy&gt;<br>
	<br>
&lt;/json-config&gt;<br>
</code></pre>


<b>root</b> configuration is for validating the root level, this is mandatory to validate the root level is JSON/JSON_ARRAY<br>
<br>
<b>sample</b> configuration is for the key/value pairs under sample json string. As per the above configuration, <b>default</b> configuration is applicable for all the key/value pairs whenever there is no specific validation configured for keys. In this case <b>key2</b> requirement is to have separate validation configuration. so overriding the default one.<br>
<br>
<b>Validation data types</b>

<table><thead><th>JSON </th><th> validates for JSON presence</th></thead><tbody>
<tr><td>JSON_ARRAY </td><td> validates for JSON_ARRAY presence</td></tr>
<tr><td>STRING_LITERAL </td><td> validates for double quoted string presence</td></tr>
<tr><td>STRING </td><td> Validates for simple string with alphanumeric data</td></tr>
<tr><td>INTEGER </td><td> Validates for number data, doesnt allow double type of values</td></tr>
<tr><td>DOUBLE </td><td> Validates for number data, allows double type of values</td></tr>
<tr><td>BOOLEAN </td><td> Validates for boolean value (true or false)</td></tr>
<tr><td>NULL </td><td> Validates for null         </td></tr></tbody></table>



<b>E.g.2</b>

<b>Input JSON String</b>

<pre><code>sample={<br>
"key":"value",<br>
"key1":["value1",234234.32,adfasdf],<br>
"key2":234234234<br>
}<br>
</code></pre>

Validation Configuration for the above json string would be,<br>
<br>
<pre><code>&lt;json-config&gt;<br>
	&lt;json-heirarchy path="root"&gt;<br>
		&lt;KeyValues&gt;<br>
			&lt;KeyValue name="ROOT" valueType="JSON"/&gt;<br>
		&lt;/KeyValues&gt;<br>
	&lt;/json-heirarchy&gt;<br>
<br>
	&lt;json-heirarchy path="sample"&gt;<br>
		&lt;KeyValues&gt;<br>
			&lt;KeyValue name="default" valueType="STRING_LITERAL"/&gt;<br>
			&lt;KeyValue name="key1" valueType="JSON_ARRAY"/&gt;<br>
			&lt;KeyValue name="key2" valueType="INTEGER"/&gt;<br>
		&lt;/KeyValues&gt;<br>
	&lt;/json-heirarchy&gt;<br>
	<br>
	&lt;json-heirarchy path="sample/key1"&gt;<br>
		&lt;KeyValues&gt;<br>
			&lt;KeyValue name="default" valueType="STRING_LITERAL"/&gt;<br>
			&lt;KeyValue index="1" valueType="DOUBLE"/&gt;<br>
			&lt;KeyValue index="2" valueType="STRING"/&gt;<br>
		&lt;/KeyValues&gt;<br>
	&lt;/json-heirarchy&gt;	<br>
	<br>
&lt;/json-config&gt;<br>
</code></pre>
<br><br>

<h1>quick-json Validating parser Usage - with JSON based validation configuration</h1>

quick json validating parser can be configure with JSON based validation configuration  whenever other json has to be validated at every level to see if the format is expected or not. Keys/Values, Sub-Json, Array and its elements can be validated.<br>
<br>
What/When/Where needs to be validated ? All this information is expected to be passed to the parser during initialization.<br>
<br>
Below is the sample way of initializing and working with validating parser with JSON based validation configuration.<br>
<br>
<pre><code>JsonParserFactory factory=JsonParserFactory.getInstance();<br>
<br>
JSONParser parser=factory.newJsonParser(ValidationConfigType.JSON);<br>
			<br>
parser.initializeWithJson(json_based_validation_config_stream);<br>
			<br>
parser.setValidating(true);<br>
<br>
//parse input json string with validating parser instance<br>
Map jsonData=parser.parseJson(inputJsonString);<br>
<br>
</code></pre>

<b>E.g.1</b>

<pre><code>[{<br>
"key":"value",<br>
"key1":[234234.32,true ],<br>
"key2":[arrayvalue,arrayvalue1,arrayvalue2]<br>
},<br>
{<br>
"key":{<br>
	subjsonkey:subjsonvalue<br>
	}<br>
},<br>
"Rajesh Putta",<br>
234234.23]<br>
</code></pre>

Below would be the JSON based validation configuration,<br>
<br>
<pre><code>{<br>
	"root":{<br>
		"ROOT":{valueType:"JSON_ARRAY"},<br>
		"0":{valueType:"JSON"},<br>
		"1":{valueType:"JSON"},<br>
		"2":{valueType:"STRING_LITERAL"},<br>
		"3":{valueType:"DOUBLE"}<br>
	},<br>
	"root[0]":{<br>
		"key1":{valueType:"JSON_ARRAY"},<br>
		"key2":{valueType:"JSON_ARRAY"}<br>
	},<br>
	"root[1]":{<br>
		"key":{valueType:"JSON"}<br>
	},<br>
	"root[0]/key1":{<br>
		"0":{valueType:"DOUBLE"},<br>
		"1":{valueType:"BOOLEAN"}<br>
	},<br>
	"root[0]/key2":{<br>
		"default":{valueType:"STRING"}<br>
	},<br>
	"root[1]/key":{<br>
		"default":{valueType:"STRING"}<br>
	},<br>
}<br>
</code></pre>



<br><br>
<h1>Json Generator Usage</h1>

JSONGenerator helps in serializing the java objects to JSON format.<br>
<br>
- Supports serialization of Classes, Arrays, Map, List, Set, Properties, String, Date, Integer, Float, Double, Boolean, etc types of data<br>
<br>
- Strictly adheres to the JSON spec during serialization process<br>
<br>
<b>E.g.</b>

Here is the example data set hierarchy to be serialized to JSON format,<br>
<br>
<pre><code>		Map data=new HashMap();<br>
		<br>
		Properties prop=new Properties();<br>
		<br>
		prop.setProperty("1", "1");<br>
		prop.setProperty("2", "2");<br>
		prop.setProperty("3", "3");<br>
		<br>
		data.put("name", "Rajesh Putta");<br>
		data.put("age", 28);<br>
		data.put("city", new StringBuilder("hyderabad"));<br>
		data.put("subdata", prop);<br>
		data.put("array", new int[]{234,555,777,888});<br>
		data.put("chararray", new char[]{'a','b','c'});<br>
		data.put("doublearray", new double[]{234,555,777,888});<br>
		data.put("floatarray", new byte[]{1,2,34,35});<br>
<br>
		Map submap=new HashMap();<br>
		submap.put(1, 10);<br>
		submap.put(2, 20);		<br>
		<br>
		TestPojo tp=new TestPojo();<br>
		<br>
		tp.setAge(28);<br>
		tp.setName("Rajesh");<br>
		tp.setSs(3223.33);<br>
		tp.setData(submap);		<br>
		<br>
		Set set=new HashSet();<br>
		set.add(234);<br>
		set.add(2343);<br>
		set.add("asdfasfd");<br>
		set.add(tp);<br>
		<br>
<br>
		data.put("set-pojo", set);<br>
		<br>
<br>
		data.put("objectarray", new Object[]{submap,set,submap,tp});<br>
</code></pre>


Here is the implementation for serializing the above data set<br>
<br>
<pre><code>		JsonGeneratorFactory factory=JsonGeneratorFactory.getInstance();<br>
		JSONGenerator generator=factory.newJsonGenerator();<br>
		String json=generator.generateJson(data);<br>
</code></pre>

Here is the serialized data object,<br>
<br>
<pre><code>[{"age":28,"doublearray":[234.0,555.0,777.0,888.0],"floatarray":[1,2,34,35],"set-pojo":["asdfasfd",{"name":"Rajesh","age":28,"ss":3223.33,"data":{"2":20,"1":10},},2343,234],"subdata":{"3":"3","2":"2","1":"1"},"objectarray":[{"2":20,"1":10},{"2":20,"1":10},{"name":"Rajesh","age":28,"ss":3223.33,"data":{"2":20,"1":10},}],"name":"Rajesh Putta","chararray":[a,b,c],"city":"hyderabad","array":[234,555,777,888]}]<br>
</code></pre>