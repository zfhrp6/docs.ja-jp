---
title: "&lt;knownType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;knownType&gt;
逆シリアル化中に <xref:System.Runtime.Serialization.DataContractSerializer> によって使用される型を指定します。  この要素には、"宣言型" のフィールドまたはプロパティによって返される "既知の型" を指定します。詳細については、「[既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」を参照してください。  
  
## 構文  
  
```  
  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## 型  
 `string`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|型|型 \(名前空間を含む\)、アセンブリ名、バージョン、カルチャ、および公開キー トークンを指定します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<parameter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|宣言型がジェネリック型である場合に、パラメーター インデックスを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|宣言されたタイプのコレクションに、宣言されたタイプを追加します。|  
  
## 解説  
 既知の型の詳細については、「[既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」および「<xref:System.Runtime.Serialization.DataContractSerializer>」を参照してください。  
  
 この要素の使用例については、「[\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)」を参照してください。  
  
## 使用例  
  
```  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)