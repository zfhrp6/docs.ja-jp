---
title: "方法 : メディアの再生を反復する | Microsoft Docs"
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
  - "メディアを繰り返し再生"
  - "繰り返し (メディアの再生を)"
  - "マルチ メディア、メディアの再生を繰り返す"
  - "繰り返しのメディアの再生"
ms.assetid: 02ab486d-c6b6-4918-9edd-45a12aca4683
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : メディアの再生を反復する
この例では、どのメディアの再生に無期限には、無限ループで再生するように、メディアを設定することです。  
  
## <a name="example"></a>例  
 次の例では使用<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.Animation.Storyboard>無限ループにメディア クリップを再生します。  
  
 [!code-xml[MediaGallery_snippet#SoundRepeatExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundRepeatExample.xaml#soundrepeatexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.MediaElement>   
 <xref:System.Windows.Media.MediaTimeline>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [操作方法に関するトピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)   
 [グラフィックスとマルチ メディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)