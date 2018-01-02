---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c5d526ccd48ea5e822d5d29fb38dacd895c2556c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
構成、<xref:System.IdentityModel.Services.ChunkedCookieHandler>です。 この要素が存在するのみ場合、`mode`の属性、`<cookieHandler>`要素が"Default"または「チャンク」です。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
\<chunkedCookieHandler >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|chunkSize|任意の 1 つの HTTP クッキーを HTTP cookie のデータの文字の最大サイズ。 チャンク サイズを調整するときに注意する必要があります。 Web ブラウザーの cookie とドメインごとに許可される数のサイズに異なる制限されている場合。 元の Netscape 仕様がこれらの制限を規定するなど、: (cookie の値だけでなく、メタデータを含む)、[cookie] ヘッダーあたり 4096 バイトと 20 cookie ドメインごと、300 cookie の合計します。 既定値は 2000 です。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) は、読み取りし、書き込みの cookie を使用します。|  
  
## <a name="remarks"></a>コメント  
 指定すると、<xref:System.IdentityModel.Services.ChunkedCookieHandler>を設定して、`mode`の属性、`<cookieHandler>`を"Default"または"Chunked"要素を含めることで cookie を読み書きするクッキー ハンドラーを使用するチャンク サイズを指定できます、`<chunkedCookieHandler>`子要素と設定の`chunkSize`属性。 場合、`<chunkedCookieHandler>`要素が存在しない、2000 バイトの既定のチャンク サイズを使用します。 この要素にすることはできない時に指定された、`mode`属性が"Custom"に設定します。  
  
 `<chunkedCookieHandler>`要素として表されます、<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>クラスです。  
  
## <a name="example"></a>例  
 次の例では、3000 バイトのチャンク単位で cookie を書き込むチャンクされたクッキー ハンドラーを構成します。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
