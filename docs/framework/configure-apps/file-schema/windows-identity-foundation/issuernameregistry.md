---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b695cc6d66e5b9e45bb6a5fd22d594bc22ea3cba
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuernameregistrygt"></a>&lt;issuerNameRegistry&gt;
トークン ハンドラーはコレクション内のハンドラーによって使用される発行者名レジストリを構成します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
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
|型|派生する型、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラスです。 詳細については、ユーザー設定を指定する方法についての`type`、[カスタム型の参照] を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|ときに、`type`属性構成ベースの発行者名レジストリの指定 (、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラス) では、 [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素を指定する必要があります。 [ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素がかかることが`<add>`、 `<clear>`、または`<remove>`子要素としての要素。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラーのセキュリティのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>コメント  
 すべての発行者トークンは、発行者名レジストリを使用して検証されます。 これはから派生するオブジェクト、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラスです。 発行者名レジストリを使用して、対応する発行元によって生成されるトークンの署名を確認するために必要な暗号化マテリアルをニーモニック名を関連付けます。 発行者名レジストリでは、証明書利用者 (rp) アプリケーションで信頼される発行者の一覧を管理します。 使用して、発行者名レジストリの型を指定、`type`属性。 `<issuerNameRegistry>`要素は、指定した種類の構成を提供する 1 つまたは複数の子要素を持つことができます。 オーバーライドすることでこれらの子要素を処理するロジックを提供する、<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>メソッドです。  
  
 WIF では、単一の発行者名レジストリの型を既定で、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラスです。 このクラスは、一連の構成で指定されている信頼された発行者の証明書を使用します。 構成の子要素では、必要な`<trustedIssuers>`、信頼された発行者の証明書のコレクションが構成されています。 信頼された証明書が、ASN.1 を使用してエンコードされた証明書の拇印の形式とが追加または削除をコレクションからを使用して指定`<add>`、 `<clear>`、または`<remove>`要素。  
  
 `<issuerNameRegistry>`要素として表されます、<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>クラスです。  
  
> [!NOTE]
>  指定する、`<issuerNameRegistry>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。 上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。  
  
## <a name="example"></a>例  
 次の XML では、名前のレジストリをベースの構成の発行者を指定する方法を示します。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
