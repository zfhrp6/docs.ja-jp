---
title: "&lt;authorizationPolicies&gt; の &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &lt;authorizationPolicies&gt; の &lt;add&gt;
クレームの変換の承認ポリシーを指定します。  
  
## 構文  
  
```  
  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## 型  
 `Type`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`policyType`|必須の文字列属性。<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アクセス制御モデルは、承認ポリシーのセットを型として提供します。  この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。  アクセス制御は、それに基づいて許可または拒否されます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<authorizationPolicies\>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|承認ポリシーの種類のコレクションを指定します。|  
  
## 解説  
 各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。  この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。  アクセス制御は、それに基づいて許可または拒否されます。  認証ポリシーの動作の詳細については、「<xref:System.IdentityModel.Policy.IAuthorizationPolicy>」および「[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)」を参照してください。  
  
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