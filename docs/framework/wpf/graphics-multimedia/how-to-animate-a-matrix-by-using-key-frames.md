---
title: "方法 : キー フレームを使用して行列をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 行列プロパティをキー フレームで"
  - "キー フレーム, アニメーション化 (行列プロパティを)"
  - "行列プロパティ, アニメーション化 (キー フレームを使用して)"
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : キー フレームを使用して行列をアニメーション化する
次の例は、キー フレームを使用して <xref:System.Windows.Media.MatrixTransform> の <xref:System.Windows.Media.MatrixTransform.Matrix%2A> プロパティにアニメーションを適用する方法を示しています。  
  
## 使用例  
 次のコード例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Media.MatrixTransform> の <xref:System.Windows.Media.MatrixTransform.Matrix%2A> プロパティにアニメーションを適用しています。  この例では、<xref:System.Windows.Media.MatrixTransform> オブジェクトを使用して <xref:System.Windows.Controls.Button> の外観と位置を変換します。  
  
 このアニメーションでは、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> クラスを使用して 2 つのキー フレームを作成し、そのキー フレームで次の処理を行います。  
  
1.  最初の 0.2 秒の間に、1 番目の <xref:System.Windows.Media.Matrix> をアニメーション化します。  この例では、<xref:System.Windows.Media.Matrix> の <xref:System.Windows.Media.Matrix.M11%2A> プロパティおよび <xref:System.Windows.Media.Matrix.M12%2A> プロパティを変更します。  この変更によって、ボタンは引き伸ばされ、傾斜します。  また、ここでは、<xref:System.Windows.Media.Matrix.OffsetX%2A> プロパティと <xref:System.Windows.Media.Matrix.OffsetY%2A> プロパティを変更することによって、ボタンの位置を変えます。  
  
2.  1.0 秒の時点で、2 番目の <xref:System.Windows.Media.Matrix> をアニメーション化します。  ボタンは、傾斜と引き伸ばしがなくなると同時に、別の位置に移動します。  
  
3.  このアニメーションを無制限に繰り返します。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> オブジェクトから派生するキー フレームは、値間で突然のジャンプを作成します。つまり、アニメーションの動きはぎくしゃくしています。  
  
 [!code-xml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>   
 <xref:System.Windows.Media.MatrixTransform>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)