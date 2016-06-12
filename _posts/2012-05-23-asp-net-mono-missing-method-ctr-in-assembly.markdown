---
layout: post
status: publish
published: true
title: ASP.NET Mono "Missing method .ctr in assembly"
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 277
wordpress_url: http://codenuggets.com/?p=277
date: '2012-05-23 20:18:43 -0500'
date_gmt: '2012-05-23 20:18:43 -0500'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ASP.NET
- ".NET"
tags:
- Linux
- ASP.NET
- Ubuntu
- Mono
- Apache
- mod_mono
comments:
- id: 666
  author: Upgrading Mono and Mod_Mono « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/05/23/upgrading-mono-and-mod_mono/
  date: '2012-05-23 21:17:15 -0500'
  date_gmt: '2012-05-23 21:17:15 -0500'
  content: "[...] obscure error message that says &quot;Warning **: Missing method
    .ctor [..]&quot; (for the entire message see this post. After long research on
    the web, I found that my mono installation is out of date and my [...]"
---
I'm trying to run one of my research ASP.NET application on Ubuntu Linux using Mono. The machine I'm running on previously had Mono and mod_mono installed on it. This is the error message I got from running locally.

```
Server Error in '/geostore' Application
Compilation Error

Description: Error compiling a resource required to service this request. Review your source file and modify it to fix this error.

Compiler Error Message: : ** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Missing method .ctor in assembly /var/www/geostore/bin/GeoStoreClient.dll, type System.Runtime.Versioning.TargetFrameworkAttribute
~/Global.asax


Show Detailed Compiler Output:

gmcs /target:library /lib:"/var/www/geostore/bin" /debug- /optimize+ /warn:0 /out:"/tmp/www-data-temp-aspnet-0/875b7ed3/App_global.asax_71d76655.dll" /r:"/usr/lib/mono/gac/System/2.0.0.0__b77a5c561934e089/System.dll" /r:"/usr/lib/mono/gac/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll" /r:"/usr/lib/mono/gac/System.Data/2.0.0.0__b77a5c561934e089/System.Data.dll" /r:"/usr/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll" /r:"/usr/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll" /r:"/usr/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a/System.Web.Services.dll" /r:"/usr/lib/mono/gac/System.Runtime.Serialization/3.0.0.0__b77a5c561934e089/System.Runtime.Serialization.dll" /r:"/usr/lib/mono/gac/System.IdentityModel/3.0.0.0__b77a5c561934e089/System.IdentityModel.dll" /r:"/usr/lib/mono/gac/System.ServiceModel/3.0.0.0__b77a5c561934e089/System.ServiceModel.dll" /r:"/usr/lib/mono/gac/System.ServiceModel.Web/3.5.0.0__31bf3856ad364e35/System.ServiceModel.Web.dll" /r:"/usr/lib/mono/gac/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll" /r:"/var/www/geostore/bin/GeoStoreClient.dll" /r:"/var/www/geostore/bin/GeoStoreCommon.dll" /r:"/var/www/geostore/bin/GeoStoreWebClient.dll" /r:"/var/www/geostore/bin/UCharge.Geometry.dll" /r:"/var/www/geostore/bin/UCharge.Geospatial.dll"  /nowarn:0169  -- "/tmp/www-data-temp-aspnet-0/875b7ed3/App_global.asax_71d76655_0.cs" 


** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Missing method .ctor in assembly /var/www/geostore/bin/GeoStoreClient.dll, type System.Runtime.Versioning.TargetFrameworkAttribute

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: The class System.Runtime.Versioning.TargetFrameworkAttribute could not be loaded, used in GeoStoreClient

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Can't find custom attr constructor image: /var/www/geostore/bin/GeoStoreClient.dll mtoken: 0x0a000001

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Missing method .ctor in assembly /var/www/geostore/bin/GeoStoreWebClient.dll, type System.Runtime.Versioning.TargetFrameworkAttribute

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Can't find custom attr constructor image: /var/www/geostore/bin/GeoStoreWebClient.dll mtoken: 0x0a000001

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Missing method .ctor in assembly /var/www/geostore/bin/UCharge.Geometry.dll, type System.Runtime.Versioning.TargetFrameworkAttribute

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Can't find custom attr constructor image: /var/www/geostore/bin/UCharge.Geometry.dll mtoken: 0x0a000001

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Missing method .ctor in assembly /var/www/geostore/bin/UCharge.Geospatial.dll, type System.Runtime.Versioning.TargetFrameworkAttribute

** (/usr/lib/mono/2.0/gmcs.exe:2243): WARNING **: Can't find custom attr constructor image: /var/www/geostore/bin/UCharge.Geospatial.dll mtoken: 0x0a000001

Unhandled Exception: System.TypeLoadException: Could not load type 'System.Runtime.Versioning.TargetFrameworkAttribute' from assembly 'GeoStoreClient'.
  at (wrapper managed-to-native) System.Reflection.Assembly:InternalGetType (System.Reflection.Module,string,bool,bool)
  at System.Reflection.Assembly.GetType (System.String name, Boolean throwOnError, Boolean ignoreCase) [0x00000] in :0 
  at System.Reflection.Assembly.GetType (System.String name) [0x00000] in :0 
  at Mono.CSharp.RootNamespace.GetTypeInAssembly (System.Reflection.Assembly assembly, System.String name) [0x00000] in :0 
  at Mono.CSharp.RootNamespace.LookupTypeReflection (Mono.CSharp.CompilerContext ctx, System.String name, Location loc, Boolean must_be_unique) [0x00000] in :0 
  at Mono.CSharp.GlobalRootNamespace.LookupTypeReflection (Mono.CSharp.CompilerContext ctx, System.String name, Location loc, Boolean must_be_unique) [0x00000] in :0 
  at Mono.CSharp.Namespace.LookupType (Mono.CSharp.CompilerContext ctx, System.String name, Location loc) [0x00000] in :0 
  at Mono.CSharp.Namespace.Lookup (Mono.CSharp.CompilerContext ctx, System.String name, Location loc) [0x00000] in :0 
  at Mono.CSharp.TypeManager.CoreLookupType (Mono.CSharp.CompilerContext ctx, System.String ns_name, System.String name, Kind type_kind, Boolean required) [0x00000] in :0 
  at Mono.CSharp.TypeManager.InitCoreTypes (Mono.CSharp.CompilerContext ctx) [0x00000] in :0 
  at Mono.CSharp.Driver.Compile () [0x00000] in :0 
  at Mono.CSharp.Driver.Main (System.String[] args) [0x00000] in :0 

Version information: Mono Runtime Version: 2.6.7 (Debian 2.6.7-5ubuntu3); ASP.NET Version: 2.0.50727.1433
```