# This page talks about quick-json non-validating parser usage

# quick-json Non-Validating parser Usage #

quick-json Non-Validating parser supports parsing of different formats of json strings which are compliant with JSON spec. Parser throws developer friendly exceptions in case of there is any syntax/semantic issues.

**E.g.**

```
 samplejson = {
   "key1": value1,
   "key_2": "value2",
   key3: value3,
   key4:234234234,
   key5:234234.233
}
```

Value can be looked up by just parsing the above JSON string using parsing API as follows,

```
 JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();
 Map jsonData=parser.parseJson(inputJsonString);

 //lookup the key 'key_2' under Json Block 'samplejson'
 String value=jsonData.get("samplejson").get("key_2");
```



```
{
"employees": [
{ "firstName":"Rajesh" , "lastName":"Putta" }, 
{ "firstName":"Rajesh" , "lastName":"P" }, 
{ "firstName":"first name" , "lastName":"last name" }
]
}
```


Value can be looked up by just parsing the above JSON string using parsing API as follows,

```
 JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();
 Map jsonData=parser.parseJson(inputJsonString);

Map rootJson=jsonData.get("root");
 List al=rootJson.get("employees");
 String fName=((Map)al.get(0)).get("firstName");
 String lName=((Map)al.get(0)).get("lastName");
```


**E.g.**

```
{
    "firstName": "John",
    "lastName": "Smith",
    "age": 25,
    "address": {
        "streetAddress": "21 2nd Street",
        "city": "New York",
        "state": "NY",
        "postalCode": 10021
    },
    "phoneNumber": [
        {
            "type": "home",
            "number": "212 555-1234"
        },
        {
            "type": "fax",
            "number": "646 555-4567"
        }
    ]
}
```

postalCode under address sub-json can be looked up by implementing as follows,

```
 JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();
 Map jsonData=parser.parseJson(inputJsonString);

 Map rootMap=jsonData.get("root");
 Map addressMap=rootMap.get("address");
 String pcode=addressMap.get("postalCode");
```