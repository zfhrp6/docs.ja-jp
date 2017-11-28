---
title: "方法 : キー フレームを使用して文字列をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8947669178de1252c10b6a8b2c01a6b55baa424
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>方法 : キー フレームを使用して文字列をアニメーション化する
この例があり、この例では、文字列をアニメーション化する方法を示しています、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティ、<xref:System.Windows.Controls.Button>キー フレームを使用して、コントロール。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>アニメーション化するクラス、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティ、<xref:System.Windows.Controls.Button>です。  
  
 この例ではすべてのキー フレームのインスタンスを使用して、<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>クラスため、キー フレームが作成される文字列のアニメーションは、個別のキー フレームにのみ使用できます。 などの個別のキー フレーム<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>されている値の間の突然のジャンプを作成する、アニメーションへの変更が迅速に行うし、微妙ではありません。  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
