---
title: "方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>方法 : 開始後のストーリーボードをイベント トリガーを使用して制御する
この例では、制御、<xref:System.Windows.Media.Animation.Storyboard>開始後にします。 開始する、<xref:System.Windows.Media.Animation.Storyboard>を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して<xref:System.Windows.Media.Animation.BeginStoryboard>オブジェクトとを開始し、ストーリー ボードのプロパティにアニメーションを配布します。 割り当てる場合<xref:System.Windows.Media.Animation.BeginStoryboard>名前を指定してその<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>プロパティ、おくことで制御可能なストーリー ボードです。 対話的に制御できますストーリー ボードを開始後にします。  
  
 と共に次のストーリー ボード操作を使用して<xref:System.Windows.EventTrigger>ストーリー ボードを制御するオブジェクト。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: ストーリー ボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: 一時停止しているストーリー ボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: ストーリー ボードの速度を変更します。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: 1 つがある場合は、その保留期間の終了をストーリー ボードを進めます。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: ストーリー ボードを停止します。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: リソースの解放、ストーリー ボードを削除します。  
  
## <a name="example"></a>例  
 次の例では、制御可能なストーリー ボード操作を使用して、ストーリー ボードを対話的に制御します。  
  
 **注:**コードを使用してストーリー ボードの制御の例を参照してください[、ストーリー ボードの後に、開始メソッドを使用してその対話型制御](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)です。  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 その他の例では、次を参照してください。、[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [対話型メソッドを使用してストーリーボードを開始後に制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
