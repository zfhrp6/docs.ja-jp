---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3151ec3511bca598e5aaabc72b821bdd3aed0b7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|トークン ハンドラーはコレクションの名前を指定します。 フレームワークによって認識される唯一の値には、"ActAs"および"OnBehalfOf"です。 これらの名前のいずれかでトークン ハンドラーのコレクションを指定する場合は、それぞれトークン ActAs または OnBehalfOf を処理するときに、コレクションが使用されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|トークン ハンドラー コレクションにセキュリティ トークン ハンドラーを追加します。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|トークンのハンドラー コレクションからすべてのセキュリティ トークン ハンドラーをクリアします。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|トークン ハンドラー コレクションからセキュリティ トークン ハンドラーを削除します。|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラーのコレクションの構成を提供します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id 設定を指定します。|  
  
## <a name="remarks"></a>コメント  
 サービス構成では、セキュリティ トークン ハンドラーの 1 つまたは複数の名前付きコレクションを指定できます。 使用して、コレクションの名前を指定することができます、`name`属性。 フレームワークを処理するだけの名前とは、"ActAs"と"OnBehalfOf"です。 ハンドラーは、これらのコレクションに存在する場合、セキュリティ トークン サービス (STS) によって代わりに使用されて、既定のハンドラーを処理するとき`ActAs`と`OnBehalfOf`トークンです。  
  
 既定では、コレクションが格納されます、次の種類のハンドラー: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、および<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>です。 使用して、コレクションを変更することができます、 `<add>`、 `<remove>`、および`<clear>`要素。 特定の型の 1 つのハンドラーのみがコレクションに存在するを確認する必要があります。 ハンドラーを派生させる場合など、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラスか、ハンドラー、または<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>両方ではなく、単一のコレクションで構成することがあります。  
  
 使用して、`<securityTokenHandlerConfiguration>`要素をコレクション内で、ハンドラーの構成設定を指定します。 この要素で指定された設定を上書きによってサービスに指定されている、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。 一部のハンドラー (いくつかの種類の組み込みのハンドラーを含む) は、子要素の追加の構成をサポートできる、`<add>`要素。 ハンドラーに指定した設定は、コレクションまたはサービスに指定した同等の設定をオーバーライドします。
