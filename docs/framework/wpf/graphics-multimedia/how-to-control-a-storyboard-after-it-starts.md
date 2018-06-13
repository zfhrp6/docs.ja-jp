---
title: '方法 : ストーリーボードを開始後に制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 2407de5029007748de691a3020078b1241b02fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561463"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>方法 : ストーリーボードを開始後に制御する
この例では、コントロールにコードを使用して、<xref:System.Windows.Media.Animation.Storyboard>開始後にします。 ストーリー ボードを制御[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して<xref:System.Windows.Trigger>と<xref:System.Windows.TriggerAction>オブジェクトです。 例については、次を参照してください。[起動を制御、ストーリー ボードの後に、イベント トリガーを使用して](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)です。  
  
 使用するストーリー ボードを開始するには、その<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>ストーリー ボードのアニメーションをアニメーション化し、ストーリーのプロパティを配信するメソッド。  
  
 ストーリー ボードを制御するためには、使用する、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドを指定して**true** 2 番目のパラメーターとして。 一時停止、再開、シーク、停止、速度が上がり、または、ストーリー ボードの速度が低下または塗りつぶし期間に進めることにし、ストーリー ボードの対話型のメソッドを使用できます。 ストーリー ボードの対話型のメソッドの一覧を次に示します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: ストーリー ボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: 一時停止しているストーリー ボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: ストーリー ボードの対話速度を設定します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: ストーリー ボードの指定した位置をシークします。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: 指定した場所にストーリー ボードを目指しています。 異なり、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>メソッド、この操作は次のタイマー刻みの前に処理します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: 1 つがある場合は、その保留期間をストーリー ボードを進めます。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: ストーリー ボードを停止します。  
  
 次の例では、いくつかのストーリー ボード メソッドは、ストーリー ボードを対話的に制御に使用されます。  
  
 **注:** でトリガーを使用したストーリー ボードを制御する例を参照する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を参照してください[イベント トリガーを使用して、ストーリー ボードの後に開始を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)です。  
  
## <a name="example"></a>例  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>関連項目  
 [開始後のストーリーボードをイベント トリガーを使用して制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
