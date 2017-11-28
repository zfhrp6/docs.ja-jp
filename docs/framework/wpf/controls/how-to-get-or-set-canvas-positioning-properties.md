---
title: "方法 : Canvas の配置プロパティを取得または設定する"
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
helpviewer_keywords: Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b2f20754c8425149f73f10af773604539125adb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a><span data-ttu-id="d764e-102">方法 : Canvas の配置プロパティを取得または設定する</span><span class="sxs-lookup"><span data-stu-id="d764e-102">How to: Get or Set Canvas Positioning Properties</span></span>
<span data-ttu-id="d764e-103">この例の配置のメソッドを使用する方法を示しています、<xref:System.Windows.Controls.Canvas>要素に子コンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="d764e-103">This example shows how to use the positioning methods of the <xref:System.Windows.Controls.Canvas> element to position child content.</span></span> <span data-ttu-id="d764e-104">この例の内容を使用して、<xref:System.Windows.Controls.ListBoxItem>を表す位置指定値し、のインスタンスに値を変換します<xref:System.Double>、これは必須の引数の位置を決定します。</span><span class="sxs-lookup"><span data-stu-id="d764e-104">This example uses content in a <xref:System.Windows.Controls.ListBoxItem> to represent positioning values and converts the values into instances of <xref:System.Double>, which is a required argument for positioning.</span></span> <span data-ttu-id="d764e-105">値は文字列に変換し、内のテキストとして表示されます、<xref:System.Windows.Controls.TextBlock>要素を使用して、<xref:System.Windows.Controls.Canvas.GetLeft%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d764e-105">The values are then converted back into strings and displayed as text in a <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.Canvas.GetLeft%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d764e-106">例</span><span class="sxs-lookup"><span data-stu-id="d764e-106">Example</span></span>  
 <span data-ttu-id="d764e-107">次の例を作成、<xref:System.Windows.Controls.ListBox>を持つ 11 個の選択可能な要素<xref:System.Windows.Controls.ListBoxItem>要素。</span><span class="sxs-lookup"><span data-stu-id="d764e-107">The following example creates a <xref:System.Windows.Controls.ListBox> element that has eleven selectable <xref:System.Windows.Controls.ListBoxItem> elements.</span></span> <span data-ttu-id="d764e-108"><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベント トリガー、`ChangeLeft`後続のコード ブロックを定義するカスタム メソッド。</span><span class="sxs-lookup"><span data-stu-id="d764e-108">The <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event triggers the `ChangeLeft` custom method, which the subsequent code block defines.</span></span>  
  
 <span data-ttu-id="d764e-109">各<xref:System.Windows.Controls.ListBoxItem>を表す、<xref:System.Double>は引数の 1 つの値を<xref:System.Windows.Controls.Canvas.SetLeft%2A>メソッドの<xref:System.Windows.Controls.Canvas>を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="d764e-109">Each <xref:System.Windows.Controls.ListBoxItem> represents a <xref:System.Double> value, which is one of the arguments that the <xref:System.Windows.Controls.Canvas.SetLeft%2A> method of <xref:System.Windows.Controls.Canvas> accepts.</span></span> <span data-ttu-id="d764e-110">使用するために、<xref:System.Windows.Controls.ListBoxItem>のインスタンスを表す<xref:System.Double>、最初に変換する必要があります、<xref:System.Windows.Controls.ListBoxItem>を正しいデータ型。</span><span class="sxs-lookup"><span data-stu-id="d764e-110">In order to use a <xref:System.Windows.Controls.ListBoxItem> to represent an instance of <xref:System.Double>, you must first convert the <xref:System.Windows.Controls.ListBoxItem> to the correct data type.</span></span>  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="d764e-111">ユーザーが変更されたとき、<xref:System.Windows.Controls.ListBox>を呼び出すの選択、`ChangeLeft`カスタム メソッド。</span><span class="sxs-lookup"><span data-stu-id="d764e-111">When a user changes the <xref:System.Windows.Controls.ListBox> selection, it invokes the `ChangeLeft` custom method.</span></span> <span data-ttu-id="d764e-112">このメソッドは、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.LengthConverter>に変換するオブジェクト、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Double>(この値は既にに変換されたことを確認、<xref:System.String>を使用して、 <xref:System.Windows.Controls.Control.ToString%2A>メソッドの場合)。</span><span class="sxs-lookup"><span data-stu-id="d764e-112">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.LengthConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double> (notice that this value has already been converted to a <xref:System.String> by using the <xref:System.Windows.Controls.Control.ToString%2A> method).</span></span> <span data-ttu-id="d764e-113">この値に渡され、<xref:System.Windows.Controls.Canvas.SetLeft%2A>と<xref:System.Windows.Controls.Canvas.GetLeft%2A>のメソッド<xref:System.Windows.Controls.Canvas>の位置を変更するために、`text1`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d764e-113">This value is then passed back to the <xref:System.Windows.Controls.Canvas.SetLeft%2A> and <xref:System.Windows.Controls.Canvas.GetLeft%2A> methods of <xref:System.Windows.Controls.Canvas> in order to change the position of the `text1` object.</span></span>  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d764e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d764e-114">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [<span data-ttu-id="d764e-115">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="d764e-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
