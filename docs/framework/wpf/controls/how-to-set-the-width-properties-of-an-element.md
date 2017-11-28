---
title: "方法 : 要素の Width プロパティを設定する"
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
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 830289f13ac89601f0d3539e2f4400e56a2476f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="5db16-102">方法 : 要素の Width プロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="5db16-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="5db16-103">例</span><span class="sxs-lookup"><span data-stu-id="5db16-103">Example</span></span>  
 <span data-ttu-id="5db16-104">この例は、レンダリングの 4 つの幅に関連するプロパティの間での動作の違いを視覚的にでは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="5db16-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="5db16-105"><xref:System.Windows.FrameworkElement>クラスは、要素の幅の特性を説明する 4 つのプロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="5db16-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="5db16-106">これら 4 つのプロパティが競合することと優先する値は次のように決定されます、:<xref:System.Windows.FrameworkElement.MinWidth%2A>値よりも優先、<xref:System.Windows.FrameworkElement.MaxWidth%2A>値で、さらによりも優先、<xref:System.Windows.FrameworkElement.Width%2A>値。</span><span class="sxs-lookup"><span data-stu-id="5db16-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="5db16-107">4 番目のプロパティ<xref:System.Windows.FrameworkElement.ActualWidth%2A>は読み取り専用、およびレイアウトの処理との対話によって決定される実際の幅を報告します。</span><span class="sxs-lookup"><span data-stu-id="5db16-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="5db16-108">次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例の描画、<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) の子として<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="5db16-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="5db16-109">幅のプロパティを変更することができます、<xref:System.Windows.Shapes.Rectangle>の系列を使用して、<xref:System.Windows.Controls.ListBox>のプロパティ値を表す要素<xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.MaxWidth%2A>、および<xref:System.Windows.FrameworkElement.Width%2A>です。</span><span class="sxs-lookup"><span data-stu-id="5db16-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="5db16-110">この方法で各プロパティの優先度が視覚的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5db16-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="5db16-111">次のコード ビハインド例は、イベントを処理する、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="5db16-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="5db16-112">各カスタム メソッドからの入力を受け取り、 <xref:System.Windows.Controls.ListBox>、として値を解析して、 <xref:System.Double>、し、指定した幅に関連するプロパティに値を適用します。</span><span class="sxs-lookup"><span data-stu-id="5db16-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="5db16-113">幅の値も文字列に変換され、さまざまなに書き込まれる<xref:System.Windows.Controls.TextBlock>要素 (それらの要素の定義は、選択した XAML には表示されません)。</span><span class="sxs-lookup"><span data-stu-id="5db16-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="5db16-114">サンプル全体については、次を参照してください。[幅のプロパティの比較サンプル](http://go.microsoft.com/fwlink/?LinkID=160050)です。</span><span class="sxs-lookup"><span data-stu-id="5db16-114">For the complete sample, see [Width Properties Comparison Sample](http://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db16-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5db16-115">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [<span data-ttu-id="5db16-116">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="5db16-116">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="5db16-117">要素の Height プロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="5db16-117">Set the Height Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [<span data-ttu-id="5db16-118">幅のプロパティの比較サンプル</span><span class="sxs-lookup"><span data-stu-id="5db16-118">Width Properties Comparison Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160050)
