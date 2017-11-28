---
title: "方法 : VideoDrawing を使用してメディアを再生する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2753db8e06c8c1b50c6e5cee17330d421e88511f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-using-a-videodrawing"></a>方法 : VideoDrawing を使用してメディアを再生する
使用するオーディオまたはビデオ ファイルを再生するには<xref:System.Windows.Media.VideoDrawing>と<xref:System.Windows.Media.MediaPlayer>です。 メディアを読み込んで再生するには、2 つの方法があります。 最初を使用して、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>自体、および 2 番目で方法は、独自に作成する<xref:System.Windows.Media.MediaTimeline>で使用する、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>です。  
  
> [!NOTE]
>  アプリケーションでメディアを配布するときは、イメージのようにプロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.VideoDrawing>と<xref:System.Windows.Media.MediaPlayer>を 1 回、ビデオ ファイルを再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 使用して、メディア上で別のタイミングを制御する、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>オブジェクト。 <xref:System.Windows.Media.MediaTimeline>ビデオを繰り返す必要があるかどうかを指定することができます。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>ビデオを繰り返し再生するオブジェクト。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 なお、使用すると、 <xref:System.Windows.Media.MediaTimeline>、対話型を使用する<xref:System.Windows.Media.Animation.ClockController>から返される、<xref:System.Windows.Media.Animation.Clock.Controller%2A>のプロパティ、<xref:System.Windows.Media.MediaClock>の対話的な方法ではなくメディア再生を制御する<xref:System.Windows.Media.MediaPlayer>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.VideoDrawing>  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
