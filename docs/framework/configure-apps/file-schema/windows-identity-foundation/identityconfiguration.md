---
title: '&lt;identityConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5070d9e886b8f5a8a0abf27593d40df8b5281267
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758998"
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
サービス レベルの id 設定を指定します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|Id の構成セクションの名前。 この名前を使用すると、特定の構成セクションを参照します。 ない場合は`name`属性を指定すると、セクションが既定の構成を定義します。 既定の構成は常に、パッシブなフェデレーション シナリオで使用します。 詳細については、次を参照してください。、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。|  
|saveBootstrapContext|セッション トークンにブートス トラップ トークンを含める必要があるかどうかを指定します。 設定して、値がトークン ハンドラー コレクションに設定することも可能性があります、`saveBootstrapContext`属性を[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。|  
|maximumClockSkew|A<xref:System.TimeSpan>最大許容される時計の誤差を指定します。 サインイン セッションの有効期限の検証などの時間が重要な操作を実行するときは、最大許容される時計の誤差を制御します。 既定値は 5 分、"00: 継続"です。 指定する方法について<xref:System.TimeSpan>値を参照してください[Timespan 値](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。 設定して、最大の時刻のずれがトークン ハンドラー コレクションに設定することも可能性があります、`maximumClockSkew`属性を[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<キャッシュ >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。 サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。 任意。|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|トークン ハンドラーを使用して証明書の検証の設定を制御します。 サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。 任意。|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|入力方向の要求の要求認証マネージャーに登録します。 任意。|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|入力方向の要求の要求の承認マネージャーを登録します。 任意。|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|必要な受信セキュリティ トークンのクレームのセットを指定します。 任意。|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|セキュリティ トークン ハンドラーのコレクションを指定します。 セキュリティ トークン ハンドラーの 0 個以上のコレクションを指定することができます。 任意。|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|トークン リプレイ検出を有効にし、トークンの有効期限を指定します。 サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。 任意。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|アプリケーションで Windows Identity Foundation (WIF) オプションを有効にするための構成を提供します。|  
  
## <a name="remarks"></a>コメント  
 複数の id が構成を定義することがあります、それぞれに一意の名前。 動作は次のとおりです。  
  
1.  ない場合は`<identityConfiguration>`要素を指定します。 既定の id 構成では、実行時に作成され、既定値で設定されます。  
  
2.  場合、1 つ`<identityConfiguration>`要素を指定します。 既定の id 構成することをお勧めします。 という名前または名前のないかどうかは関係ありません。  
  
3.  複数`<identityConfiguration>`の要素を指定します。 名前なし要素は、既定の id 構成を指定します。 推奨複数指定するときに`<identityConfiguration>`要素、これらのいずれかができない名前付きです。  
  
> [!WARNING]
>  複数指定する場合`<identityConfiguration>`要素、これらのいずれかができない名前付きです。 名前なし要素は、既定の id 構成になります。  
  
 指定された設定の一部、`<identityConfiguration>`要素は、セキュリティ トークン ハンドラーのコレクションの設定によって、または個々 のセキュリティ トークン ハンドラーの設定によってオーバーライドできます。  
  
> [!IMPORTANT]
>  使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コードによって参照される id の構成でクレーム ベースのアクセス制御を提供するクラス、`<federationConfiguration>`要素は、要求承認マネージャーとを使用して、ポリシーを構成します。承認を決定します。 これは、true の場合、パッシブの Web シナリオ、たとえば、Windows Communication Foundation (WCF) アプリケーションや Web ベースではないアプリケーションではないシナリオであってもです。 アプリケーションが、パッシブ Web アプリケーションではない場合、 [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)要素 (とその子ポリシー要素、存在する場合) のみに適用される設定は、参照される id の構成のです。 その他のすべての設定は無視されます。 詳細については、次を参照してください。、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。  
  
 `<identityConfiguration>`要素として表されます、<xref:System.IdentityModel.Configuration.IdentityConfigurationElement>クラスです。 Id の構成セクションで表される、<xref:System.IdentityModel.Configuration.IdentityConfiguration>クラスです。  
  
> [!IMPORTANT]
>  子要素として、次の要素を指定する、`<identityConfiguration>`動作はまだサポートされていますが旧バージョンとの互換性のための要素は推奨されていません。 これらの要素は、代わりに、指定する必要があります、 [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素。  
>   
>  -   [\<Audienceuri >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>例  
 次の例では、"alternateConfiguration"という名前 id の構成を作成します。 Id の構成では、既定の設定を指定します。  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
