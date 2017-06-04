---
title: "方法 : アニメーションをテキストに適用する | Microsoft Docs"
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
  - "アニメーション, テキスト"
  - "タイポグラフィ, アニメーション"
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : アニメーションをテキストに適用する
アニメーションを使用すると、アプリケーション内のテキストの表示と外観を変えることができます。  次の例では、 <xref:System.Windows.Controls.TextBlock> コントロール内のテキストの表示に影響を及ぼす、異なる種類のアニメーションを使用しています。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> を使用してテキスト ブロックの幅をアニメーション化しています。  10 秒間で幅の値がテキスト ブロックの幅から 0 まで変化してから、幅の値が逆に戻る変化が繰り返されます。  この種類のアニメーションにより、ワイプ効果がもたらされます。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> を使用してテキスト ブロックの不透明度をアニメーション化しています。  5 秒間で不透明度の値が 1.0 から 0 まで変化してから、その不透明度の値が逆行する変化が繰り返されます。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> で定義されている 5 秒間に不透明度が `1.00` から `0.00` まで変化する <xref:System.Windows.Controls.TextBlock> コントロールの効果を次の図に示します。  
  
 ![不透明度を 1.00 から 0.00 に変更するテキスト](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
1.00 から 0.00 まで変更するテキストの不透明度  
  
 次の例では、<xref:System.Windows.Media.Animation.ColorAnimation> を使用してテキスト ブロックの前景色をアニメーション化しています。  5 秒間で前景色の値がある色から別の色に変化してから、その色の値が逆行する変化が繰り返されます。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation> を使用してテキスト ブロックを回転させています。  20 秒間でテキスト ブロックが完全に回転してから、回転が繰り返されます。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)