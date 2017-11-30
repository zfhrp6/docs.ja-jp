---
title: "スレッドの使用とスレッド処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80eb4c3bb98acdd1f83dbf5bcf57b2f7b295742b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="5540f-102">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="5540f-102">Using Threads and Threading</span></span>
<span data-ttu-id="5540f-103">このセクションのトピックでは、作成と管理のマネージ スレッド、マネージ スレッドにデータを渡すし、結果を取得する方法、およびスレッドの破棄を処理する方法について説明、<xref:System.Threading.ThreadAbortException>です。</span><span class="sxs-lookup"><span data-stu-id="5540f-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5540f-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5540f-104">In This Section</span></span>  
 [<span data-ttu-id="5540f-105">スレッドを作成し、開始時にデータを渡す</span><span class="sxs-lookup"><span data-stu-id="5540f-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="5540f-106">について説明し、データを取得する方法と、新しいスレッドにデータを渡す方法を含め、マネージ スレッドの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5540f-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="5540f-107">スレッドの一時中断と再開</span><span class="sxs-lookup"><span data-stu-id="5540f-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="5540f-108">一時停止と再開のマネージ スレッドがもたらす影響をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5540f-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="5540f-109">スレッドの破棄</span><span class="sxs-lookup"><span data-stu-id="5540f-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="5540f-110">マネージ スレッドは、および処理する方法を破棄するがもたらす影響について説明します、<xref:System.Threading.ThreadAbortException>です。</span><span class="sxs-lookup"><span data-stu-id="5540f-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="5540f-111">スレッドのスケジューリング</span><span class="sxs-lookup"><span data-stu-id="5540f-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="5540f-112">スレッドの優先順位とスレッドのスケジューリング影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="5540f-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5540f-113">参照</span><span class="sxs-lookup"><span data-stu-id="5540f-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="5540f-114">リファレンス ドキュメントを提供、<xref:System.Threading.Thread>クラスで、送信元は、アンマネージ コードまたはマネージ アプリケーションで作成されたかどうか、マネージ スレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="5540f-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="5540f-115">リファレンス ドキュメントを提供、<xref:System.Threading.ThreadStart>パラメーターのないスレッド プロシージャを表すデリゲート。</span><span class="sxs-lookup"><span data-stu-id="5540f-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="5540f-116">ありませんが、厳密な型指定には、スレッド プロシージャにデータを渡すための簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="5540f-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5540f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5540f-117">Related Sections</span></span>  
 [<span data-ttu-id="5540f-118">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="5540f-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="5540f-119">マネージ スレッド処理の概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="5540f-119">Provides an introduction to managed threading.</span></span>
