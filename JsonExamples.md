# This page is to list out sample json examples

**E.g.1**

```
JSON:

{
    "glossary": {
        "title": "example glossary",
		"GlossDiv": {
            "title": "S",
			"GlossList": {
                "GlossEntry": {
                    "ID": "SGML",
					"SortAs": "SGML",
					"GlossTerm": "Standard Generalized Markup Language",
					"Acronym": "SGML",
					"Abbrev": "ISO 8879:1986",
					"GlossDef": {
                        "para": "A meta-markup language, used to create markup languages such as DocBook.",
						"GlossSeeAlso": ["GML", "XML"]
                    },
					"GlossSee": "markup"
                }
            }
        }
    }
}
```

<br><b>The same text expressed as XML:</b><br>

<pre><code>&lt;!DOCTYPE glossary PUBLIC "-//OASIS//DTD DocBook V3.1//EN"&gt;<br>
 &lt;glossary&gt;&lt;title&gt;example glossary&lt;/title&gt;<br>
  &lt;GlossDiv&gt;&lt;title&gt;S&lt;/title&gt;<br>
   &lt;GlossList&gt;<br>
    &lt;GlossEntry ID="SGML" SortAs="SGML"&gt;<br>
     &lt;GlossTerm&gt;Standard Generalized Markup Language&lt;/GlossTerm&gt;<br>
     &lt;Acronym&gt;SGML&lt;/Acronym&gt;<br>
     &lt;Abbrev&gt;ISO 8879:1986&lt;/Abbrev&gt;<br>
     &lt;GlossDef&gt;<br>
      &lt;para&gt;A meta-markup language, used to create markup<br>
languages such as DocBook.&lt;/para&gt;<br>
      &lt;GlossSeeAlso OtherTerm="GML"&gt;<br>
      &lt;GlossSeeAlso OtherTerm="XML"&gt;<br>
     &lt;/GlossDef&gt;<br>
     &lt;GlossSee OtherTerm="markup"&gt;<br>
    &lt;/GlossEntry&gt;<br>
   &lt;/GlossList&gt;<br>
  &lt;/GlossDiv&gt;<br>
 &lt;/glossary&gt;<br>
</code></pre>


<b>E.g.2</b>

<pre><code>JSON:<br>
<br>
{"menu": {<br>
  "id": "file",<br>
  "value": "File",<br>
  "popup": {<br>
    "menuitem": [<br>
      {"value": "New", "onclick": "CreateNewDoc()"},<br>
      {"value": "Open", "onclick": "OpenDoc()"},<br>
      {"value": "Close", "onclick": "CloseDoc()"}<br>
    ]<br>
  }<br>
}}<br>
</code></pre>

<br><b>The same text expressed as XML:</b><br>
<pre><code>&lt;menu id="file" value="File"&gt;<br>
  &lt;popup&gt;<br>
    &lt;menuitem value="New" onclick="CreateNewDoc()" /&gt;<br>
    &lt;menuitem value="Open" onclick="OpenDoc()" /&gt;<br>
    &lt;menuitem value="Close" onclick="CloseDoc()" /&gt;<br>
  &lt;/popup&gt;<br>
&lt;/menu&gt;<br>
</code></pre>


<b>E.g.3</b>

<pre><code>JSON:<br>
<br>
{"widget": {<br>
    "debug": "on",<br>
    "window": {<br>
        "title": "Sample Konfabulator Widget",<br>
        "name": "main_window",<br>
        "width": 500,<br>
        "height": 500<br>
    },<br>
    "image": { <br>
        "src": "Images/Sun.png",<br>
        "name": "sun1",<br>
        "hOffset": 250,<br>
        "vOffset": 250,<br>
        "alignment": "center"<br>
    },<br>
    "text": {<br>
        "data": "Click Here",<br>
        "size": 36,<br>
        "style": "bold",<br>
        "name": "text1",<br>
        "hOffset": 250,<br>
        "vOffset": 100,<br>
        "alignment": "center",<br>
        "onMouseUp": "sun1.opacity = (sun1.opacity / 100) * 90;"<br>
    }<br>
}}   <br>
</code></pre>
<br><b>The same text expressed as XML:</b><br>
<pre><code>&lt;widget&gt;<br>
    &lt;debug&gt;on&lt;/debug&gt;<br>
    &lt;window title="Sample Konfabulator Widget"&gt;<br>
        &lt;name&gt;main_window&lt;/name&gt;<br>
        &lt;width&gt;500&lt;/width&gt;<br>
        &lt;height&gt;500&lt;/height&gt;<br>
    &lt;/window&gt;<br>
    &lt;image src="Images/Sun.png" name="sun1"&gt;<br>
        &lt;hOffset&gt;250&lt;/hOffset&gt;<br>
        &lt;vOffset&gt;250&lt;/vOffset&gt;<br>
        &lt;alignment&gt;center&lt;/alignment&gt;<br>
    &lt;/image&gt;<br>
    &lt;text data="Click Here" size="36" style="bold"&gt;<br>
        &lt;name&gt;text1&lt;/name&gt;<br>
        &lt;hOffset&gt;250&lt;/hOffset&gt;<br>
        &lt;vOffset&gt;100&lt;/vOffset&gt;<br>
        &lt;alignment&gt;center&lt;/alignment&gt;<br>
        &lt;onMouseUp&gt;<br>
            sun1.opacity = (sun1.opacity / 100) * 90;<br>
        &lt;/onMouseUp&gt;<br>
    &lt;/text&gt;<br>
&lt;/widget&gt;<br>
<br>
</code></pre>


<b>E.g.4</b>

<pre><code>JSON:<br>
<br>
{"web-app": {<br>
  "servlet": [   <br>
    {<br>
      "servlet-name": "cofaxCDS",<br>
      "servlet-class": "org.cofax.cds.CDSServlet",<br>
      "init-param": {<br>
        "configGlossary:installationAt": "Philadelphia, PA",<br>
        "configGlossary:adminEmail": "ksm@pobox.com",<br>
        "configGlossary:poweredBy": "Cofax",<br>
        "configGlossary:poweredByIcon": "/images/cofax.gif",<br>
        "configGlossary:staticPath": "/content/static",<br>
        "templateProcessorClass": "org.cofax.WysiwygTemplate",<br>
        "templateLoaderClass": "org.cofax.FilesTemplateLoader",<br>
        "templatePath": "templates",<br>
        "templateOverridePath": "",<br>
        "defaultListTemplate": "listTemplate.htm",<br>
        "defaultFileTemplate": "articleTemplate.htm",<br>
        "useJSP": false,<br>
        "jspListTemplate": "listTemplate.jsp",<br>
        "jspFileTemplate": "articleTemplate.jsp",<br>
        "cachePackageTagsTrack": 200,<br>
        "cachePackageTagsStore": 200,<br>
        "cachePackageTagsRefresh": 60,<br>
        "cacheTemplatesTrack": 100,<br>
        "cacheTemplatesStore": 50,<br>
        "cacheTemplatesRefresh": 15,<br>
        "cachePagesTrack": 200,<br>
        "cachePagesStore": 100,<br>
        "cachePagesRefresh": 10,<br>
        "cachePagesDirtyRead": 10,<br>
        "searchEngineListTemplate": "forSearchEnginesList.htm",<br>
        "searchEngineFileTemplate": "forSearchEngines.htm",<br>
        "searchEngineRobotsDb": "WEB-INF/robots.db",<br>
        "useDataStore": true,<br>
        "dataStoreClass": "org.cofax.SqlDataStore",<br>
        "redirectionClass": "org.cofax.SqlRedirection",<br>
        "dataStoreName": "cofax",<br>
        "dataStoreDriver": "com.microsoft.jdbc.sqlserver.SQLServerDriver",<br>
        "dataStoreUrl": "jdbc:microsoft:sqlserver://LOCALHOST:1433;DatabaseName=goon",<br>
        "dataStoreUser": "sa",<br>
        "dataStorePassword": "dataStoreTestQuery",<br>
        "dataStoreTestQuery": "SET NOCOUNT ON;select test='test';",<br>
        "dataStoreLogFile": "/usr/local/tomcat/logs/datastore.log",<br>
        "dataStoreInitConns": 10,<br>
        "dataStoreMaxConns": 100,<br>
        "dataStoreConnUsageLimit": 100,<br>
        "dataStoreLogLevel": "debug",<br>
        "maxUrlLength": 500}},<br>
    {<br>
      "servlet-name": "cofaxEmail",<br>
      "servlet-class": "org.cofax.cds.EmailServlet",<br>
      "init-param": {<br>
      "mailHost": "mail1",<br>
      "mailHostOverride": "mail2"}},<br>
    {<br>
      "servlet-name": "cofaxAdmin",<br>
      "servlet-class": "org.cofax.cds.AdminServlet"},<br>
 <br>
    {<br>
      "servlet-name": "fileServlet",<br>
      "servlet-class": "org.cofax.cds.FileServlet"},<br>
    {<br>
      "servlet-name": "cofaxTools",<br>
      "servlet-class": "org.cofax.cms.CofaxToolsServlet",<br>
      "init-param": {<br>
        "templatePath": "toolstemplates/",<br>
        "log": 1,<br>
        "logLocation": "/usr/local/tomcat/logs/CofaxTools.log",<br>
        "logMaxSize": "",<br>
        "dataLog": 1,<br>
        "dataLogLocation": "/usr/local/tomcat/logs/dataLog.log",<br>
        "dataLogMaxSize": "",<br>
        "removePageCache": "/content/admin/remove?cache=pages&amp;id=",<br>
        "removeTemplateCache": "/content/admin/remove?cache=templates&amp;id=",<br>
        "fileTransferFolder": "/usr/local/tomcat/webapps/content/fileTransferFolder",<br>
        "lookInContext": 1,<br>
        "adminGroupID": 4,<br>
        "betaServer": true}}],<br>
  "servlet-mapping": {<br>
    "cofaxCDS": "/",<br>
    "cofaxEmail": "/cofaxutil/aemail/*",<br>
    "cofaxAdmin": "/admin/*",<br>
    "fileServlet": "/static/*",<br>
    "cofaxTools": "/tools/*"},<br>
 <br>
  "taglib": {<br>
    "taglib-uri": "cofax.tld",<br>
    "taglib-location": "/WEB-INF/tlds/cofax.tld"}}}<br>
</code></pre>

<br><b>The same file expressed as XML:</b><br>

<pre><code>&lt;?xml version="1.0" encoding="ISO-8859-1"?&gt;<br>
<br>
&lt;!DOCTYPE web-app<br>
    PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.2//EN"<br>
    "http://java.sun.com/j2ee/dtds/web-app_2.2.dtd"&gt;<br>
&lt;web-app&gt;<br>
    &lt;servlet&gt;<br>
        &lt;servlet-name&gt;<br>
            cofaxCDS<br>
        &lt;/servlet-name&gt;<br>
        &lt;servlet-class&gt;<br>
            org.cofax.cds.CDSServlet<br>
        &lt;/servlet-class&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;configGlossary:installationAt&lt;/param-name&gt;<br>
      &lt;param-value&gt;Philadelphia, PA&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;configGlossary:adminEmail&lt;/param-name&gt;<br>
      &lt;param-value&gt;ksm@pobox.com&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;configGlossary:poweredBy&lt;/param-name&gt;<br>
      &lt;param-value&gt;Cofax&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;configGlossary:poweredByIcon&lt;/param-name&gt;<br>
      &lt;param-value&gt;/images/cofax.gif&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;configGlossary:staticPath&lt;/param-name&gt;<br>
      &lt;param-value&gt;/content/static&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
     &lt;init-param&gt;<br>
          &lt;param-name&gt;templateProcessorClass&lt;/param-name&gt;<br>
      &lt;param-value&gt;org.cofax.WysiwygTemplate&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;templateLoaderClass&lt;/param-name&gt;<br>
      &lt;param-value&gt;org.cofax.FilesTemplateLoader&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;templatePath&lt;/param-name&gt;<br>
      &lt;param-value&gt;templates&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;templateOverridePath&lt;/param-name&gt;<br>
      &lt;param-value&gt;&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
     &lt;init-param&gt;<br>
          &lt;param-name&gt;defaultListTemplate&lt;/param-name&gt;<br>
      &lt;param-value&gt;listTemplate.htm&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
       &lt;init-param&gt;<br>
          &lt;param-name&gt;defaultFileTemplate&lt;/param-name&gt;<br>
      &lt;param-value&gt;articleTemplate.htm&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
       &lt;init-param&gt;<br>
          &lt;param-name&gt;useJSP&lt;/param-name&gt;<br>
      &lt;param-value&gt;false&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;jspListTemplate&lt;/param-name&gt;<br>
      &lt;param-value&gt;listTemplate.jsp&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
       &lt;init-param&gt;<br>
          &lt;param-name&gt;jspFileTemplate&lt;/param-name&gt;<br>
      &lt;param-value&gt;articleTemplate.jsp&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
     &lt;init-param&gt;<br>
          &lt;param-name&gt;cachePackageTagsTrack&lt;/param-name&gt;<br>
      &lt;param-value&gt;200&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cachePackageTagsStore&lt;/param-name&gt;<br>
      &lt;param-value&gt;200&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cachePackageTagsRefresh&lt;/param-name&gt;<br>
      &lt;param-value&gt;60&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
     &lt;init-param&gt;<br>
          &lt;param-name&gt;cacheTemplatesTrack&lt;/param-name&gt;<br>
      &lt;param-value&gt;100&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cacheTemplatesStore&lt;/param-name&gt;<br>
      &lt;param-value&gt;50&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cacheTemplatesRefresh&lt;/param-name&gt;<br>
      &lt;param-value&gt;15&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cachePagesTrack&lt;/param-name&gt;<br>
      &lt;param-value&gt;200&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cachePagesStore&lt;/param-name&gt;<br>
      &lt;param-value&gt;100&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cachePagesRefresh&lt;/param-name&gt;<br>
      &lt;param-value&gt;10&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;cachePagesDirtyRead&lt;/param-name&gt;<br>
      &lt;param-value&gt;10&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
     &lt;init-param&gt;<br>
          &lt;param-name&gt;searchEngineListTemplate&lt;/param-name&gt;<br>
      &lt;param-value&gt;forSearchEnginesList.htm&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
       &lt;init-param&gt;<br>
          &lt;param-name&gt;searchEngineFileTemplate&lt;/param-name&gt;<br>
      &lt;param-value&gt;forSearchEngines.htm&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
       &lt;init-param&gt;<br>
          &lt;param-name&gt;searchEngineRobotsDb&lt;/param-name&gt;<br>
      &lt;param-value&gt;WEB-INF/robots.db&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;init-param&gt;<br>
          &lt;param-name&gt;useDataStore&lt;/param-name&gt;<br>
      &lt;param-value&gt;true&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
     &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreClass&lt;/param-name&gt;<br>
      &lt;param-value&gt;org.cofax.SqlDataStore&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;redirectionClass&lt;/param-name&gt;<br>
      &lt;param-value&gt;org.cofax.SqlRedirection&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreName&lt;/param-name&gt;<br>
      &lt;param-value&gt;cofax&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreDriver&lt;/param-name&gt;<br>
      &lt;param-value&gt;com.microsoft.jdbc.sqlserver.SQLServerDriver&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreUrl&lt;/param-name&gt;<br>
      &lt;param-value&gt;jdbc:microsoft:sqlserver://LOCALHOST:1433;DatabaseName=goon&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreUser&lt;/param-name&gt;<br>
      &lt;param-value&gt;sa&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStorePassword&lt;/param-name&gt;<br>
      &lt;param-value&gt;&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreTestQuery&lt;/param-name&gt;<br>
      &lt;param-value&gt;SET NOCOUNT ON;select test='test';&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreLogFile&lt;/param-name&gt;<br>
      &lt;param-value&gt;/usr/local/tomcat/logs/datastore.log&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreInitConns&lt;/param-name&gt;<br>
      &lt;param-value&gt;10&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreMaxConns&lt;/param-name&gt;<br>
      &lt;param-value&gt;100&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreConnUsageLimit&lt;/param-name&gt;<br>
      &lt;param-value&gt;100&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
 &lt;init-param&gt;<br>
          &lt;param-name&gt;dataStoreLogLevel&lt;/param-name&gt;<br>
      &lt;param-value&gt;debug&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
     &lt;init-param&gt;<br>
          &lt;param-name&gt;maxUrlLength&lt;/param-name&gt;<br>
      &lt;param-value&gt;500&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;/servlet&gt;<br>
<br>
     &lt;servlet&gt;<br>
        &lt;servlet-name&gt;<br>
            cofaxEmail<br>
        &lt;/servlet-name&gt;<br>
        &lt;servlet-class&gt;<br>
            org.cofax.cds.EmailServlet<br>
        &lt;/servlet-class&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;mailHost&lt;/param-name&gt;<br>
      &lt;param-value&gt;mail1&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;mailHostOverride&lt;/param-name&gt;<br>
      &lt;param-value&gt;mail2&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
    &lt;/servlet&gt;<br>
<br>
    &lt;servlet&gt;<br>
        &lt;servlet-name&gt;<br>
            cofaxAdmin<br>
        &lt;/servlet-name&gt;<br>
        &lt;servlet-class&gt;<br>
            org.cofax.cds.AdminServlet<br>
        &lt;/servlet-class&gt;<br>
    &lt;/servlet&gt;<br>
<br>
    &lt;servlet&gt;<br>
         &lt;servlet-name&gt;<br>
             fileServlet<br>
         &lt;/servlet-name&gt;<br>
         &lt;servlet-class&gt;<br>
             org.cofax.cds.FileServlet<br>
         &lt;/servlet-class&gt;<br>
    &lt;/servlet&gt;<br>
<br>
   &lt;servlet&gt;<br>
        &lt;servlet-name&gt;<br>
            cofaxTools<br>
        &lt;/servlet-name&gt;<br>
        &lt;servlet-class&gt;<br>
            org.cofax.cms.CofaxToolsServlet<br>
        &lt;/servlet-class&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;templatePath&lt;/param-name&gt;<br>
          &lt;param-value&gt;toolstemplates/&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;log&lt;/param-name&gt;<br>
          &lt;param-value&gt;1&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;logLocation&lt;/param-name&gt;<br>
          &lt;param-value&gt;/usr/local/tomcat/logs/CofaxTools.log&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;logMaxSize&lt;/param-name&gt;<br>
          &lt;param-value&gt;&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataLog&lt;/param-name&gt;<br>
          &lt;param-value&gt;1&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataLogLocation&lt;/param-name&gt;<br>
          &lt;param-value&gt;/usr/local/tomcat/logs/dataLog.log&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;dataLogMaxSize&lt;/param-name&gt;<br>
          &lt;param-value&gt;&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;removePageCache&lt;/param-name&gt;<br>
          &lt;param-value&gt;/content/admin/remove?cache=pages&amp;id=&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;removeTemplateCache&lt;/param-name&gt;<br>
          &lt;param-value&gt;/content/admin/remove?cache=templates&amp;id=&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;fileTransferFolder&lt;/param-name&gt;<br>
          &lt;param-value&gt;/usr/local/tomcat/webapps/content/fileTransferFolder&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
         &lt;init-param&gt;<br>
          &lt;param-name&gt;lookInContext&lt;/param-name&gt;<br>
          &lt;param-value&gt;1&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;adminGroupID&lt;/param-name&gt;<br>
          &lt;param-value&gt;4&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
        &lt;init-param&gt;<br>
          &lt;param-name&gt;betaServer&lt;/param-name&gt;<br>
          &lt;param-value&gt;true&lt;/param-value&gt;<br>
        &lt;/init-param&gt;<br>
<br>
    &lt;/servlet&gt;<br>
<br>
    &lt;servlet-mapping&gt;<br>
    &lt;servlet-name&gt;<br>
    cofaxCDS<br>
    &lt;/servlet-name&gt;<br>
    &lt;url-pattern&gt;<br>
    /<br>
    &lt;/url-pattern&gt;<br>
    &lt;/servlet-mapping&gt;<br>
<br>
    &lt;servlet-mapping&gt;<br>
    &lt;servlet-name&gt;<br>
    cofaxEmail<br>
    &lt;/servlet-name&gt;<br>
    &lt;url-pattern&gt;<br>
    /cofaxutil/aemail/*<br>
    &lt;/url-pattern&gt;<br>
    &lt;/servlet-mapping&gt;<br>
<br>
    &lt;servlet-mapping&gt;<br>
        &lt;servlet-name&gt;<br>
        cofaxAdmin<br>
        &lt;/servlet-name&gt;<br>
        &lt;url-pattern&gt;<br>
        /admin/*<br>
        &lt;/url-pattern&gt;<br>
    &lt;/servlet-mapping&gt;<br>
<br>
    &lt;servlet-mapping&gt;<br>
         &lt;servlet-name&gt;<br>
         fileServlet<br>
         &lt;/servlet-name&gt;<br>
         &lt;url-pattern&gt;<br>
         /static/*<br>
         &lt;/url-pattern&gt;<br>
     &lt;/servlet-mapping&gt;<br>
<br>
  &lt;servlet-mapping&gt;<br>
        &lt;servlet-name&gt;<br>
        cofaxTools<br>
        &lt;/servlet-name&gt;<br>
        &lt;url-pattern&gt;<br>
        /tools/*<br>
        &lt;/url-pattern&gt;<br>
    &lt;/servlet-mapping&gt;<br>
<br>
   &lt;taglib&gt;<br>
      &lt;taglib-uri&gt;cofax.tld&lt;/taglib-uri&gt;<br>
      &lt;taglib-location&gt;/WEB-INF/tlds/cofax.tld&lt;/taglib-location&gt;<br>
   &lt;/taglib&gt;<br>
<br>
&lt;/web-app&gt;<br>
</code></pre>

<b>E.g.5</b>

<pre><code>JSON:<br>
<br>
{"menu": {<br>
    "header": "SVG Viewer",<br>
    "items": [<br>
        {"id": "Open"},<br>
        {"id": "OpenNew", "label": "Open New"},<br>
        null,<br>
        {"id": "ZoomIn", "label": "Zoom In"},<br>
        {"id": "ZoomOut", "label": "Zoom Out"},<br>
        {"id": "OriginalView", "label": "Original View"},<br>
        null,<br>
        {"id": "Quality"},<br>
        {"id": "Pause"},<br>
        {"id": "Mute"},<br>
        null,<br>
        {"id": "Find", "label": "Find..."},<br>
        {"id": "FindAgain", "label": "Find Again"},<br>
        {"id": "Copy"},<br>
        {"id": "CopyAgain", "label": "Copy Again"},<br>
        {"id": "CopySVG", "label": "Copy SVG"},<br>
        {"id": "ViewSVG", "label": "View SVG"},<br>
        {"id": "ViewSource", "label": "View Source"},<br>
        {"id": "SaveAs", "label": "Save As"},<br>
        null,<br>
        {"id": "Help"},<br>
        {"id": "About", "label": "About Adobe CVG Viewer..."}<br>
    ]<br>
}}<br>
</code></pre>
<br><b>The same message expressed as XML:</b><br>

<pre><code>&lt;menu&gt;<br>
    &lt;header&gt;Adobe SVG Viewer&lt;/header&gt;<br>
    &lt;item action="Open" id="Open"&gt;Open&lt;/item&gt;<br>
    &lt;item action="OpenNew" id="OpenNew"&gt;Open New&lt;/item&gt;<br>
    &lt;separator/&gt;<br>
    &lt;item action="ZoomIn" id="ZoomIn"&gt;Zoom In&lt;/item&gt;<br>
    &lt;item action="ZoomOut" id="ZoomOut"&gt;Zoom Out&lt;/item&gt;<br>
    &lt;item action="OriginalView" id="OriginalView"&gt;Original View&lt;/item&gt;<br>
    &lt;separator/&gt;<br>
    &lt;item action="Quality" id="Quality"&gt;Quality&lt;/item&gt;<br>
    &lt;item action="Pause" id="Pause"&gt;Pause&lt;/item&gt;<br>
    &lt;item action="Mute" id="Mute"&gt;Mute&lt;/item&gt;<br>
    &lt;separator/&gt;<br>
    &lt;item action="Find" id="Find"&gt;Find...&lt;/item&gt;<br>
    &lt;item action="FindAgain" id="FindAgain"&gt;Find Again&lt;/item&gt;<br>
    &lt;item action="Copy" id="Copy"&gt;Copy&lt;/item&gt;<br>
    &lt;item action="CopyAgain" id="CopyAgain"&gt;Copy Again&lt;/item&gt;<br>
    &lt;item action="CopySVG" id="CopySVG"&gt;Copy SVG&lt;/item&gt;<br>
    &lt;item action="ViewSVG" id="ViewSVG"&gt;View SVG&lt;/item&gt;<br>
    &lt;item action="ViewSource" id="ViewSource"&gt;View Source&lt;/item&gt;<br>
    &lt;item action="SaveAs" id="SaveAs"&gt;Save As&lt;/item&gt;<br>
    &lt;separator/&gt;<br>
    &lt;item action="Help" id="Help"&gt;Help&lt;/item&gt;<br>
    &lt;item action="About" id="About"&gt;About Adobe CVG Viewer...&lt;/item&gt;<br>
&lt;/menu&gt;<br>
</code></pre>