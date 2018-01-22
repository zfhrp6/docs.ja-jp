---
title: "方法 : PointAnimation を使用してオブジェクトの位置をアニメーション化する"
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
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f741770077a90bef33d75640726019496fe8eb8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>方法 : PointAnimation を使用してオブジェクトの位置をアニメーション化する
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.PointAnimation>に沿ってオブジェクトをアニメーション化するクラス、<xref:System.Windows.Shapes.Path>です。  
  
## <a name="example"></a>例  
 次の例では、楕円を移動、<xref:System.Windows.Shapes.Path>別の画面上の 1 つのポイントから。 この例の位置をアニメーション化、<xref:System.Windows.Media.EllipseGeometry>を使用して<xref:System.Windows.Media.Animation.PointAnimation>アニメーション化する、<xref:System.Windows.Media.EllipseGeometry.Center%2A>プロパティです。  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [アニメーションおよびタイミング](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
