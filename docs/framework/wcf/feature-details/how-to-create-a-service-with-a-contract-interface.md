---
title: "方法 : コントラクト インターフェイスを使用してサービスを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 方法 : コントラクト インターフェイスを使用してサービスを作成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] コントラクトの作成には、インターフェイスの使用が適しています。このコントラクトでは、サービスが提供する操作にアクセスするために必要なメッセージのコレクションと構造を指定します。このインターフェイスでは、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用し、公開するメソッドに <xref:System.ServiceModel.OperationContractAttribute> クラスを適用して、入力と出力の種類を定義します。  
  
 サービス コントラクト[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)」を参照してください。  
  
### インターフェイスを使用した WCF コントラクトの作成  
  
1.  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、C\#、またはその他の共通言語ランタイム言語を使用して、新しいインターフェイスを作成します。  
  
2.  インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。  
  
3.  インターフェイスのメソッドを定義します。  
  
4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のパブリック コントラクトの一部として公開する必要のある各メソッドに、<xref:System.ServiceModel.OperationContractAttribute> クラスを適用します。  
  
## 使用例  
 次のコード例は、サービス コントラクトを定義するインターフェイスを示しています。  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求\/応答メッセージ パターンを使用します。このメッセージ パターン[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 要求\/応答コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)」を参照してください。属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。その他の例については、「[方法 : 一方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)」および「[方法 : 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)」を参照してください。  
  
## 参照  
 <xref:System.ServiceModel.ServiceContractAttribute>   
 <xref:System.ServiceModel.OperationContractAttribute>