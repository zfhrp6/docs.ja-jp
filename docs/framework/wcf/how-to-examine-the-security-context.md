---
title: "方法 : セキュリティ コンテキストを調べる | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Claimset クラス"
  - "ServiceSecurityContext クラス"
  - "WCF, セキュリティ"
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# 方法 : セキュリティ コンテキストを調べる
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスのプログラミングを行う場合、サービス セキュリティ コンテキストを使用すると、サービスの認証で使用されるクライアントの資格情報とクレームの詳細を確認できます。これは、<xref:System.ServiceModel.ServiceSecurityContext> クラスのプロパティを使用することで可能になります。  
  
 たとえば、<xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> プロパティまたは <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティを使用すると、現在のクライアントの ID を取得できます。クライアントが匿名であるかどうかを確認するには、<xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> プロパティを使用します。  
  
 また、<xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> プロパティにあるクレームのコレクションを反復処理することによって、クライアントのためにどのようなクレームが作成されているのかを確認することもできます。  
  
### 現在のセキュリティ コンテキストを取得するには  
  
-   現在のセキュリティ コンテキストを取得するためには、静的プロパティ <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> にアクセスします。参照から現在のコンテキストの任意のプロパティを調べます。  
  
### 呼び出し元の ID を確認するには  
  
1.  <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> プロパティおよび <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティの値を表示します。  
  
### 呼び出し元のクレームを解析するには  
  
1.  現在の <xref:System.IdentityModel.Policy.AuthorizationContext> クラスを返します。<xref:System.ServiceModel.ServiceSecurityContext.Current%2A> プロパティを使用して、現在のサービス セキュリティ コンテキストを返し、次に <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> プロパティを使用して `AuthorizationContext` を返します。  
  
2.  <xref:System.IdentityModel.Policy.AuthorizationContext> クラスの <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> プロパティによって返された <xref:System.IdentityModel.Claims.ClaimSet> オブジェクトのコレクションを解析します。  
  
## 使用例  
 次の例では、現在のセキュリティ コンテキストの <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティおよび <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> プロパティの値、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> プロパティの値、クレームのリソース値、および現在のセキュリティ コンテキストのすべてのクレームの <xref:System.IdentityModel.Claims.Claim.Right%2A> プロパティを表示します。  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## コードのコンパイル  
 コードでは、次の名前空間を使用します。  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## 参照  
 [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)   
 [サービス ID と認証](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)