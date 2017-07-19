---
title: "方法 : クロックを対話的に制御する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クロック, 制御 (対話形式で)"
  - "制御 (クロックを対話形式で)"
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : クロックを対話的に制御する
<xref:System.Windows.Media.Animation.Clock> オブジェクトの <xref:System.Windows.Media.Animation.ClockController> プロパティを使用すれば、対話形式でクロックを開始、一時停止、再開、シーク、区間の最後までの前進、停止できます。  対話形式で制御できるのは、タイミング ツリーのルートに位置するクロックのみです。  
  
> [!NOTE]
>  クロックを直接操作せずにアニメーションを対話形式で制御する方法もあります。それは、ストーリーボードを使用する方法です。  ストーリーボードは、マークアップとコードの両方でサポートされています。  例については、「[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)」または「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 次の例では、さまざまなボタンを使用して、アニメーション クロックを対話形式で制御しています。  
  
## 使用例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## 参照  
 [ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)