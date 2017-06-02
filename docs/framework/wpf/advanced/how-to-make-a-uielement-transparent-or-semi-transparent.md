---
title: "方法 : UIElement を透明または半透明にする | Microsoft Docs"
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
  - "不透明, UIElement"
  - "透過性 (UIElement の)"
  - "UIElements, 不透明"
  - "UIElements, 透過性"
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : UIElement を透明または半透明にする
<xref:System.Windows.UIElement> を透明または半透明にする方法を次の例に示します。  要素を透明または半透明にするには、その <xref:System.Windows.UIElement.Opacity%2A> プロパティを設定します。  値 `0.0` は、要素が完全に透明であることを示し、値 `1.0` は、要素が完全に不透明であることを示します。  値 `0.5` は、この要素の不透明度が 50% であることを示します。他も同様です。  既定では、要素の <xref:System.Windows.UIElement.Opacity%2A> は `1.0` に設定されます。  
  
## 使用例  
 次の例では、ボタンの <xref:System.Windows.UIElement.Opacity%2A> を `0.25` に設定することにより、ボタンとそのコンテンツ \(この例ではボタンのテキスト\) の不透明度を 25% にしています。  
  
 [!code-xml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 要素のコンテンツに独自の <xref:System.Windows.UIElement.Opacity%2A> が設定されている場合は、それらの値と、含まれている要素の <xref:System.Windows.UIElement.Opacity%2A> が乗算されます。  
  
 ボタンの <xref:System.Windows.UIElement.Opacity%2A> を `0.25` に設定し、そのボタンに含まれている <xref:System.Windows.Controls.Image> コントロールの <xref:System.Windows.UIElement.Opacity%2A> を `0.5` に設定する例を次に示します。  結果として、イメージは 12.5% \(0.25 × 0.5 \= 0.125\) の不透明度で表示されます。  
  
 [!code-xml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 要素の不透明度は、要素を描画する <xref:System.Windows.Media.Brush> の不透明度を設定することによって制御することもできます。  この方法を使用すると、1 つの要素の各部分の不透明度を選択して変更でき、要素の <xref:System.Windows.UIElement.Opacity%2A> プロパティを使用するよりもパフォーマンスが向上します。  ボタンの <xref:System.Windows.Controls.Control.Background%2A> を描画するために使用される <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.Brush.Opacity%2A> を `0.25` に設定する例を次に示します。  結果として、ブラシの背景の不透明度は 25% になりますが、そのコンテンツ \(ボタンのテキスト\) の不透明度は 100% のままです。  
  
 [!code-xml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 また、ブラシ内の個々の色の不透明度を制御することもできます。  色とブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  要素の不透明度をアニメーション化する方法の例については、「[要素またはブラシの不透明度をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)」を参照してください。