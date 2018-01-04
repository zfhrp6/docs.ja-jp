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
ms.workload: dotnet
ms.openlocfilehash: 773a0a1e2252b3f7154ef218f887be6f56e9995f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="1d8a5-102">方法 : VideoDrawing を使用してメディアを再生する</span><span class="sxs-lookup"><span data-stu-id="1d8a5-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="1d8a5-103">使用するオーディオまたはビデオ ファイルを再生するには<xref:System.Windows.Media.VideoDrawing>と<xref:System.Windows.Media.MediaPlayer>です。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="1d8a5-104">メディアを読み込んで再生するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-104">There are two ways to load and play media.</span></span> <span data-ttu-id="1d8a5-105">最初を使用して、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>自体、および 2 番目で方法は、独自に作成する<xref:System.Windows.Media.MediaTimeline>で使用する、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>です。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d8a5-106">アプリケーションでメディアを配布するときは、イメージのようにプロジェクト リソースとしてメディア ファイルを使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="1d8a5-107">プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d8a5-108">例</span><span class="sxs-lookup"><span data-stu-id="1d8a5-108">Example</span></span>  
 <span data-ttu-id="1d8a5-109">次の例では、<xref:System.Windows.Media.VideoDrawing>と<xref:System.Windows.Media.MediaPlayer>を 1 回、ビデオ ファイルを再生します。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="1d8a5-110">使用して、メディア上で別のタイミングを制御する、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="1d8a5-111"><xref:System.Windows.Media.MediaTimeline>ビデオを繰り返す必要があるかどうかを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d8a5-112">例</span><span class="sxs-lookup"><span data-stu-id="1d8a5-112">Example</span></span>  
 <span data-ttu-id="1d8a5-113">次の例では、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>ビデオを繰り返し再生するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="1d8a5-114">なお、使用すると、 <xref:System.Windows.Media.MediaTimeline>、対話型を使用する<xref:System.Windows.Media.Animation.ClockController>から返される、<xref:System.Windows.Media.Animation.Clock.Controller%2A>のプロパティ、<xref:System.Windows.Media.MediaClock>の対話的な方法ではなくメディア再生を制御する<xref:System.Windows.Media.MediaPlayer>です。</span><span class="sxs-lookup"><span data-stu-id="1d8a5-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d8a5-115">参照</span><span class="sxs-lookup"><span data-stu-id="1d8a5-115">See Also</span></span>  
 <xref:System.Windows.Media.VideoDrawing>  
 [<span data-ttu-id="1d8a5-116">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="1d8a5-116">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
