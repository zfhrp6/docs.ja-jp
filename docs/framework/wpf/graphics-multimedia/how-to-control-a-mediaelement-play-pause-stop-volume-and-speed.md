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
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>方法 : MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する
次の例を使用してメディアの再生を制御する方法を示しています、<xref:System.Windows.Controls.MediaElement>です。 この例を使用すると、再生、一時停止、停止、メディアで前後にスキップし、ボリュームと速度比を調整する簡単なメディア プレーヤーを作成します。  
  
## <a name="example"></a>例  
 次のコードでは、UI を作成します。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>プロパティ<xref:System.Windows.Controls.MediaElement>に設定する必要があります`Manual`できるように対話的を停止、一時停止、およびメディアを再生します。  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>例  
 次のコードでは、サンプルの UI コントロールの機能を実装します。 <xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、および<xref:System.Windows.Controls.MediaElement.Stop%2A>メソッドを使用して、それぞれの再生、一時停止およびメディアを停止します。 変更、<xref:System.Windows.Controls.MediaElement.Position%2A>のプロパティ、<xref:System.Windows.Controls.MediaElement>のメディア スキップすることができます。 最後に、<xref:System.Windows.Controls.MediaElement.Volume%2A>と<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>プロパティを使用して、メディアのボリュームと再生速度を調整します。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>参照  
 [ストーリーボードを使用して MediaElement を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
