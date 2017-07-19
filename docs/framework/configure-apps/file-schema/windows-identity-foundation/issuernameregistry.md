---
title: "&lt;issuerNameRegistry&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# &lt;issuerNameRegistry&gt;
ハンドラーで、トークン ハンドラー コレクションで使用される発行者名レジストリを構成します。  
  
## 構文  
  
```  
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
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|派生した型は<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラス。  ユーザー設定を指定する方法の詳細については`type`を参照してください[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|`type`属性には、構成ベースの発行者名レジストリを指定します \(、 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラス\) は、 [\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素を指定する必要があります。  [\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素を取ることができます`<add>`、 `<clear>`、または`<remove>`要素の子要素として。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|構成コレクションのセキュリティ トークン ハンドラーを提供します。|  
  
## 解説  
 すべてのトークンの発行者、発行者名レジストリを使用して検証されます。  これからの派生オブジェクトです、 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラス。  発行者名レジストリ ニーモニックの名前に対応する発行者によって作成されたトークンの署名を確認するために必要な暗号化の材料を関連付けるために使用されます。  発行者名レジストリ依存元のパーティ \(RP\) アプリケーションによって信頼されている発行者の一覧を維持します。  発行者名レジストリの種類を使用して指定される、 `type`属性。  `<issuerNameRegistry>`要素は、指定した型の構成を提供する 1 つまたは複数の子要素を持つことができます。  オーバーライドして子要素を処理するロジックを提供、 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>メソッド。  
  
 名前レジストリの種類、ボックスの外の提供、シングル ・発行者をたんだぜ、 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラス。  このクラスは、一連の構成で指定されている信頼された発行者の証明書を使用します。  これは、子の構成要素、する必要があります`<trustedIssuers>`、\[信頼できる発行元の証明書のコレクションを設定されている場合します。  証明書を指定する、ASN.1 を使用してエンコードされた形式の証明書の拇印と追加またはを使用して、コレクションからの削除を信頼`<add>`、 `<clear>`、または`<remove>`の要素。  
  
 `<issuerNameRegistry>`要素で表される、 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>クラス。  
  
> [!NOTE]
>  指定する、 `<issuerNameRegistry>`要素の子要素として、 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんが、旧バージョンとの互換性のためのサポートもします。  設定で、 `<securityTokenHandlerConfiguration>`要素無効もに、 `<identityConfiguration>`要素。  
  
## 使用例  
 次の XML 名のレジストリをベースの構成の発行者を指定する方法を示します。  
  
```  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
  
```  
  
## 参照  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>   
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>