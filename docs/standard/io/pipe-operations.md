---
title: .NET Framework でのパイプ操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e0d2747abbacf766ddeda6f41404d8701cbc273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="3166f-102">.NET Framework でのパイプ操作</span><span class="sxs-lookup"><span data-stu-id="3166f-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="3166f-103">パイプは、プロセス間通信の手段となります。</span><span class="sxs-lookup"><span data-stu-id="3166f-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="3166f-104">パイプには、2 種類あります。</span><span class="sxs-lookup"><span data-stu-id="3166f-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="3166f-105">匿名パイプ。</span><span class="sxs-lookup"><span data-stu-id="3166f-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="3166f-106">匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="3166f-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="3166f-107">匿名パイプは、名前付きパイプより必要なオーバーヘッドは少ないですが、提供するサービスは限られています。</span><span class="sxs-lookup"><span data-stu-id="3166f-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="3166f-108">匿名パイプは一方向であり、ネットワーク経由で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="3166f-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="3166f-109">これでは、1 つのサーバー インスタンスのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3166f-109">They support only a single server instance.</span></span> <span data-ttu-id="3166f-110">匿名パイプは、スレッド間、またはパイプ ハンドルを作成時に子プロセスに簡単に渡すことができる親と子のプロセス間の通信で便利です。</span><span class="sxs-lookup"><span data-stu-id="3166f-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="3166f-111">.NET Framework では、<xref:System.IO.Pipes.AnonymousPipeServerStream> と <xref:System.IO.Pipes.AnonymousPipeClientStream> クラスを使用して匿名パイプを実装します。</span><span class="sxs-lookup"><span data-stu-id="3166f-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="3166f-112">「[方法: ローカルのプロセス間通信で匿名パイプを使用する](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3166f-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="3166f-113">名前付きパイプ。</span><span class="sxs-lookup"><span data-stu-id="3166f-113">Named pipes.</span></span>  
  
     <span data-ttu-id="3166f-114">名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。</span><span class="sxs-lookup"><span data-stu-id="3166f-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="3166f-115">名前付きパイプは、一方向であることも、双方向であることも可能です。</span><span class="sxs-lookup"><span data-stu-id="3166f-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="3166f-116">これでは、メッセージ ベースの通信がサポートされ、同じパイプ名を使用して複数のクライアントが同時にサーバー プロセスに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="3166f-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="3166f-117">名前付きパイプでは、プロセスを接続してリモート サーバーで独自のアクセス許可を使用する、偽装もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3166f-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="3166f-118">.NET Framework では、<xref:System.IO.Pipes.NamedPipeServerStream> と <xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用して名前付きパイプを実装します。</span><span class="sxs-lookup"><span data-stu-id="3166f-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="3166f-119">「[方法: ネットワークのプロセス間通信で名前付きパイプを使用する](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3166f-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3166f-120">参照</span><span class="sxs-lookup"><span data-stu-id="3166f-120">See Also</span></span>  
 [<span data-ttu-id="3166f-121">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="3166f-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="3166f-122">方法: ローカルのプロセス間通信で匿名パイプを使用する</span><span class="sxs-lookup"><span data-stu-id="3166f-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="3166f-123">方法: ネットワークのプロセス間通信で名前付きパイプを使用する</span><span class="sxs-lookup"><span data-stu-id="3166f-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
