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
# <a name="how-to-seek-a-clock-synchronously"></a><span data-ttu-id="3a159-102">方法 : クロックを同期的にシークする</span><span class="sxs-lookup"><span data-stu-id="3a159-102">How to: Seek a Clock Synchronously</span></span>
<span data-ttu-id="3a159-103">使用して、<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>メソッドを特定の時点までのクロックを同期的にシークします。</span><span class="sxs-lookup"><span data-stu-id="3a159-103">Use the <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> method to seek a clock to a specific point synchronously.</span></span> <span data-ttu-id="3a159-104">次の例では、両方を示しています、<xref:System.Windows.Media.Animation.ClockController.Seek%2A>と<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>のメソッド、<xref:System.Windows.Media.Animation.ClockController>です。</span><span class="sxs-lookup"><span data-stu-id="3a159-104">The following example demonstrates both the <xref:System.Windows.Media.Animation.ClockController.Seek%2A> and <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> methods of a <xref:System.Windows.Media.Animation.ClockController>.</span></span>  
  
 <span data-ttu-id="3a159-105">この例では、シーク、 <xref:System.Windows.Media.Animation.Clock>; を参照してください、ストーリー ボードをシークする方法を示す例については[、ストーリー ボード同期的にシーク](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a159-105">This example shows how to seek a <xref:System.Windows.Media.Animation.Clock>; for an example showing how to seek a storyboard, see [Seek a Storyboard Synchronously](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md) .</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a159-106">例</span><span class="sxs-lookup"><span data-stu-id="3a159-106">Example</span></span>  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
