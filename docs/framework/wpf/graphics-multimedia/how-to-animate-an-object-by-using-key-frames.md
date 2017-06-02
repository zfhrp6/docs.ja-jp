---
title: "方法 : キー フレームを使用してオブジェクトをアニメーション化する | Microsoft Docs"
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
  - "アニメーション, オブジェクトをキー フレームで"
  - "キー フレーム, アニメーション化 (オブジェクトを)"
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : キー フレームを使用してオブジェクトをアニメーション化する
この例では、<xref:System.Windows.Controls.Page> コントロールの <xref:System.Windows.Controls.Page.Background%2A> プロパティであるオブジェクトを、キー フレームを使用してアニメーション化する方法について説明します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> クラスを使用して、<xref:System.Windows.Controls.Page> コントロールの <xref:System.Windows.Controls.Page.Background%2A> プロパティの色の変更をアニメーション化します。  この例のアニメーションは、別の背景ブラシに定期的に変化します。  このアニメーションは、<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> クラスを使用して 3 つの異なるキー フレームを作成します。  次の方法でキー フレームを使用します。  
  
1.  最初の 1 秒間の終わりに、<xref:System.Windows.Media.LinearGradientBrush> クラスのインスタンスをアニメーション化します。  このセクションでは、線形グラデーションを背景色に適用して、その色を黄色からオレンジ、赤へと変化させます。  
  
2.  2 秒目の終わりに、<xref:System.Windows.Media.RadialGradientBrush> クラスのインスタンスをアニメーション化します。  このセクションでは、放射状グラデーションを背景色に適用して、その色を白から青、黒へと変化させます。  
  
3.  3 秒目の終わりに、<xref:System.Windows.Media.DrawingBrush> クラスのインスタンスをアニメーション化します。  このセクションでは、背景に市松模様を適用します。  
  
4.  アニメーションが再度始まり、無制限に繰り返します。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> は、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> クラスで使用できるキー フレームの唯一の型です。  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> のようなキー フレームは、値の突然の変化を作成するので、この例での色の変化は突然起こります。  
  
 [!code-xml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>   
 <xref:System.Windows.Controls.Page.Background%2A>   
 <xref:System.Windows.Controls.Page>   
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>   
 <xref:System.Windows.Media.LinearGradientBrush>   
 <xref:System.Windows.Media.RadialGradientBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)