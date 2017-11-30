---
title: "スレッドを作成し、開始時にデータを渡す"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="2831c-102">スレッドを作成し、開始時にデータを渡す</span><span class="sxs-lookup"><span data-stu-id="2831c-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="2831c-103">オペレーティング システム プロセスが作成されると、オペレーティング システムは、元のアプリケーション ドメインを含め、そのプロセスでコードを実行するスレッドを挿入します。</span><span class="sxs-lookup"><span data-stu-id="2831c-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="2831c-104">その時点から、アプリケーション ドメインを作成および破棄オペレーティング システム スレッドを必ずしも作成中または破棄します。</span><span class="sxs-lookup"><span data-stu-id="2831c-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="2831c-105">実行対象のコードが管理されている場合、コード、<xref:System.Threading.Thread>オブジェクトの静的なを取得することによって、現在のアプリケーション ドメインで実行するスレッドを取得できるの<xref:System.Threading.Thread.CurrentThread%2A>型のプロパティ<xref:System.Threading.Thread>です。</span><span class="sxs-lookup"><span data-stu-id="2831c-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="2831c-106">このトピックでは、スレッドの作成について説明し、データをスレッド プロシージャに渡すための代替案について説明します。</span><span class="sxs-lookup"><span data-stu-id="2831c-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="2831c-107">スレッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2831c-107">Creating a Thread</span></span>  
 <span data-ttu-id="2831c-108">新たに作成する<xref:System.Threading.Thread>オブジェクトは、新しいマネージ スレッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2831c-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="2831c-109"><xref:System.Threading.Thread>クラスを受け取るコンス トラクターには、<xref:System.Threading.ThreadStart>委任または<xref:System.Threading.ParameterizedThreadStart>委任; デリゲートを呼び出すときに、新しいスレッドで呼び出されるメソッドをラップする、<xref:System.Threading.Thread.Start%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2831c-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="2831c-110">呼び出す<xref:System.Threading.Thread.Start%2A>により複数回、<xref:System.Threading.ThreadStateException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2831c-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="2831c-111"><xref:System.Threading.Thread.Start%2A>メソッドを返しますすぐに、多くの場合、新しいスレッドが実際に開始する前にします。</span><span class="sxs-lookup"><span data-stu-id="2831c-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="2831c-112">使用することができます、<xref:System.Threading.Thread.ThreadState%2A>と<xref:System.Threading.Thread.IsAlive%2A>スレッドの活動を同期するためのプロパティを 1 つの時点でスレッドの状態の確認がこれらのプロパティを使用する必要があることはありません。</span><span class="sxs-lookup"><span data-stu-id="2831c-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2831c-113">参照を保持する必要はありませんは、スレッドの開始後、<xref:System.Threading.Thread>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2831c-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="2831c-114">スレッドは、スレッド プロシージャが終了するまでの実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="2831c-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="2831c-115">次のコード例では、別のオブジェクトのインスタンスと静的メソッドを呼び出す 2 つの新しいスレッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="2831c-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="2831c-116">データをスレッドに渡すと、スレッドからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="2831c-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="2831c-117">.NET framework version 2.0 では、<xref:System.Threading.ParameterizedThreadStart>デリゲートを呼び出すときに、スレッドにデータを格納するオブジェクトを渡すための簡単な方法を提供する、<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>メソッドのオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="2831c-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="2831c-118">コード例については、「<xref:System.Threading.ParameterizedThreadStart>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2831c-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="2831c-119">使用して、<xref:System.Threading.ParameterizedThreadStart>デリゲートは、タイプ セーフな方法、データを渡すため、<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>メソッドのオーバー ロードは、任意のオブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2831c-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="2831c-120">代わりに、スレッド処理とヘルパー クラスでデータをカプセル化しを使用し、<xref:System.Threading.ThreadStart>スレッド プロシージャを実行するデリゲート。</span><span class="sxs-lookup"><span data-stu-id="2831c-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="2831c-121">この手法は次の 2 つのコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="2831c-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="2831c-122">どちらの非同期呼び出しのデータを返す先がないために、デリゲートは戻り値。</span><span class="sxs-lookup"><span data-stu-id="2831c-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="2831c-123">スレッド メソッドの結果を取得するには、2 つ目のコード例で示すようにコールバック メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2831c-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="2831c-124">コールバック メソッドを使用してデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="2831c-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="2831c-125">次の例では、スレッドのスレッドからデータを取得するコールバック メソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="2831c-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="2831c-126">データおよびスレッド メソッドを含むクラスのコンス トラクターは、コールバック メソッドを表すデリゲートも受け取ります。スレッド メソッドが終了する前に、コールバック デリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2831c-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2831c-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="2831c-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2831c-128">スレッド化</span><span class="sxs-lookup"><span data-stu-id="2831c-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="2831c-129">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="2831c-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
