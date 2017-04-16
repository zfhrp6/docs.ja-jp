---
title: "&lt;wsFederation&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;wsFederation&gt;
構成を提供、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\)。  
  
## 構文  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
        freshness=xs:decimal  
        homerealm=xs:string (URI)  
        issuer=xs:string (URI)  
        persistentCookiesOnPassiveRedirects=xs:boolean  
        passiveRedirectEnabled=xs:boolean  
        policy=xs:string (URI)  
        realm=xs:string (URI)  
        reply=xs:string (URI)  
        request=xs:string (URI)  
        requestPtr=xs:string (URI)  
        requireHttps=xs:boolean  
        resource=xs:string (URI)  
        signInQueryString=xs:string  
        signOutQueryString=xs:string  
        signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|authenticationType|認証の種類を指定する URI。  WS フェデレーションのサインイン要求の wauth パラメーターを設定します。  省略可能です。  既定値は、wauth パラメーターが要求に含まれていないを指定します。 空の文字列です。|  
|最新状態に維持|認証要求を目的の最大年齢 \(分単位\)。  WS フェデレーションのサインイン要求の wfresh パラメーターを設定します。  省略可能です。  既定値は 0 です。  省略可能です。 **Warning:**  次のリリースで。NET Framework 4.5 は、 `freshness`属性の種類が`xs:string`とその既定値は`null`。|  
|homeRealm|ホーム ・ レルムの認証に使用する id プロバイダー \(IP\)。  WS フェデレーション サインイン要求の whr パラメーターを設定します。  省略可能です。  Whr パラメーターが要求に含まれていないことを指定します。 空の文字列が省略されます。|  
|issuer|目的のトークン発行者の URI を指定します。  要求の基本 URL の Ws\-federation サインインとサインアウトの要求のために必要なに設定します。|  
|persistentCookiesOnPassiveRedirects|認証の永続的な cookie が発行されたかどうかを指定します。  省略可能です。  既定値は"false"が、cookie が発行されませんでした。|  
|passiveRedirectEnabled|WSFAM は、STS に認証されていない要求を自動的にリダイレクトできるかどうかを指定します。  省略可能です。  既定値は"true"が、認証されていない要求を自動的にリダイレクトされます。|  
|policy|サインイン要求で使用する、関連するポリシーの場所を指定します。 URL を指定します。  既定値は空の文字列です。  WS フェデレーション サインイン要求の wp のパラメーターを設定します。  省略可能です。  既定値は、wp のパラメーター要求に含まれていないことを指定します。 空の文字列です。|  
|realm|要求元の領域の URI。  \(依存元の相手 \(RP\) が、セキュリティ トークン サービス \(STS\) を識別する URI です。\)要求 wtrealm Ws\-federation サインイン要求のパラメーターを設定します。  必ず指定します。|  
|返信|依存元パーティ \(RP\) が、セキュリティ トークン サービス \(STS から\) の返信を受信したいアドレスを識別する URL を指定します。  WS フェデレーションのサインイン要求の wreply パラメーターを設定します。  省略可能です。  既定値は、wreply パラメーターが要求に含まれていないを指定します。 空の文字列です。|  
|要求|トークンの発行要求します。  WS フェデレーションのサインイン要求の wreq パラメーターを設定します。  省略可能です。  既定値は、wreq パラメーターが要求に含まれていないを指定します。 空の文字列です。  STS は、トークンを発行するのにはどのような知っている、wreq または wreqptr パラメーター内の要求を含まないを意味します。|  
|requestPtr|トークン発行要求の場所を指定します。 URL を指定します。  要求の wreqptr パラメーターを設定します。  省略可能です。  既定値は、wreqptr パラメーターが要求に含まれていないを指定します。 空の文字列です。  STS は、トークンを発行するのにはどのような知っている、wreq または wreqptr パラメーター内の要求を含まないを意味します。|  
|requireHttps|セキュリティ トークン サービス \(STS\) との通信が HTTPS プロトコルを使用する必要があるかどうかを指定します。  省略可能です。  既定値は"true"は、HTTPS を使用する必要があります。|  
|リソース|アクセスして、リソース、依存元の相手 \(RP\) を識別する URI、セキュリティ トークン サービス \(STS\) にします。  省略可能です。  WS フェデレーションのサインイン要求の wres パラメーターを設定します。  省略可能です。  既定値は、wres パラメーターが要求に含まれていないを指定します。 空の文字列です。 **Note:**  wres は、従来型のパラメーターです。  指定、 `realm` wtrealm パラメーターを代わりに使用する属性。|  
|signInQueryString|WS フェデレーション サインイン要求の URL にクエリ パラメーターを定義するアプリケーションを指定するのには、機能拡張ポイントを提供します。  省略可能です。  既定値は、要求で追加のパラメーターを含めるしないことを指定します。 空の文字列です。  パラメーターは次の形式を使用してクエリ文字列のフラグメントとして指定されている: `“param1=value1&param2=value2&param3=value3”`といった。 **Note:**  構成ファイル内の ' &"は、エンティティ参照を使用して、クエリ文字列内の文字を指定する必要が`&`。|  
|signOutQueryString|WS フェデレーション サインイン要求の URL にクエリ パラメーターを定義するアプリケーションを指定するのには、機能拡張ポイントを提供します。  省略可能です。  既定値は、要求で追加のパラメーターを含めるしないことを指定します。 空の文字列です。  パラメーターは次の形式を使用してクエリ文字列のフラグメントとして指定されている: `“param1=value1&param2=value2&param3=value3”`といった。 **Note:**  構成ファイル内の ' &"は、エンティティ参照を使用して、クエリ文字列内の文字を指定する必要が`&`。|  
|signOutReply|パッシブ、Ws\-federation プロトコルをサインアウト時のセキュリティ トークン サービス \(STS\) にクライアントがリダイレクトする URL を指定します。  Ws\-federation サインアウト要求には、wreply パラメーターを設定します。  省略可能です。  既定値は、要求で追加のパラメーターを含めるしないことを指定します。 空の文字列です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定を含む、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) と、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。|  
  
## 解説  
 使用できます、 `<wsFederation>` 、WSFAM の Ws\-federation パラメーターの既定値の設定および既定の動作を構成するのには。  WS フェデレーション パラメーターの設定\] で定義されている、 `<wsFederation>`要素によって公開されるのと同じプロパティを設定する、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラス。  これらのプロパティを使用すると、WSFAM によって発行されるすべての要求を同じです。  WSFAM によって公開されるイベントのイベント ハンドラーを追加することにより処理要求の実行中に、Ws\-federation パラメーターを動的に変更できます。 例えば、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>イベント。  詳細については、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> クラスのドキュメントを参照してください。  
  
 `<wsFederation>`要素で表される、 <xref:System.IdentityModel.Services.Configuration.WSFederationElement>クラス。  構成オブジェクトによって表される、 <xref:System.IdentityModel.Services.Configuration.WSFederationConfiguration>クラス。  1 つの<xref:System.IdentityModel.Services.Configuration.WSFederationConfiguration>インスタンスの設定には、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>を通じてアクセスされるオブジェクト、 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>プロパティと構成、WSFAM を提供します。  
  
## 使用例  
 次の XML に示す、 `<wsFederation>` 、WSFAM の設定を指定する要素。  
  
> [!WARNING]
>  この例では、WSFAM を HTTPS を使用する必要はありません。  これは、ためには、 `requireHttps`の属性、 `<wsFederation>`が要素を設定`false`。  セキュリティ上のリスクを提示可能性がありますようにこの設定ほとんどの運用環境でしないでください。  
  
```  
<wsFederation passiveRedirectEnabled="true"   
  issuer="http://localhost:15839/wsFederationSTS/Issue"   
  realm="http://localhost:50969/"   
  reply="http://localhost:50969/"   
  requireHttps="false"   
  signOutReply="http://localhost:50969/SignedOutPage.html"   
  signOutQueryString="Param1=value2&Param2=value2"   
  persistentCookiesOnPassiveRedirects="true" />  
  
```  
  
## 参照  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>