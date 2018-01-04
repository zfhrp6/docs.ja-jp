---
title: "方法 : アニメーションの出力値をアニメーションの開始値に追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1a6a5923655c5857b813df778b36b6c7fd208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>方法 : アニメーションの出力値をアニメーションの開始値に追加する
この例では、アニメーションの開始値をアニメーションの出力値を追加する方法を示します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>プロパティをアニメーション化されたプロパティの開始値 (基本値) に追加されるアニメーションの出力値にするかどうかを指定します。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>最も基本的なアニメーションとほとんどのキー フレーム アニメーションのプロパティです。 詳細については、次を参照してください。[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)と[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)です。  
  
 次の例を使用しての効果を示しています、<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType>を持つプロパティ<xref:System.Windows.Media.Animation.DoubleAnimation>を使用して、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType>を持つプロパティ<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>です。  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>参照  
 [反復サイクル中にアニメーション値を累積する](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [アニメーションおよびタイミング](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
