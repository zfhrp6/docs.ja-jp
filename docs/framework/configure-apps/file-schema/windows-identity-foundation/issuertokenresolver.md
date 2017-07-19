---
title: "&lt;issuerTokenResolver&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;issuerTokenResolver&gt;
ハンドラーで、トークン ハンドラー コレクションで使用される発行者トークン リゾルバーを登録します。  署名トークンにトークンとメッセージの受信を解決するには、発行者トークン リゾルバーが使用されます。  
  
## 構文  
  
```  
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
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|発行者、トークン リゾルバーの種類を指定します。  いずれかにする必要があります、 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスまたはから派生した型は<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラス。  指定する方法の詳細については、 `type`属性は、 [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。  必ず指定します。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|構成コレクションのセキュリティ トークン ハンドラーを提供します。|  
  
## 解説  
 署名トークンにトークンとメッセージの受信を解決するには、発行者トークン リゾルバーが使用されます。  これは、暗号署名をチェックするために使用される材料を取得するために使用されます。  指定する必要があります、 `type`属性。  指定された型はいずれかになります<xref:System.IdentityModel.Tokens.IssuerTokenResolver>またはから派生するカスタム型は<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラス。  
  
 一部トークン ハンドラー構成で発行者トークン リゾルバーの設定を指定することができます。  指定されたセキュリティ トークン ハンドラー コレクションで個々 のトークン ハンドラーの設定をオーバーライドします。  
  
> [!NOTE]
>  指定する、 `<issuerTokenResolver>`要素の子要素として、 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんが、旧バージョンとの互換性のためのサポートもします。  設定で、 `<securityTokenHandlerConfiguration>`要素無効もに、 `<identityConfiguration>`要素。  
  
## 使用例  
 次の XML から派生するカスタム クラスに基づいて、発行者トークン リゾルバーの構成を示しています<xref:System.IdentityModel.Tokens.IssuerTokenResolver>。  トークン リゾルバーからカスタムの構成要素が初期化される対象キーのペアのディクショナリを保持しています \(`<AddAudienceKeyPair>`\) のクラスを定義します。  クラスのオーバーライド、 <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>この要素を処理するメソッド。  オーバーライドは、次の例では、表示されます。 ただし、それを呼び出す方法を簡潔にするため表示されません。  完全な例についてを参照してください、 `CustomToken`サンプル。  
  
```  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## 使用例  
  
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
  
## 参照  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>