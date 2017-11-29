---
title: "インク スレッド モデル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: efbd05f88b962363e3b866fbf914f6d3a37823cc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="the-ink-threading-model"></a><span data-ttu-id="f3328-102">インク スレッド モデル</span><span class="sxs-lookup"><span data-stu-id="f3328-102">The Ink Threading Model</span></span>
<span data-ttu-id="f3328-103">Tablet PC 上のインクの利点の 1 つは、ことが多くように感じますが書き込みと用紙と正規ペンでです。</span><span class="sxs-lookup"><span data-stu-id="f3328-103">One of the benefits of ink on a Tablet PC is that it feels a lot like writing with a regular pen and paper.</span></span>  <span data-ttu-id="f3328-104">これを行うには、タブレット ペンは、速度が大幅に高くマウスは、ユーザーの書き込みとインクをレンダリングよりも入力データを収集します。</span><span class="sxs-lookup"><span data-stu-id="f3328-104">To accomplish this, the tablet pen collects input data at a much higher rate than a mouse does and renders the ink as the user writes.</span></span>  <span data-ttu-id="f3328-105">アプリケーションのユーザー インターフェイス (UI) スレッドではありませんペンのデータとレンダリング インクを収集するための十分なブロックになることができます。</span><span class="sxs-lookup"><span data-stu-id="f3328-105">The application's user interface (UI) thread is not sufficient for collecting pen data and rendering ink, because it can become blocked.</span></span>  <span data-ttu-id="f3328-106">これを解決するために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが、ユーザーがインクを書き込む場合に、追加の 2 つのスレッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f3328-106">To solve this, a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application uses two additional threads when a user writes ink.</span></span>  
  
 <span data-ttu-id="f3328-107">次の一覧には、収集およびデジタル インクをレンダリングに関係するスレッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f3328-107">The following list describes the threads that take part in collecting and rendering digital ink:</span></span>  
  
-   <span data-ttu-id="f3328-108">ペンのスレッドのスタイラスからの入力を受け取るスレッドです。</span><span class="sxs-lookup"><span data-stu-id="f3328-108">Pen thread - the thread that takes input from the stylus.</span></span>  <span data-ttu-id="f3328-109">(実際には、スレッド プールでは、これは、このトピックでは、ペン スレッドとして)。</span><span class="sxs-lookup"><span data-stu-id="f3328-109">(In reality, this is a thread pool, but this topic refers to it as a pen thread.)</span></span>  
  
-   <span data-ttu-id="f3328-110">アプリケーション ユーザー インターフェイス スレッドのアプリケーションのユーザー インターフェイスを制御するスレッド。</span><span class="sxs-lookup"><span data-stu-id="f3328-110">Application user interface thread - the thread that controls the user interface of the application.</span></span>  
  
-   <span data-ttu-id="f3328-111">動的なレンダリング スレッドに対し、ユーザーのインクをレンダリングするスレッドがストロークを描画します。</span><span class="sxs-lookup"><span data-stu-id="f3328-111">Dynamic rendering thread - the thread that renders the ink while the user draws a stroke.</span></span> <span data-ttu-id="f3328-112">ウィンドウ Presentation Foundation で説明したように、動的なレンダリング スレッドは、アプリケーションの場合は、他の UI 要素を描画するスレッドとは異なる[スレッド モデル](../../../../docs/framework/wpf/advanced/threading-model.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3328-112">The dynamic rendering thread is different than the thread that renders other UI elements for the application, as mentioned in Window Presentation Foundation [Threading Model](../../../../docs/framework/wpf/advanced/threading-model.md).</span></span>  
  
 <span data-ttu-id="f3328-113">インクのモデルは、同じアプリケーションを使用しているかどうか、<xref:System.Windows.Controls.InkCanvas>またはカスタム コントロールでのような[インク入力コントロールを作成する](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3328-113">The inking model is the same whether the application uses the <xref:System.Windows.Controls.InkCanvas> or a custom control similar to the one in [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  <span data-ttu-id="f3328-114">このトピックの観点でスレッド処理について説明しますが、 <xref:System.Windows.Controls.InkCanvas>、カスタム コントロールを作成するときに、同じ概念が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f3328-114">Although this topic discusses threading in terms of the <xref:System.Windows.Controls.InkCanvas>, the same concepts apply when you create a custom control.</span></span>  
  
## <a name="threading-overview"></a><span data-ttu-id="f3328-115">スレッド処理の概要</span><span class="sxs-lookup"><span data-stu-id="f3328-115">Threading Overview</span></span>  
 <span data-ttu-id="f3328-116">次の図は、ユーザーがストロークを描画するときに、スレッディング モデルを示します。</span><span class="sxs-lookup"><span data-stu-id="f3328-116">The following diagram illustrates the threading model when a user draws a stroke:</span></span>  
  
 <span data-ttu-id="f3328-117">![ストローク描画中のスレッド モデルです。] (../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")</span><span class="sxs-lookup"><span data-stu-id="f3328-117">![Threading model while drawing a stroke.](../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")</span></span>  
  
1.  <span data-ttu-id="f3328-118">ユーザーがストロークを描画中に発生するアクション</span><span class="sxs-lookup"><span data-stu-id="f3328-118">Actions occurring while the user draws the stroke</span></span>  
  
    1.  <span data-ttu-id="f3328-119">ユーザーがストロークを描画、スタイラス ポイントは、ペン スレッド上で提供されます。</span><span class="sxs-lookup"><span data-stu-id="f3328-119">When the user draws a stroke, the stylus points come in on the pen thread.</span></span>  <span data-ttu-id="f3328-120">スタイラス プラグインを含む、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>は、ペンのスレッドでスタイラス ポイントを使用し、前にそれらを変更する可能性が高く、<xref:System.Windows.Controls.InkCanvas>受信します。</span><span class="sxs-lookup"><span data-stu-id="f3328-120">Stylus plug-ins, including the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, accept the stylus points on the pen thread and have the chance to modify them before the <xref:System.Windows.Controls.InkCanvas> receives them.</span></span>  
  
    2.  <span data-ttu-id="f3328-121"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>動的レンダリング スレッドでスタイラス ポイントを表示します。</span><span class="sxs-lookup"><span data-stu-id="f3328-121">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the stylus points on the dynamic rendering thread.</span></span> <span data-ttu-id="f3328-122">これは、前の手順と同時に発生します。</span><span class="sxs-lookup"><span data-stu-id="f3328-122">This happens at the same time as the previous step.</span></span>  
  
    3.  <span data-ttu-id="f3328-123"><xref:System.Windows.Controls.InkCanvas> UI スレッドでスタイラス ポイントを受信します。</span><span class="sxs-lookup"><span data-stu-id="f3328-123">The <xref:System.Windows.Controls.InkCanvas> receives the stylus points on the UI thread.</span></span>  
  
2.  <span data-ttu-id="f3328-124">ユーザーがストロークを終了した後に発生するアクション</span><span class="sxs-lookup"><span data-stu-id="f3328-124">Actions occurring after the user ends the stroke</span></span>  
  
    1.  <span data-ttu-id="f3328-125">ユーザーがストロークを描画を終了するときに、<xref:System.Windows.Controls.InkCanvas>を作成、<xref:System.Windows.Ink.Stroke>オブジェクトを追加して、 <xref:System.Windows.Controls.InkPresenter>、静的にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="f3328-125">When the user finishes drawing the stroke, the <xref:System.Windows.Controls.InkCanvas> creates a <xref:System.Windows.Ink.Stroke> object and adds it to the <xref:System.Windows.Controls.InkPresenter>, which statically renders it.</span></span>  
  
    2.  <span data-ttu-id="f3328-126">UI スレッドのアラート、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>線が表示される静的にするため、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ストロークのビジュアル表現を削除します。</span><span class="sxs-lookup"><span data-stu-id="f3328-126">The UI thread alerts the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> that the stroke is statically rendered, so the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> removes its visual representation of the stroke.</span></span>  
  
## <a name="ink-collection-and-stylus-plug-ins"></a><span data-ttu-id="f3328-127">スタイラス プラグインとインクの収集</span><span class="sxs-lookup"><span data-stu-id="f3328-127">Ink collection and Stylus Plug-ins</span></span>  
 <span data-ttu-id="f3328-128">各<xref:System.Windows.UIElement>が、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>です。</span><span class="sxs-lookup"><span data-stu-id="f3328-128">Each <xref:System.Windows.UIElement> has a <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span>  <span data-ttu-id="f3328-129"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>内のオブジェクト、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>受信およびペン スレッド上のスタイラス ポイントを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f3328-129">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> receive and can modify the stylus points on the pen thread.</span></span> <span data-ttu-id="f3328-130"><xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>オブジェクトを受け取るスタイラス ポイント順に従って、<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>です。</span><span class="sxs-lookup"><span data-stu-id="f3328-130">The <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objects receive the stylus points according to their order in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.</span></span>  
  
 <span data-ttu-id="f3328-131">次の図は、仮想的な状況を示しています。 ここで、<xref:System.Windows.UIElement.StylusPlugIns%2A>のコレクション、<xref:System.Windows.UIElement>が含まれています`stylusPlugin1`、 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>、および`stylusPlugin2`点で、注文します。</span><span class="sxs-lookup"><span data-stu-id="f3328-131">The following diagram illustrates the hypothetical situation where the <xref:System.Windows.UIElement.StylusPlugIns%2A> collection of a <xref:System.Windows.UIElement> contains `stylusPlugin1`, a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, and `stylusPlugin2`, in that order.</span></span>  
  
 <span data-ttu-id="f3328-132">![スタイラス プラグインの順序では、出力に影響します。] (../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")</span><span class="sxs-lookup"><span data-stu-id="f3328-132">![Order of Stylus Plugins affect output.](../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")</span></span>  
  
 <span data-ttu-id="f3328-133">上の図に、次の動作が行わをれます。</span><span class="sxs-lookup"><span data-stu-id="f3328-133">In the previous diagram, the following behavior takes place:</span></span>  
  
1.  <span data-ttu-id="f3328-134">`StylusPlugin1`x の値を変更し、y です。</span><span class="sxs-lookup"><span data-stu-id="f3328-134">`StylusPlugin1` modifies the values for x and y.</span></span>  
  
2.  <span data-ttu-id="f3328-135"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>スタイラスの更新ポイントを受信し、動的なレンダリング スレッドでそれらを表示します。</span><span class="sxs-lookup"><span data-stu-id="f3328-135"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives the modified stylus points and renders them on the dynamic rendering thread.</span></span>  
  
3.  <span data-ttu-id="f3328-136">`StylusPlugin2`スタイラスの更新ポイントを受信し、さらに x の値を変更し、y です。</span><span class="sxs-lookup"><span data-stu-id="f3328-136">`StylusPlugin2` receives the modified stylus points and further modifies the values for x and y.</span></span>  
  
4.  <span data-ttu-id="f3328-137">アプリケーションでは、スタイラス ポイントを収集し、ユーザーがストロークを完了すると、静的にストロークを描画します。</span><span class="sxs-lookup"><span data-stu-id="f3328-137">The application collects the stylus points, and, when the user finishes the stroke, statically renders the stroke.</span></span>  
  
 <span data-ttu-id="f3328-138">仮定します`stylusPlugin1`四角形にスタイラスのポイントを制限し、`stylusPlugin2`右側にスタイラスのポイントに変換します。</span><span class="sxs-lookup"><span data-stu-id="f3328-138">Suppose that `stylusPlugin1` restricts the stylus points to a rectangle and `stylusPlugin2` translates the stylus points to the right.</span></span>  <span data-ttu-id="f3328-139">上記のシナリオでは、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>が制限されたスタイラス ポイントが、翻訳済みのスタイラス点ではないです。</span><span class="sxs-lookup"><span data-stu-id="f3328-139">In the previous scenario, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> receives the restricted stylus points, but not the translated stylus points.</span></span>  <span data-ttu-id="f3328-140">ユーザーがストロークを描画、ストロークは、四角形の境界内でレンダリングされますが、ユーザーがペンを持ち上げるまでに翻訳する線が表示されません。</span><span class="sxs-lookup"><span data-stu-id="f3328-140">When the user draws the stroke, the stroke is rendered within the bounds of the rectangle, but the stroke doesn't appear to be translated until the user lifts the pen.</span></span>  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a><span data-ttu-id="f3328-141">スタイラスの UI スレッドでプラグインを使用して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="f3328-141">Performing operations with a Stylus Plug-in on the UI thread</span></span>  
 <span data-ttu-id="f3328-142">ペンのスレッドでは、正確なヒット テストを実行できない、ためにによっては、いくつかの要素がスタイラス入力用の他の要素を受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="f3328-142">Because accurate hit-testing cannot be performed on the pen thread, some elements might occasionally receive stylus input intended for other elements.</span></span> <span data-ttu-id="f3328-143">サブスクライブしで操作を実行する操作を実行する前に、入力が正しく回送されたことを確認する必要がある場合、 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>、 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>、または<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f3328-143">If you need to make sure the input was routed correctly before performing an operation, subscribe to and perform the operation in the <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, or <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> method.</span></span> <span data-ttu-id="f3328-144">これらのメソッドは、正確なヒット テストが実行された後に、アプリケーションのスレッドによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f3328-144">These methods are invoked by the application thread after accurate hit-testing has been performed.</span></span> <span data-ttu-id="f3328-145">これらのメソッドをサブスクライブする、<xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A>ペンのスレッドで使用されるメソッドのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f3328-145">To subscribe to these methods, call the <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> method in the method that occurs on the pen thread.</span></span>  
  
 <span data-ttu-id="f3328-146">次の図は、ペン スレッドとのスタイラス イベントに関して UI スレッド間のリレーションシップ、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>です。</span><span class="sxs-lookup"><span data-stu-id="f3328-146">The following diagram illustrates the relationship between the pen thread and UI thread with respect to the stylus events of a <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.</span></span>  
  
 <span data-ttu-id="f3328-147">![インク スレッド処理モデル &#40;です。UI およびペン &#41;] (../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")</span><span class="sxs-lookup"><span data-stu-id="f3328-147">![Ink Threading Models &#40;UI and Pen&#41;](../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")</span></span>  
  
## <a name="rendering-ink"></a><span data-ttu-id="f3328-148">インクをレンダリング</span><span class="sxs-lookup"><span data-stu-id="f3328-148">Rendering Ink</span></span>  
 <span data-ttu-id="f3328-149">ユーザーがストロークを描画と<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>"をフローする"、ペンから UI スレッドがビジー状態である場合でも、インクが表示されるように、別のスレッド上のインクをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="f3328-149">As the user draws a stroke, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the ink on a separate thread so the ink appears to "flow" from the pen even when the UI thread is busy.</span></span>  <span data-ttu-id="f3328-150"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>スタイラス ポイントを収集するように、動的なレンダリング スレッドでビジュアル ツリーを構築します。</span><span class="sxs-lookup"><span data-stu-id="f3328-150">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> builds a visual tree on the dynamic rendering thread as it collects stylus points.</span></span>  <span data-ttu-id="f3328-151">ユーザーがストロークを完了すると、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>アプリケーションが実行すると、次の表示パスに通知するように要求します。</span><span class="sxs-lookup"><span data-stu-id="f3328-151">When the user finishes the stroke, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> asks to be notified when the application does the next rendering pass.</span></span>  <span data-ttu-id="f3328-152">アプリケーションが、次のレンダリング パスが完了した後、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>そのビジュアル ツリーをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="f3328-152">After the application completes the next rendering pass, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cleans up its visual tree.</span></span>  <span data-ttu-id="f3328-153">次の図は、このプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="f3328-153">The following diagram illustrates this process.</span></span>  
  
 <span data-ttu-id="f3328-154">![インク スレッド処理図](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")</span><span class="sxs-lookup"><span data-stu-id="f3328-154">![Ink threading diagram](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")</span></span>  
  
1.  <span data-ttu-id="f3328-155">ユーザーがストロークを開始します。</span><span class="sxs-lookup"><span data-stu-id="f3328-155">The user begins the stroke.</span></span>  
  
    1.  <span data-ttu-id="f3328-156"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ビジュアル ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3328-156">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> creates the visual tree.</span></span>  
  
2.  <span data-ttu-id="f3328-157">ユーザーがストロークを描画します。</span><span class="sxs-lookup"><span data-stu-id="f3328-157">The user is drawing the stroke.</span></span>  
  
    1.  <span data-ttu-id="f3328-158"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>ビジュアル ツリーを構築します。</span><span class="sxs-lookup"><span data-stu-id="f3328-158">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> builds the visual tree.</span></span>  
  
3.  <span data-ttu-id="f3328-159">ユーザーがストロークを終了します。</span><span class="sxs-lookup"><span data-stu-id="f3328-159">The user ends the stroke.</span></span>  
  
    1.  <span data-ttu-id="f3328-160"><xref:System.Windows.Controls.InkPresenter>ストロークをそのビジュアル ツリーに追加します。</span><span class="sxs-lookup"><span data-stu-id="f3328-160">The <xref:System.Windows.Controls.InkPresenter> adds the stroke to its visual tree.</span></span>  
  
    2.  <span data-ttu-id="f3328-161">メディアの統合レイヤー (数 600万個) は、静的にストロークを描画します。</span><span class="sxs-lookup"><span data-stu-id="f3328-161">The Media Integration Layer (MIL) statically renders the strokes.</span></span>  
  
    3.  <span data-ttu-id="f3328-162"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>のビジュアルをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="f3328-162">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> cleans up the visuals.</span></span>
