---
title: "接続の管理"
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
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a4d0ca3b6aed1213405dc24f322b53a21dbd4fbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="managing-connections"></a><span data-ttu-id="05702-102">接続の管理</span><span class="sxs-lookup"><span data-stu-id="05702-102">Managing Connections</span></span>
<span data-ttu-id="05702-103">HTTP を使用してデータ リソースに接続するアプリケーションは、.NET Framework の <xref:System.Net.ServicePoint> クラスと <xref:System.Net.ServicePointManager> クラスを使用してインターネットに対する接続を管理し、最適なスケールとパフォーマンスを達成することができます。</span><span class="sxs-lookup"><span data-stu-id="05702-103">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="05702-104">**ServicePoint** クラスは、アプリケーションがインターネット リソースにアクセスするときに、接続に使用できるエンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="05702-104">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="05702-105">各 **ServicePoint** には、接続間で最適化情報を共有してパフォーマンスを改善することで、インターネット サーバーとの接続を最適化できる情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="05702-105">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="05702-106">各 **ServicePoint** は、Uniform Resource Identifier (URI) で識別され、URI のスキーム識別子とホスト フラグメントに従って分類されます。</span><span class="sxs-lookup"><span data-stu-id="05702-106">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="05702-107">たとえば、スキーム識別子 (http) とホスト フラグメント (www.contoso.com) が同じため、1 つの **ServicePoint** インスタンスから URI http://www.contoso.com/index.htm と http://www.contoso.com/news.htm?date=today に対して要求が提供されます。</span><span class="sxs-lookup"><span data-stu-id="05702-107">For example, the same **ServicePoint** instance would provide requests to the URIs http://www.contoso.com/index.htm and http://www.contoso.com/news.htm?date=today since they have the same scheme identifier (http) and host fragments (www.contoso.com).</span></span> <span data-ttu-id="05702-108">サーバー www.contoso.com に対する永続的な接続が既にあるアプリケーションの場合、2 つの接続を作成する必要がないように、その接続を使用して両方の要求が取得されます。</span><span class="sxs-lookup"><span data-stu-id="05702-108">If the application already has a persistent connection to the server www.contoso.com, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="05702-109">**ServicePointManager** は、**ServicePoint** インスタンスの作成と破棄を管理する静的クラスです。</span><span class="sxs-lookup"><span data-stu-id="05702-109">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="05702-110">既存の **ServicePoint** インスタンスのコレクション内にないインターネット リソースをアプリケーションから要求された場合、**ServicePointManager** によって **ServicePoint** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="05702-110">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="05702-111">最大アイドル時間を超えた場合、または既存の **ServicePoint** インスタンスがアプリケーションの最大 **ServicePoint** インスタンス数を超えた場合、**ServicePoint** インスタンスは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="05702-111">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="05702-112">既定の最大アイドル時間と最大 **ServicePoint** インスタンス数はいずれも、**ServicePointManager** で <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> プロパティと <xref:System.Net.ServicePointManager.MaxServicePoints%2A> プロパティを設定して制御できます。</span><span class="sxs-lookup"><span data-stu-id="05702-112">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="05702-113">クライアントとサーバー間の接続数は、アプリケーションのスループットに大きな影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05702-113">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="05702-114">既定で、<xref:System.Net.HttpWebRequest> クラスを使用するアプリケーションは、特定のサーバーに対して最大で 2 つの永続的な接続を使用しますが、最大接続数はアプリケーションごとに設定できます。</span><span class="sxs-lookup"><span data-stu-id="05702-114">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05702-115">HTTP/1.1 仕様では、アプリケーションからの接続数をサーバーごとに 2 接続に制限しています。</span><span class="sxs-lookup"><span data-stu-id="05702-115">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="05702-116">最適な接続数は、アプリケーションが実行されている実際の条件によって変わります。</span><span class="sxs-lookup"><span data-stu-id="05702-116">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="05702-117">アプリケーションに使用できる接続数を増やしても、アプリケーションのパフォーマンスに影響しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05702-117">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="05702-118">接続数を増やした場合の影響を判断するには、接続数を変えながらパフォーマンス テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="05702-118">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="05702-119">アプリケーションが使用する接続数を変更するには、次のコード例のように、アプリケーションの初期化時に **ServicePointManager** クラスの静的な <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="05702-119">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="05702-120">**ServicePointManager.DefaultConnectionLimit** プロパティを変更しても、既に初期化されている **ServicePoint** インスタンスに影響はありません。</span><span class="sxs-lookup"><span data-stu-id="05702-120">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="05702-121">次のコードは、サーバー http://www.contoso.com の既存の **ServicePoint** の接続制限を、`newLimit` に保存されている値に変更する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="05702-121">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server http://www.contoso.com to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="05702-122">参照</span><span class="sxs-lookup"><span data-stu-id="05702-122">See Also</span></span>  
 [<span data-ttu-id="05702-123">接続のグループ化</span><span class="sxs-lookup"><span data-stu-id="05702-123">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)  
 [<span data-ttu-id="05702-124">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="05702-124">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
