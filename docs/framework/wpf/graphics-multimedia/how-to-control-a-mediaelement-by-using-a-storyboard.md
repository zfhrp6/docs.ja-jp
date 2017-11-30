---
title: "方法 : ストーリーボードを使用して MediaElement を制御する"
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
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2341d2814e5bd42c652865c76d115defcc5b15b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="f9db7-102">方法 : ストーリーボードを使用して MediaElement を制御する</span><span class="sxs-lookup"><span data-stu-id="f9db7-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="f9db7-103">この例では、制御、<xref:System.Windows.Controls.MediaElement>を使用して、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="f9db7-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9db7-104">例</span><span class="sxs-lookup"><span data-stu-id="f9db7-104">Example</span></span>  
 <span data-ttu-id="f9db7-105">使用すると、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.Animation.Storyboard>のタイミングを制御する、 <xref:System.Windows.Controls.MediaElement>、機能は、他の機能と同じ<xref:System.Windows.Media.Animation.Timeline>アニメーションなどのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f9db7-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="f9db7-106">たとえば、<xref:System.Windows.Media.MediaTimeline>使用<xref:System.Windows.Media.Animation.Timeline>などのプロパティ、<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>を開始するタイミングを指定するプロパティ、 <xref:System.Windows.Controls.MediaElement> (メディアの再生を開始)。</span><span class="sxs-lookup"><span data-stu-id="f9db7-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="f9db7-107">使用して、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティを指定する時間、<xref:System.Windows.Controls.MediaElement>がアクティブ (メディアの再生の期間)。</span><span class="sxs-lookup"><span data-stu-id="f9db7-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="f9db7-108">使用しての詳細については<xref:System.Windows.Media.Animation.Timeline>オブジェクトと、<xref:System.Windows.Media.Animation.Storyboard>を参照してください[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9db7-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="f9db7-109">この例を使用する単純なメディア プレーヤーを作成する方法を示しています、<xref:System.Windows.Media.MediaTimeline>再生を制御します。</span><span class="sxs-lookup"><span data-stu-id="f9db7-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="f9db7-110">メディア プレーヤーには、再生、一時停止、再開、およびボタンを停止します。</span><span class="sxs-lookup"><span data-stu-id="f9db7-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="f9db7-111">また、<xref:System.Windows.Controls.Slider>進行状況バーとして機能するコントロール。</span><span class="sxs-lookup"><span data-stu-id="f9db7-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="f9db7-112">次の例を作成、 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] media player のです。</span><span class="sxs-lookup"><span data-stu-id="f9db7-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="f9db7-113">次の例では、進行状況バーの機能を作成します。</span><span class="sxs-lookup"><span data-stu-id="f9db7-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f9db7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9db7-114">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="f9db7-115">MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する</span><span class="sxs-lookup"><span data-stu-id="f9db7-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [<span data-ttu-id="f9db7-116">ストーリーボードの概要</span><span class="sxs-lookup"><span data-stu-id="f9db7-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="f9db7-117">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="f9db7-117">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="f9db7-118">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="f9db7-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="f9db7-119">方法トピック</span><span class="sxs-lookup"><span data-stu-id="f9db7-119">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="f9db7-120">グラフィックスとマルチメディア</span><span class="sxs-lookup"><span data-stu-id="f9db7-120">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
