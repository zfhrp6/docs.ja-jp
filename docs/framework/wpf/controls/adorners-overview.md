---
title: 装飾の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 6dd38b9e24b42de8945c0e9729f8f30cf901fc3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557122"
---
# <a name="adorners-overview"></a><span data-ttu-id="f2c7f-102">装飾の概要</span><span class="sxs-lookup"><span data-stu-id="f2c7f-102">Adorners Overview</span></span>
<span data-ttu-id="f2c7f-103">装飾は、特殊な種類の<xref:System.Windows.FrameworkElement>で視覚的な手掛かりをユーザーに提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="f2c7f-104">装飾は、要素への機能ハンドル追加やコントロールに関する状態情報の提供など、さまざまな用途に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="f2c7f-105">装飾について</span><span class="sxs-lookup"><span data-stu-id="f2c7f-105">About Adorners</span></span>  
 <span data-ttu-id="f2c7f-106"><xref:System.Windows.Documents.Adorner>カスタム<xref:System.Windows.FrameworkElement>にバインドされている、<xref:System.Windows.UIElement>です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="f2c7f-107">装飾は、 <xref:System.Windows.Documents.AdornerLayer>、装飾される要素、または装飾される要素のコレクションの上には、常にするための描画サーフェイスであります。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="f2c7f-108">装飾のレンダリングがレンダリングから独立して、<xref:System.Windows.UIElement>に装飾がバインドされています。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="f2c7f-109">通常、装飾は、装飾対象の要素の左上に位置する標準の 2 次元座標の原点を使用して、バインド先の要素に対して相対的な位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="f2c7f-110">装飾の一般的な用途は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="f2c7f-111">機能のハンドルへの追加、 <xref:System.Windows.UIElement> (サイズ変更、回転、再配置など) 何らかの方法で要素を操作するユーザーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="f2c7f-112">視覚的なフィードバックによって、さまざまな状態を表示し、各種のイベントに応答する。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="f2c7f-113">ビジュアルの装飾をオーバーレイ、<xref:System.Windows.UIElement>です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="f2c7f-114">視覚的にマスクまたはの一部またはすべてを上書き、<xref:System.Windows.UIElement>です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="f2c7f-115"> は、視覚的要素を装飾する基本的なフレームワークを提供します。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-115"> provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="f2c7f-116">次の表に示すのは、オブジェクトの装飾に使用する主な種類と、その用途の一覧です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="f2c7f-117">その後に、使用例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="f2c7f-118">具体的な装飾の実装すべての継承元になる抽象基本クラス。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="f2c7f-119">装飾される 1 つ以上の要素に対する、装飾のレンダリング層を表すクラス。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="f2c7f-120">1 つの装飾層を要素のコレクションに関連付けることを可能にするクラス。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="f2c7f-121">カスタム装飾の実装</span><span class="sxs-lookup"><span data-stu-id="f2c7f-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="f2c7f-122">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が提供する装飾フレームワークは、カスタム装飾の作成をサポートすることを主な目的としています。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="f2c7f-123">カスタムの装飾が抽象から継承するクラスを実装することによって作成された<xref:System.Windows.Documents.Adorner>クラスです。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2c7f-124">親、<xref:System.Windows.Documents.Adorner>は、<xref:System.Windows.Documents.AdornerLayer>表示するための<xref:System.Windows.Documents.Adorner>装飾される要素ではなく、します。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="f2c7f-125">次の例では、簡単な装飾を実装するクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="f2c7f-126">例の装飾は、の<xref:System.Windows.UIElement>円でします。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="f2c7f-127">次の図に適用される SimpleCircleAdorner、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="f2c7f-128">![装飾の例: 装飾された TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="f2c7f-128">![Adorners Example: An adorned TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="f2c7f-129">装飾のレンダリング動作</span><span class="sxs-lookup"><span data-stu-id="f2c7f-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="f2c7f-130">装飾自体にはレンダリング動作が備わっていないので、装飾のレンダリングは装飾の実装側の責任で行う必要がある点に、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="f2c7f-131">レンダリング動作を実装する一般的な方法は、上書きする、<xref:System.Windows.UIElement.OnRender%2A>メソッドと 1 つ以上を使用して<xref:System.Windows.Media.DrawingContext>に応じて (上記の例で示した部分) の装飾のビジュアルを表示するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2c7f-132">装飾層に配置されているすべてのものは、設定した他のすべてのスタイルの上に描画されます。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="f2c7f-133">つまり、装飾は常に視覚的に最上位にあり、z オーダーを使用してオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="f2c7f-134">イベントおよびヒット テスト</span><span class="sxs-lookup"><span data-stu-id="f2c7f-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="f2c7f-135">ガイドと同じように、他の入力イベントを受信する<xref:System.Windows.FrameworkElement>です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="f2c7f-136">装飾が入力イベントを受け取る装飾には、常には、adorns 要素よりも高い z オーダーがあるため (など<xref:System.Windows.UIElement.Drop>または<xref:System.Windows.UIElement.MouseMove>) 要素を装飾する、基になるを想定可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="f2c7f-137">装飾は、特定の入力イベントをリッスンし、それらのイベントを再度発生させることによって、下位にある装飾対象の要素に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="f2c7f-138">装飾の下の要素のパススルー ヒット テストを有効にするには、ヒット テストを設定<xref:System.Windows.UIElement.IsHitTestVisible%2A>プロパティを**false**で装飾します。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="f2c7f-139">ヒット テストの詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="f2c7f-140">[ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-140">[Hit Testing in the Visual Layer](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="f2c7f-141">単一の UIElement の装飾</span><span class="sxs-lookup"><span data-stu-id="f2c7f-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="f2c7f-142">特定の装飾にバインドする<xref:System.Windows.UIElement>、これらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f2c7f-143">静的メソッドを呼び出す<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>を取得する、<xref:System.Windows.Documents.AdornerLayer>オブジェクトに対して、<xref:System.Windows.UIElement>を装飾します。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="f2c7f-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 指定した位置を開始、ビジュアル ツリーを調べて<xref:System.Windows.UIElement>、し、見つかった最初の装飾層を返します。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="f2c7f-145">(装飾層が見つからない場合、メソッドにより null が返されます)。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="f2c7f-146">呼び出す、<xref:System.Windows.Documents.AdornerLayer.Add%2A>装飾をターゲットにバインドするメソッド<xref:System.Windows.UIElement>です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="f2c7f-147">次の例に (上記) SimpleCircleAdorner、<xref:System.Windows.Controls.TextBox>という*myTextBox*です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="f2c7f-148">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="f2c7f-149">パネルの子の装飾</span><span class="sxs-lookup"><span data-stu-id="f2c7f-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="f2c7f-150">子に装飾をバインドする、 <xref:System.Windows.Controls.Panel>、これらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f2c7f-151">呼び出す、`static`メソッド<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>子によって実装されている要素の装飾層が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="f2c7f-152">親要素と呼び出しの子を列挙、<xref:System.Windows.Documents.AdornerLayer.Add%2A>装飾を各子要素にバインドするメソッド。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="f2c7f-153">次の例では、子に (上記) SimpleCircleAdorner、<xref:System.Windows.Controls.StackPanel>という*myStackPanel*です。</span><span class="sxs-lookup"><span data-stu-id="f2c7f-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="f2c7f-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2c7f-154">See Also</span></span>  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [<span data-ttu-id="f2c7f-155">WPF での図形と基本描画の概要</span><span class="sxs-lookup"><span data-stu-id="f2c7f-155">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="f2c7f-156">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="f2c7f-156">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="f2c7f-157">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="f2c7f-157">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="f2c7f-158">方法トピック</span><span class="sxs-lookup"><span data-stu-id="f2c7f-158">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
