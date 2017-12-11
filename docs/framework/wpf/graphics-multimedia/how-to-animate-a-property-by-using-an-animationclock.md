---
title: "方法 : AnimationClock を使用してプロパティをアニメーション化する"
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
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47df7aaad45000bc8c761a9bb9022d37e0f0828c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>方法 : AnimationClock を使用してプロパティをアニメーション化する
この例を使用する方法を示しています。<xref:System.Windows.Media.Animation.Clock>プロパティをアニメーション化するオブジェクト。  
  
 依存関係プロパティをアニメーション化するには次の 3 つの方法があります。  
  
-   作成、<xref:System.Windows.Media.Animation.AnimationTimeline>を使用してそのプロパティに関連付けると、<xref:System.Windows.Media.Animation.Storyboard>です。  
  
-   オブジェクトの<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを 1 つを適用する<xref:System.Windows.Media.Animation.AnimationTimeline>対象のプロパティにします。  
  
-   作成、<xref:System.Windows.Media.Animation.AnimationClock>から、<xref:System.Windows.Media.Animation.AnimationTimeline>し、プロパティに適用します。  
  
 <xref:System.Windows.Media.Animation.Storyboard>オブジェクトおよび<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドに直接作成および時計を配布することがなくプロパティをアニメーション化することが有効にする (例については、次を参照してください[ストーリー ボードを使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)と[プロパティなしをアニメーション化します。ストーリー ボードを使って](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)) です。クロックが作成され、自動的に配布します。  
  
## <a name="example"></a>例  
 次の例を作成する方法を示しています、<xref:System.Windows.Media.Animation.AnimationClock>し、同様の 2 つのプロパティに適用します。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 対話的に制御する方法を示す例については、<xref:System.Windows.Media.Animation.Clock>が起動したらを参照してください。[クロックを対話的に制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
