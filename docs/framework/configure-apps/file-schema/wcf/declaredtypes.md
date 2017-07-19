---
title: "&lt;declaredTypes&gt; | Microsoft Docs"
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
  - "<declaredTypes> 要素"
  - "DataContractSerializer"
  - "dataContractSerializer 要素"
  - "declaredTypes 要素"
  - "KnownTypes"
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# &lt;declaredTypes&gt;
逆シリアル化時に <xref:System.Runtime.Serialization.DataContractSerializer> が使用する既知の型が含まれています。  
  
 データ コントラクトと既知の型の詳細については、「[既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」を参照してください。  
  
## 構文  
  
```  
  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
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
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|既知の型を必要とする型を追加します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<xref:System.Runtime.Serialization.DataContractSerializer> 用の設定データが含まれています。|  
  
## 解説  
 既知の型[!INCLUDE[crabout](../../../../../includes/crabout-md.md)]、「[既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」および「<xref:System.Runtime.Serialization.DataContractSerializer>」を参照してください。  
  
## 使用例  
 次の XML コードに、`DataContractSerializer`  要素に追加された宣言型と既知の型を示します。  この例は、追加された 3 つの型を示しています。  最初の型は、"Item" という既知の型を使用する "Orders" という名前のカスタム型です。  2 つ目の宣言型は、既知の型として `Item` を使用する <xref:System.Collections.Generic.List%601> です。  最後の 3 つ目の宣言型は、<xref:System.Collections.Generic.Dictionary%602> です。  <xref:System.Collections.Generic.Dictionary%602> クラスの型は、2 種類のパラメーターを持つジェネリック型です。  最初のパラメーターはキーを表し、2 番目のパラメーターは値を表します。  次の例は、2 番目の型 \(値\) の <xref:System.Collections.Generic.List%601> を既知の型の一覧に追加します。  `index` 属性を使用して、既知の型で使用する型パラメーターを指定する必要があります。  この場合には、"1" に設定された index 属性 \(コレクションは 0 から始まる\) によって値型が示されます。  
  
```  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)