---
title: '方法 : パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: ebe24f060a342633a93b778d5e8030173970029c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559906"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="b6688-102">方法 : パスに沿ってオブジェクトをアニメーション化する (ダブル アニメーション)</span><span class="sxs-lookup"><span data-stu-id="b6688-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="b6688-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>クラスによって定義されるパスに沿ってオブジェクトを移動する、<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="b6688-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6688-104">例</span><span class="sxs-lookup"><span data-stu-id="b6688-104">Example</span></span>  
 <span data-ttu-id="b6688-105">次の例を使用して 2 つ<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>オブジェクトのジオメトリのパスに沿った四角形を移動します。</span><span class="sxs-lookup"><span data-stu-id="b6688-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="b6688-106">最初の<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、<xref:System.Windows.Media.TranslateTransform.X%2A>の<xref:System.Windows.Media.TranslateTransform>四角形に適用します。</span><span class="sxs-lookup"><span data-stu-id="b6688-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="b6688-107">これにより、四角形がパスに沿って水平に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6688-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="b6688-108">2 番目<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>をアニメーション化、<xref:System.Windows.Media.TranslateTransform.Y%2A>の<xref:System.Windows.Media.TranslateTransform>四角形に適用します。</span><span class="sxs-lookup"><span data-stu-id="b6688-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="b6688-109">これにより、四角形がパスに沿って垂直に移動します。</span><span class="sxs-lookup"><span data-stu-id="b6688-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="b6688-110">サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。</span><span class="sxs-lookup"><span data-stu-id="b6688-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="b6688-111">幾何学模様のパスを使用してオブジェクトを移動する別の方法を使用して、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b6688-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="b6688-112">例については、次を参照してください。[オブジェクトに沿って、パス (行列アニメーション) をアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6688-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6688-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6688-113">See Also</span></span>  
 [<span data-ttu-id="b6688-114">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="b6688-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b6688-115">パス アニメーションに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="b6688-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
