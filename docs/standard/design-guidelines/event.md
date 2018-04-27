---
title: イベントのデザイン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3d66d4e137c52310710f8b178167ceb3cca042c7
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="event-design"></a><span data-ttu-id="9473b-102">イベントのデザイン</span><span class="sxs-lookup"><span data-stu-id="9473b-102">Event Design</span></span>
<span data-ttu-id="9473b-103">イベントは、コールバック (ユーザー コードを呼び出すために、フレームワークを許可するコンストラクト) の最も一般的に使用される形式です。</span><span class="sxs-lookup"><span data-stu-id="9473b-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="9473b-104">その他のコールバック機構には、デリゲート、仮想メンバー、およびプラグインのインターフェイス ベースを取得するメンバーが含まれます。ユーザビリティ調査においてからのデータは、開発者の大部分が快適他のコールバック機構を使用するよりもイベントを使用することを示します。</span><span class="sxs-lookup"><span data-stu-id="9473b-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="9473b-105">イベントは、Visual Studio および多くの言語に適切に統合されています。</span><span class="sxs-lookup"><span data-stu-id="9473b-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="9473b-106">イベントの 2 つのグループがあることを確認することが重要: 前のイベント、および状態が変更した後に発生するイベントと呼ばれる、システムの変更の状態の前に発生したイベントには後のイベントが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9473b-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="9473b-107">イベントの前の例としては`Form.Closing`フォームが閉じる前に、これが発生します。</span><span class="sxs-lookup"><span data-stu-id="9473b-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="9473b-108">後のイベントの例としては`Form.Closed`フォームが閉じられた後、これが発生します。</span><span class="sxs-lookup"><span data-stu-id="9473b-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="9473b-109">**✓ しないで**イベントではなく「"発生させる」や「トリガー」の「生成」という用語を使用</span><span class="sxs-lookup"><span data-stu-id="9473b-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="9473b-110">**✓ しないで**使用<xref:System.EventHandler%601?displayProperty=nameWithType>イベント ハンドラーとして使用する新しいデリゲートを手動で作成する代わりにします。</span><span class="sxs-lookup"><span data-stu-id="9473b-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="9473b-111">**✓ を検討してください**のサブクラスを使用して<xref:System.EventArgs>イベントの引数としてイベントをイベント メソッドを処理するデータを実行する必要はありませんが確実でない限り、その場合は行うこともできます、`EventArgs`を直接入力します。</span><span class="sxs-lookup"><span data-stu-id="9473b-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="9473b-112">API を使用して、出荷する場合`EventArgs`直接、しないことができますを互換性の問題なしイベントに実行されるようにデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="9473b-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="9473b-113">サブクラスを使用する場合でもかどうか、最初に完全に空ことができます必要なときに、サブクラスにプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="9473b-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="9473b-114">**✓ しないで**各イベントを生成するプロテクト仮想メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9473b-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="9473b-115">これは構造体、シール クラス、または静的イベントが、封印されていないクラスで静的でないイベントに適用します。</span><span class="sxs-lookup"><span data-stu-id="9473b-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="9473b-116">メソッドの目的は、上書きを使用して、イベントを処理する派生クラスの手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="9473b-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="9473b-117">オーバーライドは、派生クラスで基底クラスのイベントを処理するより柔軟で、高速より自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="9473b-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="9473b-118">規則では、メソッドの名前が"On"で開始する必要があり、イベントの名前の後にします。</span><span class="sxs-lookup"><span data-stu-id="9473b-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="9473b-119">派生クラスは、そのオーバーライドで、メソッドの基本実装を呼び出していないを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9473b-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="9473b-120">正常に動作する基本クラスに必要なメソッドでなんらかの処理を含めないことでこれを準備します。</span><span class="sxs-lookup"><span data-stu-id="9473b-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="9473b-121">**✓ しないで**イベントを発生させる保護されたメソッドを 1 つのパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9473b-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="9473b-122">パラメーターの名前が付けられます`e`と、イベント引数クラスとして自動的に入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9473b-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="9473b-123">**X しないで**静的でないイベントを発生させる場合するセンダとして null を渡します。</span><span class="sxs-lookup"><span data-stu-id="9473b-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="9473b-124">**✓ しないで**静的イベントを発生させる場合するセンダとして null を渡します。</span><span class="sxs-lookup"><span data-stu-id="9473b-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="9473b-125">**X しないで**イベントを発生させるときにイベント データ パラメーターとして null を渡します。</span><span class="sxs-lookup"><span data-stu-id="9473b-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="9473b-126">渡す必要があります`EventArgs.Empty`イベント処理メソッドに、データの受け渡ししたくない場合。</span><span class="sxs-lookup"><span data-stu-id="9473b-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="9473b-127">開発者は、いない null にするには、このパラメーターを必要とします。</span><span class="sxs-lookup"><span data-stu-id="9473b-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="9473b-128">**✓ を検討してください**エンドユーザーが取り消すことができるイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="9473b-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="9473b-129">これは、前のイベントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="9473b-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="9473b-130">使用して<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>またはエンドユーザーのイベントをキャンセルできるイベントの引数としてそのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="9473b-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="9473b-131">カスタム イベント ハンドラーのデザイン</span><span class="sxs-lookup"><span data-stu-id="9473b-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="9473b-132">場合がある`EventHandler<T>`フレームワークが、ジェネリックをサポートしていませんでしたが、CLR の以前のバージョンを使用する必要がある場合など、使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9473b-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="9473b-133">このような場合は、デザインおよびカスタム イベント ハンドラーのデリゲートを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9473b-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="9473b-134">**✓ しないで**イベント ハンドラーの void の戻り値の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="9473b-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="9473b-135">イベント ハンドラーは、可能性のある複数のオブジェクトのメソッドを処理する複数のイベントを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9473b-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="9473b-136">イベント処理メソッドの戻り値が許可された場合は、各イベントの呼び出しに複数の戻り値があります。</span><span class="sxs-lookup"><span data-stu-id="9473b-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="9473b-137">**✓ は**を使用して`object`イベント ハンドラーの最初のパラメーターの型としてそれを呼び出すと`sender`です。</span><span class="sxs-lookup"><span data-stu-id="9473b-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="9473b-138">**✓ しないで**を使用して<xref:System.EventArgs?displayProperty=nameWithType>またはそのサブクラスをイベント ハンドラーの 2 番目のパラメーターの型としてそれを呼び出すと`e`です。</span><span class="sxs-lookup"><span data-stu-id="9473b-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="9473b-139">**X しないで**イベント ハンドラーに次の 2 つ以上のパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="9473b-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="9473b-140">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="9473b-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9473b-141">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="9473b-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9473b-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="9473b-142">See Also</span></span>  
 [<span data-ttu-id="9473b-143">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="9473b-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="9473b-144">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="9473b-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
