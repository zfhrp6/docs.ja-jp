---
title: ".NET Framework でのパイプ操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="0f4db-102">.NET Framework でのパイプ操作</span><span class="sxs-lookup"><span data-stu-id="0f4db-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="0f4db-103">パイプは、プロセス間通信の手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="0f4db-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="0f4db-104">パイプの 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="0f4db-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="0f4db-105">匿名パイプします。</span><span class="sxs-lookup"><span data-stu-id="0f4db-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="0f4db-106">匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="0f4db-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="0f4db-107">匿名パイプは、名前付きパイプよりもオーバーヘッドは小さくなりますが、限られたサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="0f4db-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="0f4db-108">匿名パイプは一方向であり、ネットワーク経由で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="0f4db-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="0f4db-109">1 台のサーバー インスタンスのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="0f4db-109">They support only a single server instance.</span></span> <span data-ttu-id="0f4db-110">匿名パイプは、スレッド間または場所パイプ ハンドルで簡単に渡すことが子プロセスの作成時に、親と子のプロセス間通信に便利です。</span><span class="sxs-lookup"><span data-stu-id="0f4db-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="0f4db-111">.NET framework を使用して匿名パイプを実装する、<xref:System.IO.Pipes.AnonymousPipeServerStream>と<xref:System.IO.Pipes.AnonymousPipeClientStream>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0f4db-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="0f4db-112">参照してください[する方法: 匿名パイプを使用して、ローカルのプロセス間通信に](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f4db-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="0f4db-113">名前付きパイプ。</span><span class="sxs-lookup"><span data-stu-id="0f4db-113">Named pipes.</span></span>  
  
     <span data-ttu-id="0f4db-114">名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。</span><span class="sxs-lookup"><span data-stu-id="0f4db-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="0f4db-115">名前付きパイプには、一方向または双方向を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0f4db-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="0f4db-116">メッセージ ベースの通信をサポートし、複数のクライアントが同時に同じパイプ名を使用して、サーバー プロセスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="0f4db-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="0f4db-117">名前付きパイプでは、プロセスを接続してリモート サーバーで独自のアクセス許可を使用するには、偽装もサポートします。</span><span class="sxs-lookup"><span data-stu-id="0f4db-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="0f4db-118">.NET framework を使用して名前付きパイプを実装する、<xref:System.IO.Pipes.NamedPipeServerStream>と<xref:System.IO.Pipes.NamedPipeClientStream>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0f4db-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="0f4db-119">参照してください[する方法: ネットワーク プロセス間通信に名前付きパイプを使用して](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f4db-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f4db-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f4db-120">See Also</span></span>  
 [<span data-ttu-id="0f4db-121">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="0f4db-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="0f4db-122">方法: ローカルのプロセス間通信で匿名パイプを使用する</span><span class="sxs-lookup"><span data-stu-id="0f4db-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="0f4db-123">方法: ネットワークのプロセス間通信で名前付きパイプを使用する</span><span class="sxs-lookup"><span data-stu-id="0f4db-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
