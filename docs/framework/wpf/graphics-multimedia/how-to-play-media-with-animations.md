---
title: "方法 : アニメーションを使用してメディアを再生する | Microsoft Docs"
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
  - "アニメーションを含む、マルチ メディアの再生"
  - "メディア、アニメーションの再生"
  - "アニメーションとメディアの再生"
  - "メディア、アニメーションを再生"
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : アニメーションを使用してメディアを再生する
この例を使用して、同時にメディアおよびアニメーションを再生する方法を示しています、 <xref:System.Windows.Media.MediaTimeline>と<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 、同じクラス<xref:System.Windows.Media.Animation.Storyboard>します。  
  
## <a name="example"></a>例  
 1 つまたは複数を使用する<xref:System.Windows.Media.MediaTimeline>内のオブジェクト、<xref:System.Windows.Media.Animation.Storyboard>他の<xref:System.Windows.Media.Animation.Timeline>アニメーションなどのオブジェクト。  
  
 設定を次に例を<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Storyboard>の値に`Slip`アニメーションが、メディア (この例ではビデオ) が進行するまでに進まないを指定します。 読み込み時間の原因でメディアの再生が遅延される場合、この機能を必要があります。  
  
 [!code-xml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>   
 [操作方法に関するトピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [グラフィックスとマルチ メディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)