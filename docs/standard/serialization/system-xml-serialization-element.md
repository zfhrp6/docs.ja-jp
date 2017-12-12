---
title: "&lt;system.xml.serialization&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d70879d5e0a579af7b5c507910d4dcb19ddee52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemxmlserializationgt-element"></a>&lt;system.xml.serialization&gt; 要素
XML シリアル化を制御する最上位の要素です。 構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<dateTimeSerialization> 要素](../../../docs/standard/serialization/datetimeserialization-element.md)|<xref:System.DateTime> オブジェクトのシリアル化モードを決定します。|  
|[\<schemaImporterExtensions> 要素](../../../docs/standard/serialization/schemaimporterextensions-element.md)|XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を含みます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration> 要素](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.DateTime> オブジェクトのシリアル化モードを指定し、XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を示します。  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<dateTimeSerialization> 要素](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [\<schemaImporterExtensions> 要素](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<xmlSchemaImporterExtensions> の \<add> 要素](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)
