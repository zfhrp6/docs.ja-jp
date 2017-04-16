---
title: "方法 : ストーリーボードを使用してアニメーション化した後にプロパティを設定する | Microsoft Docs"
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
  - "アニメーション, 変更 (後でプロパティ値を)"
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : ストーリーボードを使用してアニメーション化した後にプロパティを設定する
状況によっては、プロパティをアニメーション化した後に、そのプロパティの値を変更できないように見えることがあります。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard> を使用して <xref:System.Windows.Media.SolidColorBrush> の色をアニメーション化します。  ボタンがクリックされると、ストーリーボードがトリガーされます。  <xref:System.Windows.Media.Animation.Timeline.Completed> イベントを処理することで、<xref:System.Windows.Media.Animation.ColorAnimation> が完了したときにプログラムが通知を受け取るようにします。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## 使用例  
 <xref:System.Windows.Media.Animation.ColorAnimation> が完了したら、ブラシの色を青に変更します。  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 前のコードは、何も実行しないように見えます。ブラシは黄色のまま、つまりブラシをアニメーション化した <xref:System.Windows.Media.Animation.ColorAnimation> によって設定された値のままになっています。  実際には、基になるプロパティ値 \(基本値\) は青に変更されています。  しかし、実効値、つまり現在の値が黄色のままであるのは、<xref:System.Windows.Media.Animation.ColorAnimation> が基本値をオーバーライドしたままであるからです。  基本値を再び実効値にするには、アニメーションによるプロパティへの影響を停止する必要があります。  ストーリーボード アニメーションでこのようにするには、次の 3 つの方法があります。  
  
-   アニメーションの <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティを <xref:System.Windows.Media.Animation.FillBehavior> に設定する。  
  
-   ストーリーボード全体を削除する。  
  
-   個々のプロパティからアニメーションを削除する。  
  
## アニメーションの FillBehavior プロパティを Stop に設定する  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> を <xref:System.Windows.Media.Animation.FillBehavior> に設定することで、アニメーションがアクティブ期間の終わりに到達したらターゲット プロパティに影響を与えなくなるように指定します。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## ストーリーボード全体を削除する  
 <xref:System.Windows.Media.Animation.RemoveStoryboard> トリガーまたは <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=fullName> メソッドを使用することで、ストーリーボード アニメーションによるターゲット プロパティへの影響を停止します。  この方法と、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティを設定する方法の違いは、ストーリーボードはいつでも削除できるのに対し、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティの効果が現れるのはアニメーションがアクティブ期間の終わりに到達したときのみという点です。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## 個々のプロパティからアニメーションを削除する  
 アニメーションによるプロパティへの影響を停止するには、アニメーション化するオブジェクトの <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> メソッドを使用するという方法もあります。  アニメーション化するプロパティを最初のパラメーターとして指定し、`null` を 2 番目のパラメーターとして指定します。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 この方法は、ストーリーボード以外の手法によるアニメーションにも利用できます。  
  
## 参照  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>   
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Media.Animation.RemoveStoryboard>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)