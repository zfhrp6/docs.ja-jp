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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1d69c1b943d15b9ad8c80b4d7dbafebc54990ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mutexes"></a><span data-ttu-id="5ef70-102">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="5ef70-102">Mutexes</span></span>
<span data-ttu-id="5ef70-103">使用することができます、<xref:System.Threading.Mutex>リソースへの排他アクセスを提供するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5ef70-103">You can use a <xref:System.Threading.Mutex> object to provide exclusive access to a resource.</span></span> <span data-ttu-id="5ef70-104"><xref:System.Threading.Mutex>クラスよりも多くのシステム リソースを使用して、<xref:System.Threading.Monitor>クラスが、それをアプリケーション ドメインの境界を越えてマーシャ リングできる、複数の待機時間で使えるおよび異なるプロセスでスレッドを同期するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ef70-104">The <xref:System.Threading.Mutex> class uses more system resources than the <xref:System.Threading.Monitor> class, but it can be marshaled across application domain boundaries, it can be used with multiple waits, and it can be used to synchronize threads in different processes.</span></span> <span data-ttu-id="5ef70-105">マネージ同期メカニズムの比較については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ef70-105">For a comparison of managed synchronization mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="5ef70-106">コード例については、リファレンス ドキュメントを参照して、<xref:System.Threading.Mutex.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="5ef70-106">For code examples, see the reference documentation for the <xref:System.Threading.Mutex.%23ctor%2A> constructors.</span></span>  
  
## <a name="using-mutexes"></a><span data-ttu-id="5ef70-107">ミューテックスの使用</span><span class="sxs-lookup"><span data-stu-id="5ef70-107">Using Mutexes</span></span>  
 <span data-ttu-id="5ef70-108">スレッドが呼び出す、<xref:System.Threading.WaitHandle.WaitOne%2A>所有権を要求するミュー テックスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="5ef70-108">A thread calls the <xref:System.Threading.WaitHandle.WaitOne%2A> method of a mutex to request ownership.</span></span> <span data-ttu-id="5ef70-109">この呼び出しは、ミューテックスを使用できるようになるまで、あるいはオプションのタイムアウト期間を超過するまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="5ef70-109">The call blocks until the mutex is available, or until the optional timeout interval elapses.</span></span> <span data-ttu-id="5ef70-110">所有しているスレッドがない場合、ミューテックスはシグナル状態になります。</span><span class="sxs-lookup"><span data-stu-id="5ef70-110">The state of a mutex is signaled if no thread owns it.</span></span>  
  
 <span data-ttu-id="5ef70-111">スレッドが呼び出すことにより、ミュー テックスを解放その<xref:System.Threading.Mutex.ReleaseMutex%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5ef70-111">A thread releases a mutex by calling its <xref:System.Threading.Mutex.ReleaseMutex%2A> method.</span></span> <span data-ttu-id="5ef70-112">ミューテックスにはスレッド アフィニティがあります。つまり、ミューテックスはそれを所有するスレッドによってのみ解放することができます。</span><span class="sxs-lookup"><span data-stu-id="5ef70-112">Mutexes have thread affinity; that is, the mutex can be released only by the thread that owns it.</span></span> <span data-ttu-id="5ef70-113">スレッドが所有していないミュー テックスを解放する場合、<xref:System.ApplicationException>スレッドでスローされます。</span><span class="sxs-lookup"><span data-stu-id="5ef70-113">If a thread releases a mutex it does not own, an <xref:System.ApplicationException> is thrown in the thread.</span></span>  
  
 <span data-ttu-id="5ef70-114"><xref:System.Threading.Mutex>クラスから派生<xref:System.Threading.WaitHandle>、静的なを呼び出すこともできます<xref:System.Threading.WaitHandle.WaitAll%2A>または<xref:System.Threading.WaitHandle.WaitAny%2A>のメソッド<xref:System.Threading.WaitHandle>の所有権を要求する、<xref:System.Threading.Mutex>を他の組み合わせでは、待機ハンドル。</span><span class="sxs-lookup"><span data-stu-id="5ef70-114">Because the <xref:System.Threading.Mutex> class derives from <xref:System.Threading.WaitHandle>, you can also call the static <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> methods of <xref:System.Threading.WaitHandle> to request ownership of a <xref:System.Threading.Mutex> in combination with other wait handles.</span></span>  
  
 <span data-ttu-id="5ef70-115">スレッドが所有している場合、 <xref:System.Threading.Mutex>、スレッド、同じを指定することができます<xref:System.Threading.Mutex>; の実行をブロックすることがなく待機要求の連続呼び出しでただし、そのリリースする必要があります、<xref:System.Threading.Mutex>所有権を解放する回数だけです。</span><span class="sxs-lookup"><span data-stu-id="5ef70-115">If a thread owns a <xref:System.Threading.Mutex>, that thread can specify the same <xref:System.Threading.Mutex> in repeated wait-request calls without blocking its execution; however, it must release the <xref:System.Threading.Mutex> as many times to release ownership.</span></span>  
  
## <a name="abandoned-mutexes"></a><span data-ttu-id="5ef70-116">破棄済みミューテックス</span><span class="sxs-lookup"><span data-stu-id="5ef70-116">Abandoned Mutexes</span></span>  
 <span data-ttu-id="5ef70-117">スレッドが解放せずに終了した場合、 <xref:System.Threading.Mutex>、ミュー テックスを破棄すると言います。</span><span class="sxs-lookup"><span data-stu-id="5ef70-117">If a thread terminates without releasing a <xref:System.Threading.Mutex>, the mutex is said to be abandoned.</span></span> <span data-ttu-id="5ef70-118">ミューテックスが保護しているリソースが矛盾した状態で残る可能性があるため、多くの場合、これは重大なプログラミング エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="5ef70-118">This often indicates a serious programming error because the resource the mutex is protecting might be left in an inconsistent state.</span></span> <span data-ttu-id="5ef70-119">.NET framework version 2.0 では、<xref:System.Threading.AbandonedMutexException>ミュー テックスを取得する次のスレッドでスローされます。</span><span class="sxs-lookup"><span data-stu-id="5ef70-119">In the .NET Framework version 2.0, an <xref:System.Threading.AbandonedMutexException> is thrown in the next thread that acquires the mutex.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ef70-120">.NET Framework version 1.0 および 1.1 では、破棄済み、<xref:System.Threading.Mutex>取得所有権のスレッドが待機してと次のシグナルの状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="5ef70-120">In the .NET Framework versions 1.0 and 1.1, an abandoned <xref:System.Threading.Mutex> is set to the signaled state and the next waiting thread gets ownership.</span></span> <span data-ttu-id="5ef70-121">スレッドが待機していない場合、<xref:System.Threading.Mutex>シグナルの状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="5ef70-121">If no thread is waiting, the <xref:System.Threading.Mutex> remains in a signaled state.</span></span> <span data-ttu-id="5ef70-122">例外をスローすることはありません。</span><span class="sxs-lookup"><span data-stu-id="5ef70-122">No exception is thrown.</span></span>  
  
 <span data-ttu-id="5ef70-123">システム全体でミューテックスが有効な場合にミューテックスが破棄されたときは、アプリケーションが強制終了されたことを示している可能性があります (たとえば、Windows タスク マネージャを使用した終了)。</span><span class="sxs-lookup"><span data-stu-id="5ef70-123">In the case of a system-wide mutex, an abandoned mutex might indicate that an application has been terminated abruptly (for example, by using Windows Task Manager).</span></span>  
  
## <a name="local-and-system-mutexes"></a><span data-ttu-id="5ef70-124">ローカル ミューテックスとシステム ミューテックス</span><span class="sxs-lookup"><span data-stu-id="5ef70-124">Local and System Mutexes</span></span>  
 <span data-ttu-id="5ef70-125">ミュー テックスには、ローカル ミューテックスと名前付きシステム ミューテックスという 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="5ef70-125">Mutexes are of two types: local mutexes and named system mutexes.</span></span> <span data-ttu-id="5ef70-126">作成する場合、<xref:System.Threading.Mutex>オブジェクトの名前を受け取るコンス トラクターを使用してその名前のオペレーティング システム オブジェクトに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="5ef70-126">If you create a <xref:System.Threading.Mutex> object using a constructor that accepts a name, it is associated with an operating-system object of that name.</span></span> <span data-ttu-id="5ef70-127">名前付きシステム ミューテックスは、オペレーティング システム全体から参照でき、プロセスの動作を同期するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ef70-127">Named system mutexes are visible throughout the operating system and can be used to synchronize the activities of processes.</span></span> <span data-ttu-id="5ef70-128">複数作成できます<xref:System.Threading.Mutex>名前付きシステム ミュー テックスを同じを表すオブジェクトと、使用することができます、<xref:System.Threading.Mutex.OpenExisting%2A>を開くには、既存のメソッドに名前付きシステム ミュー テックスです。</span><span class="sxs-lookup"><span data-stu-id="5ef70-128">You can create multiple <xref:System.Threading.Mutex> objects that represent the same named system mutex, and you can use the <xref:System.Threading.Mutex.OpenExisting%2A> method to open an existing named system mutex.</span></span>  
  
 <span data-ttu-id="5ef70-129">ローカル ミューテックスは、現在のプロセス内にのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="5ef70-129">A local mutex exists only within your process.</span></span> <span data-ttu-id="5ef70-130">ローカルへの参照を含むプロセス内の任意のスレッドで使用できます<xref:System.Threading.Mutex>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5ef70-130">It can be used by any thread in your process that has a reference to the local <xref:System.Threading.Mutex> object.</span></span> <span data-ttu-id="5ef70-131">各<xref:System.Threading.Mutex>オブジェクトが別のローカル ミュー テックスです。</span><span class="sxs-lookup"><span data-stu-id="5ef70-131">Each <xref:System.Threading.Mutex> object is a separate local mutex.</span></span>  
  
### <a name="access-control-security-for-system-mutexes"></a><span data-ttu-id="5ef70-132">システム ミューテックスのアクセス制御セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5ef70-132">Access Control Security for System Mutexes</span></span>  
 <span data-ttu-id="5ef70-133">.NET Framework Version 2.0 では、名前付きシステム オブジェクトに対して Windows アクセス制御セキュリティを照会して設定できます。</span><span class="sxs-lookup"><span data-stu-id="5ef70-133">The .NET Framework version 2.0 provides the ability to query and set Windows access control security for named system objects.</span></span> <span data-ttu-id="5ef70-134">システム オブジェクトはグローバルであり、所有するコード以外のコードによってロックできるため、作成時からシステム ミューテックスを保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5ef70-134">Protecting system mutexes from the moment of creation is recommended because system objects are global and therefore can be locked by code other than your own.</span></span>  
  
 <span data-ttu-id="5ef70-135">ミュー テックスのアクセス制御セキュリティについては、次を参照してください、<xref:System.Security.AccessControl.MutexSecurity>と<xref:System.Security.AccessControl.MutexAccessRule>、クラス、<xref:System.Security.AccessControl.MutexRights>列挙体、 <xref:System.Threading.Mutex.GetAccessControl%2A>、 <xref:System.Threading.Mutex.SetAccessControl%2A>、と<xref:System.Threading.Mutex.OpenExisting%2A>のメソッド、<xref:System.Threading.Mutex>クラス、および、 。<xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="5ef70-135">For information on access control security for mutexes, see the <xref:System.Security.AccessControl.MutexSecurity> and <xref:System.Security.AccessControl.MutexAccessRule> classes, the <xref:System.Security.AccessControl.MutexRights> enumeration, the <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, and <xref:System.Threading.Mutex.OpenExisting%2A> methods of the <xref:System.Threading.Mutex> class, and the <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef70-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ef70-136">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [<span data-ttu-id="5ef70-137">スレッド化</span><span class="sxs-lookup"><span data-stu-id="5ef70-137">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="5ef70-138">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="5ef70-138">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="5ef70-139">モニター</span><span class="sxs-lookup"><span data-stu-id="5ef70-139">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [<span data-ttu-id="5ef70-140">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="5ef70-140">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
