---
title: "&lt;customCookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# &lt;customCookieHandler&gt;
Cookie のカスタム ハンドラーの種類を設定します。  この要素のみが表示される場合は、 `mode`属性の`<cookieHandler>`要素は、「ユーザー設定」。  カスタムの型から派生する必要があります、 <xref:System.IdentityModel.Services.CookieHandler>クラス。  
  
## 構文  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode=”Custom”>  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|派生するカスタム型を指定します、 <xref:System.IdentityModel.Services.CookieHandler>クラス。  指定する方法の詳細については、 `type`属性は、 [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|構成、 <xref:System.IdentityModel.Services.CookieHandler>は、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> cookie の読み書きに使用します。|  
  
## 解説  
 設定することにより、クッキーのカスタム ハンドラーを指定すると、 `mode`属性の`<cookieHandler>`要素「ユーザー設定」などでカスタム cookie のハンドラーの種類を指定する必要があります、 `<customCookieHandler>`クッキーのハンドラーの型を参照する子要素。  この要素にすることはできない時に指定、 `mode` 「チャンク」または「既定値」属性を設定します。  ハンドラーのカスタム cookie を派生する必要がありますから、 <xref:System.IdentityModel.Services.CookieHandler>クラス。  
  
 `<customCookieHandler>`要素で表される、 <xref:System.IdentityModel.Configuration.CustomTypeElement>クラス。  
  
## 使用例  
 次の使用例カスタム cookie のハンドラーの型を使用すると、SAM の構成`MyNamespace.MyCustomCookieHandler`。  
  
```  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## 参照  
 <xref:System.IdentityModel.Services.CookieHandler>