---
title: "方法 : MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する"
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
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57b140391526c5b2a0e73a8bab2355ae445b395b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a><span data-ttu-id="365a2-102">方法 : MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する</span><span class="sxs-lookup"><span data-stu-id="365a2-102">How to: Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>
<span data-ttu-id="365a2-103">次の例を使用してメディアの再生を制御する方法を示しています、<xref:System.Windows.Controls.MediaElement>です。</span><span class="sxs-lookup"><span data-stu-id="365a2-103">The following example shows how to control playback of media using a <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="365a2-104">この例を使用すると、再生、一時停止、停止、メディアで前後にスキップし、ボリュームと速度比を調整する簡単なメディア プレーヤーを作成します。</span><span class="sxs-lookup"><span data-stu-id="365a2-104">The example creates a simple media player that allows you to play, pause, stop, and skip back and forth in the media as well as adjust the volume and speed ratio.</span></span>  
  
## <a name="example"></a><span data-ttu-id="365a2-105">例</span><span class="sxs-lookup"><span data-stu-id="365a2-105">Example</span></span>  
 <span data-ttu-id="365a2-106">次のコードでは、UI を作成します。</span><span class="sxs-lookup"><span data-stu-id="365a2-106">The code below creates the UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="365a2-107"><xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>プロパティ<xref:System.Windows.Controls.MediaElement>に設定する必要があります`Manual`できるように対話的を停止、一時停止、およびメディアを再生します。</span><span class="sxs-lookup"><span data-stu-id="365a2-107">The <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> property of <xref:System.Windows.Controls.MediaElement> must be set to `Manual` in order to be able to interactively stop, pause, and play the media.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="365a2-108">例</span><span class="sxs-lookup"><span data-stu-id="365a2-108">Example</span></span>  
 <span data-ttu-id="365a2-109">次のコードでは、サンプルの UI コントロールの機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="365a2-109">The code below implements the functionality of the sample UI controls.</span></span> <span data-ttu-id="365a2-110"><xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、および<xref:System.Windows.Controls.MediaElement.Stop%2A>メソッドを使用して、それぞれの再生、一時停止およびメディアを停止します。</span><span class="sxs-lookup"><span data-stu-id="365a2-110">The <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, and <xref:System.Windows.Controls.MediaElement.Stop%2A> methods are used to respectively play, pause and stop the media.</span></span> <span data-ttu-id="365a2-111">変更、<xref:System.Windows.Controls.MediaElement.Position%2A>のプロパティ、<xref:System.Windows.Controls.MediaElement>のメディア スキップすることができます。</span><span class="sxs-lookup"><span data-stu-id="365a2-111">Changing the <xref:System.Windows.Controls.MediaElement.Position%2A> property of the <xref:System.Windows.Controls.MediaElement> allows you to skip around in the media.</span></span> <span data-ttu-id="365a2-112">最後に、<xref:System.Windows.Controls.MediaElement.Volume%2A>と<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>プロパティを使用して、メディアのボリュームと再生速度を調整します。</span><span class="sxs-lookup"><span data-stu-id="365a2-112">Finally, the <xref:System.Windows.Controls.MediaElement.Volume%2A> and <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> properties are used to adjust the volume and playback speed of the media.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="365a2-113">参照</span><span class="sxs-lookup"><span data-stu-id="365a2-113">See Also</span></span>  
 [<span data-ttu-id="365a2-114">ストーリーボードを使用して MediaElement を制御する</span><span class="sxs-lookup"><span data-stu-id="365a2-114">Control a MediaElement by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
