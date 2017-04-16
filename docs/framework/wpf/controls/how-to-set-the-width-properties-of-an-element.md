---
title: "方法 : 要素の Width プロパティを設定する | Microsoft Docs"
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
  - "Panel コントロール, Width プロパティ (要素の)"
  - "幅のプロパティ"
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 要素の Width プロパティを設定する
## 使用例  
 この例では、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の幅に関連する 4 つのプロパティについて、レンダリング動作の違いを視覚的に示します。  
  
 <xref:System.Windows.FrameworkElement> クラスは、要素の幅の特性を記述する 4 つのプロパティを公開します。  これらの 4 つのプロパティは競合する可能性がありますが、その場合は、<xref:System.Windows.FrameworkElement.MinWidth%2A> 値、<xref:System.Windows.FrameworkElement.MaxWidth%2A> 値、<xref:System.Windows.FrameworkElement.Width%2A> 値の順序で優先して使用されます。  4 つ目のプロパティの <xref:System.Windows.FrameworkElement.ActualWidth%2A> は読み取り専用で、レイアウト プロセスとのやり取りによって決定される実際の幅を報告します。  
  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の例では、<xref:System.Windows.Shapes.Rectangle> 要素 \(`rect1`\) を <xref:System.Windows.Controls.Canvas> の子として描画します。  <xref:System.Windows.Shapes.Rectangle> の幅のプロパティは、<xref:System.Windows.FrameworkElement.MinWidth%2A>、<xref:System.Windows.FrameworkElement.MaxWidth%2A>、および <xref:System.Windows.FrameworkElement.Width%2A> の各プロパティ値を表す一連の <xref:System.Windows.Controls.ListBox> 要素を使用して変更できます。  この方法では、各プロパティの優先順位が表示されます。  
  
 [!code-xml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 次の分離コードの例では、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> イベントによって発生したイベントを処理します。  各カスタム メソッドは <xref:System.Windows.Controls.ListBox> から入力を受け取り、値を <xref:System.Double> として解析し、指定された幅に関連するプロパティに値を適用します。  幅の値は文字列にも変換され、各種の <xref:System.Windows.Controls.TextBlock> 要素に書き込まれます \(それらの要素の定義は、上の XAML の例には示されていません\)。  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 サンプル全体については、[Width のプロパティの比較のサンプル](http://go.microsoft.com/fwlink/?LinkID=160050)を参照してください。  
  
## 参照  
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>   
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>   
 <xref:System.Windows.FrameworkElement.MinWidth%2A>   
 <xref:System.Windows.FrameworkElement.Width%2A>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [要素の Height プロパティを設定する](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)   
 [Width のプロパティの比較のサンプル](http://go.microsoft.com/fwlink/?LinkID=160050)