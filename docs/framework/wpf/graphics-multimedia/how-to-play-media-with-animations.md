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
ms.openlocfilehash: fb5fd3575a0caa692e4a4013452e3069210c9a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="1860a-102">方法 : アニメーションを使用してメディアを再生する</span><span class="sxs-lookup"><span data-stu-id="1860a-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="1860a-103">この例を使用して、同時にメディアおよびアニメーションを再生する方法を示しています、<xref:System.Windows.Media.MediaTimeline>と<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>、同じクラス<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="1860a-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1860a-104">例</span><span class="sxs-lookup"><span data-stu-id="1860a-104">Example</span></span>  
 <span data-ttu-id="1860a-105">1 つまたは複数を使用することができます<xref:System.Windows.Media.MediaTimeline>内のオブジェクト、<xref:System.Windows.Media.Animation.Storyboard>と共に他の<xref:System.Windows.Media.Animation.Timeline>アニメーションなどのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1860a-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="1860a-106">次の例のセット、<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Storyboard>の値に`Slip`アニメーションが、メディア (この例ではビデオ) が進行するまでに進まないを指定します。</span><span class="sxs-lookup"><span data-stu-id="1860a-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="1860a-107">この機能は、読み込み時間のためにメディアの再生が遅れる場合などに必要です。</span><span class="sxs-lookup"><span data-stu-id="1860a-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1860a-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="1860a-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="1860a-109">方法トピック</span><span class="sxs-lookup"><span data-stu-id="1860a-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="1860a-110">ストーリーボードの概要</span><span class="sxs-lookup"><span data-stu-id="1860a-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="1860a-111">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="1860a-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="1860a-112">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="1860a-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="1860a-113">グラフィックスとマルチメディア</span><span class="sxs-lookup"><span data-stu-id="1860a-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
