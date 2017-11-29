---
title: "弱いイベント パターン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a27e17e4940ff68f34d1e7e4accfb9e112bc412b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="weak-event-patterns"></a><span data-ttu-id="70bb5-102">弱いイベント パターン</span><span class="sxs-lookup"><span data-stu-id="70bb5-102">Weak Event Patterns</span></span>
<span data-ttu-id="70bb5-103">アプリケーションでは、可能であれば、イベント ソースに接続されているハンドラーは破棄されません、ハンドラーをソースに接続されているリスナー オブジェクトと連携します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="70bb5-104">このような状況は、メモリ リークが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="70bb5-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="70bb5-105">この問題に対処、特定のイベントの専用マネージャー クラスを提供して、そのイベントのリスナーにインターフェイスを実装して使用できるデザイン パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-105"> introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="70bb5-106">この設計パターンと呼ばれる、*弱いイベント パターン*です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="70bb5-107">弱いイベント パターンを実装する理由</span><span class="sxs-lookup"><span data-stu-id="70bb5-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="70bb5-108">イベントのリッスンと、メモリ リークが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="70bb5-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="70bb5-109">イベントをリッスンするための一般的な手法では、ソースでのイベントにハンドラーをアタッチする言語固有の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="70bb5-110">たとえば、 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]、構文がである:`source.SomeEvent += new SomeEventHandler(MyEventHandler)`です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-110">For example, in [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="70bb5-111">この手法は、強い参照をイベント ソースからのイベント リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="70bb5-112">オブジェクトの有効期間が影響を受けるソースのオブジェクトの有効期間 (しない限り、イベント ハンドラーが明示的に削除) にリスナーが通常は、リスナーのイベント ハンドラーをアタッチするとします。</span><span class="sxs-lookup"><span data-stu-id="70bb5-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="70bb5-113">特定の状況で、ソースの有効期間ではなく、アプリケーションのビジュアル ツリーに現在属しているかどうかなどするその他の要因によって制御されているリスナーのオブジェクトの有効期間をする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="70bb5-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="70bb5-114">ソース オブジェクトの有効期間は、リスナーのオブジェクトの有効期間からはみ出した、ときに通常のイベント パターンは、メモリ リークが発生につながります。 リスナーが有効のまま保持ためのものよりも長い時間です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="70bb5-115">弱いイベント パターンは、このメモリ リークの問題を解決するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="70bb5-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="70bb5-116">リスナーは、イベントに登録する必要がありますが、リスナーは明示的に認識できない場合の登録を解除するたびに、弱いイベント パターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="70bb5-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="70bb5-117">弱いイベント パターンは、ソースのオブジェクトの有効期間は、リスナーの役に立つオブジェクトの有効期間を超えた場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="70bb5-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="70bb5-118">(この場合、*便利*するによって決定されます)。弱いイベント パターンは、を登録し、任意の方法でリスナーのオブジェクトの有効期間の特性に影響を与えずに、イベントを受信するリスナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="70bb5-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="70bb5-119">実際には、ソースからの暗黙的な参照では、リスナーは、ガベージ コレクションの条件に適合するかどうかは不明です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="70bb5-120">参照は、弱いイベント パターンとの関連する名前付けつまり、弱い参照[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="70bb5-121">リスナーはガベージ コレクトされ、それ以外の場合は破棄、ソースが破棄されたオブジェクトへの収集ハンドラーの参照を保持せずに続行できます。</span><span class="sxs-lookup"><span data-stu-id="70bb5-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="70bb5-122">弱いイベント パターンを実装する必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="70bb5-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="70bb5-123">弱いイベント パターンを実装するは、主にコントロールの作成者にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="70bb5-124">コントロールの作成者は、ユーザーは、動作や、コントロールと挿入されているアプリケーションへの影響の含有関係担当大きくします。</span><span class="sxs-lookup"><span data-stu-id="70bb5-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="70bb5-125">これが含まれています、コントロール オブジェクトの有効期間の動作では、具体的には記載されているメモリ リークの問題の処理には、します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="70bb5-126">特定のシナリオでは、弱いイベント パターンをアプリケーション自体本質的に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="70bb5-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="70bb5-127">このようなシナリオの 1 つは、データ バインディングです。</span><span class="sxs-lookup"><span data-stu-id="70bb5-127">One such scenario is data binding.</span></span> <span data-ttu-id="70bb5-128">データ バインディングでは、ソース オブジェクトのバインディングのターゲットは、そのリスナー オブジェクトを完全に独立した一般的なです。</span><span class="sxs-lookup"><span data-stu-id="70bb5-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="70bb5-129">多くの側面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]弱いイベント パターン、イベントの実装方法で適用されるバインディングが既にデータがあります。</span><span class="sxs-lookup"><span data-stu-id="70bb5-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="70bb5-130">弱いイベント パターンを実装する方法</span><span class="sxs-lookup"><span data-stu-id="70bb5-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="70bb5-131">弱いイベント パターンを実装する次の 3 つの方法はあります。</span><span class="sxs-lookup"><span data-stu-id="70bb5-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="70bb5-132">次の表は、3 つの方法を示し、それぞれを使用する際のガイダンスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="70bb5-133">方法</span><span class="sxs-lookup"><span data-stu-id="70bb5-133">Approach</span></span>|<span data-ttu-id="70bb5-134">実装する場合</span><span class="sxs-lookup"><span data-stu-id="70bb5-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="70bb5-135">既存の弱いイベント マネージャー クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="70bb5-136">サブスクライブするイベントが、対応する<xref:System.Windows.WeakEventManager>、既存の弱いイベント マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="70bb5-137">WPF に含まれている弱いイベント マネージャーの一覧は、継承階層を参照してください、<xref:System.Windows.WeakEventManager>クラスです。</span><span class="sxs-lookup"><span data-stu-id="70bb5-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="70bb5-138">ただし、他のアプローチのいずれかを選択する必要がありますので、WPF に含まれる比較的少数の弱いイベント マネージャーがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="70bb5-138">Note, however, that there are relatively few weak event managers that are included with WPF, so you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="70bb5-139">ジェネリックの弱いイベント マネージャー クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="70bb5-140">ジェネリック型を使用して<xref:System.Windows.WeakEventManager%602>既存<xref:System.Windows.WeakEventManager>が利用できないを実装する簡単な方法を目的し、していない関係する効率。</span><span class="sxs-lookup"><span data-stu-id="70bb5-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="70bb5-141">ジェネリック<xref:System.Windows.WeakEventManager%602>既存またはカスタムの弱いイベント マネージャーより効率が下がります。</span><span class="sxs-lookup"><span data-stu-id="70bb5-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="70bb5-142">たとえば、discover イベントのイベントの名前を指定するために複数のリフレクションでは、ジェネリック クラス。</span><span class="sxs-lookup"><span data-stu-id="70bb5-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="70bb5-143">ジェネリックを使用して、イベントを登録するコードも、<xref:System.Windows.WeakEventManager%602>がより既存を使用するよりも詳細なまたは custom<xref:System.Windows.WeakEventManager>です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="70bb5-144">カスタムの弱いイベント マネージャー クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="70bb5-145">カスタム作成<xref:System.Windows.WeakEventManager>ときに既存する<xref:System.Windows.WeakEventManager>は使用できません最適な効率性を必要とします。</span><span class="sxs-lookup"><span data-stu-id="70bb5-145">Create a custom <xref:System.Windows.WeakEventManager> when you an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="70bb5-146">使用するカスタム<xref:System.Windows.WeakEventManager>をサブスクライブするイベントをより効率的になりますが、先頭にさらにコードを記述するコストが発生する操作を行います。</span><span class="sxs-lookup"><span data-stu-id="70bb5-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
  
 <span data-ttu-id="70bb5-147">次のセクションでは、弱いイベント パターンを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-147">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="70bb5-148">この説明の目的は、サブスクライブするイベントは、次の特性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="70bb5-148">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
-   <span data-ttu-id="70bb5-149">イベント名が`SomeEvent`です。</span><span class="sxs-lookup"><span data-stu-id="70bb5-149">The event name is `SomeEvent`.</span></span>  
  
-   <span data-ttu-id="70bb5-150">このイベントは、`EventSource`クラスです。</span><span class="sxs-lookup"><span data-stu-id="70bb5-150">The event is raised by the `EventSource` class.</span></span>  
  
-   <span data-ttu-id="70bb5-151">イベント ハンドラーが型: `SomeEventEventHandler` (または`EventHandler<SomeEventEventArgs>`)。</span><span class="sxs-lookup"><span data-stu-id="70bb5-151">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
-   <span data-ttu-id="70bb5-152">このイベントは、型のパラメーターを渡します`SomeEventEventArgs`イベント ハンドラーにします。</span><span class="sxs-lookup"><span data-stu-id="70bb5-152">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="70bb5-153">既存の弱いイベント マネージャー クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-153">Using an Existing Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="70bb5-154">既存の弱いイベント マネージャーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="70bb5-154">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="70bb5-155">WPF に含まれている弱いイベント マネージャーの一覧は、継承階層を参照してください、<xref:System.Windows.WeakEventManager>クラスです。</span><span class="sxs-lookup"><span data-stu-id="70bb5-155">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2.  <span data-ttu-id="70bb5-156">通常のイベント フックアップの代わりに新しいの弱いイベント マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-156">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="70bb5-157">たとえば、コードでは、次のパターンを使用してイベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="70bb5-157">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="70bb5-158">次のパターンに変更します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-158">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="70bb5-159">同様に、コードがイベントをアンサブスク ライブするのに次のパターンを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="70bb5-159">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="70bb5-160">次のパターンに変更します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="70bb5-161">ジェネリックの弱いイベント マネージャー クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-161">Using the Generic Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="70bb5-162">ジェネリックを使用して<xref:System.Windows.WeakEventManager%602>通常のイベント フックアップではなくクラスです。</span><span class="sxs-lookup"><span data-stu-id="70bb5-162">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="70bb5-163">使用すると<xref:System.Windows.WeakEventManager%602>イベント リスナーを登録するには、イベント ソースを指定し、<xref:System.EventArgs>への呼び出し、クラス型のパラメーターとして型<xref:System.Windows.WeakEventManager%602.AddHandler%2A>次のコードに示すように。</span><span class="sxs-lookup"><span data-stu-id="70bb5-163">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="70bb5-164">カスタムの弱いイベント マネージャー クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-164">Creating a Custom Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="70bb5-165">次のクラス テンプレートをプロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="70bb5-165">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="70bb5-166">このクラスから継承、<xref:System.Windows.WeakEventManager>クラスです。</span><span class="sxs-lookup"><span data-stu-id="70bb5-166">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  <span data-ttu-id="70bb5-167">置換、`SomeEventWeakEventManager`名に置き換えて名前。</span><span class="sxs-lookup"><span data-stu-id="70bb5-167">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3.  <span data-ttu-id="70bb5-168">イベントの対応する名前の前に説明した 3 つの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="70bb5-168">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="70bb5-169">(`SomeEvent`、 `EventSource`、および`SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="70bb5-169">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4.  <span data-ttu-id="70bb5-170">管理イベントと同様に表示するには、弱いイベント マネージャー クラスの可視性 (パブリック/内部/プライベート) を設定します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-170">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5.  <span data-ttu-id="70bb5-171">通常のイベント フックアップの代わりに新しいの弱いイベント マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-171">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="70bb5-172">たとえば、コードでは、次のパターンを使用してイベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="70bb5-172">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="70bb5-173">次のパターンに変更します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-173">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="70bb5-174">同様に、コードがイベントをアンサブスク ライブするのに次のパターンを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="70bb5-174">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="70bb5-175">次のパターンに変更します。</span><span class="sxs-lookup"><span data-stu-id="70bb5-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="70bb5-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="70bb5-176">See Also</span></span>  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [<span data-ttu-id="70bb5-177">ルーティング イベントの概要</span><span class="sxs-lookup"><span data-stu-id="70bb5-177">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="70bb5-178">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="70bb5-178">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
