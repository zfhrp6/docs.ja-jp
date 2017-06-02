---
title: "&lt;chunkedCookieHandler&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;chunkedCookieHandler&gt;
構成、 <xref:System.IdentityModel.Services.ChunkedCookieHandler>。  この要素のみが表示される場合、 `mode`属性の`<cookieHandler>` "Default"または「チャンク」です。  
  
## 構文  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|chunkSize|文字数を 1 つの HTTP cookie を HTTP cookie データの最大サイズです。  チャンクのサイズを調整する場合は慎重に行ってください。  Web ブラウザー cookie およびドメインごとに許可される数のサイズに異なる制限をあります。  これらの制限は、元の Netscape 仕様規定をされて: 300 cookie の合計、4096 バイト \(cookie 値だけでなくすべてのメタデータを含む\)、cookie ヘッダーごとおよびドメインごとの 20 の cookie。  既定値は 2000 です。  必ず指定します。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|構成、 <xref:System.IdentityModel.Services.CookieHandler>は、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) を使用して cookie を読み書きします。|  
  
## 解説  
 指定すると、 <xref:System.IdentityModel.Services.ChunkedCookieHandler>設定、 `mode`属性の`<cookieHandler>`要素には、"Default"または「チャンク」などで cookie の読み書きに cookie のハンドラーを使用して、チャンク サイズを指定することができます、 `<chunkedCookieHandler>`子要素および設定、 `chunkSize`属性。  場合は、 `<chunkedCookieHandler>`要素が存在しない、既定のチャンク サイズは 2000 バイトが使用されます。  この要素にすることはできませんが指定されて、 `mode`属性が「カスタム」に設定します。  
  
 `<chunkedCookieHandler>`要素で表される、 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>クラス。  
  
## 使用例  
 次の例では、cookie を 3000 バイトのチャンク単位で書き込むチャンク cookie ハンドラーを構成します。  
  
```  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## 参照  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>