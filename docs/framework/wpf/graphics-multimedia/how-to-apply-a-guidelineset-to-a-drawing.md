---
title: "方法 : 描画に GuidelineSet を適用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf689f8a7c475dbdda416297e28118d43bfdbff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="e2a3a-102">方法 : 描画に GuidelineSet を適用する</span><span class="sxs-lookup"><span data-stu-id="e2a3a-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="e2a3a-103">この例では、適用、<xref:System.Windows.Media.GuidelineSet>を<xref:System.Windows.Media.DrawingGroup>です。</span><span class="sxs-lookup"><span data-stu-id="e2a3a-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="e2a3a-104"><xref:System.Windows.Media.DrawingGroup>クラスは、タイプののみ<xref:System.Windows.Media.Drawing>を持つ、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e2a3a-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="e2a3a-105">適用する、<xref:System.Windows.Media.GuidelineSet>の別の型に<xref:System.Windows.Media.Drawing>に追加、<xref:System.Windows.Media.DrawingGroup>適用し、<xref:System.Windows.Media.GuidelineSet>を<xref:System.Windows.Media.DrawingGroup>です。</span><span class="sxs-lookup"><span data-stu-id="e2a3a-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2a3a-106">例</span><span class="sxs-lookup"><span data-stu-id="e2a3a-106">Example</span></span>  
 <span data-ttu-id="e2a3a-107">次の例では、2 つ作成されます<xref:System.Windows.Media.DrawingGroup>とほぼ同じです。 唯一の違いがあるオブジェクト: 2 つ目<xref:System.Windows.Media.DrawingGroup>が、<xref:System.Windows.Media.GuidelineSet>最初がないとします。</span><span class="sxs-lookup"><span data-stu-id="e2a3a-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="e2a3a-108">この例からの出力を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="e2a3a-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="e2a3a-109">違いは、2 つの表示のため<xref:System.Windows.Media.DrawingGroup>オブジェクトはあまり軽度でないの図面の特定の部分は拡大されます。</span><span class="sxs-lookup"><span data-stu-id="e2a3a-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="e2a3a-110">![GuidelineSet が有効/無効な DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="e2a3a-110">![A DrawingGroup with and without a GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e2a3a-111">参照</span><span class="sxs-lookup"><span data-stu-id="e2a3a-111">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [<span data-ttu-id="e2a3a-112">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="e2a3a-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
