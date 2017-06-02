---
title: "&lt;authorizationPolicies&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;authorizationPolicies&gt;
この構成セクションには、`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションが含まれています。  各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。  この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。  アクセス制御は、それに基づいて許可または拒否されます。  認証ポリシーの動作の詳細については、「<xref:System.IdentityModel.Policy.IAuthorizationPolicy>」および「[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)」を参照してください。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>   
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>   
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>   
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>   
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>   
 [サービス操作へのアクセスの承認](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)   
 [方法 : サービスで使用するカスタム承認マネージャーを作成する](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)   
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)   
 [承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)