---
title: "&lt;serviceAuthorization&gt; 要素 | Microsoft Docs"
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
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# &lt;serviceAuthorization&gt; 要素
サービス操作へのアクセスを許可する設定を指定します。  
  
## 構文  
  
```  
  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
      <authorizationPolicies>  
         <add policyType="String" />  
      </authorizationPolicies>  
</serviceAuthorization>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|impersonateCallerForAllOperations|サービスのすべての操作が呼び出し元を偽装するかどうかを指定するブール値。  既定値は、`false` です。<br /><br /> 特定のサービス操作が呼び出し元を偽装する場合、スレッド コンテキストは、指定されたサービスを実行する前に呼び出し元のコンテキストに切り替えられます。|  
|principalPermissionMode|サーバーでの操作を実行するために使用されるプリンシパルを設定します。  次の値があります。<br /><br /> -   なし<br />-   UseWindowsGroups<br />-   UseAspNetRoles<br />-   Custom<br /><br /> 既定値は UseWindowsGroups です。  値は、<xref:System.ServiceModel.Description.PrincipalPermissionMode> 型です。  この属性の使い方の詳細については、「[方法 : PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)」を参照してください。|  
|roleProviderName|Windows Communication Foundation \(WCF\) アプリケーションにロール情報を提供するロール プロバイダーの名前を指定する文字列。  既定値は空の文字列です。|  
|ServiceAuthorizationManagerType|サービス承認マネージャーの型を含む文字列。  詳細については、「<xref:System.ServiceModel.ServiceAuthorizationManager>」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|authorizationPolicies|`add` キーワードを使用して追加できる承認ポリシーの種類のコレクションを含みます。  各承認ポリシーは、文字列の単一の必須属性 `policyType` を含みます。  この属性は、入力クレームのセットをクレームの別のセットに変換することを可能にする承認ポリシーを指定します。  アクセス制御は、それに基づいて許可または拒否されます。  詳細については、「<xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>」を参照してください。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|サービスの動作設定のコレクションが含まれています。|  
  
## 解説  
 このセクションには、承認、カスタム ロール プロバイダー、および偽装に影響する要素が含まれています。  
  
 `principalPermissionMode` 属性は、保護メソッドの使用を承認するときに使用するユーザー グループを指定します。  既定値は `UseWindowsGroups` で、リソースにアクセスしようとしている ID を、"Administrators" や "Users" などの Windows グループから検索するように指定します。  `UseAspNetRoles` を指定すると、次のコードに示すように、\<system.web\> 要素の下で構成されるカスタム ロール プロバイダーを使用することもできます。  
  
```  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 `principalPermissionMode` 属性で `roleProviderName` を使用する方法を次のコードに示します。  
  
```  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 この構成要素の使い方の詳細な例については、「[サービス操作へのアクセスの承認](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)」および「[承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)」を参照してください。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>   
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>   
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [サービス操作へのアクセスの承認](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)   
 [方法 : サービスで使用するカスタム承認マネージャーを作成する](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)   
 [方法 : PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)   
 [承認ポリシー](../../../../../docs/framework/wcf/samples/authorization-policy.md)