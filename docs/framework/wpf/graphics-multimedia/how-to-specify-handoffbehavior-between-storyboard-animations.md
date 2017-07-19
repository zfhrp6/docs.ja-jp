---
title: "方法 : ストーリーボード アニメーション間で HandoffBehavior を指定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アニメーション, ハンドオフ動作"
  - "ストーリーボード, アニメーション間のハンドオフ動作"
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : ストーリーボード アニメーション間で HandoffBehavior を指定する
この例では、ストーリーボード アニメーション間のハンドオフ動作を指定する方法を示します。  <xref:System.Windows.Media.Animation.BeginStoryboard> の <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> プロパティは、新しいアニメーションが、プロパティに既に適用されている既存のアニメーションと対話する方法を指定します。  
  
## 使用例  
 次の例では、2 つのボタンを作成します。これらのボタンは、マウス カーソルが上に移動すると大きくなり、カーソルが離れると小さくなります。  マウス カーソルをボタンの上に移動した直後にカーソルを離すと、最初のアニメーションが完了する前に 2 番目のアニメーションが適用されます。  2 つのアニメーションがこのようにオーバーラップする状況では、<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> の値が <xref:System.Windows.Media.Animation.HandoffBehavior> と <xref:System.Windows.Media.Animation.HandoffBehavior> である場合の違いが明確にわかります。  値が <xref:System.Windows.Media.Animation.HandoffBehavior> の場合は、オーバーラップするアニメーションが合成され、アニメーション間の移行がスムーズになります。一方、値が <xref:System.Windows.Media.Animation.HandoffBehavior> の場合は、オーバーラップされる古いアニメーションが新しいアニメーションに直ちに置換されます。  
  
 [!code-xml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## 参照  
 <xref:System.Windows.Media.Animation.BeginStoryboard>   
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)