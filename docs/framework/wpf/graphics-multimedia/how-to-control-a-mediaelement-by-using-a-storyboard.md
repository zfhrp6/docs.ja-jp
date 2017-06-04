---
title: "方法 : ストーリーボードを使用して MediaElement を制御する | Microsoft Docs"
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
  - "制御 (メディアの再生を), ストーリーボードで"
  - "メディア, 制御 (ストーリーボードで再生を)"
  - "マルチメディア, 制御 (ストーリーボードでメディアの再生を)"
  - "再生 (メディアの), 制御 (ストーリーボードで)"
  - "ストーリーボード, 制御 (メディアの再生を)"
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : ストーリーボードを使用して MediaElement を制御する
この例では、<xref:System.Windows.Media.Animation.Storyboard> 内の <xref:System.Windows.Media.MediaTimeline> を使用して、<xref:System.Windows.Controls.MediaElement> を制御する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.Animation.Storyboard> 内の <xref:System.Windows.Media.MediaTimeline> を使用して <xref:System.Windows.Controls.MediaElement> のタイミングを制御する場合、その機能は、アニメーションなど他の <xref:System.Windows.Media.Animation.Timeline> オブジェクトの機能と同じです。  たとえば、<xref:System.Windows.Media.MediaTimeline> は、<xref:System.Windows.Media.Animation.Timeline> プロパティを <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> プロパティのように使用して、<xref:System.Windows.Controls.MediaElement> を開始する \(メディアの再生を開始する\) 時刻を指定します。  また、<xref:System.Windows.Media.Animation.Timeline.Duration%2A> プロパティを使用して、<xref:System.Windows.Controls.MediaElement> をアクティブにする時間 \(メディアの再生時間\) を指定します。  <xref:System.Windows.Media.Animation.Storyboard> で <xref:System.Windows.Media.Animation.Timeline> オブジェクトを使用する方法の詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 この例では、<xref:System.Windows.Media.MediaTimeline> を使用して再生を制御する単純なメディア プレーヤーを作成する方法を示します。  このメディア プレーヤーには、再生、一時停止、再開、停止ボタンがあります。  また、進行状況バーとして機能する <xref:System.Windows.Controls.Slider> コントロールもあります。  
  
 メディア プレーヤーの[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を作成する例を次に示します。  
  
 [!code-xml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 進行状況バーの機能を作成する例を次に示します。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## 参照  
 <xref:System.Windows.Controls.MediaElement>   
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [MediaElement \(再生、一時停止、停止、ボリューム、および速度\) を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)