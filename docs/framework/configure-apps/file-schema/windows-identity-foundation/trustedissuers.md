---
title: "&lt;trustedIssuers&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;trustedIssuers&gt;
構成ベースの発行者名レジストリで使用される信頼された発行者の証明書の一覧を構成する \(<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>\)。  
  
## 構文  
  
```  
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
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|証明書を信頼された発行元のコレクションに追加します。  証明書が指定されて、 `thumbprint`属性。  この属性は必須であり、証明書の拇印の ASN.1 のエンコード形式が含まれている必要があります。  `name`属性はオプションであり、証明書のフレンドリ名を指定するのに使用できます。|  
|`<clear>`|すべての証明書を信頼された発行元のコレクションから削除します。|  
|`<remove thumbprint=xs:string>`|証明書は、信頼できる発行元のコレクションから削除します。  証明書が指定されて、 `thumbprint`属性。  この属性は必須です。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<issuerNameRegistry\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|発行者名レジストリを構成します。 **Important:**  `type`属性の`<issuerNameRegistry>`要素を参照するには、する必要があります、 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>のクラス、 `<trustedIssuers>`要素が有効であること。|  
  
## 解説  
 たんだ Windows アイデンティティ基盤 \(ぜ\) の単一の実装を提供する、 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラス ボックスのアウト、 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラス。  構成の発行者名レジストリ構成から読み込まれる信頼された発行者の一覧を維持します。  一覧では、各発行者名、発行者によって作成されたトークンの署名を確認するために必要な X.509 証明書が関連付けられます。  信頼された発行者の証明書の一覧で指定される、 `<trustedIssuers>`要素。  リスト内の各要素はその発行者によって作成されたトークンの署名を確認するために必要な X.509 証明書、ニーモニックの発行者名を関連付けます。  証明書は、ASN.1 エンコード形式の証明書の拇印を指定して、コレクションを使用して追加の信頼`<add>`要素。  オフにしたり、発行者 \(証明書\) を使用して、一覧からの削除、 `<clear>`と`<remove>`の要素。  
  
 `type`属性の`<issuerNameRegistry>`要素を参照するには、する必要があります、 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>のクラス、 `<trustedIssuers>`要素が有効であること。  
  
## 使用例  
 次の XML 名のレジストリをベースの構成の発行者を指定する方法を示します。  
  
```  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
  
```  
  
## 参照  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>   
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>