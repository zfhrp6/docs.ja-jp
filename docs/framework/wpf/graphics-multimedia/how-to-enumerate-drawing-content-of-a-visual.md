---
title: '方法 : ビジュアルの描画コンテンツを列挙する'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 19c37ec7df3542eb46b182f4790059eb16fef90b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559403"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="3d1c5-102">方法 : ビジュアルの描画コンテンツを列挙する</span><span class="sxs-lookup"><span data-stu-id="3d1c5-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="3d1c5-103"><xref:System.Windows.Media.Drawing>オブジェクトの内容を列挙するためのオブジェクト モデルの提供、<xref:System.Windows.Media.Visual>です。</span><span class="sxs-lookup"><span data-stu-id="3d1c5-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d1c5-104">例</span><span class="sxs-lookup"><span data-stu-id="3d1c5-104">Example</span></span>  
 <span data-ttu-id="3d1c5-105">次の例では、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>を取得する方法、<xref:System.Windows.Media.DrawingGroup>の値、<xref:System.Windows.Media.Visual>およびそれを列挙します。</span><span class="sxs-lookup"><span data-stu-id="3d1c5-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d1c5-106">ビジュアルの内容を列挙しているときに取得する<xref:System.Windows.Media.Drawing>オブジェクト、および、基になる表現ではありませんレンダー データ ベクトル グラフィックス命令リストとして。</span><span class="sxs-lookup"><span data-stu-id="3d1c5-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="3d1c5-107">詳しくは、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3d1c5-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="3d1c5-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d1c5-108">See Also</span></span>  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="3d1c5-109">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="3d1c5-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="3d1c5-110">WPF グラフィックス レンダリングの概要</span><span class="sxs-lookup"><span data-stu-id="3d1c5-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
