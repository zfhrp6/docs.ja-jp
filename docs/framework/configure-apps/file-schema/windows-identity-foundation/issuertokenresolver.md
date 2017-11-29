---
title: '&lt;issuerTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 02e2beb285cb0c4d88f98c3155ab5a3ff5e31e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltissuertokenresolvergt"></a>&lt;issuerTokenResolver&gt;
トークン ハンドラーはコレクション内のハンドラーによって使用される発行者トークン リゾルバーを登録します。 発行者トークン リゾルバーを使用して、入力方向のトークンとメッセージの署名のトークンを解決します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<issuerTokenResolver >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
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
|型|発行者トークン リゾルバーの種類を指定します。 いずれかである必要があります、<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスまたはその派生型、<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスです。 必須です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラーのセキュリティのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>コメント  
 発行者トークン リゾルバーを使用して、入力方向のトークンとメッセージの署名のトークンを解決します。 これを使用して、署名の確認のために使用される暗号化マテリアルを取得します。 指定する必要があります、`type`属性。 指定された型には、いずれかを指定できる<xref:System.IdentityModel.Tokens.IssuerTokenResolver>やカスタム型から派生した、<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスです。  
  
 いくつかのトークン ハンドラーを使用すると、構成内の発行者トークン リゾルバーの設定を指定できます。 セキュリティ トークン ハンドラーのコレクションで指定された個々 のトークン ハンドラーの設定をオーバーライドします。  
  
> [!NOTE]
>  指定する、`<issuerTokenResolver>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。 上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。  
  
## <a name="example"></a>例  
 次の XML から派生するカスタム クラスに基づいている発行者トークン リゾルバーの構成を表示する<xref:System.IdentityModel.Tokens.IssuerTokenResolver>です。 トークン リゾルバーは、カスタム構成要素から初期化された対象ユーザー キーのペアのディクショナリを保持 (`<AddAudienceKeyPair>`) クラスに対して定義されています。 クラスのオーバーライド、<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>この要素を処理するメソッド。 次の例で、上書きを表示します。ただし、それが呼び出すメソッドは、簡略化のためには表示されません。 完全な例については、`CustomToken`サンプルです。  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a>例  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
