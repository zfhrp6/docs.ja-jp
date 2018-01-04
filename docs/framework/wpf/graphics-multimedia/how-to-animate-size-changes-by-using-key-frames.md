---
title: "方法 : キー フレームを使用してサイズの変更をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30ee897efd01712bf4313da87e1050c5a16e4523
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>方法 : キー フレームを使用してサイズの変更をアニメーション化する
この例では、キー フレームを使用してサイズの変更をアニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Media.ArcSegment.Size%2A>のプロパティ、<xref:System.Windows.Media.ArcSegment>です。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初、0.5 秒、アニメーションの中のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>円弧のサイズが徐々 に増加するクラス。などの線形のキー フレーム<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>値の間のスムーズな線形遷移を作成します。  
  
2.  インスタンスを使用している 0.5 秒は、次の最後に、<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>円弧のサイズが突然増加するクラス。などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>されている値の間の突然のジャンプを作成、サイズの変更が突然発生して、微妙ではありません。  
  
3.  インスタンスが使用する最後の 2 秒、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>円弧のサイズを大きくクラス。スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>変数の値に基づいて値の間で遷移を作成する、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>プロパティです。 この例では、円弧のサイズは最初はゆっくり大きくなりますが、時間セグメントの終点に向かって急激に大きくなります。  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
