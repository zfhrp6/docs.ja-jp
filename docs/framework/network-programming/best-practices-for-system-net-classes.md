---
title: "System.Net クラスのベスト プラクティス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e50df22f66d4d55298aad5f3cc501dfb39ffcd9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="ffed0-102">System.Net クラスのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="ffed0-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="ffed0-103">次の推奨事項は、<xref:System.Net> に含まれるクラスを最大限に活用するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ffed0-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="ffed0-104">派生クラスに型キャストするのではなく、可能な限り、<xref:System.Net.WebRequest> および <xref:System.Net.WebResponse> を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffed0-104">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="ffed0-105">**WebRequest** と **WebResponse** を使用するアプリケーションでは、コードを大幅に変更せずに新しいインターネット プロトコルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="ffed0-105">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="ffed0-106">**System.Net** クラスを使用するサーバー上で実行する ASP.NET アプリケーションを作成する場合、一般に、パフォーマンスを考慮して、非同期メソッドを <xref:System.Net.WebRequest.GetResponse%2A> および <xref:System.Net.WebResponse.GetResponseStream%2A> に対して使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffed0-106">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="ffed0-107">インターネット リソースに対して開いている接続の数が、ネットワークのパフォーマンスやスループットに大きく影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ffed0-107">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="ffed0-108">既定では、**System.Net** は、各ホストのアプリケーションごとに 2 つの接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffed0-108">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="ffed0-109">アプリケーションの <xref:System.Net.ServicePoint> に <xref:System.Net.ServicePoint.ConnectionLimit%2A> プロパティを設定すると、特定のホストでこの数を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="ffed0-109">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="ffed0-110"><xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> プロパティを設定すると、すべてのホストでこの既定値を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="ffed0-110">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="ffed0-111">ソケット レベルのプロトコルを作成する場合は、<xref:System.Net.Sockets.Socket>に直接書き込むのではなく、可能な限り、<xref:System.Net.Sockets.TcpClient> または <xref:System.Net.Sockets.UdpClient> を使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ffed0-111">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="ffed0-112">これら 2 つのクライアント クラスは TCP ソケットおよび UDP ソケットの作成をカプセル化するため、接続の詳細を処理する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="ffed0-112">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="ffed0-113">資格情報を必要とするサイトにアクセスする場合、要求ごとに資格情報を入力するのではなく、<xref:System.Net.CredentialCache> クラスを使用して資格情報のキャッシュを作成します。</span><span class="sxs-lookup"><span data-stu-id="ffed0-113">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="ffed0-114">**CredentialCache** クラスがキャッシュを検索して要求で表示する適切な資格情報を検索するため、ユーザーは URL に基づいて資格情報を作成したり、表示したりする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="ffed0-114">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffed0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffed0-115">See Also</span></span>  
 [<span data-ttu-id="ffed0-116">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="ffed0-116">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
