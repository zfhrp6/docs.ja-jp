---
title: "&lt;system.runtime.serialization&gt; の &lt;dataContractSerializer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;system.runtime.serialization&gt; の &lt;dataContractSerializer&gt;
<xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。  
  
## 構文  
  
```  
  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
            maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String">  
          <knownType type="String">  
             <parameter index="Integer"  
                        type="String" />  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|要素|説明|  
|--------|--------|  
|ignoreExtensionDataObject|エンドポイントがシリアル化または逆シリアル化されているときに、そのエンドポイントにより提供されるデータを無視するかどうかを指定するブール値。  この属性は、`<behavior>` 要素の下の `<dataContractSerializer>` でのみ設定可能です。|  
|maxItemsInObjectGraph|シリアル化または逆シリアル化する項目の最大数を指定する整数。  この属性は 65536 です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<declaredTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|逆シリアル化時に <xref:System.Runtime.Serialization.DataContractSerializer> が使用する既知の型が含まれています。<br /><br /> データ コントラクトと既知の型の詳細については、「[既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」を参照してください。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.runtime.serialization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<xref:System.Runtime.Serialization> 名前空間セクションのルート要素を表し、<xref:System.Runtime.Serialization.DataContractSerializer> のオプションを設定するための要素を含みます。|  
  
## 解説  
 既知の型の詳細については、「<xref:System.Runtime.Serialization.DataContractSerializer>」および「[既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」を参照してください。  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>   
 [既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)