---
title: "イベント ベースの非同期パターン (EAP)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b5f242b9586c4ea3b045daf8f10b84127b81085
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="19870-102">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="19870-102">Event-based Asynchronous Pattern (EAP)</span></span>
<span data-ttu-id="19870-103">非同期機能をクライアント コードに公開する方法は数多くあります。</span><span class="sxs-lookup"><span data-stu-id="19870-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="19870-104">イベント ベースの非同期パターンは、クラスが非同期動作を示す 1 つの方法を規定します。</span><span class="sxs-lookup"><span data-stu-id="19870-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19870-105">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、タスク並列ライブラリによって非同期/並列プログラミングの新しいモデルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="19870-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="19870-106">詳細については、[並列プログラミング](../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="19870-106">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19870-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="19870-107">In This Section</span></span>  
 [<span data-ttu-id="19870-108">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="19870-108">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="19870-109">イベント ベースの非同期パターンによって、マルチスレッド デザイン固有の多くの複雑な問題を気にせずに、マルチスレッド アプリケーションの利点を活用できるしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="19870-110">イベントベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="19870-110">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="19870-111">非同期機能を持つクラスをパッケージ化するための標準的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="19870-112">イベントベースの非同期パターンを実装するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="19870-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="19870-113">イベント ベースの非同期パターンに従って非同期機能を公開するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="19870-114">イベントベースの非同期パターンをいつ実装するかの決定</span><span class="sxs-lookup"><span data-stu-id="19870-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="19870-115">どのような場合に、<xref:System.IAsyncResult> パターンではなく、イベント ベースの非同期パターンの実装を選択するかを判断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="19870-116">チュートリアル: イベントベースの非同期パターンをサポートするコンポーネントの実装</span><span class="sxs-lookup"><span data-stu-id="19870-116">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="19870-117">イベント ベースの非同期パターンを実装するコンポーネントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="19870-117">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="19870-118">これは、<xref:System.ComponentModel?displayProperty=nameWithType> 名前空間のヘルパー クラスを使用して実装します。これにより、コンポーネントは任意のアプリケーション モデルで正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="19870-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="19870-119">方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する</span><span class="sxs-lookup"><span data-stu-id="19870-119">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="19870-120">イベント ベースの非同期パターンをサポートするコンポーネントの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-120">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="19870-121">参照</span><span class="sxs-lookup"><span data-stu-id="19870-121">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="19870-122"><xref:System.ComponentModel.AsyncOperation> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="19870-122">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="19870-123"><xref:System.ComponentModel.AsyncOperationManager> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="19870-123">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="19870-124"><xref:System.ComponentModel.BackgroundWorker> コンポーネントについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="19870-124">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="19870-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="19870-125">Related Sections</span></span>  
 [<span data-ttu-id="19870-126">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="19870-126">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="19870-127">非同期操作および並列操作のプログラミング モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-127">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="19870-128">スレッド化</span><span class="sxs-lookup"><span data-stu-id="19870-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="19870-129">.NET Framework のマルチスレッド機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-129">Describes multithreading features in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="19870-130">スレッド化</span><span class="sxs-lookup"><span data-stu-id="19870-130">Threading</span></span>](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 <span data-ttu-id="19870-131">C# 言語と Visual Basic 言語のマルチスレッド機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="19870-131">Describes multithreading features in the C# and Visual Basic languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19870-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="19870-132">See Also</span></span>  
 [<span data-ttu-id="19870-133">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="19870-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="19870-134">イベント</span><span class="sxs-lookup"><span data-stu-id="19870-134">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="19870-135">コンポーネントのマルチスレッド</span><span class="sxs-lookup"><span data-stu-id="19870-135">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="19870-136">非同期プログラミングのデザイン パターン</span><span class="sxs-lookup"><span data-stu-id="19870-136">Asynchronous Programming Design Patterns</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
