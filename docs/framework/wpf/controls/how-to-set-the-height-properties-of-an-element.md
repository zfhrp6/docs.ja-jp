---
title: "方法 : 要素の Height プロパティを設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "高さのプロパティ"
  - "Panel コントロール, 高さのプロパティ (要素の)"
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 要素の Height プロパティを設定する
## 使用例  
 この例では、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の高さに関連する 4 つのプロパティについて、描画の動作の違いを視覚的に示します。  
  
 <xref:System.Windows.FrameworkElement> クラスは、要素の高さの特性を記述する 4 つのプロパティを公開します。  これらの 4 つのプロパティは競合する可能性がありますが、その場合は、<xref:System.Windows.FrameworkElement.MinHeight%2A> 値、<xref:System.Windows.FrameworkElement.MaxHeight%2A> 値、<xref:System.Windows.FrameworkElement.Height%2A> 値の順序で優先して使用されます。  4 つ目のプロパティの <xref:System.Windows.FrameworkElement.ActualHeight%2A> は読み取り専用で、レイアウト プロセスとのやり取りによって決定される実際の高さを報告します。  
  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の例では、<xref:System.Windows.Shapes.Rectangle> 要素 \(`rect1`\) を <xref:System.Windows.Controls.Canvas> の子として描画します。  <xref:System.Windows.Shapes.Rectangle> の高さのプロパティは、<xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>、および <xref:System.Windows.FrameworkElement.Height%2A> の各プロパティ値を表す一連の <xref:System.Windows.Controls.ListBox> 要素を使用して変更できます。  この方法では、各プロパティの優先順位が表示されます。  
  
 [!code-xml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 次の分離コードの例では、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> イベントによって発生したイベントを処理します。  各ハンドラーは <xref:System.Windows.Controls.ListBox> から入力を受け取り、値を <xref:System.Double> として解析し、指定された高さに関連するプロパティに値を適用します。  高さの値は文字列にも変換され、各種の <xref:System.Windows.Controls.TextBlock> 要素に書き込まれます \(それらの要素の定義は、上の XAML の例には示されていません\)。  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 サンプル全体については、[Height プロパティのサンプル](http://go.microsoft.com/fwlink/?LinkID=159993)を参照してください。  
  
## 参照  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>   
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>   
 <xref:System.Windows.FrameworkElement.MinHeight%2A>   
 <xref:System.Windows.FrameworkElement.Height%2A>   
 [要素の Width プロパティを設定する](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Height プロパティのサンプル](http://go.microsoft.com/fwlink/?LinkID=159993)