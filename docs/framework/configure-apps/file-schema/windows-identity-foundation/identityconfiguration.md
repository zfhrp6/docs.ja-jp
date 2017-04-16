---
title: "&lt;identityConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# &lt;identityConfiguration&gt;
サービス ・ レベルの id の設定を指定します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|name|Id の構成セクションの名前。  特定の構成セクションを参照するのにには、この名前を使用できます。  ない場合は`name`属性を指定すると、既定の構成セクションを定義します。  既定の構成は、パッシブ フェデレーション シナリオでは常に使用されます。  詳細については、[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 要素を参照してください。|  
|saveBootstrapContext|ブートス トラップのトークンをセッション トークンを含める必要がかどうかを指定します。  値も、トークン ハンドラーのコレクションを設定する可能性があります、 `saveBootstrapContext`の属性を[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。  サービスに設定されている値、トークン ハンドラーのコレクションの設定値をオーバーライドします。|  
|maximumClockSkew|A <xref:System.TimeSpan>は、最大許可された時計の傾斜を指定します。  サインイン セッションの有効期限の検証など、急を要する操作を実行するときの最大許可された時計の傾斜を制御します。  既定値は 5 分です\] 00: 05:00"。  指定する方法の詳細については、 <xref:System.TimeSpan>の値を参照してください[Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues)。  最大クロック スキューも、トークン ハンドラーのコレクションを設定する可能性があります、 `maximumClockSkew`の属性を[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。  サービスに設定されている値、トークン ハンドラーのコレクションの設定値をオーバーライドします。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<キャッシュ\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|セッション トークンをトークンのリプレイ検出を使用して、キャッシュを登録します。  サービス ・ レベルやセキュリティ トークン ハンドラーのコレクションを指定できます。  省略可能です。|  
|[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|証明書を検証するトークン ハンドラーを使用する設定を制御します。  サービス ・ レベルやセキュリティ トークン ハンドラーのコレクションを指定できます。  省略可能です。|  
|[\<claimsAuthenticationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|クレーム認証マネージャーの入力方向の要求を登録します。  省略可能です。|  
|[\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|要求の承認マネージャーは、入力方向の要求を登録します。  省略可能です。|  
|[\<claimTypeRequired\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|入力方向のセキュリティ トークンに必要なクレームのセットを指定します。  省略可能です。|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|セキュリティ トークン ハンドラーのコレクションを指定します。  0 個以上のコレクションのセキュリティ トークン ハンドラーを指定できます。  省略可能です。|  
|[\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|トークンのリプレイ検出を有効にし、トークンの有効期限を指定します。  サービス ・ レベルやセキュリティ トークン ハンドラーのコレクションを指定できます。  省略可能です。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<system.identityModel\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|アプリケーションでんだ Windows アイデンティティ基盤 \(ぜ\) オプションを有効にする構成を提供します。|  
  
## 解説  
 複数のアイデンティティが構成が定義可能性がありますが、それぞれに一意の名前。  動作は次のとおりです。  
  
1.  ない場合は`<identityConfiguration>`要素を指定します。  既定のユーザー構成実行時に作成され、既定値が指定されました。  
  
2.  場合は 1 つの`<identityConfiguration>`要素を指定します。  これは、ユーザーの既定の構成です。  名前または名前のないかどうかは関係ありません。  
  
3.  場合は、複数`<identityConfiguration>`要素を指定します。  無名の要素には、ユーザーの既定の構成を指定します。  複数指定する場合にお勧め`<identityConfiguration>`要素、それらのいずれかする必要がありますできない名前付き。  
  
> [!WARNING]
>  複数指定する場合`<identityConfiguration>`要素、それらのいずれかする必要がありますできない名前付き。  名前のない要素は、ユーザーの既定の構成になります。  
  
 指定した設定のいくつかの`<identityConfiguration>`セキュリティ トークン ハンドラーのコレクションを設定または個々 のセキュリティ トークン ハンドラーの設定によって、要素をオーバーライドできます。  
  
> [!IMPORTANT]
>  使用すると、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>や、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クラスをコードで参照されている識別情報構成でクレーム ベースのアクセス制御を提供するために、 `<federationConfiguration>`要素は、要求承認マネージャー、承認決定を行うために使用するポリシーを構成します。  パッシブ Web シナリオ、たとえば、Windows 通信基盤 \(WCF\) アプリケーションまたは Web ベースでないアプリケーションではない場合も同様です。  アプリケーションがパッシブの Web アプリケーションでない場合、 [\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)要素とその子ポリシー要素が存在する場合\) 参照の id の構成をされるだけの設定を適用します。  これ以外の設定は、すべて無視されます。  詳細については、[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 要素を参照してください。  
  
 `<identityConfiguration>`要素で表される、 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>クラス。  ユーザーの構成\] セクションで表される、 <xref:System.IdentityModel.Configuration.IdentityConfiguration>クラス。  
  
> [!IMPORTANT]
>  子要素として、次の要素を指定する、 `<identityConfiguration>`要素が廃止されました、旧バージョンとの互換性はまだ動作がサポートされていますが。  これらの要素で指定する必要があります、 [\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。  
>   
>  -   [\<audienceUris\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## 使用例  
 次の使用例は、"alternateConfiguration"という名前は、身元の構成を作成します。  ユーザーの構成の既定の設定を指定します。  
  
```  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## 参照  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>   
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>