---
title: ".NET Framework の並列処理と同時実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, parallel processing
- parallel processing [.NET Framework]
- concurrency [.NET Framework]
- .NET Framework, concurrency
ms.assetid: e573faa8-0212-44b1-a850-ce85dc54f47f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ab15fd38a467eec398f8383e40067d2135c042b5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="parallel-processing-and-concurrency-in-the-net-framework"></a><span data-ttu-id="ddcf7-102">.NET Framework の並列処理と同時実行</span><span class="sxs-lookup"><span data-stu-id="ddcf7-102">Parallel Processing and Concurrency in the .NET Framework</span></span>
<span data-ttu-id="ddcf7-103">.NET Framework には、ユーザーのコンピューターのパフォーマンスを最大化しながら、アプリケーションのユーザーに対する応答性を維持するために、複数の実行スレッドを使用する方法がいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="ddcf7-103">The .NET Framework provides several ways for you to use multiple threads of execution to keep your application responsive to your user while maximizing the performance of your user's computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddcf7-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ddcf7-104">In This Section</span></span>  
 [<span data-ttu-id="ddcf7-105">スレッド化</span><span class="sxs-lookup"><span data-stu-id="ddcf7-105">Threading</span></span>](../../docs/standard/threading/index.md)  
 <span data-ttu-id="ddcf7-106">.NET Framework に用意されている基本的な同時実行および同期のための機構について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddcf7-106">Describes the basic concurrency and synchronization mechanisms provided by the .NET Framework.</span></span>  
  
 [<span data-ttu-id="ddcf7-107">非同期プログラミングのパターン</span><span class="sxs-lookup"><span data-stu-id="ddcf7-107">Asynchronous Programming Patterns</span></span>](../../docs/standard/asynchronous-programming-patterns/index.md)  
 <span data-ttu-id="ddcf7-108">.NET Framework でサポートされている 3 種類の非同期パターンのプログラミングの概要が記載されています。</span><span class="sxs-lookup"><span data-stu-id="ddcf7-108">Provides a brief overview of the three asynchronous programming patterns supported in the .NET Framework:</span></span>  
  
-   <span data-ttu-id="ddcf7-109">[非同期プログラミング モデル (APM)](../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (レガシ)</span><span class="sxs-lookup"><span data-stu-id="ddcf7-109">[Asynchronous Programming Model (APM)](../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
-   <span data-ttu-id="ddcf7-110">[イベント ベースの非同期パターン (EAP)](../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (レガシ)</span><span class="sxs-lookup"><span data-stu-id="ddcf7-110">[Event-based Asynchronous Pattern (EAP)](../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
-   <span data-ttu-id="ddcf7-111">[タスク ベースの非同期パターン (TAP)](../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (新規の開発に推奨)</span><span class="sxs-lookup"><span data-stu-id="ddcf7-111">[Task-based Asynchronous Pattern (TAP)](../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  
  
 [<span data-ttu-id="ddcf7-112">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="ddcf7-112">Parallel Programming</span></span>](../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="ddcf7-113">並行開発を簡素化するタスクベースのプログラミング モデルについて説明します。このモデルにより、スレッドやスレッド プールを直接操作することなく、効率的で詳細な、拡張性のある並列コードを自然な表現方法で記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ddcf7-113">Describes a task-based programming model that simplifies parallel development, enabling you to write efficient, fine-grained, and scalable parallel code in a natural idiom without having to work directly with threads or the thread pool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcf7-114">参照</span><span class="sxs-lookup"><span data-stu-id="ddcf7-114">See Also</span></span>  
 [<span data-ttu-id="ddcf7-115">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="ddcf7-115">Development Guide</span></span>](../../docs/framework/development-guide.md)
