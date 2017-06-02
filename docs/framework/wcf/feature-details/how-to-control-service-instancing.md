---
title: "方法 : サービスのインスタンス化を制御する | Microsoft Docs"
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
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# 方法 : サービスのインスタンス化を制御する
サービスのインスタンス モードを設定することにより、<xref:System.ServiceModel.InstanceContext?displayProperty=fullName> \(およびそのユーザー定義のサービス オブジェクト\) をいつ生成するかを指定できます。  設定できるモードについては、<xref:System.ServiceModel.InstanceContextMode> 列挙体を参照してください。  動作[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)」を参照してください。  実施例については、「[動作](../../../../docs/framework/wcf/samples/behaviors.md)」を参照してください。  
  
### サービス インスタンスの有効期間をコードで制御するには  
  
1.  サービス クラスに <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を適用します。  
  
2.  <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティを <xref:System.ServiceModel.InstanceContextMode>、<xref:System.ServiceModel.InstanceContextMode>、<xref:System.ServiceModel.InstanceContextMode> のいずれかの値に設定します。  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## 使用例  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性の <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティを <xref:System.ServiceModel.InstanceContextMode> に設定するコード例を示します。  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## 参照  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>   
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>   
 <xref:System.ServiceModel.InstanceContextMode>   
 [Service: Behaviors Samples](http://msdn.microsoft.com/ja-jp/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)