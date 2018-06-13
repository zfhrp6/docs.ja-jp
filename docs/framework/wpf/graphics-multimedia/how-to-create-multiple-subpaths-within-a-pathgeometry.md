---
title: '方法 : PathGeometry 内に複数のサブパスを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 5b129b1bacb5dc2cba87376e8df70e115a5ebd72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559332"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="e58cc-102">方法 : PathGeometry 内に複数のサブパスを作成する</span><span class="sxs-lookup"><span data-stu-id="e58cc-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="e58cc-103">この例は、内の複数のサブパスを作成する方法を示します、<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="e58cc-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e58cc-104">作成する複数のサブパスを作成するには<xref:System.Windows.Media.PathFigure>各サブ パスにします。</span><span class="sxs-lookup"><span data-stu-id="e58cc-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e58cc-105">例</span><span class="sxs-lookup"><span data-stu-id="e58cc-105">Example</span></span>  
 <span data-ttu-id="e58cc-106">次の例は、1 つずつ、2 つのサブパス三角形を作成します。</span><span class="sxs-lookup"><span data-stu-id="e58cc-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="e58cc-107">次の例を使用して複数のサブパスを作成する方法を示しています、<xref:System.Windows.Shapes.Path>と[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性構文です。</span><span class="sxs-lookup"><span data-stu-id="e58cc-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="e58cc-108">各`M`されるため、例では、三角形を描画それぞれ 2 つのサブパスを作成する新しいサブパスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e58cc-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="e58cc-109">(この属性の構文が実際に作成するメモ、 <xref:System.Windows.Media.StreamGeometry>、軽量バージョンの<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="e58cc-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e58cc-110">詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」のページを参照してください。)</span><span class="sxs-lookup"><span data-stu-id="e58cc-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58cc-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="e58cc-111">See Also</span></span>  
 [<span data-ttu-id="e58cc-112">ジオメトリの概要</span><span class="sxs-lookup"><span data-stu-id="e58cc-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
