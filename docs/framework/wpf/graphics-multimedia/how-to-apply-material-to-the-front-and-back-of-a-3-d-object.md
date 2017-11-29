---
title: "方法 : 3-D オブジェクトの前面および背面に素材を適用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce4605208be264418088399253298798205c3f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="3edd5-102">方法 : 3-D オブジェクトの前面および背面に素材を適用する</span><span class="sxs-lookup"><span data-stu-id="3edd5-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="3edd5-103">次の例に適用する方法を示しています、<xref:System.Windows.Media.Media3D.Material>を最前面へと 3-D 裏面オブジェクトおよびオブジェクトの両方の側を表示するオブジェクトをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="3edd5-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="3edd5-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>のプロパティ、<xref:System.Windows.Media.Media3D.GeometryModel3D>赤いを適用するために使用<xref:System.Windows.Media.Brush>オブジェクトの前面に、<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>のプロパティ、<xref:System.Windows.Media.Media3D.GeometryModel3D>青いを適用するために使用<xref:System.Windows.Media.Brush>オブジェクトの背面にします。</span><span class="sxs-lookup"><span data-stu-id="3edd5-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="3edd5-105">次のコードは、オブジェクトへの素材のアプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="3edd5-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="3edd5-106">例</span><span class="sxs-lookup"><span data-stu-id="3edd5-106">Example</span></span>  
 <span data-ttu-id="3edd5-107">次のコードでは、全体のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="3edd5-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3edd5-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="3edd5-108">See Also</span></span>  
 [<span data-ttu-id="3edd5-109">3-D シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="3edd5-109">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="3edd5-110">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="3edd5-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="3edd5-111">3-D シーンで素材プロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="3edd5-111">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [<span data-ttu-id="3edd5-112">3-D モデルに放射性素材を適用する</span><span class="sxs-lookup"><span data-stu-id="3edd5-112">Apply Emissive Material to a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
