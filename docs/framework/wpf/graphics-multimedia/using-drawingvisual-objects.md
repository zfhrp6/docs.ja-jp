---
title: "DrawingVisual オブジェクトの使用"
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
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a33e56b69a357694a1d1a23d5cd3c887c88cea37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-drawingvisual-objects"></a><span data-ttu-id="57bc9-102">DrawingVisual オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="57bc9-102">Using DrawingVisual Objects</span></span>
<span data-ttu-id="57bc9-103">このトピックの使用方法の概要を説明する<xref:System.Windows.Media.DrawingVisual>内のオブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ビジュアル層です。</span><span class="sxs-lookup"><span data-stu-id="57bc9-103">This topic provides an overview of how to use <xref:System.Windows.Media.DrawingVisual> objects in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual layer.</span></span>  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a><span data-ttu-id="57bc9-104">DrawingVisual オブジェクト</span><span class="sxs-lookup"><span data-stu-id="57bc9-104">DrawingVisual Object</span></span>  
 <span data-ttu-id="57bc9-105"><xref:System.Windows.Media.DrawingVisual>は、軽量な図形、画像、またはテキストを表示するために使用されるクラスを描画します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-105">The <xref:System.Windows.Media.DrawingVisual> is a lightweight drawing class that is used to render shapes, images, or text.</span></span> <span data-ttu-id="57bc9-106">このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。</span><span class="sxs-lookup"><span data-stu-id="57bc9-106">This class is considered lightweight because it does not provide layout or event handling, which improves its performance.</span></span> <span data-ttu-id="57bc9-107">そのため、背景やクリップ アートの描画に適しています。</span><span class="sxs-lookup"><span data-stu-id="57bc9-107">For this reason, drawings are ideal for backgrounds and clip art.</span></span>  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a><span data-ttu-id="57bc9-108">DrawingVisual ホスト コンテナー</span><span class="sxs-lookup"><span data-stu-id="57bc9-108">DrawingVisual Host Container</span></span>  
 <span data-ttu-id="57bc9-109">使用するために<xref:System.Windows.Media.DrawingVisual>オブジェクト、オブジェクトのホストのコンテナーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bc9-109">In order to use <xref:System.Windows.Media.DrawingVisual> objects, you need to create a host container for the objects.</span></span> <span data-ttu-id="57bc9-110">ホストのコンテナー オブジェクトがから派生する必要があります、<xref:System.Windows.FrameworkElement>レイアウトやイベント処理のサポートを提供するクラス、<xref:System.Windows.Media.DrawingVisual>クラスがありません。</span><span class="sxs-lookup"><span data-stu-id="57bc9-110">The host container object must derive from the <xref:System.Windows.FrameworkElement> class, which provides the layout and event handling support that the <xref:System.Windows.Media.DrawingVisual> class lacks.</span></span> <span data-ttu-id="57bc9-111">ホスト コンテナー オブジェクトの主な目的は子オブジェクトを格納することなので、ホスト コンテナー オブジェクトでは可視プロパティは表示されません。</span><span class="sxs-lookup"><span data-stu-id="57bc9-111">The host container object does not display any visible properties, since its main purpose is to contain child objects.</span></span> <span data-ttu-id="57bc9-112">ただし、<xref:System.Windows.UIElement.Visibility%2A>にコンテナー ホストのプロパティを設定する必要があります<xref:System.Windows.Visibility.Visible>以外の場合、その子要素の [なし] が表示されます。</span><span class="sxs-lookup"><span data-stu-id="57bc9-112">However, the <xref:System.Windows.UIElement.Visibility%2A> property of the host container must be set to <xref:System.Windows.Visibility.Visible>; otherwise, none of its child elements will be visible.</span></span>  
  
 <span data-ttu-id="57bc9-113">ビジュアル オブジェクトのホストのコンテナー オブジェクトを作成するときのビジュアル オブジェクトの参照を保存する必要があります、<xref:System.Windows.Media.VisualCollection>です。</span><span class="sxs-lookup"><span data-stu-id="57bc9-113">When you create a host container object for visual objects, you need to store the visual object references in a <xref:System.Windows.Media.VisualCollection>.</span></span> <span data-ttu-id="57bc9-114">使用して、<xref:System.Windows.Media.VisualCollection.Add%2A>ホスト コンテナーにビジュアル オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-114">Use the <xref:System.Windows.Media.VisualCollection.Add%2A> method to add a visual object to the host container.</span></span> <span data-ttu-id="57bc9-115">次の例では、ホストのコンテナー オブジェクトが作成、および 3 つのビジュアル オブジェクトに追加されます、<xref:System.Windows.Media.VisualCollection>です。</span><span class="sxs-lookup"><span data-stu-id="57bc9-115">In the following example, a host container object is created, and three visual objects are added to its <xref:System.Windows.Media.VisualCollection>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  <span data-ttu-id="57bc9-116">上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57bc9-116">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994).</span></span>  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a><span data-ttu-id="57bc9-117">Creating DrawingVisual オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="57bc9-117">Creating DrawingVisual Objects</span></span>  
 <span data-ttu-id="57bc9-118">作成するときに、<xref:System.Windows.Media.DrawingVisual>オブジェクトの描画コンテンツがありません。</span><span class="sxs-lookup"><span data-stu-id="57bc9-118">When you create a <xref:System.Windows.Media.DrawingVisual> object, it has no drawing content.</span></span> <span data-ttu-id="57bc9-119">テキスト、グラフィック、またはイメージのコンテンツを追加するには、オブジェクトを取得することによって<xref:System.Windows.Media.DrawingContext>とそこに描画します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-119">You can add text, graphics, or image content by retrieving the object's <xref:System.Windows.Media.DrawingContext> and drawing into it.</span></span> <span data-ttu-id="57bc9-120">A<xref:System.Windows.Media.DrawingContext>呼び出しによって返される、<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>のメソッド、<xref:System.Windows.Media.DrawingVisual>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="57bc9-120">A <xref:System.Windows.Media.DrawingContext> is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span>  
  
 <span data-ttu-id="57bc9-121">四角形を描く、<xref:System.Windows.Media.DrawingContext>を使用して、<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>のメソッド、<xref:System.Windows.Media.DrawingContext>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="57bc9-121">To draw a rectangle into the <xref:System.Windows.Media.DrawingContext>, use the <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> method of the <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="57bc9-122">他の種類のコンテンツを描画するための同様のメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="57bc9-122">Similar methods exist for drawing other types of content.</span></span> <span data-ttu-id="57bc9-123">描画の内容を完了すると、 <xref:System.Windows.Media.DrawingContext>、呼び出し、<xref:System.Windows.Media.DrawingContext.Close%2A>を終了するメソッド、<xref:System.Windows.Media.DrawingContext>内容を保持するとします。</span><span class="sxs-lookup"><span data-stu-id="57bc9-123">When you are finished drawing content into the <xref:System.Windows.Media.DrawingContext>, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the <xref:System.Windows.Media.DrawingContext> and persist the content.</span></span>  
  
 <span data-ttu-id="57bc9-124">次の例で、<xref:System.Windows.Media.DrawingVisual>オブジェクトが作成され、四角形の描画にその<xref:System.Windows.Media.DrawingContext>です。</span><span class="sxs-lookup"><span data-stu-id="57bc9-124">In the following example, a <xref:System.Windows.Media.DrawingVisual> object is created, and a rectangle is drawn into its <xref:System.Windows.Media.DrawingContext>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a><span data-ttu-id="57bc9-125">FrameworkElement メンバーのオーバーライドの作成</span><span class="sxs-lookup"><span data-stu-id="57bc9-125">Creating Overrides for FrameworkElement Members</span></span>  
 <span data-ttu-id="57bc9-126">ホスト コンテナー オブジェクトは、ビジュアル オブジェクトのコレクションを管理します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-126">The host container object is responsible for managing its collection of visual objects.</span></span> <span data-ttu-id="57bc9-127">これは、ホスト コンテナーが派生クラスのメンバーのオーバーライドを実装する必要があります<xref:System.Windows.FrameworkElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="57bc9-127">This requires that the host container implement member overrides for the derived <xref:System.Windows.FrameworkElement> class.</span></span>  
  
 <span data-ttu-id="57bc9-128">オーバーライドする必要がある 2 つのメンバーを次に示します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-128">The following list describes the two members you must override:</span></span>  
  
-   <span data-ttu-id="57bc9-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: 子要素のコレクションから指定したインデックス位置の子を返します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Returns a child at the specified index from the collection of child elements.</span></span>  
  
-   <span data-ttu-id="57bc9-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: この要素内でビジュアル子要素の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Gets the number of visual child elements within this element.</span></span>  
  
 <span data-ttu-id="57bc9-131">次の例では、2 つのオーバーライド<xref:System.Windows.FrameworkElement>メンバーが実装されます。</span><span class="sxs-lookup"><span data-stu-id="57bc9-131">In the following example, overrides for the two <xref:System.Windows.FrameworkElement> members are implemented.</span></span>  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a><span data-ttu-id="57bc9-132">ヒット テストのサポート</span><span class="sxs-lookup"><span data-stu-id="57bc9-132">Providing Hit Testing Support</span></span>  
 <span data-ttu-id="57bc9-133">イベント処理の表示プロパティが表示されない場合でも、そのホストのコンテナー オブジェクトを提供できます: ただし、その<xref:System.Windows.UIElement.Visibility%2A>プロパティに設定する必要があります<xref:System.Windows.Visibility.Visible>です。</span><span class="sxs-lookup"><span data-stu-id="57bc9-133">The host container object can provide event handling even if it does not display any visible properties—however, its <xref:System.Windows.UIElement.Visibility%2A> property must be set to <xref:System.Windows.Visibility.Visible>.</span></span> <span data-ttu-id="57bc9-134">これにより、マウス イベント (マウスの左ボタンのリリースなど) をトラップできる、ホスト コンテナーのイベント処理ルーチンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="57bc9-134">This allows you to create an event handling routine for the host container that can trap mouse events, such as the release of the left mouse button.</span></span> <span data-ttu-id="57bc9-135">イベントの処理ルーチンを呼び出すことによって、ヒット テスト実装できます、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="57bc9-135">The event handling routine can then implement hit testing by invoking the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="57bc9-136">メソッドの<xref:System.Windows.Media.HitTestResultCallback>パラメーターは、ヒット テストの結果として得られるアクションを決定するのに使用できるユーザー定義のプロシージャを表します。</span><span class="sxs-lookup"><span data-stu-id="57bc9-136">The method's <xref:System.Windows.Media.HitTestResultCallback> parameter refers to a user-defined procedure that you can use to determine the resulting action of a hit test.</span></span>  
  
 <span data-ttu-id="57bc9-137">次の例では、ホスト コンテナー オブジェクトとその子に対してヒット テストのサポートを実装しています。</span><span class="sxs-lookup"><span data-stu-id="57bc9-137">In the following example, hit testing support is implemented for the host container object and its children.</span></span>  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="57bc9-138">参照</span><span class="sxs-lookup"><span data-stu-id="57bc9-138">See Also</span></span>  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [<span data-ttu-id="57bc9-139">WPF グラフィックス レンダリングの概要</span><span class="sxs-lookup"><span data-stu-id="57bc9-139">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="57bc9-140">ビジュアル層でのヒット テスト</span><span class="sxs-lookup"><span data-stu-id="57bc9-140">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
