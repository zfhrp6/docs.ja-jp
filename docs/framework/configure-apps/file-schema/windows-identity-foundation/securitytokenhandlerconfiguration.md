---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ac7284fa418c1540582c40bd744e913ba31aa881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
トークン ハンドラーのコレクションの構成を提供します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|saveBootstrapContext|セッション トークンにブートス トラップ トークンを含める必要があるかどうかを指定します。 設定して、値がトークン ハンドラー コレクションに設定することも可能性があります、`saveBootstrapContext`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。|  
|maximumClockSkew|A<xref:System.TimeSpan>最大許容される時計の誤差を指定します。 サインイン セッションの有効期限の検証などの時間が重要な操作を実行するときは、最大許容される時計の誤差を制御します。 既定値は 5 分、"00: 継続"です。 指定する方法について<xref:System.TimeSpan>値を参照してください[Timespan 値](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。 設定して、最大の時刻のずれがサービス レベルで設定することも可能性があります、`maximumClockSkew`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。 トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Audienceuri >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|この証明書利用者の許容可能な識別子 Uri のセットを指定します。 任意。|  
|[\<キャッシュ >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。 サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。 任意。|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|トークン ハンドラーを使用して証明書の検証の設定を制御します。 サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。 特定のハンドラーが、独自の検証コントロールで構成されている場合、これらの設定は上書きされます。 任意。|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|トークン ハンドラーはコレクション内のハンドラーによって使用される発行者名レジストリを構成します。 任意。|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|トークン ハンドラーはコレクション内のハンドラーによって使用される発行者トークン リゾルバーを登録します。 発行者トークン リゾルバーを使用して、入力方向のトークンとメッセージの署名のトークンを解決します。 任意。|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|トークン ハンドラーはコレクション内のハンドラーによって使用されるサービスのトークン リゾルバーを登録します。 サービスのトークン リゾルバーを使用して、入力方向のトークンとメッセージの暗号化トークンを解決します。 任意。|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|トークン リプレイ検出を有効にし、トークンの有効期限を指定します。 サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。 任意。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。|  
  
## <a name="remarks"></a>コメント  
 このセクションで説明のプロパティの値、<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>オブジェクト。 このセクションで構成した設定は、サービスで構成されているものをオーバーライドします。 これらの設定の一部は、ハンドラーがセキュリティ トークン ハンドラーのコレクションに追加されたときに指定されている設定によってさらに、オーバーライド、できます。  
  
## <a name="example"></a>例  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
