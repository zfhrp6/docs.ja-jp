---
title: "方法 : クラスまたは構造体に基本的なデータ コントラクトを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "データ コントラクト [WCF], クラスまたは構造体に作成"
  - "DataContractAttribute クラス"
  - "DataMemberAttribute"
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# 方法 : クラスまたは構造体に基本的なデータ コントラクトを作成する
このトピックでは、クラスまたは構造体を使用してデータ コントラクトを作成する基本的な手順を示します。  データ コントラクトおよびその使用方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)」を参照してください。  
  
 基本的な [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスおよびクライアントの作成方法を順を追って解説したチュートリアルが必要な場合は、「[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  基本的なサービスとクライアントで構成される実際のサンプル アプリケーションについては、「[基本的なデータ コントラクト](../../../../docs/framework/wcf/samples/basic-data-contract.md)」を参照してください。  
  
### クラスまたは構造体に基本的なデータ コントラクトを作成するには  
  
1.  クラスに <xref:System.Runtime.Serialization.DataContractAttribute> 属性を適用することにより、データ コントラクトを持つ型であることを宣言します。  パブリック型は、属性のないものも含めてすべてシリアル化されます。  <xref:System.Runtime.Serialization.DataContractAttribute> 属性がない場合は、<xref:System.Runtime.Serialization.DataContractSerializer> によってデータ コントラクトが推論されます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[シリアル化可能な型](../../../../docs/framework/wcf/feature-details/serializable-types.md)」を参照してください。  
  
2.  シリアル化するメンバー \(プロパティ、フィールド、またはイベント\) を定義します。これは、該当する各メンバーに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用することで行います。  このようなメンバーのことを、データ メンバーと呼びます。  既定では、すべてのパブリック型がシリアル化されます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[シリアル化可能な型](../../../../docs/framework/wcf/feature-details/serializable-types.md)」を参照してください。  
  
    > [!NOTE]
    >  プライベート フィールドであっても、<xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用すると、データが外部に公開されることになります。  機密性のあるデータが含まれていないかどうか確認してください。  
  
## 使用例  
 次の例では、<xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性をクラスとそのメンバーに適用して、`Person` 型のデータ コントラクトを作成する方法を示します。  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>   
 [データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)   
 [チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)   
 [概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)