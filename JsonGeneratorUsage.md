# This page talks about the usage of Json Generator to serialize java objects to json format

# Json Generator Usage #

JSONGenerator helps in serializing the java objects to JSON format.

- Supports serialization of Classes, Arrays, Map, List, Set, Properties, String, Date, Integer, Float, Double, Boolean, etc types of data

- Strictly adheres to the JSON spec during serialization process

**E.g.**

Here is the example data set hierarchy to be serialized to JSON format,

```
		Map data=new HashMap();
		
		Properties prop=new Properties();
		
		prop.setProperty("1", "1");
		prop.setProperty("2", "2");
		prop.setProperty("3", "3");
		
		data.put("name", "Rajesh Putta");
		data.put("age", 28);
		data.put("city", new StringBuilder("hyderabad"));
		data.put("subdata", prop);
		data.put("array", new int[]{234,555,777,888});
		data.put("chararray", new char[]{'a','b','c'});
		data.put("doublearray", new double[]{234,555,777,888});
		data.put("floatarray", new byte[]{1,2,34,35});

		Map submap=new HashMap();
		submap.put(1, 10);
		submap.put(2, 20);		
		
		TestPojo tp=new TestPojo();
		
		tp.setAge(28);
		tp.setName("Rajesh");
		tp.setSs(3223.33);
		tp.setData(submap);		
		
		Set set=new HashSet();
		set.add(234);
		set.add(2343);
		set.add("asdfasfd");
		set.add(tp);
		

		data.put("set-pojo", set);
		

		data.put("objectarray", new Object[]{submap,set,submap,tp});
```


Here is the implementation for serializing the above data set

```
		JsonGeneratorFactory factory=JsonGeneratorFactory.getInstance();
		JSONGenerator generator=factory.newJsonGenerator();
		String json=generator.generateJson(data);
```

Here is the serialized data object,

```
[{"age":28,"doublearray":[234.0,555.0,777.0,888.0],"floatarray":[1,2,34,35],"set-pojo":["asdfasfd",{"name":"Rajesh","age":28,"ss":3223.33,"data":{"2":20,"1":10},},2343,234],"subdata":{"3":"3","2":"2","1":"1"},"objectarray":[{"2":20,"1":10},{"2":20,"1":10},{"name":"Rajesh","age":28,"ss":3223.33,"data":{"2":20,"1":10},}],"name":"Rajesh Putta","chararray":[a,b,c],"city":"hyderabad","array":[234,555,777,888]}]
```