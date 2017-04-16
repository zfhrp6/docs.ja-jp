---
title: "方法 : VideoDrawing を使用してメディアを再生する | Microsoft Docs"
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
  - "クラス, MediaPlayer"
  - "クラス, VideoDrawing"
  - "MediaPlayer クラス"
  - "再生 (メディアの)"
  - "VideoDrawing クラス"
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : VideoDrawing を使用してメディアを再生する
オーディオ ファイルまたはビデオ ファイルを再生するには、<xref:System.Windows.Media.VideoDrawing> と <xref:System.Windows.Media.MediaPlayer> を使用します。  メディアを読み込んで再生するには、2 つの方法があります。  1 つ目の方法は、<xref:System.Windows.Media.MediaPlayer> および <xref:System.Windows.Media.VideoDrawing> を単独で使用するもので、2 つ目の方法は、独自の <xref:System.Windows.Media.MediaTimeline> を作成して <xref:System.Windows.Media.MediaPlayer> および <xref:System.Windows.Media.VideoDrawing> と共に使用するものです。  
  
> [!NOTE]
>  アプリケーションでメディアを配布する場合は、メディア ファイルをイメージと同じようにプロジェクト リソースとして使用することはできません。  代わりにプロジェクト ファイルでメディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
## 使用例  
 <xref:System.Windows.Media.VideoDrawing> および <xref:System.Windows.Media.MediaPlayer> を使用してビデオ ファイルを 1 回再生する例を次に示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 メディアのタイミングをさらに細かく制御するには、<xref:System.Windows.Media.MediaPlayer> オブジェクトおよび <xref:System.Windows.Media.VideoDrawing> オブジェクトと共に <xref:System.Windows.Media.MediaTimeline> を使用します。  <xref:System.Windows.Media.MediaTimeline> を使用すると、ビデオを繰り返すかどうかを指定できます。  
  
## 使用例  
 <xref:System.Windows.Media.MediaTimeline> を <xref:System.Windows.Media.MediaPlayer> および <xref:System.Windows.Media.VideoDrawing> オブジェクトと共に使用してビデオを繰り返し再生する例を次に示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <xref:System.Windows.Media.MediaTimeline> を使用するときは、<xref:System.Windows.Media.MediaPlayer> の対話型メソッドを使用するのではなく、<xref:System.Windows.Media.MediaClock> の <xref:System.Windows.Media.Animation.Clock.Controller%2A> プロパティから返される対話型の <xref:System.Windows.Media.Animation.ClockController> を使用してメディアの再生を制御することに注意してください。  
  
## 参照  
 <xref:System.Windows.Media.VideoDrawing>   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)