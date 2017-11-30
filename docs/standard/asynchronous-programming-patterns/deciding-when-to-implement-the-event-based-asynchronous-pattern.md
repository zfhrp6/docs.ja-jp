---
title: "イベントベースの非同期パターンをいつ実装するかの決定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48de1b736c251a61a2ad34975c77bc2bca139626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a><span data-ttu-id="79dcf-102">イベントベースの非同期パターンをいつ実装するかの決定</span><span class="sxs-lookup"><span data-stu-id="79dcf-102">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="79dcf-103">イベント ベースの非同期パターンは、クラスの非同期動作を公開するため、パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="79dcf-103">The Event-based Asynchronous Pattern provides a pattern for exposing the asynchronous behavior of a class.</span></span> <span data-ttu-id="79dcf-104">このパターンの導入に伴い、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]非同期動作を公開するための 2 つのパターンを定義します: 非同期パターンがに基づいて、<xref:System.IAsyncResult?displayProperty=nameWithType>インターフェイス、およびイベント ベースのパターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-104">With the introduction of this pattern, the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] defines two patterns for exposing asynchronous behavior: the Asynchronous Pattern based on the <xref:System.IAsyncResult?displayProperty=nameWithType> interface, and the event-based pattern.</span></span> <span data-ttu-id="79dcf-105">このトピックが両方のパターンを実装するための適切な場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="79dcf-105">This topic describes when it is appropriate for you to implement both patterns.</span></span>  
  
 <span data-ttu-id="79dcf-106">使用した非同期プログラミングの詳細については、<xref:System.IAsyncResult>インターフェイスを参照してください[イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)です。</span><span class="sxs-lookup"><span data-stu-id="79dcf-106">For more information about asynchronous programming with the <xref:System.IAsyncResult> interface, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
## <a name="general-principles"></a><span data-ttu-id="79dcf-107">一般原則</span><span class="sxs-lookup"><span data-stu-id="79dcf-107">General Principles</span></span>  
 <span data-ttu-id="79dcf-108">一般に、- イベント ベースの非同期パターンが使用可能な限り非同期機能を公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79dcf-108">In general, you should expose asynchronous features using the Event-based Asynchronous Pattern whenever possible.</span></span> <span data-ttu-id="79dcf-109">ただし、いくつかの要件を満たしていないイベント ベースのパターンがあります。</span><span class="sxs-lookup"><span data-stu-id="79dcf-109">However, there are some requirements that the event-based pattern cannot meet.</span></span> <span data-ttu-id="79dcf-110">その場合を実装する必要があります、<xref:System.IAsyncResult>イベント ベースのパターンに加えてパターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-110">In those cases, you may need to implement the <xref:System.IAsyncResult> pattern in addition to the event-based pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79dcf-111">これはまれであるため、<xref:System.IAsyncResult>も実装されているイベントに基づくパターンせずに実装するパターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-111">It is rare for the <xref:System.IAsyncResult> pattern to be implemented without the event-based pattern also being implemented.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="79dcf-112">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="79dcf-112">Guidelines</span></span>  
 <span data-ttu-id="79dcf-113">次に、イベント ベースの非同期パターンを実装する場合のガイドラインを説明します。</span><span class="sxs-lookup"><span data-stu-id="79dcf-113">The following list describes the guidelines for when you should implement Event-based Asynchronous Pattern:</span></span>  
  
-   <span data-ttu-id="79dcf-114">既定 API とイベント ベースのパターンを使用して、クラスの非同期動作を公開します。</span><span class="sxs-lookup"><span data-stu-id="79dcf-114">Use the event-based pattern as the default API to expose asynchronous behavior for your class.</span></span>  
  
-   <span data-ttu-id="79dcf-115">公開しない、<xref:System.IAsyncResult>パターンをクラスは、主に、クライアント アプリケーションで Windows フォームなどの使用時にします。</span><span class="sxs-lookup"><span data-stu-id="79dcf-115">Do not expose the <xref:System.IAsyncResult> pattern when your class is primarily used in a client application, for example Windows Forms.</span></span>  
  
-   <span data-ttu-id="79dcf-116">だけを公開、<xref:System.IAsyncResult>パターンを要件を満たすために必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="79dcf-116">Only expose the <xref:System.IAsyncResult> pattern when it is necessary for meeting your requirements.</span></span> <span data-ttu-id="79dcf-117">たとえば、既存の API との互換性が必要がありますを公開する、<xref:System.IAsyncResult>パターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-117">For example, compatibility with an existing API may require you to expose the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="79dcf-118">公開しない、<xref:System.IAsyncResult>イベント ベースのパターンを公開せずパターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-118">Do not expose the <xref:System.IAsyncResult> pattern without also exposing the event-based pattern.</span></span>  
  
-   <span data-ttu-id="79dcf-119">必要がありますを公開する場合、<xref:System.IAsyncResult>パターンは、高度なオプションとして。</span><span class="sxs-lookup"><span data-stu-id="79dcf-119">If you must expose the <xref:System.IAsyncResult> pattern, do so as an advanced option.</span></span> <span data-ttu-id="79dcf-120">たとえば、プロキシ オブジェクトを生成する場合、このイベント ベースのパターンを既定では、生成するオプションが生成、<xref:System.IAsyncResult>パターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-120">For example, if you generate a proxy object, generate the event-based pattern by default, with an option to generate the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="79dcf-121">イベント ベースのパターンの実装の構築、<xref:System.IAsyncResult>パターンの実装です。</span><span class="sxs-lookup"><span data-stu-id="79dcf-121">Build your event-based pattern implementation on your <xref:System.IAsyncResult> pattern implementation.</span></span>  
  
-   <span data-ttu-id="79dcf-122">両方のイベント ベースのパターンを公開しないように、<xref:System.IAsyncResult>パターンは、同じクラスです。</span><span class="sxs-lookup"><span data-stu-id="79dcf-122">Avoid exposing both the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class.</span></span> <span data-ttu-id="79dcf-123">「高レベル」のクラスでイベント ベースのパターンを公開し、<xref:System.IAsyncResult>パターンの「レベルを下げる」クラスです。</span><span class="sxs-lookup"><span data-stu-id="79dcf-123">Expose the event-based pattern on "higher level" classes and the <xref:System.IAsyncResult> pattern on "lower level" classes.</span></span> <span data-ttu-id="79dcf-124">たとえば、イベント ベースのパターンと比較、<xref:System.Net.WebClient>コンポーネントを<xref:System.IAsyncResult>のパターン、<xref:System.Web.HttpRequest>クラスです。</span><span class="sxs-lookup"><span data-stu-id="79dcf-124">For example, compare the event-based pattern on the <xref:System.Net.WebClient> component with the <xref:System.IAsyncResult> pattern on the <xref:System.Web.HttpRequest> class.</span></span>  
  
    -   <span data-ttu-id="79dcf-125">イベント ベースのパターンを公開し、<xref:System.IAsyncResult>パターンは、互換性が必要とするときに、同じクラスです。</span><span class="sxs-lookup"><span data-stu-id="79dcf-125">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class when compatibility requires it.</span></span> <span data-ttu-id="79dcf-126">たとえばを使用する API が既に解放されている場合、<xref:System.IAsyncResult>パターンでは、保持する必要は、<xref:System.IAsyncResult>旧バージョンとの互換性のためのパターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-126">For example, if you have already released an API that uses the <xref:System.IAsyncResult> pattern, you would need to retain the <xref:System.IAsyncResult> pattern for backward compatibility.</span></span>  
  
    -   <span data-ttu-id="79dcf-127">イベント ベースのパターンを公開し、<xref:System.IAsyncResult>オブジェクト モデルの結果として得られる複雑性が、実装を分離することの利点を上回る場合に、同じクラスのパターンします。</span><span class="sxs-lookup"><span data-stu-id="79dcf-127">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class if the resulting object model complexity outweighs the benefit of separating the implementations.</span></span> <span data-ttu-id="79dcf-128">イベント ベースのパターンを公開することを避けるよりも 1 つのクラスで両方のパターンを公開することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="79dcf-128">It is better to expose both patterns on a single class than to avoid exposing the event-based pattern.</span></span>  
  
    -   <span data-ttu-id="79dcf-129">両方のイベント ベースのパターンを公開する必要がある場合と<xref:System.IAsyncResult>パターンは、1 つのクラスを使用して<xref:System.ComponentModel.EditorBrowsableAttribute>に設定<xref:System.ComponentModel.EditorBrowsableState.Advanced>をマークする、<xref:System.IAsyncResult>高度な機能としてのパターンの実装です。</span><span class="sxs-lookup"><span data-stu-id="79dcf-129">If you must expose both the event-based pattern and <xref:System.IAsyncResult> pattern on a single class, use <xref:System.ComponentModel.EditorBrowsableAttribute> set to <xref:System.ComponentModel.EditorBrowsableState.Advanced> to mark the <xref:System.IAsyncResult> pattern implementation as an advanced feature.</span></span> <span data-ttu-id="79dcf-130">など、デザイン環境に示すこの[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]を表示しないように、IntelliSense、<xref:System.IAsyncResult>プロパティとメソッド。</span><span class="sxs-lookup"><span data-stu-id="79dcf-130">This indicates to design environments, such as [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] IntelliSense, not to display the <xref:System.IAsyncResult> properties and methods.</span></span> <span data-ttu-id="79dcf-131">これらのプロパティとメソッドが完全に使用可能ではまだが IntelliSense によって、開発者が API の鮮明に表示します。</span><span class="sxs-lookup"><span data-stu-id="79dcf-131">These properties and methods are still fully usable, but the developer working through IntelliSense has a clearer view of the API.</span></span>  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a><span data-ttu-id="79dcf-132">イベント ベースのパターンに加えて IAsyncResult パターンを公開するための条件</span><span class="sxs-lookup"><span data-stu-id="79dcf-132">Criteria for Exposing the IAsyncResult Pattern in Addition to the Event-based Pattern</span></span>  
 <span data-ttu-id="79dcf-133">イベント ベースの非同期パターンには、前述のシナリオで多くの利点がありますがいくつかの欠点は、パフォーマンスが最も重要な要件である場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="79dcf-133">While the Event-based Asynchronous Pattern has many benefits under the previously mentioned scenarios, it does have some drawbacks, which you should be aware of if performance is your most important requirement.</span></span>  
  
 <span data-ttu-id="79dcf-134">イベント ベースのパターンでは取り上げませんが 3 つのシナリオはだけでなく、<xref:System.IAsyncResult>パターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-134">There are three scenarios that the event-based pattern does not address as well as the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="79dcf-135">1 つで待機をブロック<xref:System.IAsyncResult></span><span class="sxs-lookup"><span data-stu-id="79dcf-135">Blocking wait on one <xref:System.IAsyncResult></span></span>  
  
-   <span data-ttu-id="79dcf-136">多くの待機をブロックして<xref:System.IAsyncResult>オブジェクト</span><span class="sxs-lookup"><span data-stu-id="79dcf-136">Blocking wait on many <xref:System.IAsyncResult> objects</span></span>  
  
-   <span data-ttu-id="79dcf-137">完了のポーリング、<xref:System.IAsyncResult></span><span class="sxs-lookup"><span data-stu-id="79dcf-137">Polling for completion on the <xref:System.IAsyncResult></span></span>  
  
 <span data-ttu-id="79dcf-138">イベント ベースのパターンを使用して、こうしたシナリオに対処することができますが、これは、使用するよりも煩雑、<xref:System.IAsyncResult>パターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-138">You can address these scenarios by using the event-based pattern, but doing so is more cumbersome than using the <xref:System.IAsyncResult> pattern.</span></span>  
  
 <span data-ttu-id="79dcf-139">開発者は多くの場合、使用して、<xref:System.IAsyncResult>通常非常に高いパフォーマンスの要件を設定しているサービスのパターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-139">Developers often use the <xref:System.IAsyncResult> pattern for services that typically have very high performance requirements.</span></span> <span data-ttu-id="79dcf-140">たとえば、完了のシナリオのポーリングは、高パフォーマンス サーバー手法です。</span><span class="sxs-lookup"><span data-stu-id="79dcf-140">For example, the polling for completion scenario is a high-performance server technique.</span></span>  
  
 <span data-ttu-id="79dcf-141">さらに、イベント ベースのパターンより効率が下がります、<xref:System.IAsyncResult>特に複数のオブジェクトを作成するためのパターンを<xref:System.EventArgs>、およびスレッド間で同期するためです。</span><span class="sxs-lookup"><span data-stu-id="79dcf-141">Additionally, the event-based pattern is less efficient than the <xref:System.IAsyncResult> pattern because it creates more objects, especially <xref:System.EventArgs>, and because it synchronizes across threads.</span></span>  
  
 <span data-ttu-id="79dcf-142">次の一覧を使用する場合に実行する推奨事項を示しています、<xref:System.IAsyncResult>パターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-142">The following list shows some recommendations to follow if you decide to use the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="79dcf-143">だけを公開、<xref:System.IAsyncResult>のサポートを特に必要とするときのパターンを<xref:System.Threading.WaitHandle>または<xref:System.IAsyncResult>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="79dcf-143">Only expose the <xref:System.IAsyncResult> pattern when you specifically require support for <xref:System.Threading.WaitHandle> or <xref:System.IAsyncResult> objects.</span></span>  
  
-   <span data-ttu-id="79dcf-144">だけを公開、<xref:System.IAsyncResult>パターンを使用する既存の API がある場合、<xref:System.IAsyncResult>パターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-144">Only expose the <xref:System.IAsyncResult> pattern when you have an existing API that uses the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="79dcf-145">基づく既存の API がある場合、<xref:System.IAsyncResult>パターンも、イベント ベースのパターンで、次のリリースで公開することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="79dcf-145">If you have an existing API based on the <xref:System.IAsyncResult> pattern, consider also exposing the event-based pattern in your next release.</span></span>  
  
-   <span data-ttu-id="79dcf-146">だけを公開<xref:System.IAsyncResult>パターンを確認する高パフォーマンスの要件がある場合は、イベント ベースのパターンで満たすことができませんが、によって満たすことができます、<xref:System.IAsyncResult>パターン。</span><span class="sxs-lookup"><span data-stu-id="79dcf-146">Only expose <xref:System.IAsyncResult> pattern if you have high performance requirements which you have verified cannot be met by the event-based pattern but can be met by the <xref:System.IAsyncResult> pattern.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79dcf-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="79dcf-147">See Also</span></span>  
 [<span data-ttu-id="79dcf-148">チュートリアル: イベントベースの非同期パターンをサポートするコンポーネントの実装</span><span class="sxs-lookup"><span data-stu-id="79dcf-148">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="79dcf-149">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="79dcf-149">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="79dcf-150">イベント ベースの非同期パターンを使用したマルチスレッド プログラミング</span><span class="sxs-lookup"><span data-stu-id="79dcf-150">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="79dcf-151">イベントベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="79dcf-151">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="79dcf-152">イベントベースの非同期パターンを実装するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="79dcf-152">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="79dcf-153">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="79dcf-153">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
