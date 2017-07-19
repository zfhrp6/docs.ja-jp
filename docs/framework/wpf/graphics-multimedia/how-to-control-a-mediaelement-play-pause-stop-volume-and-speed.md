---
title: "方法 : MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する | Microsoft Docs"
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
  - "制御 (メディアの再生を)"
  - "メディア, 制御 (再生を)"
  - "マルチメディア, 制御 (メディアの再生を)"
  - "再生 (メディアの), 制御"
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する
<xref:System.Windows.Controls.MediaElement> を使用して、メディアの再生を制御する方法を次の例に示します。  ここでは、再生、一時停止、停止、メディア内での前後へのスキップ、ボリューム調整、速度比率調整が可能な単純なメディア プレーヤーを作成します。  
  
## 使用例  
 次のコードでは、UI を作成します。  
  
> [!NOTE]
>  メディアを対話的に停止、一時停止、および再生できるようにするには、<xref:System.Windows.Controls.MediaElement> の <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> プロパティを `Manual` に設定する必要があります。  
  
 [!code-xml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## 使用例  
 次のコードでは、サンプル UI コントロールの機能を実装します。  <xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A>、および <xref:System.Windows.Controls.MediaElement.Stop%2A> メソッドは、それぞれメディアの再生、一時停止、停止に使用します。  <xref:System.Windows.Controls.MediaElement> の <xref:System.Windows.Controls.MediaElement.Position%2A> プロパティを変更すると、メディア内で前後にスキップできます。  最後に、<xref:System.Windows.Controls.MediaElement.Volume%2A> プロパティと <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> プロパティを使用して、ボリュームとメディアの再生速度を調整します。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## 参照  
 [ストーリーボードを使用して MediaElement を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)