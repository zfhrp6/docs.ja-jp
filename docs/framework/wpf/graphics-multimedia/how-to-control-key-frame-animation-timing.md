---
title: "方法 : キー フレーム アニメーションのタイミングを制御する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc3566cf25282749a09c5f2372cd1c81e3ce881
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-key-frame-animation-timing"></a>方法 : キー フレーム アニメーションのタイミングを制御する
この例では、キー フレーム アニメーション内のキー フレームのタイミングを制御する方法を示します。 キー フレーム アニメーションにあるその他のアニメーションと同様に、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティです。 アニメーションの duration を指定するだけでなくその期間のどの部分がそのキー フレームのそれぞれに割り当てられているを指定する必要があります。 指定した時間を割り当てる、<xref:System.Windows.Media.Animation.KeyTime>の各キー フレーム アニメーションにします。  
  
 <xref:System.Windows.Media.Animation.KeyTime>の (は指定しませんキー フレームの再生時間の長さ) のキー フレームの終了時に、各キー フレームを指定します。 指定することができます、<xref:System.Windows.Media.Animation.KeyTime>として、<xref:System.TimeSpan>値、パーセンテージ、または、<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>または<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊な値です。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>を四角形を画面にアニメーション化します。 キー フレームのキー時刻が設定されて<xref:System.TimeSpan>値。  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 次の図の各キー フレームの値に達したときにします。  
  
 ![キーの値が 3、4、および 10 秒の位置に到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 次の例では、パーセンテージの値でキー フレームのキー時刻を設定する点を除いて同じですが、あるアニメーションを示します。  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 次の図の各キー フレームの値に達したときにします。  
  
 ![キーの値が 3、4、および 10 秒の位置に到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 次の例では<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>キー時刻値。  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 次の図の各キー フレームの値に達したときにします。  
  
 ![キーの値に達した 3.3、6.6、および 9.9 秒](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 最後の例を使用して<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>キー時刻値。  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 次の図の各キー フレームの値に達したときにします。  
  
 ![キーの値が 0、5、および 10 秒の位置に到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 わかりやすくするため、コードでは、この例を使用してローカル、アニメーションのないストーリー ボードを 1 つのプロパティを 1 つのアニメーションが適用されているが、ストーリー ボードを代わりに使用する例を変更する可能性があります。 コード内のストーリー ボードを宣言する方法を示す例は、次を参照してください。[ストーリー ボードを使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)です。  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。 キー フレーム アニメーションの詳細については、次を参照してください。、[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
