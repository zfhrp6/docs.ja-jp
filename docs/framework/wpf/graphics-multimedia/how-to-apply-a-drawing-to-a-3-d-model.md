---
title: "方法 : 3-D モデルに描画を適用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="df053-102">方法 : 3-D モデルに描画を適用する</span><span class="sxs-lookup"><span data-stu-id="df053-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="df053-103">この例を使用する方法を示しています、<xref:System.Windows.Media.DrawingBrush>として、<xref:System.Windows.Media.Media3D.Material>に適用される、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]モデル。</span><span class="sxs-lookup"><span data-stu-id="df053-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="df053-104">次のコード定義、<xref:System.Windows.Media.DrawingGroup>の内容として、<xref:System.Windows.Media.DrawingBrush>です。</span><span class="sxs-lookup"><span data-stu-id="df053-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="df053-105"><xref:System.Windows.Media.DrawingBrush>として設定されている、<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>のプロパティ、<xref:System.Windows.Media.Media3D.DiffuseMaterial>に適用される、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面。</span><span class="sxs-lookup"><span data-stu-id="df053-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="df053-106">**注:**複雑なオブジェクトと次の図のように値を再利用できるし、コードを簡素化されるリソースとして定義すると便利です。</span><span class="sxs-lookup"><span data-stu-id="df053-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="df053-107">参照してください[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="df053-107">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="df053-108">例</span><span class="sxs-lookup"><span data-stu-id="df053-108">Example</span></span>  
 <span data-ttu-id="df053-109">次のコードでは、全体のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="df053-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="df053-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="df053-110">See Also</span></span>  
 [<span data-ttu-id="df053-111">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="df053-111">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="df053-112">3-D シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="df053-112">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="df053-113">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="df053-113">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="df053-114">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="df053-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
