---
title: "方法 : クロックを対話的に制御する"
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
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24a5154607bf535cbf995705332092bb86ca02e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-interactively-control-a-clock"></a>方法 : クロックを対話的に制御する
A<xref:System.Windows.Media.Animation.Clock>オブジェクトの<xref:System.Windows.Media.Animation.ClockController>プロパティでは、対話形式で開始、一時停止、再開、シーク、塗りつぶし期間、時計を進めるおよび時計を停止することができます。 タイミング ツリーのルート クロックのみを対話的に制御できます。  
  
> [!NOTE]
>  クロックを直接操作することを必要としないアニメーションを対話的に制御するには、その他の方法があります: ストーリー ボードを使用することもできます。 ストーリー ボードは、マークアップとコードの両方でサポートされます。 例については、次を参照してください。[ストーリー ボードを使用してプロパティをアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)または[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
 次の例では、いくつかのボタンはアニメーション クロックを対話的に制御に使用されます。  
  
## <a name="example"></a>例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>参照  
 [ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
