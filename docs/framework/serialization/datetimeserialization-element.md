---
title: "&lt;dateTimeSerialization&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<dateTimeSerialization> 要素"
  - "dateTimeSerialization 要素"
  - "XML シリアル化, 構成"
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;dateTimeSerialization&gt; 要素
<xref:System.DateTime> オブジェクトのシリアル化モードを決定します。  
  
## 構文  
  
```  
  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`mode`|省略可能です。  シリアル化モードを指定します。  <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 値のいずれかに設定します。  既定値は、**RoundTrip** です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|system.xml.serialization|XML シリアル化を制御する最上位の要素です。|  
  
## 解説  
 .NET Framework の 1.0、1.1、2.0、およびそれ以降のバージョンで、このプロパティを **Local** に設定した場合、<xref:System.DateTime> オブジェクトは常に現地時刻形式になります。  つまり、ローカル タイム ゾーンの情報が、シリアル化されたデータに必ず組み込まれます。  .NET Framework の以前のバージョンとの互換性を保証するには、このプロパティを **Local** に設定します。  
  
 バージョン 2.0 以降の .NET Framework で、このプロパティを **Roundtrip** に設定すると、<xref:System.DateTime> オブジェクトが調べられ、タイム ゾーンが現地時刻、UTC、または未指定のいずれであるかが特定されます。  その後、この特定された情報を保持する形で、<xref:System.DateTime> オブジェクトがシリアル化されます。  これは既定の動作であり、.NET Framework の以前のバージョンと通信を行わない、すべての新しいアプリケーションで推奨されます。  
  
## 参照  
 <xref:System.DateTime>   
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<schemaImporterExtensions\> 要素](../../../docs/framework/serialization/schemaimporterextensions-element.md)   
 [\<xmlSchemaImporterExtensions\> の \<add\> 要素](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)   
 [\<system.xml.serialization\> 要素](../../../docs/framework/serialization/system-xml-serialization-element.md)