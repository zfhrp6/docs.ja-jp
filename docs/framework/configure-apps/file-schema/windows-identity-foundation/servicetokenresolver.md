---
title: "&lt;serviceTokenResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;serviceTokenResolver&gt;
ハンドラーで、トークン ハンドラー コレクションにより使用されるサービス トークン リゾルバーを登録します。  サービス トークン リゾルバーを使用すると、受信トークンとメッセージの暗号化トークンを解決します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|サービス トークン リゾルバーの種類を指定します。  一方、 <xref:System.IdentityModel.Selectors.SecurityTokenResolver>型または派生型、 <xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラス。  指定する方法の詳細については、 `type`属性は、 [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。  必ず指定します。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|構成コレクションのセキュリティ トークン ハンドラーを提供します。|  
  
## 解説  
 受信トークンとメッセージの暗号化トークンを解決するには、サービス トークン リゾルバーを使用できます。  これは、着信トークンを復号化に使用するキーを取得するために使用されます。  指定する必要があります、 `type`属性。  指定された型はいずれかになります<xref:System.IdentityModel.Selectors.SecurityTokenResolver>またはから派生するカスタム型は<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラス。  
  
 一部トークン ハンドラー構成でサービス トークン リゾルバーの設定を指定することができます。  指定されたセキュリティ トークン ハンドラー コレクションで個々 のトークン ハンドラーの設定をオーバーライドします。  
  
> [!NOTE]
>  指定する、 `<serviceTokenResolver>`要素の子要素として、 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんが、旧バージョンとの互換性のためのサポートもします。  設定で、 `<securityTokenHandlerConfiguration>`要素無効もに、 `<identityConfiguration>`要素。  
  
## 使用例  
  
```  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```