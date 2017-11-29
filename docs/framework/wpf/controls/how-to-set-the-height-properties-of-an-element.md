---
title: "方法 : 要素の Height プロパティを設定する"
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
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ae66e60375cfbc45a4f1e8834b6420bc5c0b70a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="93457-102">方法 : 要素の Height プロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="93457-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="93457-103">例</span><span class="sxs-lookup"><span data-stu-id="93457-103">Example</span></span>  
 <span data-ttu-id="93457-104">この例は、レンダリングの 4 つの高さに関連したプロパティの間での動作の違いを視覚的にでは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="93457-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="93457-105"><xref:System.Windows.FrameworkElement>クラスは、要素の高さの特性を説明する 4 つのプロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="93457-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="93457-106">これら 4 つのプロパティが競合することと優先する値は次のように決定されます、:<xref:System.Windows.FrameworkElement.MinHeight%2A>値よりも優先、<xref:System.Windows.FrameworkElement.MaxHeight%2A>値で、さらによりも優先、<xref:System.Windows.FrameworkElement.Height%2A>値。</span><span class="sxs-lookup"><span data-stu-id="93457-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="93457-107">4 番目のプロパティ<xref:System.Windows.FrameworkElement.ActualHeight%2A>は読み取り専用、およびレイアウトの処理との対話によって決定される実際の高さを報告します。</span><span class="sxs-lookup"><span data-stu-id="93457-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="93457-108">次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例の描画、<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) の子として<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="93457-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="93457-109">高さのプロパティを変更することができます、<xref:System.Windows.Shapes.Rectangle>の系列を使用して、<xref:System.Windows.Controls.ListBox>のプロパティ値を表す要素<xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>、および<xref:System.Windows.FrameworkElement.Height%2A>です。</span><span class="sxs-lookup"><span data-stu-id="93457-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="93457-110">この方法で各プロパティの優先度が視覚的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="93457-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="93457-111">次のコード ビハインド例は、イベントを処理する、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="93457-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="93457-112">各ハンドラーからの入力を受け取り、 <xref:System.Windows.Controls.ListBox>、として値を解析して、 <xref:System.Double>、し、指定した高さに関連するプロパティに値を適用します。</span><span class="sxs-lookup"><span data-stu-id="93457-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="93457-113">高さの値も文字列に変換され、さまざまなに書き込まれる<xref:System.Windows.Controls.TextBlock>要素 (それらの要素の定義は、選択した XAML には表示されません)。</span><span class="sxs-lookup"><span data-stu-id="93457-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="93457-114">サンプル全体については、次を参照してください。[高さのプロパティのサンプル](http://go.microsoft.com/fwlink/?LinkID=159993)です。</span><span class="sxs-lookup"><span data-stu-id="93457-114">For the complete sample, see [Height Properties Sample](http://go.microsoft.com/fwlink/?LinkID=159993).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93457-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="93457-115">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [<span data-ttu-id="93457-116">要素の Width プロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="93457-116">Set the Width Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [<span data-ttu-id="93457-117">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="93457-117">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="93457-118">高さのプロパティのサンプル</span><span class="sxs-lookup"><span data-stu-id="93457-118">Height Properties Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159993)
