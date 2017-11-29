---
title: HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 701ff252380ef93dbe3668c8aca73f08a8425d6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="http"></a><span data-ttu-id="35b52-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="35b52-102">HTTP</span></span>
<span data-ttu-id="35b52-103">.NET Framework ですべてのインターネット トラフィックの大部分を構成する HTTP プロトコルに対して包括的なサポートを提供する、<xref:System.Net.HttpWebRequest>と<xref:System.Net.HttpWebResponse>クラスです。</span><span class="sxs-lookup"><span data-stu-id="35b52-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="35b52-104"><xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> から派生したこれらのクラスは、静的メソッド <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> が "http" または "https" で始まる URI に遭遇するたびに既定で返されます。</span><span class="sxs-lookup"><span data-stu-id="35b52-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="35b52-105">ほとんどの場合、**WebRequest** クラスと **WebResponse** クラスは、要求を行うために必要なすべてを提供しますが、プロパティとして公開されている HTTP 固有の機能にアクセスする必要がある場合は、これらのクラスを **HttpWebRequest** または **HttpWebResponse** に型キャストすることができますです。</span><span class="sxs-lookup"><span data-stu-id="35b52-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="35b52-106">**HttpWebRequest** と **HttpWebResponse** は、標準の HTTP 要求-応答のトランザクションをカプセル化し、一般的な HTTP ヘッダーへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="35b52-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="35b52-107">これらのクラスは、パイプライン処理、チャック内データの送受信、認証、事前認証、暗号化、プロキシのサポート、サーバー証明書の検証、接続の管理を含むほとんどの HTTP 1.1 の機能もサポートします。</span><span class="sxs-lookup"><span data-stu-id="35b52-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="35b52-108">カスタム ヘッダー、およびプロパティを介して提供されていないヘッダーを格納し、**Headers** プロパティを介してアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="35b52-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="35b52-109">**HttpWebRequest** は、**WebRequest** によって使用される既定のクラスであり、**WebRequest.Create** メソッドに URI を渡す前に登録する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="35b52-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="35b52-110"><xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> プロパティを **true** (既定) に設定することで自動的に HTTP リダイレクトに従うアプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="35b52-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="35b52-111">アプリケーションが、要求をリダイレクトし、**HttpWebResponse** の <xref:System.Net.HttpWebResponse.ResponseUri%2A> プロパティに要求に応答した実際の Web リソースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="35b52-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="35b52-112">**AllowAutoRedirect** を **false** に設定した場合、アプリケーションは、HTTP プロトコル エラーとしてリダイレクトを処理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="35b52-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="35b52-113">アプリケーションでは、<xref:System.Net.WebException.Status%2A> を <xref:System.Net.WebExceptionStatus> に設定し、<xref:System.Net.WebException> をキャッチすることによって HTTP プロトコル エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="35b52-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="35b52-114"><xref:System.Net.WebException.Response%2A> プロパティは、サーバーによって送信された **WebResponse** を含み、実際の HTTP エラーがに発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="35b52-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b52-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="35b52-115">See Also</span></span>  
 [<span data-ttu-id="35b52-116">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="35b52-116">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="35b52-117">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="35b52-117">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="35b52-118">方法: HTTP 固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="35b52-118">How to: Access HTTP-Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
