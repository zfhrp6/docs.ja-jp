---
title: スレッドの使用とスレッド処理
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725a47cae6e3e91cf9e7385427bceece81f3c918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="90134-102">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="90134-102">Using Threads and Threading</span></span>
<span data-ttu-id="90134-103">このセクションのトピックでは、マネージ スレッドの作成と管理、マネージ スレッドにデータを渡して結果を戻す方法、およびスレッドを破棄して <xref:System.Threading.ThreadAbortException> を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90134-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90134-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="90134-104">In This Section</span></span>  
 [<span data-ttu-id="90134-105">スレッドを作成し、開始時にデータを渡す</span><span class="sxs-lookup"><span data-stu-id="90134-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="90134-106">データを新しいスレッドに渡す方法とデータを戻す方法など、マネージ スレッドの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="90134-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="90134-107">スレッドの一時中断と再開</span><span class="sxs-lookup"><span data-stu-id="90134-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="90134-108">マネージ スレッドの一時中断と再開の影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="90134-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="90134-109">スレッドの破棄</span><span class="sxs-lookup"><span data-stu-id="90134-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="90134-110">マネージ スレッドの破棄の影響と、<xref:System.Threading.ThreadAbortException> の処理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90134-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="90134-111">スレッドのスケジューリング</span><span class="sxs-lookup"><span data-stu-id="90134-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="90134-112">スレッドの優先順位とスレッドのスケジューリングへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="90134-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90134-113">参照</span><span class="sxs-lookup"><span data-stu-id="90134-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="90134-114"><xref:System.Threading.Thread> クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="90134-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="90134-115">パラメーターなしのスレッド プロシージャを表す <xref:System.Threading.ThreadStart> デリゲートに関するリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="90134-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="90134-116">厳密な型指定はありませんが、スレッド プロシージャにデータを渡す簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="90134-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="90134-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="90134-117">Related Sections</span></span>  
 [<span data-ttu-id="90134-118">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="90134-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="90134-119">マネージ スレッドの概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="90134-119">Provides an introduction to managed threading.</span></span>
