---
title: "方法 : カスタム コントロールからインクを選択する"
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
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 972ece6964d1f3cc42c6221c3b18336e3353bc18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-ink-from-a-custom-control"></a><span data-ttu-id="f87d9-102">方法 : カスタム コントロールからインクを選択する</span><span class="sxs-lookup"><span data-stu-id="f87d9-102">How to: Select Ink from a Custom Control</span></span>
<span data-ttu-id="f87d9-103">追加することによって、 <xref:System.Windows.Ink.IncrementalLassoHitTester> 、カスタム コントロールを有効にできますコントロールと同じように、選択ツールを使用してインクをユーザーが選択できるように、<xref:System.Windows.Controls.InkCanvas>なげなわを使用してインクを選択します。</span><span class="sxs-lookup"><span data-stu-id="f87d9-103">By adding an <xref:System.Windows.Ink.IncrementalLassoHitTester> to your custom control, you can enable your control so that a user can select ink with a lasso tool, similar to the way the <xref:System.Windows.Controls.InkCanvas> selects ink with a lasso.</span></span>  
  
 <span data-ttu-id="f87d9-104">この例では、インクが有効なカスタム コントロールの作成に慣れて前提としています。</span><span class="sxs-lookup"><span data-stu-id="f87d9-104">This example assumes you are familiar with creating an ink-enabled custom control.</span></span>  <span data-ttu-id="f87d9-105">インク入力を受け付けるカスタム コントロールを作成するを参照してください。[インク入力コントロールを作成する](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-105">To create a custom control that accepts ink input, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f87d9-106">例</span><span class="sxs-lookup"><span data-stu-id="f87d9-106">Example</span></span>  
 <span data-ttu-id="f87d9-107">ユーザーが、なげなわを描画するとき、<xref:System.Windows.Ink.IncrementalLassoHitTester>するストロークは、ユーザーがなげなわが完了したら、なげなわのパスの境界内を予測します。</span><span class="sxs-lookup"><span data-stu-id="f87d9-107">When the user draws a lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> predicts which strokes will be within the lasso path's boundaries after the user completes the lasso.</span></span>  <span data-ttu-id="f87d9-108">なげなわのパスの境界内にあると判断したストロークは、選択されていると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="f87d9-108">Strokes that are determined to be within the lasso path's boundaries can be thought of as being selected.</span></span>  <span data-ttu-id="f87d9-109">選択されたストロークをオフになっていることができますもなります。</span><span class="sxs-lookup"><span data-stu-id="f87d9-109">Selected strokes can also become unselected.</span></span>  <span data-ttu-id="f87d9-110">たとえば、ユーザー、描画中には方向が反転、<xref:System.Windows.Ink.IncrementalLassoHitTester>のストロークを選択解除できます。</span><span class="sxs-lookup"><span data-stu-id="f87d9-110">For example, if the user reverses direction while drawing the lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> may unselect some strokes.</span></span>  
  
 <span data-ttu-id="f87d9-111"><xref:System.Windows.Ink.IncrementalLassoHitTester>を生成、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベントで、ユーザーは、描画中に応答する、カスタムの制御を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f87d9-111">The <xref:System.Windows.Ink.IncrementalLassoHitTester> raises the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, which enables your custom control to respond while the user is drawing the lasso.</span></span>  <span data-ttu-id="f87d9-112">たとえば、ユーザーを選択し、それらの選択を解除すると、ストロークの外観を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f87d9-112">For example, you can change the appearance of strokes as the user selects and unselects them.</span></span>  
  
## <a name="managing-the-ink-mode"></a><span data-ttu-id="f87d9-113">インク モードの管理</span><span class="sxs-lookup"><span data-stu-id="f87d9-113">Managing the Ink Mode</span></span>  
 <span data-ttu-id="f87d9-114">なげなわがコントロール上のインクが異なって表示される場合、ユーザーに便利です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-114">It is helpful to the user if the lasso appears differently than the ink on your control.</span></span> <span data-ttu-id="f87d9-115">これを実現するには、カスタム コントロールする必要がありますの追跡、ユーザーが記述またはインクを選択するかどうか。</span><span class="sxs-lookup"><span data-stu-id="f87d9-115">To accomplish this, your custom control must keep track of whether the user is writing or selecting ink.</span></span> <span data-ttu-id="f87d9-116">これを行う最も簡単な方法は 2 つの値を持つ列挙体を宣言する: インクと、ユーザーがインクを選択することを示すために 1 つに、ユーザーを作成することを示すために 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f87d9-116">The easiest way to do this is to declare an enumeration with two values: one to indicate that the user is writing ink and one to indicate that the user is selecting ink.</span></span>  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 <span data-ttu-id="f87d9-117">次に、2 つ追加<xref:System.Windows.Ink.DrawingAttributes>クラス: ユーザーがユーザーには、インクが選択したときに使用する 1 つのインクを書き込むときに使用する 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f87d9-117">Next, add two <xref:System.Windows.Ink.DrawingAttributes> to the class: one to use when the user writes ink, one to use when the user selects ink.</span></span>  <span data-ttu-id="f87d9-118">コンス トラクターで初期化、<xref:System.Windows.Ink.DrawingAttributes>とアタッチ両方<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>同じイベント ハンドラーにイベント。</span><span class="sxs-lookup"><span data-stu-id="f87d9-118">In the constructor, initialize the <xref:System.Windows.Ink.DrawingAttributes> and attach both <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> events to the same event handler.</span></span> <span data-ttu-id="f87d9-119">設定して、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>のプロパティ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>インク<xref:System.Windows.Ink.DrawingAttributes>です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-119">Then set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the ink <xref:System.Windows.Ink.DrawingAttributes>.</span></span>  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 <span data-ttu-id="f87d9-120">選択モードを公開するプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="f87d9-120">Add a property that exposes the selection mode.</span></span> <span data-ttu-id="f87d9-121">選択モードを変更するときの設定、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>のプロパティ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を適切な<xref:System.Windows.Ink.DrawingAttributes>オブジェクトを再アタッチし、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>プロパティを<xref:System.Windows.Controls.InkPresenter>です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-121">When the user changes the selection mode, set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the appropriate <xref:System.Windows.Ink.DrawingAttributes> object and then reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> Property to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 <span data-ttu-id="f87d9-122">公開、<xref:System.Windows.Ink.DrawingAttributes>としてプロパティのアプリケーションは、インク ストロークと選択線の外観を特定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f87d9-122">Expose the <xref:System.Windows.Ink.DrawingAttributes> as properties so applications can determine the appearance of the ink strokes and selection strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 <span data-ttu-id="f87d9-123">場合のプロパティ、<xref:System.Windows.Ink.DrawingAttributes>オブジェクトに対する変更を<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>にアタッチする必要があります、<xref:System.Windows.Controls.InkPresenter>です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-123">When a property of a <xref:System.Windows.Ink.DrawingAttributes> object changes, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> must be reattached to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="f87d9-124">イベント ハンドラーで、<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>イベント、再接続、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>を<xref:System.Windows.Controls.InkPresenter>です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-124">In the event handler for the <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> event, reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a><span data-ttu-id="f87d9-125">使用して、IncrementalLassoHitTester</span><span class="sxs-lookup"><span data-stu-id="f87d9-125">Using the IncrementalLassoHitTester</span></span>  
 <span data-ttu-id="f87d9-126">作成し、初期化、<xref:System.Windows.Ink.StrokeCollection>選択されたストロークを格納しています。</span><span class="sxs-lookup"><span data-stu-id="f87d9-126">Create and initialize a <xref:System.Windows.Ink.StrokeCollection> that contains the selected strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 <span data-ttu-id="f87d9-127">ユーザーがストロークを描画を開始、ときにインクまたはなげなわのいずれかの選択を解除、選択されたストロークです。</span><span class="sxs-lookup"><span data-stu-id="f87d9-127">When the user starts to draw a stroke, either ink or the lasso, unselect any selected strokes.</span></span> <span data-ttu-id="f87d9-128">次に、ユーザーはなげなわを描画して場合に作成、<xref:System.Windows.Ink.IncrementalLassoHitTester>を呼び出して<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>にサブスクライブ、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベント、および呼び出し<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-128">Then, if the user is drawing a lasso, create an <xref:System.Windows.Ink.IncrementalLassoHitTester> by calling <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subscribe to the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, and call <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span></span> <span data-ttu-id="f87d9-129">このコードを別のメソッドを指定できから呼び出される、<xref:System.Windows.UIElement.OnStylusDown%2A>と<xref:System.Windows.UIElement.OnMouseDown%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f87d9-129">This code can be a separate method and called from the <xref:System.Windows.UIElement.OnStylusDown%2A> and <xref:System.Windows.UIElement.OnMouseDown%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 <span data-ttu-id="f87d9-130">スタイラスのポイントを追加、<xref:System.Windows.Ink.IncrementalLassoHitTester>ユーザーが、なげなわを描画中にします。</span><span class="sxs-lookup"><span data-stu-id="f87d9-130">Add the stylus points to the <xref:System.Windows.Ink.IncrementalLassoHitTester> while the user draws the lasso.</span></span>  <span data-ttu-id="f87d9-131">次のメソッドを呼び出して、 <xref:System.Windows.UIElement.OnStylusMove%2A>、 <xref:System.Windows.UIElement.OnStylusUp%2A>、 <xref:System.Windows.UIElement.OnMouseMove%2A>、および<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f87d9-131">Call the following method from the <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, and <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 <span data-ttu-id="f87d9-132">処理、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType>イベント、ユーザーを選択し、ストロークの選択を解除するときに応答します。</span><span class="sxs-lookup"><span data-stu-id="f87d9-132">Handle the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> event to respond when the user selects and unselects strokes.</span></span>  <span data-ttu-id="f87d9-133"><xref:System.Windows.Ink.LassoSelectionChangedEventArgs>クラスには、<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A>と<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A>ストロークを取得するプロパティがオンし、オフの場合、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="f87d9-133">The <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> class has the <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> and <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> properties that get the strokes that were selected and unselected, respectively.</span></span>  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 <span data-ttu-id="f87d9-134">ユーザーは、描画が完了すると、サブスクリプションの解除、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベントと呼び出し<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>です。</span><span class="sxs-lookup"><span data-stu-id="f87d9-134">When the user finishes drawing the lasso, unsubscribe from the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event and call <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span></span>  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a><span data-ttu-id="f87d9-135">すべてまとめて配置することです。</span><span class="sxs-lookup"><span data-stu-id="f87d9-135">Putting it All Together.</span></span>  
 <span data-ttu-id="f87d9-136">次の例は、カスタム コントロールをなげなわを使用してインクを選択するユーザーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f87d9-136">The following example is a custom control that enables a user to select ink with a lasso.</span></span>  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f87d9-137">参照</span><span class="sxs-lookup"><span data-stu-id="f87d9-137">See Also</span></span>  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [<span data-ttu-id="f87d9-138">インク入力コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="f87d9-138">Creating an Ink Input Control</span></span>](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
