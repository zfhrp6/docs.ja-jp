---
title: "方法 : タイムラインの速度を変更せずにクロックの速度を変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クロック, 変更 (速度を)"
  - "速度 (クロックの), 変更"
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : タイムラインの速度を変更せずにクロックの速度を変更する
<xref:System.Windows.Media.Animation.ClockController> オブジェクトの <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> プロパティを使用すると、クロックの <xref:System.Windows.Media.Animation.Timeline> の <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> を変更せずに <xref:System.Windows.Media.Animation.Clock> の速度を変更できます。  次の例では、クロックの <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> を対話的に変更するために、<xref:System.Windows.Media.Animation.ClockController> を使用しています。  <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> イベントと、クロックの <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> プロパティを使用して、クロックの対話型 <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> が変更されるたびに、クロックの現在のグローバル速度を表示します。  
  
## 使用例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]