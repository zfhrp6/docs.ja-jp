---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f9daea7d6b78e2f6790050b35dde62db6058c60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757471"
---
# <a name="lttrustedissuersgt"></a>&lt;trustedIssuers&gt;
構成ベースの発行者名レジストリによって使用される信頼された発行者の証明書の一覧の構成 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<issuerNameRegistry >  
\<trustedIssuers >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|証明書を信頼された発行者のコレクションに追加します。 証明書を指定した、`thumbprint`属性。 この属性は必須であり、証明書の拇印のエンコードされた ASN.1 フォームを含める必要があります。 `name`属性は省略可能、証明書のフレンドリ名を指定するために使用できます。|  
|`<clear>`|信頼された発行者のコレクションからすべての証明書をクリアします。|  
|`<remove thumbprint=xs:string>`|証明書を信頼された発行者のコレクションから削除します。 証明書を指定した、`thumbprint`属性。 この属性は必須です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|発行者名レジストリを構成します。 **重要:** 、`type`の属性、`<issuerNameRegistry>`要素を参照する必要があります、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>のクラス、`<trustedIssuers>`を有効にする要素。|  
  
## <a name="remarks"></a>コメント  
 Windows Identity Foundation (WIF) の単一実装を提供する、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>すぐ、クラス、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラスです。 発行者名レジストリの構成は、構成から読み込まれる信頼された発行者の一覧を保持します。 一覧は、各発行者名を発行元によって生成されるトークンの署名を検証するために必要な X.509 証明書に関連付けます。 信頼された発行者の証明書の一覧を指定、`<trustedIssuers>`要素。 リスト内の各要素は、その発行者によって生成されるトークンの署名を検証するために必要な X.509 証明書にニーモニック発行者名を関連付けます。 信頼された証明書が証明書の拇印の形式でエンコードされた ASN.1 を使用して指定されを使用して、コレクションに追加されます`<add>`要素。 オフまたはを使用して、一覧から発行者 (証明書) を削除することができます、`<clear>`と`<remove>`要素。  
  
 `type`の属性、`<issuerNameRegistry>`要素を参照する必要があります、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>のクラス、`<trustedIssuers>`を有効にする要素。  
  
## <a name="example"></a>例  
 次の XML では、名前のレジストリをベースの構成の発行者を指定する方法を示します。  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
