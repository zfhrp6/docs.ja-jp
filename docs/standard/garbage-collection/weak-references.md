---
title: 弱い参照
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03da36090c255f635036a9bd518bdacd99404ed4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575656"
---
# <a name="weak-references"></a><span data-ttu-id="7cf81-102">弱い参照</span><span class="sxs-lookup"><span data-stu-id="7cf81-102">Weak References</span></span>
<span data-ttu-id="7cf81-103">ガベージ コレクターでは、アプリケーションのコードがオブジェクトにアクセスできる間、そのアプリケーションで使用中のオブジェクトを収集することはできません。</span><span class="sxs-lookup"><span data-stu-id="7cf81-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="7cf81-104">アプリケーションには、オブジェクトへの強い参照があると考えられます。</span><span class="sxs-lookup"><span data-stu-id="7cf81-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="7cf81-105">弱い参照は、アプリケーションからオブジェクトへのアクセスを許容したまま、そのオブジェクトをガベージ コレクターが収集できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7cf81-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="7cf81-106">弱い参照は、強い参照が存在しない場合に、オブジェクトが収集されるまでの不確定の期間中のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="7cf81-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="7cf81-107">弱い参照を使用すると、該当オブジェクトが収集されるのを回避するため、アプリケーションで強い参照を取得できます。</span><span class="sxs-lookup"><span data-stu-id="7cf81-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="7cf81-108">ただし、強い参照が再確立される前に、ガベージ コレクターが最初にオブジェクトにアクセスするリスクが常にあります。</span><span class="sxs-lookup"><span data-stu-id="7cf81-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="7cf81-109">弱い参照は、多くのメモリを使用するが、ガベージ コレクションによって回収される場合、簡単に再作成できるオブジェクトに便利です。</span><span class="sxs-lookup"><span data-stu-id="7cf81-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="7cf81-110">Windows フォーム アプリケーションのツリー ビューに、複雑な階層形式のオプション選択がユーザーに示されているとします。</span><span class="sxs-lookup"><span data-stu-id="7cf81-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="7cf81-111">基になるデータが大きければ、ユーザーがアプリケーションで他の操作を行っている場合、ツリーをメモリ内に保持しても効果的ではありません。</span><span class="sxs-lookup"><span data-stu-id="7cf81-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="7cf81-112">ユーザーがアプリケーションの別の部分に切り替えている場合、<xref:System.WeakReference> クラスを使用して、ツリーへの弱い参照を作成し、すべての強い参照を破棄できます。</span><span class="sxs-lookup"><span data-stu-id="7cf81-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="7cf81-113">ユーザーがツリーに戻ると、アプリケーションはツリーへの強い参照を取得しようとします。成功した場合、ツリーの再作成は回避されます。</span><span class="sxs-lookup"><span data-stu-id="7cf81-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="7cf81-114">オブジェクトで弱い参照を確立するには、追跡されるオブジェクトのインスタンスを使用して、<xref:System.WeakReference> を作成します。</span><span class="sxs-lookup"><span data-stu-id="7cf81-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="7cf81-115">次に、そのオブジェクトの <xref:System.WeakReference.Target%2A> プロパティを設定して、オブジェクトへの元の参照を `null` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7cf81-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="7cf81-116">コード例については、クラス ライブラリの「<xref:System.WeakReference>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cf81-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="7cf81-117">短期間と長期間の弱い参照</span><span class="sxs-lookup"><span data-stu-id="7cf81-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="7cf81-118">短期間の弱い参照または長期間の弱い参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7cf81-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="7cf81-119">Short</span><span class="sxs-lookup"><span data-stu-id="7cf81-119">Short</span></span>  
  
     <span data-ttu-id="7cf81-120">短期間の弱い参照の対象は、オブジェクトがガベージ コレクションによって回収されると、`null` になります。</span><span class="sxs-lookup"><span data-stu-id="7cf81-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="7cf81-121">弱い参照自体が管理オブジェクトであり、その他の管理オブジェクトと同じようにガベージ コレクションの対象です。</span><span class="sxs-lookup"><span data-stu-id="7cf81-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="7cf81-122">短期間の弱い参照は、<xref:System.WeakReference> の既定のコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="7cf81-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="7cf81-123">Long</span><span class="sxs-lookup"><span data-stu-id="7cf81-123">Long</span></span>  
  
     <span data-ttu-id="7cf81-124">長期間の弱い参照は、オブジェクトの <xref:System.Object.Finalize%2A> メソッドが呼び出された後も保持されます。</span><span class="sxs-lookup"><span data-stu-id="7cf81-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="7cf81-125">これにより、オブジェクトが再作成されることを許可しますが、オブジェクトの状態は予測不可能なままです。</span><span class="sxs-lookup"><span data-stu-id="7cf81-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="7cf81-126">長い参照を使用するには、<xref:System.WeakReference> コンストラクターに `true` を指定します。</span><span class="sxs-lookup"><span data-stu-id="7cf81-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="7cf81-127">オブジェクトの型に <xref:System.Object.Finalize%2A> メソッドがない場合、短期間の弱い参照の機能が適用され、弱い参照はターゲットが収集されるまで有効です。これはファイナライザーを実行した後であれば、いつでも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7cf81-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="7cf81-128">強い参照を確立して、もう一度オブジェクトを使用するには、オブジェクトの型に <xref:System.WeakReference> の <xref:System.WeakReference.Target%2A> プロパティをキャストします。</span><span class="sxs-lookup"><span data-stu-id="7cf81-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="7cf81-129"><xref:System.WeakReference.Target%2A> プロパティが `null` を返す場合、オブジェクトが収集されます。それ以外の場合、アプリケーションがその強い参照を再取得するため、オブジェクトを使用し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="7cf81-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="7cf81-130">弱い参照を使用するためのガイドライン</span><span class="sxs-lookup"><span data-stu-id="7cf81-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="7cf81-131">終了処理後のオブジェクトの状態が予測できないため、長期間の弱い参照は必要な場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="7cf81-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="7cf81-132">ポインター自体が同程度の大きさか、より大きい場合があるため、小さなオブジェクトへの弱い参照を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7cf81-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="7cf81-133">メモリ管理の問題への自動的な解決方法として、弱い参照を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7cf81-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="7cf81-134">代わりに、アプリケーションのオブジェクトを処理するために、効果的なキャッシュ ポリシーを開発します。</span><span class="sxs-lookup"><span data-stu-id="7cf81-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf81-135">参照</span><span class="sxs-lookup"><span data-stu-id="7cf81-135">See Also</span></span>  
 [<span data-ttu-id="7cf81-136">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="7cf81-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
