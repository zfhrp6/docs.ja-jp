---
title: "方法 : 要素またはブラシの不透明度をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, Opacity プロパティ"
  - "不透明, アニメーション化"
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 要素またはブラシの不透明度をアニメーション化する
フレームワーク要素のフェード インおよびフェード アウトは、その要素の <xref:System.Windows.UIElement.Opacity%2A> プロパティをアニメーション化するか、その要素の描画に使用される <xref:System.Windows.Media.Brush> \(ブラシ\) の <xref:System.Windows.Media.Brush.Opacity%2A> プロパティをアニメーション化することで作成できます。  要素の不透明度をアニメーション化すると、その要素と子要素のフェード インおよびフェード アウトを作成できます。また、要素の描画に使用されるブラシをアニメーション化することで、要素のどの部分をフェード インまたはフェード アウトするかを選択することもできます。  たとえば、ボタンの背景を描画するブラシの不透明度をアニメーション化できます。  これにより、ボタンの背景だけをフェード インおよびフェード アウトさせ、テキストの部分はそのまま残すことができます。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Brush> の <xref:System.Windows.Media.Brush.Opacity%2A> をアニメーション化した方が、要素の <xref:System.Windows.UIElement.Opacity%2A> プロパティをアニメーション化するよりも、パフォーマンス上の利点があります。  
  
 次の例では、2 つのボタンをアニメーション化してフェード インおよびフェード アウトします。  最初の <xref:System.Windows.Controls.Button> の Opacity は、<xref:System.Windows.Media.Animation.Timeline.Duration%2A> で指定した 5 秒間をかけて `1.0` から `0.0` にアニメーション化されます。  2 番目のボタンもアニメーション化されますが、ボタン全体の不透明度ではなく、<xref:System.Windows.Controls.Control.Background%2A> の描画に使用される SolidColorBrush の Opacity がアニメーション化されます。  この例を実行すると、最初のボタンは全体がフェード インおよびフェード アウトするのに対し、2 番目のボタンは背景だけがフェード インおよびフェード アウトします。  テキストと境界線は、完全に不透明のまま残ります。  
  
## 使用例  
 [!code-xml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 この例では、コードは省略されています。  サンプル全体では、<xref:System.Windows.Media.LinearGradientBrush> の <xref:System.Windows.Media.Color> の透明度をアニメーション化する方法も示します。  サンプル全体については、[要素の不透明度のアニメーション化のサンプル](http://go.microsoft.com/fwlink/?LinkID=159968)を参照してください。