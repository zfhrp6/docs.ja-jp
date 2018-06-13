---
title: '方法 : ユーザー イベントによってメディアの再生をトリガーする'
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: faa82ee29e3501f484f150100f9069a5fe011312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561476"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a>方法 : ユーザー イベントによってメディアの再生をトリガーする
この例では、メディアの再生とイベントを同期する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Controls.MediaElement>コントロールと<xref:System.Windows.Media.MediaTimeline>、ユーザーがクリックしたときに発生するサウンドを再生するクラス、<xref:System.Windows.Controls.Button>です。  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.EventTrigger.RoutedEvent%2A>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)
