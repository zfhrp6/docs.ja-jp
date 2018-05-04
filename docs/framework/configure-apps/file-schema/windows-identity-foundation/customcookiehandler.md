---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b974767aa86801bff234e200e1fce021bfc422c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomcookiehandlergt"></a>&lt;customCookieHandler&gt;
カスタム クッキー ハンドラーの種類を設定します。 この要素が存在するのみ場合、`mode`の属性、`<cookieHandler>`要素は、"Custom"です。 カスタム型から派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラスです。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
\<customCookieHandler >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|派生するカスタム型を指定します、<xref:System.IdentityModel.Services.CookieHandler>クラスです。 指定する方法について、`type`属性は、「[カスタム型の参照](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>読み取りし、書き込みの cookie を使用します。|  
  
## <a name="remarks"></a>コメント  
 設定して、カスタム クッキー ハンドラーを指定する場合、`mode`の属性、`<cookieHandler>`要素"Custom"にする必要がありますを指定するカスタム クッキー ハンドラーの型を含めることによって、`<customCookieHandler>`クッキー ハンドラー型を参照する子要素です。 この要素にすることはできない時に指定された、`mode`属性が"Chunked"または"Default"に設定します。 カスタム クッキー ハンドラーがから派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラスです。  
  
 `<customCookieHandler>`要素として表されます、<xref:System.IdentityModel.Configuration.CustomTypeElement>クラスです。  
  
## <a name="example"></a>例  
 次の例の構成の種類のカスタム クッキー ハンドラーを使用して、SAM`MyNamespace.MyCustomCookieHandler`です。  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Services.CookieHandler>
