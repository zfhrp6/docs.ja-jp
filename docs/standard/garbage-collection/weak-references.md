---
title: "弱い参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a><span data-ttu-id="86f42-102">弱い参照</span><span class="sxs-lookup"><span data-stu-id="86f42-102">Weak References</span></span>
<span data-ttu-id="86f42-103">ガベージ コレクターでは、アプリケーションのコードがオブジェクトにアクセスできる間、そのアプリケーションで使用中のオブジェクトを収集することはできません。</span><span class="sxs-lookup"><span data-stu-id="86f42-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="86f42-104">アプリケーションには、オブジェクトへの強い参照があると考えられます。</span><span class="sxs-lookup"><span data-stu-id="86f42-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="86f42-105">弱い参照は、アプリケーションからオブジェクトへのアクセスを許容したまま、そのオブジェクトをガベージ コレクターが収集できるようにします。</span><span class="sxs-lookup"><span data-stu-id="86f42-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="86f42-106">弱い参照は、強い参照が存在しない場合に、オブジェクトが収集されるまでの不確定の期間中のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="86f42-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="86f42-107">弱い参照を使用すると、該当オブジェクトが収集されるのを回避するため、アプリケーションで強い参照を取得できます。</span><span class="sxs-lookup"><span data-stu-id="86f42-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="86f42-108">ただし、強い参照が再確立される前に、ガベージ コレクターが最初にオブジェクトにアクセスするリスクが常にあります。</span><span class="sxs-lookup"><span data-stu-id="86f42-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="86f42-109">弱い参照は、多くのメモリを使用するが、ガベージ コレクションによって回収される場合、簡単に再作成できるオブジェクトに便利です。</span><span class="sxs-lookup"><span data-stu-id="86f42-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="86f42-110">たとえば、Windows フォーム アプリケーションでのツリー ビューでは、オプションの場合は、複雑な階層的な選択をユーザーに表示します。</span><span class="sxs-lookup"><span data-stu-id="86f42-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="86f42-111">基になるデータが大きければ、ユーザーがアプリケーションで他の操作を行っている場合、ツリーをメモリ内に保持しても効果的ではありません。</span><span class="sxs-lookup"><span data-stu-id="86f42-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="86f42-112">ユーザーは、アプリケーションの別の部分に切り替えて、ときに行うこともできます、<xref:System.WeakReference>クラスをツリーへの弱い参照を作成し、すべての強力な参照を破棄します。</span><span class="sxs-lookup"><span data-stu-id="86f42-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="86f42-113">ユーザーがツリーに戻ると、アプリケーションはツリーへの強い参照を取得しようとします。成功した場合、ツリーの再作成は回避されます。</span><span class="sxs-lookup"><span data-stu-id="86f42-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="86f42-114">作成するオブジェクトの弱い参照を確立するために、<xref:System.WeakReference>追跡対象となるオブジェクトのインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="86f42-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="86f42-115">設定して、<xref:System.WeakReference.Target%2A>にそのオブジェクトを設定し、オブジェクトへの参照を元のプロパティ`null`です。</span><span class="sxs-lookup"><span data-stu-id="86f42-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="86f42-116">コード例は、次を参照してください。<xref:System.WeakReference>クラス ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="86f42-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="86f42-117">短期間と長期間の弱い参照</span><span class="sxs-lookup"><span data-stu-id="86f42-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="86f42-118">短期間の弱い参照または長期間の弱い参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="86f42-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="86f42-119">Short</span><span class="sxs-lookup"><span data-stu-id="86f42-119">Short</span></span>  
  
     <span data-ttu-id="86f42-120">短期間の弱い参照の対象は、オブジェクトがガベージ コレクションによって回収されると、`null` になります。</span><span class="sxs-lookup"><span data-stu-id="86f42-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="86f42-121">弱い参照自体が管理オブジェクトであり、その他の管理オブジェクトと同じようにガベージ コレクションの対象です。</span><span class="sxs-lookup"><span data-stu-id="86f42-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="86f42-122">短いの弱い参照は、既定のコンス トラクター<xref:System.WeakReference>です。</span><span class="sxs-lookup"><span data-stu-id="86f42-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="86f42-123">Long</span><span class="sxs-lookup"><span data-stu-id="86f42-123">Long</span></span>  
  
     <span data-ttu-id="86f42-124">長期間の弱い参照はオブジェクトの後に保持されます<xref:System.Object.Finalize%2A>メソッドが呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="86f42-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="86f42-125">これにより、オブジェクトが再作成されることを許可しますが、オブジェクトの状態は予測不可能なままです。</span><span class="sxs-lookup"><span data-stu-id="86f42-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="86f42-126">長い参照を使用する指定`true`で、<xref:System.WeakReference>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="86f42-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="86f42-127">オブジェクトの型がない場合、<xref:System.Object.Finalize%2A>メソッド、短い弱い参照機能を適用および弱い参照は有効なターゲットが収集されるまでの実行がファイナライザーの後にいつ発生する可能性はします。</span><span class="sxs-lookup"><span data-stu-id="86f42-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="86f42-128">強い参照を確立し、再度オブジェクトを使用するキャスト、<xref:System.WeakReference.Target%2A>のプロパティ、<xref:System.WeakReference>オブジェクトの型にします。</span><span class="sxs-lookup"><span data-stu-id="86f42-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="86f42-129">場合、<xref:System.WeakReference.Target%2A>プロパティから返される`null`オブジェクトが収集済みです。 それ以外の場合、アプリケーションが強い参照を再取得するためにオブジェクトを使用して続行することができます。</span><span class="sxs-lookup"><span data-stu-id="86f42-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="86f42-130">弱い参照を使用するためのガイドライン</span><span class="sxs-lookup"><span data-stu-id="86f42-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="86f42-131">終了処理後のオブジェクトの状態が予測できないため、長期間の弱い参照は必要な場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="86f42-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="86f42-132">ポインター自体が同程度の大きさか、より大きい場合があるため、小さなオブジェクトへの弱い参照を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="86f42-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="86f42-133">メモリ管理の問題への自動的な解決方法として、弱い参照を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="86f42-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="86f42-134">代わりに、アプリケーションのオブジェクトを処理するために、効果的なキャッシュ ポリシーを開発します。</span><span class="sxs-lookup"><span data-stu-id="86f42-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f42-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="86f42-135">See Also</span></span>  
 [<span data-ttu-id="86f42-136">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="86f42-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
