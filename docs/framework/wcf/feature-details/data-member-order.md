---
title: "データ メンバーの順序 | Microsoft Docs"
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
  - "データ コントラクト [WCF], メンバーの順序"
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# データ メンバーの順序
一部のアプリケーションでは、各種のデータ メンバーから送信される、または受信されると予想できるデータの順序 \(たとえばシリアル化された XML でデータが表れる順序\) がわかると便利です。この順序を変更する必要が生じることもあります。ここでは、このような順序を決定する規則について説明します。  
  
## 基本的な規則  
 データの順序を決定する基本的な規則には、次のようなものがあります。  
  
-   データ コントラクト型が継承階層の一部である場合、その基本型のデータ メンバーが常に最初の順番になります。  
  
-   次に来るのは <xref:System.Runtime.Serialization.DataMemberAttribute> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> プロパティが設定されていない、現在の型のデータ メンバー \(アルファベット順\) になります。  
  
-   その次に来るのは、<xref:System.Runtime.Serialization.DataMemberAttribute> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> プロパティが設定されているすべてのデータ メンバーです。これらのデータ メンバーはまず `Order` プロパティの値によって並べられ、次に特定の `Order` 値を持つメンバーが複数ある場合は、そのアルファベット順に並びます。Order 値はスキップされることがあります。  
  
 アルファベット順は、<xref:System.String.CompareOrdinal%2A> メソッドを呼び出すことによって確立されます。  
  
## 例  
 次のコードについて考えてみましょう。  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 作成される XML は、次のようになります。  
  
```  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 [データ コントラクトの等価性](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)   
 [データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)