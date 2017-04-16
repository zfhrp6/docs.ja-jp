---
title: "&lt;dataContractSerializer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<dataContractSerializer> 要素"
  - "DataContractSerializer"
  - "dataContractSerializer 要素"
  - "KnownTypes"
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# &lt;dataContractSerializer&gt;
<xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。  この要素は、2 つの異なる階層で使用されます。  1 つは以下の「スキーマの階層」に示したもので、もう 1 つは「解説」に記載しています。  
  
## 構文  
  
```  
  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|要素|説明|  
|--------|--------|  
|ignoreExtensionDataObject|エンドポイントがシリアル化または逆シリアル化されているときに、そのエンドポイントにより提供されるデータを無視するかどうかを指定するブール値。  この属性は、`<behavior>` 要素の下の `<dataContractSerializer>` でのみ設定可能です。|  
|maxItemsInObjectGraph|シリアル化または逆シリアル化する項目の最大数を指定する整数。  この属性は 65536 です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|サービスの動作設定のコレクション。|  
|[\<system.runtime.serialization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。|  
  
## 解説  
 このトピックの冒頭で述べたように、この階層は \<X509Extension\> 要素が使用される 2 つ目の階層です。  
  
 [\<system.runtime.serialization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 既知の型の詳細については、<xref:System.Runtime.Serialization.DataContractSerializer> を参照してください。  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>   
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>   
 [既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [データ転送とシリアル化](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)