---
title: "方法 : クロックを同期的にシークする | Microsoft Docs"
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
  - "クロック, シーク (同期的に)"
  - "シーク (クロックを同期的に)"
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : クロックを同期的にシークする
<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> メソッドを使用して、特定のポイントまでクロックを同期的にシークします。  <xref:System.Windows.Media.Animation.ClockController> の <xref:System.Windows.Media.Animation.ClockController.Seek%2A> メソッドおよび <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> メソッドを次の例に示します。  
  
 この例では、<xref:System.Windows.Media.Animation.Clock> をシークする方法を示します。ストーリーボードをシークする方法の例については、「[ストーリーボードを同期的にシークする](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]