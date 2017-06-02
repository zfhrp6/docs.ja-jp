---
title: "方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする | Microsoft Docs"
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
  - "フェデレーション"
  - "WCF, フェデレーション"
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# 方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする
フェデレーション資格情報を必要とするサービスの中には、セキュリティで保護されたセッションをサポートしないものがあります。その場合は、セキュリティで保護されたセッション機能を無効にする必要があります。<xref:System.ServiceModel.WsHttpBinding> とは異なり、<xref:System.ServiceModel.WSFederationHttpBinding> クラスでは、サービスとの通信中に、セキュリティで保護されたセッションを無効にできません。代わりに、セキュリティで保護されたセッションの設定をブートストラップで置き換えるカスタム バインディングを作成する必要があります。  
  
 ここでは、<xref:System.ServiceModel.WSFederationHttpBinding> に含まれるバインド要素を変更してカスタム バインディングを作成する方法を示します。結果は、セキュリティで保護されたセッションを使用しないことを除き、<xref:System.ServiceModel.WSFederationHttpBinding> と同じです。  
  
### セキュリティで保護されたセッションを使用しないカスタム フェデレーション バインディングを作成するには  
  
1.  コードで強制的に、または構成ファイルから読み込む方法によって、<xref:System.ServiceModel.WSFederationHttpBinding> クラスのインスタンスを作成します。  
  
2.  <xref:System.ServiceModel.WSFederationHttpBinding> の複製を <xref:System.ServiceModel.Channels.CustomBinding> 内に作成します。  
  
3.  <xref:System.ServiceModel.Channels.CustomBinding> 内で <xref:System.ServiceModel.Channels.SecurityBindingElement> を見つけます。  
  
4.  <xref:System.ServiceModel.Channels.SecurityBindingElement> 内で <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> を見つけます。  
  
5.  元の <xref:System.ServiceModel.Channels.SecurityBindingElement> を <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> のブートストラップ セキュリティ バインド要素で置き換えます。  
  
## 使用例  
 次の例では、セキュリティで保護されたセッションを使用しないカスタム フェデレーション バインディングを作成します。  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## コードのコンパイル  
  
-   このコード例をコンパイルするには、System.ServiceModel.dll アセンブリを参照するプロジェクトを作成します。  
  
## 参照  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)