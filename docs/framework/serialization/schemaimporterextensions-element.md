---
title: "&lt;schemaImporterExtensions&gt; 要素 | Microsoft Docs"
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
  - "<schemaImporterExtensions> 要素"
  - "schemaImporterExtensions 要素"
  - "XML シリアル化, 構成"
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;schemaImporterExtensions&gt; 要素
XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を含みます。  構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。  
  
## 構文  
  
```  
  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<xmlSchemaImporterExtensions\> の \<add\> 要素](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)|マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。|  
  
## 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.xml.serialization\> 要素](../../../docs/framework/serialization/system-xml-serialization-element.md)|XML シリアル化を制御する最上位の要素です。|  
  
## 使用例  
 XSD の型を .NET Framework の型にマッピングする際に <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を次のコード例に示します。  
  
```  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## 参照  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<dateTimeSerialization\> 要素](../../../docs/framework/serialization/datetimeserialization-element.md)   
 [\<xmlSchemaImporterExtensions\> の \<add\> 要素](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)   
 [\<system.xml.serialization\> 要素](../../../docs/framework/serialization/system-xml-serialization-element.md)