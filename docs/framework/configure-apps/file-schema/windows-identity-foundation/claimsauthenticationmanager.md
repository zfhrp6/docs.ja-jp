---
title: "&lt;claimsAuthenticationManager&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;claimsAuthenticationManager&gt;
入力受取所の要求認証マネージャーを登録します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|<xref:System.Security.Claims.ClaimsAuthenticationManager> のクラスから派生したカスタム型を指定します。  `type` の属性を指定する方法の詳細については、 " " を参照してください。 [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferencess)|  
  
### 子要素  
 `type` の属性がない場合、または `type` の属性参照 <xref:System.Security.Claims.ClaimsAuthenticationManager> のクラス、 `<claimsAuthenticationManager>` の要素には子要素がありません; ただし、 <xref:System.Security.Claims.ClaimsAuthenticationManager> から派生したクラスは、子構成要素を定義できます。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの ID の設定を指定します。|  
  
## 解説  
 <xref:System.Security.Claims.ClaimsAuthenticationManager> のクラスにより提供される既定の動作は、入力がエコーされます。  `type` の属性が指定されていない場合、または `type` の属性が <xref:System.Security.Claims.ClaimsAuthenticationManager> のクラスを指定する場合は、 `<claimsAuthenticationManager>` の要素には子要素がありません。  カスタム動作を実行するに <xref:System.Security.Claims.ClaimsAuthenticationManager> クラスから派生した型を登録するに `type` の属性を指定できます。  派生クラスは `<claimsAuthenticationManager>` 要素の子要素を使用してこれらの要素を処理する <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> メソッドのオーバーライドにより構成をサポートできます。  子要素に定義されたスキーマは、クラスのデザイナーがあります。  
  
 `<claimsAuthenticationManager>` の要素設定 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=fullName> のプロパティ。  
  
## 使用例  
  
```  
<system.identityModel>  
    <identityConfiguration name=”MyIdentity”>  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```