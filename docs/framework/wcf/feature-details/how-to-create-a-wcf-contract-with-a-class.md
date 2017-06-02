---
title: "方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する | Microsoft Docs"
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# 方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] コントラクトの作成には、インターフェイスの使用が適しています。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).ここで説明する代替方法では、クラスを作成してから、<xref:System.ServiceModel.ServiceContractAttribute> 属性を直接そのクラスに適用し、<xref:System.ServiceModel.OperationContractAttribute> 属性をコントラクトに含まれるクラス内の各メソッドに適用します。  
  
> [!WARNING]
>  `[ServiceContract]` と `[ServiceContractAttribute]` は、同じことを行います。`[OperationContract]` と `[OperationContractAttribute]` でも、同様です。各ケースで、前者は後者の短縮形です。  
  
 サービス コントラクト[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)」を参照してください。  
  
### クラスを使用した Windows Communication Foundation コントラクトの作成  
  
1.  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、C\#、またはその他の任意の共通言語ランタイム言語を使用して、新しいクラスを作成します。  
  
2.  クラスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。  
  
3.  クラスでメソッドを作成します。  
  
4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のパブリック コントラクトの一部として公開する必要のある各メソッドに <xref:System.ServiceModel.OperationContractAttribute> クラスを適用します。  
  
## 使用例  
 次のコード例は、サービス コントラクトを定義するクラスを示しています。  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求\/応答メッセージ パターンを使用します。このメッセージ パターン[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 要求\/応答コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)」を参照してください。属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。その他の例については、「[方法 : 一方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)」および「[方法 : 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)」を参照してください。  
  
## 参照  
 <xref:System.ServiceModel.ServiceContractAttribute>   
 <xref:System.ServiceModel.OperationContractAttribute>