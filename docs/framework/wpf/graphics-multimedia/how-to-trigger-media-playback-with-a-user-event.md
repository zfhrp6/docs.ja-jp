---
title: "方法 : ユーザー イベントによってメディアの再生をトリガーする | Microsoft Docs"
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
  - "同期 (イベントとメディアの再生を)"
  - "イベントと同期するメディアの再生"
  - "イベントと再生を同期するメディア"
  - "イベントによってマルチ メディア、同期中のメディアの再生"
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : ユーザー イベントによってメディアの再生をトリガーする
この例では、イベントとメディアの再生を同期する方法を示します。  
  
## <a name="example"></a>例  
 次の例で、 <xref:System.Windows.Controls.MediaElement>コントロールと<xref:System.Windows.Media.MediaTimeline> 、ユーザーがクリックしたときに発生するサウンドを再生するクラス、<xref:System.Windows.Controls.Button>します。  
  
 [!code-xml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.MediaElement>   
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.EventTrigger.RoutedEvent%2A>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [操作方法に関するトピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [グラフィックスとマルチ メディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)