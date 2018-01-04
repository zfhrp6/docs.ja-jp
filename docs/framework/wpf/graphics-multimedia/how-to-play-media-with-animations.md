---
title: "方法 : アニメーションを使用してメディアを再生する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44ebb89c25fc37292f82533c929aae44854db5c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-media-with-animations"></a>方法 : アニメーションを使用してメディアを再生する
この例を使用して、同時にメディアおよびアニメーションを再生する方法を示しています、<xref:System.Windows.Media.MediaTimeline>と<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>、同じクラス<xref:System.Windows.Media.Animation.Storyboard>です。  
  
## <a name="example"></a>例  
 1 つまたは複数を使用することができます<xref:System.Windows.Media.MediaTimeline>内のオブジェクト、<xref:System.Windows.Media.Animation.Storyboard>と共に他の<xref:System.Windows.Media.Animation.Timeline>アニメーションなどのオブジェクト。  
  
 次の例のセット、<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Storyboard>の値に`Slip`アニメーションが、メディア (この例ではビデオ) が進行するまでに進まないを指定します。 この機能は、読み込み時間のためにメディアの再生が遅れる場合などに必要です。  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)
