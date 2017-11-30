---
title: "&lt;schemaImporterExtensions&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b3cc5e75cded5d468323a2b953bc61271f89e3e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
|[\<追加 > 要素を\<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。|  
  
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
 [\<追加 > 要素を\<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [\<system.xml.serialization> 要素](../../../docs/standard/serialization/system-xml-serialization-element.md)
