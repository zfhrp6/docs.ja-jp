---
title: "方法 : ストーリーボード アニメーション間で HandoffBehavior を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 323ea563aec7bc7ad0abec2372e3af977c7e38eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>方法 : ストーリーボード アニメーション間で HandoffBehavior を指定する
この例では、ストーリー ボードのアニメーション間ハンドオフ動作を指定する方法を示します。 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>のプロパティ<xref:System.Windows.Media.Animation.BeginStoryboard>新しいアニメーションを指定するプロパティに既に適用されている既存の対話します。  
  
## <a name="example"></a>例  
 次の例では、上にマウス カーソルが移動時に拡大し、カーソルが休暇から移動したときに小さくなる 2 つのボタンを作成します。 ボタンの上にマウス カーソルをすばやく削除すると、最初の 1 つを完了する前に 2 番目のアニメーションが適用されます。 間の違いを表示できる次のように 2 つのアニメーションが重なっている場合は、<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>値<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>と<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>です。 値<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>より滑らかな切り替え時の値にアニメーションが原因と重複するアニメーションを組み合わせて<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>新しいアニメーションをすぐに、以前に重複するアニメーションを置き換えます。  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [アニメーションおよびタイミング](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
