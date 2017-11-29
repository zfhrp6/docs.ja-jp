---
title: '&lt;cookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 88e968d025c959ec33674a9d8edb5e63341433ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) は、読み取りし、書き込みの cookie を使用します。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|書き込まれた cookie のベース名を指定します。 既定値は、"FedAuth"です。|  
|path|書き込まれた cookie のパスの値を指定します。 既定値は、"HttpRuntime.AppDomainAppVirtualPath"です。|  
|モード|1 つ、 <xref:System.IdentityModel.Services.CookieHandlerMode> SAM によって使用されるクッキー ハンドラーの種類を指定する値。 次の値を使用することがあります。<br /><br /> -"Default"、"Chunked"と同じです。<br />-「チャンク」などのインスタンスを使用して、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラスです。 このクッキー ハンドラーにより、個々 の cookie が設定された最大サイズを超えないようにします。 可能性のある「のチャンキング」1 つの論理 cookie の cookie で、ネットワークの数にして、これを実現します。<br />-"Custom"— から派生したカスタム クラスのインスタンスを使用して<xref:System.IdentityModel.Services.CookieHandler>です。 派生クラスは、によって参照される、`<customCookieHandler>`子要素です。<br /><br /> 既定値は、"Default"です。|  
|persistentSessionLifetime|永続的なセッションの有効期間を指定します。 0 の場合、一時的なセッションは常に使用します。 既定値は、「0:0:0」は、一時的なセッションを指定します。 最大値は、「365:0:0」は、365 日間のセッションを指定します。 次の制限に従って値を指定する必要があります:`<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`左端の値は、日数を指定する、中央値 (存在する場合)、時間を指定する、右端の値 (存在する場合) は、分を指定します。|  
|RequireSsl|「セキュリティで保護された」フラグは、書き込まれた cookie に対して生成するかどうかを指定します。 この値が設定されている場合、サインイン セッション cookie はできるだけ HTTPS 経由でです。 既定値は "true" です。|  
|hideFromScript|"HttpOnly"フラグは、書き込まれた cookie に対して生成するかどうかを制御します。 一部の web ブラウザーでは、cookie の値へのアクセスをクライアント側スクリプトを保持することでこのフラグが無視されます。 既定値は "true" です。|  
|ドメイン|ドメインは、書き込まれた cookie の値。 既定値は "" です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|構成、<xref:System.IdentityModel.Services.ChunkedCookieHandler>です。 この要素が存在するのみ場合、`mode`の属性、`<cookieHandler>`要素が"Default"または「チャンク」です。|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|カスタム クッキー ハンドラーの種類を設定します。 この要素が存在する必要がある場合、`mode`の属性、`<cookieHandler>`要素は、"Custom"です。 他の値の存在することはできませんが、`mode`属性。 カスタム型から派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラスです。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>コメント  
 <xref:System.IdentityModel.Services.CookieHandler>はプロトコル レベルの読み取りと書き込み、http クッキーを生の責任です。 いずれかを構成することができます、<xref:System.IdentityModel.Services.ChunkedCookieHandler>またはから派生したカスタム クッキー ハンドラー、<xref:System.IdentityModel.Services.CookieHandler>クラスです。  
  
 チャンクされたクッキー ハンドラーを構成するのには、"Chunked"または"Default"にモード属性を設定します。 既定のチャンク サイズは 2000 (バイト単位) ですが、必要に応じてを含めることによって、別のチャンク サイズを指定することがあります、`<chunkedCookieHandler>`子要素です。  
  
 カスタム クッキー ハンドラーを構成するのには、"Custom"にモード属性を設定します。 指定する必要があります、`<customCookieHandler>`カスタム ハンドラーの型を参照する子要素です。  
  
 `<cookieHandler>`要素として表されます、<xref:System.IdentityModel.Services.CookieHandlerElement>クラスです。 構成で指定されたクッキー ハンドラーはから利用可能な<xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A>のプロパティ、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトのセット、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティです。  
  
## <a name="example"></a>例  
 次の XML に示します、`<cookieHandler>`要素。 この例であるため、`mode`属性が指定されていない、SAM で使用される既定のクッキー ハンドラー。 これは、インスタンス、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラスです。 `<chunkedCookieHandler>`子要素が指定されていない、既定のチャンク サイズが使用されます。 HTTPS は必要ありませんので、`requireSsl`属性が設定されている`false`です。  
  
> [!WARNING]
>  HTTPS は、この例では、セッションの cookie を記述する必要はありません。 これは、ため、`requireSsl`属性を`<cookieHandler>`要素に設定されている`false`です。 ほとんどの実稼働環境には、セキュリティ リスクがあると、この設定はお勧めできません。  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
