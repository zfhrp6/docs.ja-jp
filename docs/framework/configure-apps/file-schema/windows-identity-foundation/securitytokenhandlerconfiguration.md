---
title: "&lt;securityTokenHandlerConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;securityTokenHandlerConfiguration&gt;
構成、トークン ハンドラーのコレクションを提供します。  
  
## 構文  
  
```  
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
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|saveBootstrapContext|ブートス トラップのトークンをセッション トークンを含める必要がかどうかを指定します。  値も、トークン ハンドラーのコレクションを設定する可能性があります、 `saveBootstrapContext`の属性を[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。  サービスに設定されている値、トークン ハンドラーのコレクションの設定値をオーバーライドします。|  
|maximumClockSkew|A <xref:System.TimeSpan>は、最大許可された時計の傾斜を指定します。  サインイン セッションの有効期限の検証など、急を要する操作を実行するときの最大許可された時計の傾斜を制御します。  既定値は 5 分です\] 00: 05:00"。  指定する方法の詳細については、 <xref:System.TimeSpan>の値を参照してください[Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues)。  最大クロックスも、サービス レベルで設定する可能性があります、 `maximumClockSkew`の属性を[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。  サービスに設定されている値、トークン ハンドラーのコレクションの設定値をオーバーライドします。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<audienceUris\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|この依存元の相手の許容可能な識別子は Uri のセットを指定します。  省略可能です。|  
|[\<キャッシュ\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|セッション トークンをトークンのリプレイ検出を使用して、キャッシュを登録します。  サービス ・ レベルやセキュリティ トークン ハンドラーのコレクションを指定できます。  省略可能です。|  
|[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|証明書を検証するトークン ハンドラーを使用する設定を制御します。  サービス ・ レベルやセキュリティ トークン ハンドラーのコレクションを指定できます。  独自の検証コントロールと、特定のハンドラーが設定されている場合、これらの設定はオーバーライドされます。  省略可能です。|  
|[\<issuerNameRegistry\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|ハンドラーで、トークン ハンドラー コレクションで使用される発行者名レジストリを構成します。  省略可能です。|  
|[\<issuerTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|ハンドラーで、トークン ハンドラー コレクションで使用される発行者トークン リゾルバーを登録します。  署名トークンにトークンとメッセージの受信を解決するには、発行者トークン リゾルバーが使用されます。  省略可能です。|  
|[\<serviceTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|ハンドラーで、トークン ハンドラー コレクションにより使用されるサービス トークン リゾルバーを登録します。  サービス トークン リゾルバーを使用すると、受信トークンとメッセージの暗号化トークンを解決します。  省略可能です。|  
|[\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|トークンのリプレイ検出を有効にし、トークンの有効期限を指定します。  サービス ・ レベルやセキュリティ トークン ハンドラーのコレクションを指定できます。  省略可能です。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|エンドポイントには登録されているセキュリティ トークン ハンドラーのコレクションを指定します。|  
  
## 解説  
 説明プロパティの値は、 <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>オブジェクト。  ここで構成した設定は、サービスで構成されているをオーバーライドします。  いくつかのこれらの設定ハンドラーはセキュリティ トークン ハンドラー コレクションに追加されるときに指定された設定によって、オーバーライドことができます。  
  
## 使用例  
  
```  
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