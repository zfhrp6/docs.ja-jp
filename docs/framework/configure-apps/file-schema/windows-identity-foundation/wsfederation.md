---
title: '&lt;wsFederation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e4779baa24e172affad2ed5e04451ad791d7cdf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltwsfederationgt"></a>&lt;wsFederation&gt;
構成を提供、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM)。  
  
\<system.identityModel.services >  
\<federationConfiguration >  
\<wsFederation >  
  
## <a name="syntax"></a>構文  
  
```xml
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
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|authenticationType|認証の種類を指定する URI。 Ws-federation サインイン要求 wauth パラメーターを設定します。 省略可能です。 既定では、要求で wauth パラメーターが含まれていないことを指定する空の文字列です。|  
|鮮度|目的の最大期間、認証要求 (分) です。 Ws-federation サインイン要求 wfresh パラメーターを設定します。 省略可能です。 既定値は 0 です。 省略可能です。 **警告:**の .NET Framework 4.5 では、次のリリースで、`freshness`型属性である`xs:string`し、その既定値に`null`です。|  
|homeRealm|認証に使用する id プロバイダー (IP) のホーム領域。 Ws-federation サインイン要求 whr パラメーターを設定します。 省略可能です。 既定では、要求に whr パラメーターが含まれていないことを指定する空の文字列です。|  
|issuer|目的のトークン発行者の URI。 ベース URL の Ws-federation サインイン要求およびサインアウト要求のために必要な設定します。|  
|persistentCookiesOnPassiveRedirects|認証で永続的な cookie が発行されるかどうかを指定します。 省略可能です。 既定値は"false"、cookie が発行されていません。|  
|passiveRedirectEnabled|自動的に承認されていない要求を STS にリダイレクトするため、WSFAM が有効になっているかどうかを指定します。 省略可能です。 既定値は"true"、不正な要求が自動的にリダイレクトします。|  
|ポリシー|サインイン要求で使用する適切なポリシーの場所を指定する URL です。 既定値は空の文字列です。 Ws-federation サインイン要求 wp パラメーターを設定します。 省略可能です。 既定では空の文字列、wp パラメーターが要求に含まれていないことを指定します。|  
|realm|要求元の領域の URI。 (識別する URI を証明書利用者 (RP) セキュリティ トークン サービス (STS) にします。)Wtrealm Ws-federation サインイン要求の要求パラメーターを設定します。 必須です。|  
|応答|これで、証明書利用者 (RP) アプリケーションにはセキュリティ トークン サービス (STS) からの応答を受信するアドレスを識別する URL です。 Ws-federation サインイン要求 wreply パラメーターを設定します。 省略可能です。 既定では空の文字列、wreply パラメーターが要求に含まれていないことを指定します。|  
|要求|トークン発行要求。 Ws-federation サインイン要求 wreq パラメーターを設定します。 省略可能です。 既定では、要求で wreq パラメーターが含まれていないことを指定する空の文字列です。 要求に含めない、wreq または wreqptr パラメーターは、STS が発行するトークンの種類を知っていることを意味します。|  
|requestPtr|トークン発行要求の場所を指定する URL です。 要求 wreqptr パラメーターを設定します。 省略可能です。 既定では、要求で wreqptr パラメーターが含まれていないことを指定する空の文字列です。 要求に含めない、wreq または wreqptr パラメーターは、STS が発行するトークンの種類を知っていることを意味します。|  
|requireHttps|セキュリティ トークン サービス (STS) との通信で HTTPS プロトコルを使用する必要があるかどうかを指定します。 省略可能です。 既定値は"true"、HTTPS を使用する必要があります。|  
|リソース|証明書利用者 (RP)、アクセスされるリソースを識別する URI をセキュリティ トークン サービス (STS) にします。 省略可能です。 Ws-federation サインイン要求 wres パラメーターを設定します。 省略可能です。 既定では、要求で wres パラメーターが含まれていないことを指定する空の文字列です。 **注:** wres は従来のパラメーターです。 指定して、 `realm` wtrealm パラメーターを代わりに使用する属性。|  
|signInQueryString|Ws-federation サインイン要求 URL で定義されているアプリケーションのクエリ パラメーターを指定するための機能拡張ポイントを提供します。 省略可能です。 既定では、要求に追加のパラメーターを含めるない必要がありますを指定する空の文字列です。 パラメーターは、次の形式を使用してクエリ文字列のフラグメントとして指定します。`"param1=value1&param2=value2&param3=value3"`などです。 **注:**構成ファイルで、' (& a)"クエリ文字列内の文字は、そのエンティティ参照を使用して指定する必要があります`&`です。|  
|signOutQueryString|Ws-federation サインイン要求 URL で定義されているアプリケーションのクエリ パラメーターを指定するための機能拡張ポイントを提供します。 省略可能です。 既定では、要求に追加のパラメーターを含めるない必要がありますを指定する空の文字列です。 パラメーターは、次の形式を使用してクエリ文字列のフラグメントとして指定します。`"param1=value1&param2=value2&param3=value3"`などです。 **注:**構成ファイルで、' (& a)"クエリ文字列内の文字は、そのエンティティ参照を使用して指定する必要があります`&`です。|  
|signOutReply|パッシブ、Ws-federation プロトコルを介してサインアウト中にセキュリティ トークン サービス (STS) によって、クライアントをリダイレクトする URL を指定します。 Ws-federation サインアウト要求を wreply パラメーターを設定します。 省略可能です。 既定では、要求に追加のパラメーターを含めるない必要がありますを指定する空の文字列です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>コメント  
 使用することができます、 `<wsFederation>` WSFAM の Ws-federation パラメーターの既定の設定と既定の動作を構成する要素。 定義されている WS フェデレーション パラメーターの設定、`<wsFederation>`要素によって公開されている同等のプロパティの設定、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラスです。 これらのプロパティは、WSFAM によって発行された要求のたびに同じです。 Ws-federation パラメーターは、要求 WSFAM; によって公開されているイベントのイベント ハンドラーを追加することで処理中に動的に変更することができます。たとえば、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>イベント。 詳細については、ドキュメントを参照して、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラスです。  
  
 `<wsFederation>`要素として表されます、<xref:System.IdentityModel.Services.Configuration.WSFederationElement>クラスです。 構成オブジェクト自体がによって表される、<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>クラスです。 1 つ<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>インスタンスに設定されて、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>を介してアクセスされるオブジェクト、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティ、WSFAM の構成を提供します。  
  
## <a name="example"></a>例  
 次の XML に示します、`<wsFederation>`要素、WSFAM の設定を指定します。  
  
> [!WARNING]
>  この例では、WSFAM は HTTPS を使用する必要はありません。 これは、ため、`requireHttps`属性を`<wsFederation>`要素が設定`false`です。 ほとんどの実稼働環境には、セキュリティ リスクがあると、この設定はお勧めできません。  
  
```xml
<wsFederation passiveRedirectEnabled="true"   
              issuer="http://localhost:15839/wsFederationSTS/Issue"   
              realm="http://localhost:50969/"   
              reply="http://localhost:50969/"   
              requireHttps="false"   
              signOutReply="http://localhost:50969/SignedOutPage.html"   
              signOutQueryString="Param1=value2&Param2=value2"   
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
