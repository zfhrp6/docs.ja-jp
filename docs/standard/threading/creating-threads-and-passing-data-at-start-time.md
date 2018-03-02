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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d17ef8a199061f56f00e39fa887e2e64f64427ec
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="723bd-102">スレッドを作成し、開始時にデータを渡す</span><span class="sxs-lookup"><span data-stu-id="723bd-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="723bd-103">オペレーティング システム プロセスが作成されると、オペレーティング システムは、元のアプリケーション ドメインを含め、そのプロセスでコードを実行するスレッドを挿入します。</span><span class="sxs-lookup"><span data-stu-id="723bd-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="723bd-104">その時点から、オペレーティング システム スレッドを作成または破棄せずに、アプリケーション ドメインを作成したり破棄したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="723bd-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="723bd-105">実行対象コードがマネージ コードである場合は、<xref:System.Threading.Thread> 型の静的 <xref:System.Threading.Thread.CurrentThread%2A> プロパティを取得することで、現在のアプリケーション ドメインで実行されるスレッドの <xref:System.Threading.Thread> オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="723bd-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="723bd-106">このトピックではスレッドの作成について説明し、データをスレッド プロシージャに渡すための代替手段について説明します。</span><span class="sxs-lookup"><span data-stu-id="723bd-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="723bd-107">スレッドの作成</span><span class="sxs-lookup"><span data-stu-id="723bd-107">Creating a Thread</span></span>  
 <span data-ttu-id="723bd-108">新しい <xref:System.Threading.Thread> オブジェクトを作成すると、新しいマネージ スレッドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="723bd-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="723bd-109"><xref:System.Threading.Thread> クラスには <xref:System.Threading.ThreadStart> デリゲートまたは <xref:System.Threading.ParameterizedThreadStart> デリゲートを受け取るコンストラクターがあります。デリゲートは、<xref:System.Threading.Thread.Start%2A> メソッドの呼び出し時に新しいスレッドで呼び出されるメソッドをラップします。</span><span class="sxs-lookup"><span data-stu-id="723bd-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="723bd-110">複数回 <xref:System.Threading.Thread.Start%2A> を呼び出すと、<xref:System.Threading.ThreadStateException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="723bd-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="723bd-111"><xref:System.Threading.Thread.Start%2A> メソッドはすぐに (多くの場合、新しいスレッドが実際に開始される前) 制御を返します。</span><span class="sxs-lookup"><span data-stu-id="723bd-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="723bd-112"><xref:System.Threading.Thread.ThreadState%2A> および <xref:System.Threading.Thread.IsAlive%2A> プロパティを使用して、任意の時点のスレッドの状態を判別できますが、スレッドのアクティビティを同期する場合にこれらのプロパティを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="723bd-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="723bd-113">スレッドが開始された後に、<xref:System.Threading.Thread> オブジェクトへの参照を保持する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="723bd-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="723bd-114">スレッドは、スレッド プロシージャが終了するまで、引き続き実行されます。</span><span class="sxs-lookup"><span data-stu-id="723bd-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="723bd-115">次のコード例では、2 つの新しいスレッドを作成し、別のオブジェクトでインスタンスおよび静的メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="723bd-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="723bd-116">スレッドへのデータの受け渡しとスレッドからのデータの取得</span><span class="sxs-lookup"><span data-stu-id="723bd-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="723bd-117">.NET framework Version 2.0 では、<xref:System.Threading.ParameterizedThreadStart> デリゲートは、<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> メソッド オーバーロードの呼び出し時にスレッドにデータを含むオブジェクトを渡すための簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="723bd-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="723bd-118">コード例については、「<xref:System.Threading.ParameterizedThreadStart>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="723bd-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="723bd-119"><xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> メソッド オーバーロードではすべてのオブジェクトを受け入れるため、<xref:System.Threading.ParameterizedThreadStart> デリゲートの使用はデータを渡すためのタイプ セーフな方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="723bd-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="723bd-120">代わりに、ヘルパー クラスにデータとスレッド プロシージャをカプセル化し、<xref:System.Threading.ThreadStart> デリゲートを使用して、スレッド プロシージャを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="723bd-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="723bd-121">この手法は、以下の 2 つのコード例で示されています。</span><span class="sxs-lookup"><span data-stu-id="723bd-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="723bd-122">非同期呼び出しからデータを返す場所がないため、いずれのデリゲートにも戻り値がありません。</span><span class="sxs-lookup"><span data-stu-id="723bd-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="723bd-123">スレッド メソッドの結果を取得するために、コールバック メソッドを使用することができます。これについては、2 つ目のコード例に示されています。</span><span class="sxs-lookup"><span data-stu-id="723bd-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="723bd-124">コールバック メソッドによるデータの取得</span><span class="sxs-lookup"><span data-stu-id="723bd-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="723bd-125">次の例では、スレッドからデータを取得するコールバック メソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="723bd-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="723bd-126">データとスレッド メソッドを含むクラスのコンストラクターは、コールバック メソッドを表すデリゲートも受け入れます。スレッド メソッドが終了する前に、コールバック デリゲートが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="723bd-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="723bd-127">参照</span><span class="sxs-lookup"><span data-stu-id="723bd-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="723bd-128">スレッド化</span><span class="sxs-lookup"><span data-stu-id="723bd-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="723bd-129">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="723bd-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
