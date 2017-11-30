---
title: "スレッド ローカル ストレージ : スレッド相対静的フィールドとデータ スロット"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39dd80d378171563f2aadadaa146278e8a417d32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a><span data-ttu-id="31cee-102">スレッド ローカル ストレージ : スレッド相対静的フィールドとデータ スロット</span><span class="sxs-lookup"><span data-stu-id="31cee-102">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>
<span data-ttu-id="31cee-103">マネージ スレッド ローカル ストレージ (TLS) データを格納するスレッドおよびアプリケーション ドメインに一意であるを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="31cee-103">You can use managed thread local storage (TLS) to store data that is unique to a thread and application domain.</span></span> <span data-ttu-id="31cee-104">.NET Framework には 2 つの方法を使用するマネージ TLS: スレッド相対静的フィールドとデータ スロット。</span><span class="sxs-lookup"><span data-stu-id="31cee-104">The .NET Framework provides two ways to use managed TLS: thread-relative static fields and data slots.</span></span>  
  
-   <span data-ttu-id="31cee-105">スレッド相対静的フィールドを使用して (スレッド相対`Shared`Visual Basic でのフィールド) コンパイル時にニーズに正確に予測できる場合です。</span><span class="sxs-lookup"><span data-stu-id="31cee-105">Use thread-relative static fields (thread-relative `Shared` fields in Visual Basic) if you can anticipate your exact needs at compile time.</span></span> <span data-ttu-id="31cee-106">スレッド相対静的フィールドは、最高のパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="31cee-106">Thread-relative static fields provide the best performance.</span></span> <span data-ttu-id="31cee-107">コンパイル時の型チェックの利点も提供します。</span><span class="sxs-lookup"><span data-stu-id="31cee-107">They also give you the benefits of compile-time type checking.</span></span>  
  
-   <span data-ttu-id="31cee-108">実際の要件は実行時にしか検出される可能性がありますとデータ スロットを使用します。</span><span class="sxs-lookup"><span data-stu-id="31cee-108">Use data slots when your actual requirements might be discovered only at run time.</span></span> <span data-ttu-id="31cee-109">データ スロットは、速度は遅くなりにくいという、スレッド相対静的フィールドよりも使用して、データ型として格納されます<xref:System.Object>ので、使用する前に、正しい型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="31cee-109">Data slots are slower and more awkward to use than thread-relative static fields, and data is stored as type <xref:System.Object>, so you must cast it to the correct type before you use it.</span></span>  
  
 <span data-ttu-id="31cee-110">使用するアンマネージ C++ で`TlsAlloc`スロットを動的に割り当てると`__declspec(thread)`スレッド相対ストレージで変数を割り当てる必要があることを宣言します。</span><span class="sxs-lookup"><span data-stu-id="31cee-110">In unmanaged C++, you use `TlsAlloc` to allocate slots dynamically and `__declspec(thread)` to declare that a variable should be allocated in thread-relative storage.</span></span> <span data-ttu-id="31cee-111">スレッド相対静的フィールドとデータ スロットは、この動作の管理対象のバージョンを提供します。</span><span class="sxs-lookup"><span data-stu-id="31cee-111">Thread-relative static fields and data slots provide the managed version of this behavior.</span></span>  
  
 <span data-ttu-id="31cee-112">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、使用することができます、<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>オブジェクトが最初に使用された場合に遅れて初期化されるスレッド ローカル オブジェクトを作成するクラス。</span><span class="sxs-lookup"><span data-stu-id="31cee-112">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to create thread-local objects that are initialized lazily when the object is first consumed.</span></span> <span data-ttu-id="31cee-113">詳細については、「[限定的な初期化](../../../docs/framework/performance/lazy-initialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31cee-113">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="uniqueness-of-data-in-managed-tls"></a><span data-ttu-id="31cee-114">管理されている TLS でのデータの一意性</span><span class="sxs-lookup"><span data-stu-id="31cee-114">Uniqueness of Data in Managed TLS</span></span>  
 <span data-ttu-id="31cee-115">スレッド相対静的フィールドまたはデータ スロットを使用するかどうかは、管理されている TLS でのデータをスレッドおよびアプリケーション ドメインの組み合わせに一意です。</span><span class="sxs-lookup"><span data-stu-id="31cee-115">Whether you use thread-relative static fields or data slots, data in managed TLS is unique to the combination of thread and application domain.</span></span>  
  
-   <span data-ttu-id="31cee-116">アプリケーション ドメイン内で 1 つのスレッドは両方のスレッドが同じフィールドまたはスロットを使用する場合でも、別のスレッドからのデータを変更できません。</span><span class="sxs-lookup"><span data-stu-id="31cee-116">Within an application domain, one thread cannot modify data from another thread, even when both threads use the same field or slot.</span></span>  
  
-   <span data-ttu-id="31cee-117">スレッドには、複数のアプリケーション ドメインからの同じフィールドまたはスロットがアクセスする、アプリケーション ドメインごとに別個の値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="31cee-117">When a thread accesses the same field or slot from multiple application domains, a separate value is maintained in each application domain.</span></span>  
  
 <span data-ttu-id="31cee-118">たとえば、スレッドの設定、スレッド相対静的フィールドの値が別のアプリケーション ドメインに入るし、フィールドの値を取得し、2 つ目のアプリケーション ドメインで取得した値は、最初のアプリケーション ドメインの値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="31cee-118">For example, if a thread sets the value of a thread-relative static field, enters another application domain, and then retrieves the value of the field, the value retrieved in the second application domain differs from the value in the first application domain.</span></span> <span data-ttu-id="31cee-119">2 つ目のアプリケーション ドメインで、フィールドの新しい値を設定しても、最初のアプリケーション ドメインにあるフィールドの値には影響しません。</span><span class="sxs-lookup"><span data-stu-id="31cee-119">Setting a new value for the field in the second application domain does not affect the field's value in the first application domain.</span></span>  
  
 <span data-ttu-id="31cee-120">同様に、スレッドは、次の 2 つの異なるアプリケーション ドメインで同じ名前付きデータ スロットを取得、ときに最初のアプリケーション ドメイン内のデータは、2 つ目のアプリケーション ドメイン内のデータの独立したままです。</span><span class="sxs-lookup"><span data-stu-id="31cee-120">Similarly, when a thread gets the same named data slot in two different application domains, the data in the first application domain remains independent of the data in the second application domain.</span></span>  
  
## <a name="thread-relative-static-fields"></a><span data-ttu-id="31cee-121">スレッド相対静的フィールド</span><span class="sxs-lookup"><span data-stu-id="31cee-121">Thread-Relative Static Fields</span></span>  
 <span data-ttu-id="31cee-122">データの一部が一意でスレッドおよびアプリケーション ドメインの組み合わせを常にある場合は、適用、<xref:System.ThreadStaticAttribute>静的フィールドに属性します。</span><span class="sxs-lookup"><span data-stu-id="31cee-122">If you know that a piece of data is always unique to a thread and application-domain combination, apply the <xref:System.ThreadStaticAttribute> attribute to the static field.</span></span> <span data-ttu-id="31cee-123">その他の静的フィールドで使用すると、フィールドを使用します。</span><span class="sxs-lookup"><span data-stu-id="31cee-123">Use the field as you would use any other static field.</span></span> <span data-ttu-id="31cee-124">フィールドのデータは、それを使用する各スレッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="31cee-124">The data in the field is unique to each thread that uses it.</span></span>  
  
 <span data-ttu-id="31cee-125">スレッド相対静的フィールドは、データ スロットよりもパフォーマンスが向上して、コンパイル時の型チェックの利点があります。</span><span class="sxs-lookup"><span data-stu-id="31cee-125">Thread-relative static fields provide better performance than data slots and have the benefit of compile-time type checking.</span></span>  
  
 <span data-ttu-id="31cee-126">すべてのクラス コンス トラクター コード フィールドにアクセスする最初のコンテキストの最初のスレッドで実行されるに注意してください。</span><span class="sxs-lookup"><span data-stu-id="31cee-126">Be aware that any class constructor code will run on the first thread in the first context that accesses the field.</span></span> <span data-ttu-id="31cee-127">他のすべてのスレッドまたは同じアプリケーション ドメイン内のコンテキストで、フィールドが初期化する`null`(`Nothing` Visual Basic で) かどうかは、参照型ではまたはしている場合の値の型の値、既定値にします。</span><span class="sxs-lookup"><span data-stu-id="31cee-127">In all other threads or contexts in the same application domain, the fields will be initialized to `null` (`Nothing` in Visual Basic) if they are reference types, or to their default values if they are value types.</span></span> <span data-ttu-id="31cee-128">そのため、クラス コンス トラクターを使用してスレッド相対静的フィールドを初期化しないでください。</span><span class="sxs-lookup"><span data-stu-id="31cee-128">Therefore, you should not rely on class constructors to initialize thread-relative static fields.</span></span> <span data-ttu-id="31cee-129">代わりに、初期化回避スレッド相対静的フィールドと仮定に初期化されます`null`(`Nothing`) または既定値にします。</span><span class="sxs-lookup"><span data-stu-id="31cee-129">Instead, avoid initializing thread-relative static fields and assume that they are initialized to `null` (`Nothing`) or to their default values.</span></span>  
  
## <a name="data-slots"></a><span data-ttu-id="31cee-130">データ スロット</span><span class="sxs-lookup"><span data-stu-id="31cee-130">Data Slots</span></span>  
 <span data-ttu-id="31cee-131">.NET Framework では、スレッドおよびアプリケーション ドメインの組み合わせに固有の動的なデータ スロットを提供します。</span><span class="sxs-lookup"><span data-stu-id="31cee-131">The .NET Framework provides dynamic data slots that are unique to a combination of thread and application-domain.</span></span> <span data-ttu-id="31cee-132">データ スロットの 2 種類があります: スロット、および名前のないスロットをという名前です。</span><span class="sxs-lookup"><span data-stu-id="31cee-132">There are two types of data slots: named slots and unnamed slots.</span></span> <span data-ttu-id="31cee-133">使用して実装されます両方、<xref:System.LocalDataStoreSlot>構造体。</span><span class="sxs-lookup"><span data-stu-id="31cee-133">Both are implemented by using the <xref:System.LocalDataStoreSlot> structure.</span></span>  
  
-   <span data-ttu-id="31cee-134">名前付きデータ スロットを作成するには、使用、<xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType>または<xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="31cee-134">To create a named data slot, use the <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> or <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="31cee-135">既存の名前付きのスロットへの参照を取得するには、自分の名前を渡します、<xref:System.Threading.Thread.GetNamedDataSlot%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="31cee-135">To get a reference to an existing named slot, pass its name to the <xref:System.Threading.Thread.GetNamedDataSlot%2A> method.</span></span>  
  
-   <span data-ttu-id="31cee-136">無名のデータ スロットを作成するには、使用、<xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="31cee-136">To create an unnamed data slot, use the <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="31cee-137">という名前し、スロットの名前の両方を使用して、<xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType>と<xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType>設定して、スロット内の情報を取得するメソッド。</span><span class="sxs-lookup"><span data-stu-id="31cee-137">For both named and unnamed slots, use the <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> methods to set and retrieve the information in the slot.</span></span> <span data-ttu-id="31cee-138">これらは、常に実行されているスレッドのデータを操作する静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="31cee-138">These are static methods that always act on the data for the thread that is currently executing them.</span></span>  
  
 <span data-ttu-id="31cee-139">名前付きスロットは便利、その名前を渡すことによって必要なときに、スロットを取得できるため、<xref:System.Threading.Thread.GetNamedDataSlot%2A>メソッドの名前のないスロットへの参照を維持するのではなく、します。</span><span class="sxs-lookup"><span data-stu-id="31cee-139">Named slots can be convenient, because you can retrieve the slot when you need it by passing its name to the <xref:System.Threading.Thread.GetNamedDataSlot%2A> method, instead of maintaining a reference to an unnamed slot.</span></span> <span data-ttu-id="31cee-140">ただし、別のコンポーネントがそのスレッド相対ストレージに対して同じ名前を使用して、スレッド コンポーネントとその他のコンポーネントの両方からコードを実行する場合は、2 つのコンポーネントにそれぞれのデータが破損している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="31cee-140">However, if another component uses the same name for its thread-relative storage and a thread executes code from both your component and the other component, the two components might corrupt each other's data.</span></span> <span data-ttu-id="31cee-141">(このシナリオでは、両方のコンポーネントが、同じアプリケーション ドメインで実行されていることと同じデータを共有するが設計されていません。)</span><span class="sxs-lookup"><span data-stu-id="31cee-141">(This scenario assumes that both components are running in the same application domain, and that they are not designed to share the same data.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31cee-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="31cee-142">See Also</span></span>  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [<span data-ttu-id="31cee-143">スレッド化</span><span class="sxs-lookup"><span data-stu-id="31cee-143">Threading</span></span>](../../../docs/standard/threading/index.md)
