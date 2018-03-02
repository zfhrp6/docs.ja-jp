---
title: "ミューテックス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2804d0c60657623b558d86386c5e1043422b648c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="mutexes"></a><span data-ttu-id="df066-102">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="df066-102">Mutexes</span></span>
<span data-ttu-id="df066-103"><xref:System.Threading.Mutex> オブジェクトを使用して、リソースへの排他的アクセスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="df066-103">You can use a <xref:System.Threading.Mutex> object to provide exclusive access to a resource.</span></span> <span data-ttu-id="df066-104"><xref:System.Threading.Mutex> クラスは <xref:System.Threading.Monitor> クラスよりも多くのシステム リソースを使用しますが、アプリケーション ドメイン境界を越えてマーシャリングしたり、複数の待機操作とともに使用したり、異なるプロセスのスレッドを同期するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="df066-104">The <xref:System.Threading.Mutex> class uses more system resources than the <xref:System.Threading.Monitor> class, but it can be marshaled across application domain boundaries, it can be used with multiple waits, and it can be used to synchronize threads in different processes.</span></span> <span data-ttu-id="df066-105">マネージ同期メカニズムの比較については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df066-105">For a comparison of managed synchronization mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="df066-106">コード例については、<xref:System.Threading.Mutex.%23ctor%2A> コンストラクターのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="df066-106">For code examples, see the reference documentation for the <xref:System.Threading.Mutex.%23ctor%2A> constructors.</span></span>  
  
## <a name="using-mutexes"></a><span data-ttu-id="df066-107">ミューテックスの使用</span><span class="sxs-lookup"><span data-stu-id="df066-107">Using Mutexes</span></span>  
 <span data-ttu-id="df066-108">スレッドはミューテックスの <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドを呼び出して、所有権を要求します。</span><span class="sxs-lookup"><span data-stu-id="df066-108">A thread calls the <xref:System.Threading.WaitHandle.WaitOne%2A> method of a mutex to request ownership.</span></span> <span data-ttu-id="df066-109">この呼び出しは、ミューテックスを使用できるようになるまで、あるいはオプションのタイムアウト期間を超過するまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="df066-109">The call blocks until the mutex is available, or until the optional timeout interval elapses.</span></span> <span data-ttu-id="df066-110">所有しているスレッドがない場合、ミューテックスはシグナル状態になります。</span><span class="sxs-lookup"><span data-stu-id="df066-110">The state of a mutex is signaled if no thread owns it.</span></span>  
  
 <span data-ttu-id="df066-111">スレッドは <xref:System.Threading.Mutex.ReleaseMutex%2A> メソッドを呼び出して、ミューテックスを解放します。</span><span class="sxs-lookup"><span data-stu-id="df066-111">A thread releases a mutex by calling its <xref:System.Threading.Mutex.ReleaseMutex%2A> method.</span></span> <span data-ttu-id="df066-112">ミューテックスにはスレッド アフィニティがあります。つまり、ミューテックスはそれを所有するスレッドによってのみ解放することができます。</span><span class="sxs-lookup"><span data-stu-id="df066-112">Mutexes have thread affinity; that is, the mutex can be released only by the thread that owns it.</span></span> <span data-ttu-id="df066-113">スレッドが所有していないミューテックスを解放すると、スレッドで <xref:System.ApplicationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="df066-113">If a thread releases a mutex it does not own, an <xref:System.ApplicationException> is thrown in the thread.</span></span>  
  
 <span data-ttu-id="df066-114"><xref:System.Threading.Mutex> クラスは <xref:System.Threading.WaitHandle> から派生するため、<xref:System.Threading.WaitHandle> の静的な <xref:System.Threading.WaitHandle.WaitAll%2A> または <xref:System.Threading.WaitHandle.WaitAny%2A> メソッドを呼び出し、他の待機ハンドルと組み合わせで <xref:System.Threading.Mutex> の所有権を要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="df066-114">Because the <xref:System.Threading.Mutex> class derives from <xref:System.Threading.WaitHandle>, you can also call the static <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> methods of <xref:System.Threading.WaitHandle> to request ownership of a <xref:System.Threading.Mutex> in combination with other wait handles.</span></span>  
  
 <span data-ttu-id="df066-115">スレッドが <xref:System.Threading.Mutex> を所有している場合、そのスレッドは待機要求呼び出しを繰り返し行うときに、実行をブロックせずに同じ <xref:System.Threading.Mutex> を指定できます。ただし、呼び出しと同じ回数だけ <xref:System.Threading.Mutex> を解放して、その所有権を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df066-115">If a thread owns a <xref:System.Threading.Mutex>, that thread can specify the same <xref:System.Threading.Mutex> in repeated wait-request calls without blocking its execution; however, it must release the <xref:System.Threading.Mutex> as many times to release ownership.</span></span>  
  
## <a name="abandoned-mutexes"></a><span data-ttu-id="df066-116">破棄済みミューテックス</span><span class="sxs-lookup"><span data-stu-id="df066-116">Abandoned Mutexes</span></span>  
 <span data-ttu-id="df066-117"><xref:System.Threading.Mutex> を解放せずにスレッドが終了すると、ミューテックスは破棄されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="df066-117">If a thread terminates without releasing a <xref:System.Threading.Mutex>, the mutex is said to be abandoned.</span></span> <span data-ttu-id="df066-118">ミューテックスが保護しているリソースが矛盾した状態で残る可能性があるため、多くの場合、これは重大なプログラミング エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="df066-118">This often indicates a serious programming error because the resource the mutex is protecting might be left in an inconsistent state.</span></span> <span data-ttu-id="df066-119">.NET Framework Version 2.0 では、ミューテックスを取得する次のスレッドで <xref:System.Threading.AbandonedMutexException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="df066-119">In the .NET Framework version 2.0, an <xref:System.Threading.AbandonedMutexException> is thrown in the next thread that acquires the mutex.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df066-120">.NET Framework Version 1.0 および 1.1 では、破棄された <xref:System.Threading.Mutex> はシグナル状態に設定され、次の待機スレッドが所有権を取得します。</span><span class="sxs-lookup"><span data-stu-id="df066-120">In the .NET Framework versions 1.0 and 1.1, an abandoned <xref:System.Threading.Mutex> is set to the signaled state and the next waiting thread gets ownership.</span></span> <span data-ttu-id="df066-121">待機しているスレッドがない場合、<xref:System.Threading.Mutex> はシグナル状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="df066-121">If no thread is waiting, the <xref:System.Threading.Mutex> remains in a signaled state.</span></span> <span data-ttu-id="df066-122">例外をスローすることはありません。</span><span class="sxs-lookup"><span data-stu-id="df066-122">No exception is thrown.</span></span>  
  
 <span data-ttu-id="df066-123">システム全体でミューテックスが有効な場合にミューテックスが破棄されたときは、アプリケーションが強制終了されたことを示している可能性があります (たとえば、Windows タスク マネージャを使用した終了)。</span><span class="sxs-lookup"><span data-stu-id="df066-123">In the case of a system-wide mutex, an abandoned mutex might indicate that an application has been terminated abruptly (for example, by using Windows Task Manager).</span></span>  
  
## <a name="local-and-system-mutexes"></a><span data-ttu-id="df066-124">ローカル ミューテックスとシステム ミューテックス</span><span class="sxs-lookup"><span data-stu-id="df066-124">Local and System Mutexes</span></span>  
 <span data-ttu-id="df066-125">ミュー テックスには、ローカル ミューテックスと名前付きシステム ミューテックスという 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="df066-125">Mutexes are of two types: local mutexes and named system mutexes.</span></span> <span data-ttu-id="df066-126">名前を受け入れるコンストラクターを使用して <xref:System.Threading.Mutex> オブジェクトを作成すると、そのオブジェクトがその名前のオペレーティング システム オブジェクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="df066-126">If you create a <xref:System.Threading.Mutex> object using a constructor that accepts a name, it is associated with an operating-system object of that name.</span></span> <span data-ttu-id="df066-127">名前付きシステム ミューテックスは、オペレーティング システム全体から参照でき、プロセスの動作を同期するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="df066-127">Named system mutexes are visible throughout the operating system and can be used to synchronize the activities of processes.</span></span> <span data-ttu-id="df066-128">同じ名前付きシステム ミューテックスを表す複数の <xref:System.Threading.Mutex> オブジェクトを作成できます。また、<xref:System.Threading.Mutex.OpenExisting%2A> メソッドを使用して、既存の名前付きシステム ミューテックスを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="df066-128">You can create multiple <xref:System.Threading.Mutex> objects that represent the same named system mutex, and you can use the <xref:System.Threading.Mutex.OpenExisting%2A> method to open an existing named system mutex.</span></span>  
  
 <span data-ttu-id="df066-129">ローカル ミューテックスは、現在のプロセス内にのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="df066-129">A local mutex exists only within your process.</span></span> <span data-ttu-id="df066-130">ローカル <xref:System.Threading.Mutex> オブジェクトを参照するプロセス内のすべてのスレッドから使用できます。</span><span class="sxs-lookup"><span data-stu-id="df066-130">It can be used by any thread in your process that has a reference to the local <xref:System.Threading.Mutex> object.</span></span> <span data-ttu-id="df066-131"><xref:System.Threading.Mutex> オブジェクトはそれぞれ別のローカル ミューテックスです。</span><span class="sxs-lookup"><span data-stu-id="df066-131">Each <xref:System.Threading.Mutex> object is a separate local mutex.</span></span>  
  
### <a name="access-control-security-for-system-mutexes"></a><span data-ttu-id="df066-132">システム ミューテックスのアクセス制御セキュリティ</span><span class="sxs-lookup"><span data-stu-id="df066-132">Access Control Security for System Mutexes</span></span>  
 <span data-ttu-id="df066-133">.NET Framework Version 2.0 では、名前付きシステム オブジェクトに対して Windows アクセス制御セキュリティを照会して設定できます。</span><span class="sxs-lookup"><span data-stu-id="df066-133">The .NET Framework version 2.0 provides the ability to query and set Windows access control security for named system objects.</span></span> <span data-ttu-id="df066-134">システム オブジェクトはグローバルであり、所有するコード以外のコードによってロックできるため、作成時からシステム ミューテックスを保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="df066-134">Protecting system mutexes from the moment of creation is recommended because system objects are global and therefore can be locked by code other than your own.</span></span>  
  
 <span data-ttu-id="df066-135">ミューテックスのアクセス制御セキュリティについては、<xref:System.Security.AccessControl.MutexSecurity> および <xref:System.Security.AccessControl.MutexAccessRule> クラス、<xref:System.Security.AccessControl.MutexRights> 列挙体、<xref:System.Threading.Mutex> クラスの <xref:System.Threading.Mutex.GetAccessControl%2A>、<xref:System.Threading.Mutex.SetAccessControl%2A>、<xref:System.Threading.Mutex.OpenExisting%2A> メソッド、<xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> コンストラクターに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="df066-135">For information on access control security for mutexes, see the <xref:System.Security.AccessControl.MutexSecurity> and <xref:System.Security.AccessControl.MutexAccessRule> classes, the <xref:System.Security.AccessControl.MutexRights> enumeration, the <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, and <xref:System.Threading.Mutex.OpenExisting%2A> methods of the <xref:System.Threading.Mutex> class, and the <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df066-136">参照</span><span class="sxs-lookup"><span data-stu-id="df066-136">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [<span data-ttu-id="df066-137">スレッド化</span><span class="sxs-lookup"><span data-stu-id="df066-137">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="df066-138">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="df066-138">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="df066-139">モニター</span><span class="sxs-lookup"><span data-stu-id="df066-139">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [<span data-ttu-id="df066-140">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="df066-140">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
