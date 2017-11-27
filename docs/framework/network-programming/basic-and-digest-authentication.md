---
title: "基本認証とダイジェスト認証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a72635cb77f23e2b87abb54f3f6a4438a3019f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="3fd71-102">基本認証とダイジェスト認証</span><span class="sxs-lookup"><span data-stu-id="3fd71-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="3fd71-103">基本認証とダイジェスト認証の <xref:System.Net> 実装では、RFC2617 – HTTP 認証: 基本認証とダイジェスト認証 (www.w3.org の World Wide Web コンソーシアム Web サイトで使用可能) に従います。</span><span class="sxs-lookup"><span data-stu-id="3fd71-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the World Wide Web Consortium's Web site at www.w3.org).</span></span>  
  
 <span data-ttu-id="3fd71-104">基本認証とダイジェスト認証を使用するには、次の例に示すように、アプリケーションはインターネットからデータを要求するために使用される <xref:System.Net.WebRequest> オブジェクトの <xref:System.Net.WebRequest.Credentials%2A> プロパティでユーザー名とパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fd71-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
>  <span data-ttu-id="3fd71-105">基本認証およびダイジェスト認証で送信されるデータは暗号化されないため、敵対者がデータを見ることができます。</span><span class="sxs-lookup"><span data-stu-id="3fd71-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="3fd71-106">また、基本認証の資格情報 (ユーザー名とパスワード) はクリア テキストで送信されるので、傍受される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3fd71-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd71-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fd71-107">See Also</span></span>  
 [<span data-ttu-id="3fd71-108">NTLM と Kerberos 認証</span><span class="sxs-lookup"><span data-stu-id="3fd71-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [<span data-ttu-id="3fd71-109">インターネット認証</span><span class="sxs-lookup"><span data-stu-id="3fd71-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
