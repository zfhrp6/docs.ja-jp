---
title: "方法 : 3-D モデルに放射性素材を適用する"
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
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 069ab4e417d639a36a9168fa950f4b4f6df4c2c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="3f495-102">方法 : 3-D モデルに放射性素材を適用する</span><span class="sxs-lookup"><span data-stu-id="3f495-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="3f495-103">次の例は、使用する方法を示しています。 <xref:System.Windows.Media.Media3D.EmissiveMaterial> EmissiveMaterial のブラシの色に等しい既存の材料に色を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f495-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="3f495-104">次のコード<xref:System.Windows.Media.Media3D.DiffuseMaterial>と<xref:System.Windows.Media.Media3D.EmissiveMaterial>DiffuseMaterial の外観に青色を追加するための組み合わせに適用します。</span><span class="sxs-lookup"><span data-stu-id="3f495-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="3f495-105">手順コード</span><span class="sxs-lookup"><span data-stu-id="3f495-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="3f495-106">例</span><span class="sxs-lookup"><span data-stu-id="3f495-106">Example</span></span>  
 <span data-ttu-id="3f495-107">次のコードは、XAML で全体のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="3f495-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="3f495-108">例</span><span class="sxs-lookup"><span data-stu-id="3f495-108">Example</span></span>  
 <span data-ttu-id="3f495-109">手続き型コードで全体のサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3f495-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3f495-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f495-110">See Also</span></span>  
 [<span data-ttu-id="3f495-111">3-D シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="3f495-111">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="3f495-112">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="3f495-112">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="3f495-113">3-D シーンで素材プロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="3f495-113">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [<span data-ttu-id="3f495-114">3-D オブジェクトの前面および背面に素材を適用する</span><span class="sxs-lookup"><span data-stu-id="3f495-114">Apply Material to the Front and Back of a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
