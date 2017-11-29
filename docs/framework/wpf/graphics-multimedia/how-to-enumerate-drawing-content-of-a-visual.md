---
title: "方法 : ビジュアルの描画コンテンツを列挙する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e498bc8e425198e479d7ce0b2328e0efa3ede70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="e297a-102">方法 : ビジュアルの描画コンテンツを列挙する</span><span class="sxs-lookup"><span data-stu-id="e297a-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="e297a-103"><xref:System.Windows.Media.Drawing>オブジェクトの内容を列挙するためのオブジェクト モデルの提供、<xref:System.Windows.Media.Visual>です。</span><span class="sxs-lookup"><span data-stu-id="e297a-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e297a-104">例</span><span class="sxs-lookup"><span data-stu-id="e297a-104">Example</span></span>  
 <span data-ttu-id="e297a-105">次の例では、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>を取得する方法、<xref:System.Windows.Media.DrawingGroup>の値、<xref:System.Windows.Media.Visual>およびそれを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e297a-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e297a-106">ビジュアルの内容を列挙しているときに取得する<xref:System.Windows.Media.Drawing>オブジェクト、および、基になる表現ではありませんレンダー データ ベクトル グラフィックス命令リストとして。</span><span class="sxs-lookup"><span data-stu-id="e297a-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="e297a-107">詳しくは、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e297a-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="e297a-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e297a-108">See Also</span></span>  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="e297a-109">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="e297a-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="e297a-110">WPF グラフィックス レンダリングの概要</span><span class="sxs-lookup"><span data-stu-id="e297a-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
