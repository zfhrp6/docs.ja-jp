---
title: "方法 : クロックを同期的にシークする"
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
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d158629b428bda8e7749df393ad0724225b5a0a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-seek-a-clock-synchronously"></a>方法 : クロックを同期的にシークする
使用して、<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>メソッドを特定の時点までのクロックを同期的にシークします。 次の例では、両方を示しています、<xref:System.Windows.Media.Animation.ClockController.Seek%2A>と<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>のメソッド、<xref:System.Windows.Media.Animation.ClockController>です。  
  
 この例では、シーク、 <xref:System.Windows.Media.Animation.Clock>; を参照してください、ストーリー ボードをシークする方法を示す例については[、ストーリー ボード同期的にシーク](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)です。  
  
## <a name="example"></a>例  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
