---
title: "&lt;cookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;cookieHandler&gt;
構成、 <xref:System.IdentityModel.Services.CookieHandler>は、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) を使用して cookie を読み書きします。  
  
## 構文  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|name|Cookie が書き込まれるすべてのベース名を指定します。  既定値は"FedAuth"です。|  
|path|書き込まれたすべての cookie のパス値を指定します。  既定値は"HttpRuntime.AppDomainAppVirtualPath"です。|  
|mode|いずれか、 <xref:System.IdentityModel.Services.CookieHandlerMode> SAM によって使用される cookie のハンドラーの種類を指定する値。  次の値を使用可能性があります。<br /><br /> -   「既定値」\-は「チャンク」します。<br />-   「チャンク」などのインスタンスを使用して、 <xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス。  この cookie のハンドラーは、個々 の cookie がセットの最大サイズを超えないことを確認します。  これは、可能性があります「1 つの論理の cookie cookie に回線の数にチャンクで」実行します。<br />-   「カスタム」などから派生したカスタム クラス インスタンスを使用して<xref:System.IdentityModel.Services.CookieHandler>。  派生クラスによって参照される、 `<customCookieHandler>`子要素。<br /><br /> 既定値は、"Default"です。|  
|persistentSessionLifetime|永続的なセッションの有効期間を指定します。  一時的なセッションは 0 にすると、常に使用されます。  既定値は「一時的なセッションを指定なさい」、です。  「365 日間のセッションを指定 365:0:0」、最大値はです。  次の制限に従って値を指定する必要があります： `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`、左端の値日数を指定します。 時間の中央値 \(存在する場合\) を指定します、分の右端の値 \(存在する場合\) を指定します。|  
|requireSsl|書き込まれた cookie に"Secure"フラグが出力されるかどうかを指定します。  この値を設定すると、サインイン セッション cookie のみ HTTPS 経由で利用できます。  既定値は"true"です。|  
|hideFromScript|書き込まれた cookie の"HttpOnly"フラグが出力されるかどうかを制御します。  一部の web ブラウザーは、cookie の値にアクセスするクライアント側スクリプトを保持することでこのフラグを優先します。  既定値は"true"です。|  
|domain|書き込まれたすべての cookie のドメイン値。  既定値は""。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<chunkedCookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|構成、 <xref:System.IdentityModel.Services.ChunkedCookieHandler>。  この要素のみが表示される場合、 `mode`属性の`<cookieHandler>` "Default"または「チャンク」です。|  
|[\<customCookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Cookie のカスタム ハンドラーの種類を設定します。  この要素が存在するにする必要がある場合は、 `mode`属性の`<cookieHandler>`要素は、「ユーザー設定」。  それの他の値が存在することはできません、 `mode`属性。  カスタムの型から派生する必要があります、 <xref:System.IdentityModel.Services.CookieHandler>クラス。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定を含む、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) と、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。|  
  
## 解説  
 <xref:System.IdentityModel.Services.CookieHandler>読み取りおよび書き込みの生の cookie では、HTTP プロトコル ・ レベルの責任を負います。  いずれかを構成することができます、 <xref:System.IdentityModel.Services.ChunkedCookieHandler>カスタム cookie のハンドラーから派生、 <xref:System.IdentityModel.Services.CookieHandler>クラス。  
  
 チャンクの cookie のハンドラーを構成するには、mode 属性を「チャンク」または「デフォルト」を設定します。  既定のチャンク サイズは 2000 バイトですが、含めることによって、別のチャンク サイズをオプションとして指定できます、 `<chunkedCookieHandler>`子要素。  
  
 Cookie のカスタム ハンドラーを構成するには、mode 属性に「カスタム」に設定します。  指定する必要があります、 `<customCookieHandler>`カスタム ハンドラーの型を参照する子要素。  
  
 `<cookieHandler>`要素で表される、 <xref:System.IdentityModel.Services.CookieHandlerElement>クラス。  構成で指定した cookie のハンドラーからは、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A>のプロパティ、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>設定オブジェクト、 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>プロパティ。  
  
## 使用例  
 次の XML に示す、 `<cookieHandler>`要素。  この例では、ため、 `mode`属性が指定されていない、cookie の既定のハンドラーが SAM によって使用されます。  これは、インスタンスのです、 <xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス。  `<chunkedCookieHandler>`子要素が指定されていない、既定のチャンク サイズを指定します。  HTTPS は必要なので、 `requireSsl`属性を設定`false`。  
  
> [!WARNING]
>  この例では、HTTPS セッション cookie を記述する必要はありません。  これは、ためには、 `requireSsl`の属性を`<cookieHandler>`要素に設定する`false`。  セキュリティ上のリスクを提示可能性がありますようにこの設定ほとんどの運用環境でしないでください。  
  
```  
<cookieHandler requireSsl="false" />  
```  
  
## 参照  
 <xref:System.IdentityModel.Services.CookieHandler>   
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>   
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>