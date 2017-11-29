---
title: "方法 : ビジュアルにテキストを描画する"
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
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 735a84a034587b1433403a45edc7c2f459340273
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="21284-102">方法 : ビジュアルにテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="21284-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="21284-103">次の例にテキストを描画する方法を示しています、<xref:System.Windows.Media.DrawingVisual>を使用して、<xref:System.Windows.Media.DrawingContext>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="21284-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="21284-104">描画のコンテキストが呼び出しによって返される、<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>のメソッド、<xref:System.Windows.Media.DrawingVisual>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="21284-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="21284-105">描画のコンテキストには、グラフィックスとテキストを描画できます。</span><span class="sxs-lookup"><span data-stu-id="21284-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="21284-106">描画のコンテキストにテキストを描画するには、使用、<xref:System.Windows.Media.DrawingContext.DrawText%2A>のメソッド、<xref:System.Windows.Media.DrawingContext>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="21284-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="21284-107">描画のコンテキストにコンテンツを描画したらを呼び出す、<xref:System.Windows.Media.DrawingContext.Close%2A>描画のコンテキストを閉じるし、内容を保持する方法です。</span><span class="sxs-lookup"><span data-stu-id="21284-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21284-108">例</span><span class="sxs-lookup"><span data-stu-id="21284-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="21284-109">上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21284-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
