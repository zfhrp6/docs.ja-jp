---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)"
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
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb1bbe43c7e1797d5943bf3da6b4aca22a11c3a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="9b02e-102">方法 : パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)</span><span class="sxs-lookup"><span data-stu-id="9b02e-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="9b02e-103">この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>によって定義されているパスに沿ってオブジェクトをアニメーション化するクラス、<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="9b02e-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b02e-104">例</span><span class="sxs-lookup"><span data-stu-id="9b02e-104">Example</span></span>  
 <span data-ttu-id="9b02e-105">次の例では、以下の処理を実行し、パスに沿ってオブジェクトをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="9b02e-105">The following example animates an object along a path by doing the following:</span></span>  
  
-   <span data-ttu-id="9b02e-106">適用される、<xref:System.Windows.Media.MatrixTransform>を移動するためにオブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="9b02e-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
-   <span data-ttu-id="9b02e-107">使用してパスを定義、<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="9b02e-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
-   <span data-ttu-id="9b02e-108">作成、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化を使用して、<xref:System.Windows.Media.Matrix>のプロパティ、<xref:System.Windows.Media.MatrixTransform>です。</span><span class="sxs-lookup"><span data-stu-id="9b02e-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="9b02e-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>受け取り、<xref:System.Windows.Media.PathGeometry>しを使用して生成<xref:System.Windows.Media.Matrix>値。</span><span class="sxs-lookup"><span data-stu-id="9b02e-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="9b02e-110">サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。</span><span class="sxs-lookup"><span data-stu-id="9b02e-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="9b02e-111">幾何学模様のパスの詳細については、次を参照してください。、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b02e-111">For more information about geometric paths, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b02e-112">参照</span><span class="sxs-lookup"><span data-stu-id="9b02e-112">See Also</span></span>  
 [<span data-ttu-id="9b02e-113">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="9b02e-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="9b02e-114">パス アニメーションのサンプル</span><span class="sxs-lookup"><span data-stu-id="9b02e-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="9b02e-115">パス アニメーションに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="9b02e-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
