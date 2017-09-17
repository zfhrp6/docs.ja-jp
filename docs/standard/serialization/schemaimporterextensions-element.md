---
title: "&lt;schemaImporterExtensions&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: 3
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: cf9ef09f514f38c0250c288e347d28d73caab295
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="ltschemaimporterextensionsgt-element"></a>&lt;schemaImporterExtensions&gt; 要素
XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を含みます。 構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<xmlSchemaImporterExtensions> の \<add> 要素](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。|  
  
## <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.xml.serialization> 要素](../../../docs/standard/serialization/system-xml-serialization-element.md)|XML シリアル化を制御する最上位の要素です。|  
  
## <a name="example"></a>例  
 XSD の型を .NET Framework の型にマッピングする際に <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を次のコード例に示します。  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<dateTimeSerialization> 要素](../../../docs/standard/serialization/datetimeserialization-element.md)   
 [\<xmlSchemaImporterExtensions> の \<add> 要素](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)   
 [\<system.xml.serialization> 要素](../../../docs/standard/serialization/system-xml-serialization-element.md)

