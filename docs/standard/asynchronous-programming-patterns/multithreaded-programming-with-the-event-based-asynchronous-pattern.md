---
title: イベント ベースの非同期パターンを使用したマルチスレッド プログラミング
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
ms.openlocfilehash: 26e555a158ced352c297952b56f7557cbd825cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a><span data-ttu-id="e2f41-102">イベント ベースの非同期パターンを使用したマルチスレッド プログラミング</span><span class="sxs-lookup"><span data-stu-id="e2f41-102">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="e2f41-103">非同期機能をクライアント コードに公開する方法は数多くあります。</span><span class="sxs-lookup"><span data-stu-id="e2f41-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="e2f41-104">イベント ベースの非同期パターンは、非同期動作を示すクラスに対して推奨される方法を規定します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-104">The Event-based Asynchronous Pattern prescribes the recommended way for classes to present asynchronous behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2f41-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e2f41-105">In This Section</span></span>  
 [<span data-ttu-id="e2f41-106">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="e2f41-106">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="e2f41-107">イベント ベースの非同期パターンによって、マルチスレッド デザイン固有の多くの複雑な問題を気にせずに、マルチスレッド アプリケーションの利点を活用できるしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-107">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="e2f41-108">イベントベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="e2f41-108">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e2f41-109">非同期機能を持つクラスをパッケージ化するための標準的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-109">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="e2f41-110">イベントベースの非同期パターンを実装するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="e2f41-110">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e2f41-111">イベント ベースの非同期パターンに従って非同期機能を公開するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-111">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="e2f41-112">イベントベースの非同期パターンをいつ実装するかの決定</span><span class="sxs-lookup"><span data-stu-id="e2f41-112">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e2f41-113">どのような場合に、<xref:System.IAsyncResult> パターンではなく、イベント ベースの非同期パターンの実装を選択するかを判断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-113">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="e2f41-114">チュートリアル: イベントベースの非同期パターンをサポートするコンポーネントの実装</span><span class="sxs-lookup"><span data-stu-id="e2f41-114">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e2f41-115">イベント ベースの非同期パターンを実装するコンポーネントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-115">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="e2f41-116">これは、<xref:System.ComponentModel?displayProperty=nameWithType> 名前空間のヘルパー クラスを使用して実装します。これにより、コンポーネントは任意のアプリケーション モデルで正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-116">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="e2f41-117">方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する</span><span class="sxs-lookup"><span data-stu-id="e2f41-117">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="e2f41-118">イベント ベースの非同期パターンをサポートするコンポーネントの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-118">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e2f41-119">参照</span><span class="sxs-lookup"><span data-stu-id="e2f41-119">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="e2f41-120"><xref:System.ComponentModel.AsyncOperation> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-120">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="e2f41-121"><xref:System.ComponentModel.AsyncOperationManager> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-121">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="e2f41-122"><xref:System.ComponentModel.BackgroundWorker> コンポーネントについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="e2f41-122">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f41-123">参照</span><span class="sxs-lookup"><span data-stu-id="e2f41-123">See Also</span></span>  
 [<span data-ttu-id="e2f41-124">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="e2f41-124">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="e2f41-125">イベント</span><span class="sxs-lookup"><span data-stu-id="e2f41-125">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="e2f41-126">コンポーネントのマルチスレッド</span><span class="sxs-lookup"><span data-stu-id="e2f41-126">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="e2f41-127">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="e2f41-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
