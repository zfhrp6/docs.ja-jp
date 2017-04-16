---
title: "&lt;parameter&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;parameter&gt;
宣言された型がジェネリック型である場合、ジェネリック パラメーターを指定します。  
  
## 構文  
  
```  
  
<parameter index="integer"  
                      type=String" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|インデックス|宣言された型がジェネリック型である場合、既知の型を返すジェネリック パラメーターを指定します。|  
|型|シリアル化と逆シリアル化で使用される既知の型を説明する文字列。|  
  
## index 属性  
  
|値|説明|  
|-------|--------|  
|"0"|ジェネリック型の最初のパラメーター。  たとえば、<xref:System.Collections.Generic.List%601> にはパラメーターが 1 つだけあります。  宣言型として使用される場合、index は "0" に設定されます。|  
|"1"|ジェネリック型の 2 番目のパラメーター。  たとえば、<xref:System.Collections.Generic.Dictionary%602> には 2 つのパラメーターがあります。  2 番目のパラメーターによって既知の型が返される場合は、index 属性を "1" に設定します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<knownType\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|宣言型のフィールドまたはプロパティによって返される既知の型を指定します。|  
  
## 解説  
 既知の型[!INCLUDE[crabout](../../../../../includes/crabout-md.md)]、「[既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」および「<xref:System.Runtime.Serialization.DataContractSerializer>」を参照してください。  
  
 この要素の使用例については、「[\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)」を参照してください。  
  
 この構成要素に、両方の属性を同時に設定することはできません。  両方の属性が設定された場合、<xref:System.Configuration.ConfigurationErrorsException> が発生します。  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)