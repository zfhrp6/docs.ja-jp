---
title: "カスタム レンダリング インク"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90d2ab68f76bef8d8f437a7dd6096011889303fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="custom-rendering-ink"></a><span data-ttu-id="be7ea-102">カスタム レンダリング インク</span><span class="sxs-lookup"><span data-stu-id="be7ea-102">Custom Rendering Ink</span></span>
<span data-ttu-id="be7ea-103"><xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>ストロークのプロパティでは、そのサイズ、色、および図形など、線の外観を指定することができますが、機能の外観をカスタマイズすることもあります<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>を許可します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-103">The <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property of a stroke allows you to specify the appearance of a stroke, such as its size, color, and shape, but there may be times that you want to customize the appearance beyond what <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> allow.</span></span> <span data-ttu-id="be7ea-104">エアブラシ、油絵、およびその他の多くの効果の外観でレンダリングすることで、インクの外観をカスタマイズしたい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="be7ea-104">You may want to customize the appearance of ink by rendering in the appearance of an air brush, oil paint, and many other effects.</span></span> <span data-ttu-id="be7ea-105">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]により、カスタムを実装することでインクをレンダリングすると、カスタム<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>と<xref:System.Windows.Ink.Stroke>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="be7ea-105">The [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] allows you to custom render ink by implementing a custom <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and <xref:System.Windows.Ink.Stroke> object.</span></span>  
  
 <span data-ttu-id="be7ea-106">このトピックは、次の内容で構成されています。</span><span class="sxs-lookup"><span data-stu-id="be7ea-106">This topic contains the following subsections:</span></span>  
  
-   [<span data-ttu-id="be7ea-107">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="be7ea-107">Architecture</span></span>](#Architecture)  
  
-   [<span data-ttu-id="be7ea-108">動的なレンダラーの実装</span><span class="sxs-lookup"><span data-stu-id="be7ea-108">Implementing a Dynamic Renderer</span></span>](#ImplementingADynamicRenderer)  
  
-   [<span data-ttu-id="be7ea-109">カスタム ストロークの実装</span><span class="sxs-lookup"><span data-stu-id="be7ea-109">Implementing Custom Strokes</span></span>](#ImplementingCustomStrokes)  
  
-   [<span data-ttu-id="be7ea-110">カスタム InkCanvas の実装</span><span class="sxs-lookup"><span data-stu-id="be7ea-110">Implementing a Custom InkCanvas</span></span>](#ImplementingACustomInkCanvas)  
  
-   [<span data-ttu-id="be7ea-111">まとめ</span><span class="sxs-lookup"><span data-stu-id="be7ea-111">Conclusion</span></span>](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a><span data-ttu-id="be7ea-112">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="be7ea-112">Architecture</span></span>  
 <span data-ttu-id="be7ea-113">インク レンダリングは 2 回発生します。ユーザーがインクを手描き入力サーフェイスに書き込む時と、ストロークが手書き対応のサーフェスに追加された後です。</span><span class="sxs-lookup"><span data-stu-id="be7ea-113">Ink rendering occurs two times; when a user writes ink to an inking surface, and again after the stroke is added to the ink-enabled surface.</span></span> <span data-ttu-id="be7ea-114"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 、ユーザーは、デジタイザー上でタブレット ペンを動かすと、インクをレンダリングおよび<xref:System.Windows.Ink.Stroke>要素に追加すること自体を表示します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-114">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the ink when the user moves the tablet pen on the digitizer, and the <xref:System.Windows.Ink.Stroke> renders itself once it is added to an element.</span></span>  
  
 <span data-ttu-id="be7ea-115">インクを動的にレンダリングするときに実装する 3 つのクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="be7ea-115">There are three classes to implement when dynamically rendering ink.</span></span>  
  
1.  <span data-ttu-id="be7ea-116">**DynamicRenderer**: から派生するクラスを実装する<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>です。</span><span class="sxs-lookup"><span data-stu-id="be7ea-116">**DynamicRenderer**: Implement a class that derives from <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="be7ea-117">このクラスは、特殊な<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>表示するための線が描画されるとします。</span><span class="sxs-lookup"><span data-stu-id="be7ea-117">This class is a specialized <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> that renders the stroke as it is drawn.</span></span> <span data-ttu-id="be7ea-118"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>アプリケーション ユーザー インターフェイス (UI) スレッドがブロックされている場合でも、インクを収集する場合は、インクの画面が表示されるように、別のスレッドでレンダリングがします。</span><span class="sxs-lookup"><span data-stu-id="be7ea-118">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> does the rendering on a separate thread, so the inking surface appears to collect ink even when the application user interface (UI) thread is blocked.</span></span> <span data-ttu-id="be7ea-119">スレッド処理モデルの詳細については、「[インク スレッド モデル](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be7ea-119">For more information about the threading model, see [The Ink Threading Model](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).</span></span> <span data-ttu-id="be7ea-120">ストロークを動的に表示をカスタマイズするには、上書き、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-120">To customize dynamically rendering a stroke, override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
2.  <span data-ttu-id="be7ea-121">**ストローク**: から派生するクラスを実装する<xref:System.Windows.Ink.Stroke>です。</span><span class="sxs-lookup"><span data-stu-id="be7ea-121">**Stroke**: Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="be7ea-122">静的表示するため、このクラスは、<xref:System.Windows.Input.StylusPoint>データに変換した後、<xref:System.Windows.Ink.Stroke>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="be7ea-122">This class is responsible for static rendering of the <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="be7ea-123">上書き、<xref:System.Windows.Ink.Stroke.DrawCore%2A>ストロークの静的なレンダリングできることを確認するメソッドは動的なレンダリングと一致します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-123">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> method to ensure that static rendering of the stroke is consistent with dynamic rendering.</span></span>  
  
3.  <span data-ttu-id="be7ea-124">**InkCanvas:**から派生するクラスを実装する<xref:System.Windows.Controls.InkCanvas>です。</span><span class="sxs-lookup"><span data-stu-id="be7ea-124">**InkCanvas:** Implement a class that derives from <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="be7ea-125">カスタマイズされた割り当てる<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-125">Assign the customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property.</span></span> <span data-ttu-id="be7ea-126">上書き、<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>メソッドにカスタムの線を追加し、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-126">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method and add a custom stroke to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property.</span></span> <span data-ttu-id="be7ea-127">これにより、インクの外観に一貫性を確保します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-127">This ensures that the appearance of the ink is consistent.</span></span>  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a><span data-ttu-id="be7ea-128">動的なレンダラーの実装</span><span class="sxs-lookup"><span data-stu-id="be7ea-128">Implementing a Dynamic Renderer</span></span>  
 <span data-ttu-id="be7ea-129"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>クラスは、標準の一部の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、以上を実行するには、レンダリング特化したから派生したカスタマイズされた動的レンダラーを作成する必要があります、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>をオーバーライドし、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-129">Although the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> class is a standard part of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], to perform more specialized rendering, you must create a customized dynamic renderer that derives from the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
 <span data-ttu-id="be7ea-130">次の例で、カスタマイズされた<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>線形グラデーション ブラシ効果のあるインクを描画します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-130">The following example demonstrates a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> that draws ink with a linear gradient brush effect.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a><span data-ttu-id="be7ea-131">カスタム ストロークの実装</span><span class="sxs-lookup"><span data-stu-id="be7ea-131">Implementing Custom Strokes</span></span>  
 <span data-ttu-id="be7ea-132"><xref:System.Windows.Ink.Stroke> から派生するクラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-132">Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="be7ea-133">このクラスは、レンダリング<xref:System.Windows.Input.StylusPoint>データに変換した後、<xref:System.Windows.Ink.Stroke>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="be7ea-133">This class is responsible for rendering <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="be7ea-134">上書き、<xref:System.Windows.Ink.Stroke.DrawCore%2A>実際の描画を実行するクラス。</span><span class="sxs-lookup"><span data-stu-id="be7ea-134">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> class to do the actual drawing.</span></span>  
  
 <span data-ttu-id="be7ea-135">ストローク クラスを使用してカスタム データを格納も、<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-135">Your Stroke class can also store custom data by using the <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> method.</span></span> <span data-ttu-id="be7ea-136">このデータは、保持されるときにストローク データと共に格納されます。</span><span class="sxs-lookup"><span data-stu-id="be7ea-136">This data is stored with the stroke data when persisted.</span></span>  
  
 <span data-ttu-id="be7ea-137"><xref:System.Windows.Ink.Stroke>クラスは、ヒット テストも実行できます。</span><span class="sxs-lookup"><span data-stu-id="be7ea-137">The <xref:System.Windows.Ink.Stroke> class can also perform hit testing.</span></span> <span data-ttu-id="be7ea-138">独自のヒットをオーバーライドすることでアルゴリズムをテストを実装することも、<xref:System.Windows.Ink.Stroke.HitTest%2A>現在のクラスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-138">You can also implement your own hit testing algorithm by overriding the <xref:System.Windows.Ink.Stroke.HitTest%2A> method in the current class.</span></span>  
  
 <span data-ttu-id="be7ea-139">次の c# コードをカスタムに示します<xref:System.Windows.Ink.Stroke>レンダリング クラス<xref:System.Windows.Input.StylusPoint>3-D ストロークとしてデータ。</span><span class="sxs-lookup"><span data-stu-id="be7ea-139">The following C# code demonstrates a custom <xref:System.Windows.Ink.Stroke> class that renders <xref:System.Windows.Input.StylusPoint> data as a 3-D stroke.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a><span data-ttu-id="be7ea-140">カスタム InkCanvas の実装</span><span class="sxs-lookup"><span data-stu-id="be7ea-140">Implementing a Custom InkCanvas</span></span>  
 <span data-ttu-id="be7ea-141">カスタマイズしたを使用する最も簡単な方法<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ストロークから派生するクラスを実装して<xref:System.Windows.Controls.InkCanvas>し、これらのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-141">The easiest way to use your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and stroke is to implement a class that derives from <xref:System.Windows.Controls.InkCanvas> and uses these classes.</span></span> <span data-ttu-id="be7ea-142"><xref:System.Windows.Controls.InkCanvas>が、<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>ユーザーが描画するときに、線がどのように表示されるかを指定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-142">The <xref:System.Windows.Controls.InkCanvas> has a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property that specifies how the stroke is rendered when the user is drawing it.</span></span>  
  
 <span data-ttu-id="be7ea-143">カスタム上のストロークの表示、<xref:System.Windows.Controls.InkCanvas>次の操作します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-143">To custom render strokes on an <xref:System.Windows.Controls.InkCanvas> do the following:</span></span>  
  
-   <span data-ttu-id="be7ea-144">派生するクラスを作成、<xref:System.Windows.Controls.InkCanvas>です。</span><span class="sxs-lookup"><span data-stu-id="be7ea-144">Create a class that derives from the <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
-   <span data-ttu-id="be7ea-145">カスタマイズした割り当てる<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-145">Assign your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="be7ea-146"><xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="be7ea-146">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method.</span></span> <span data-ttu-id="be7ea-147">このメソッドで、InkCanvas に追加された元のストロークを削除します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-147">In this method, remove the original stroke that was added to the InkCanvas.</span></span> <span data-ttu-id="be7ea-148">カスタム線を作成し、それを追加、<xref:System.Windows.Controls.InkCanvas.Strokes%2A>プロパティ、および呼び出し、基本クラスを新しい<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>カスタム線を格納しています。</span><span class="sxs-lookup"><span data-stu-id="be7ea-148">Then create a custom stroke, add it to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property, and call the base class with a new <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> that contains the custom stroke.</span></span>  
  
 <span data-ttu-id="be7ea-149">次の c# コードに示しますカスタム<xref:System.Windows.Controls.InkCanvas>を使用して、カスタマイズされたクラス<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>し、カスタムのストロークを収集します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-149">The following C# code demonstrates a custom <xref:System.Windows.Controls.InkCanvas> class that uses a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and collects custom strokes.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <span data-ttu-id="be7ea-150"><xref:System.Windows.Controls.InkCanvas> 1 つ以上の<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>します。</span><span class="sxs-lookup"><span data-stu-id="be7ea-150">An <xref:System.Windows.Controls.InkCanvas> can have more than one <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="be7ea-151">複数を追加する<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>オブジェクトを<xref:System.Windows.Controls.InkCanvas>に追加することによって、<xref:System.Windows.UIElement.StylusPlugIns%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-151">You can add multiple <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objects to the <xref:System.Windows.Controls.InkCanvas> by adding them to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span>  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="be7ea-152">まとめ</span><span class="sxs-lookup"><span data-stu-id="be7ea-152">Conclusion</span></span>  
 <span data-ttu-id="be7ea-153">インクの外観をカスタマイズするには、独自の派生によって<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、 <xref:System.Windows.Ink.Stroke>、および<xref:System.Windows.Controls.InkCanvas>クラスです。</span><span class="sxs-lookup"><span data-stu-id="be7ea-153">You can customize the appearance of ink by deriving your own <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, and <xref:System.Windows.Controls.InkCanvas> classes.</span></span> <span data-ttu-id="be7ea-154">これらのクラスを合わせて、ユーザーがストロークを描画し、その後ストロークが収集される際に、ストロークの外観を一致させます。</span><span class="sxs-lookup"><span data-stu-id="be7ea-154">Together, these classes ensure that the appearance of the stroke is consistent when the user draws the stroke and after it is collected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7ea-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="be7ea-155">See Also</span></span>  
 [<span data-ttu-id="be7ea-156">高度なインク処理</span><span class="sxs-lookup"><span data-stu-id="be7ea-156">Advanced Ink Handling</span></span>](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
