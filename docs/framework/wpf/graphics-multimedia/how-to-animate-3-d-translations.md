---
title: "方法 : 3-D 変換をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d49ad52906787eed9ab115adeb763b89b2ea38e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="45881-102">方法 : 3-D 変換をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="45881-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="45881-103">このトピックで設定の変換の変換をアニメーション化する方法を示します、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]モデル。</span><span class="sxs-lookup"><span data-stu-id="45881-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="45881-104">次のコードのアプリケーション、<xref:System.Windows.Media.Media3D.TranslateTransform3D>オブジェクトを<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>のプロパティ、<xref:System.Windows.Media.Media3D.GeometryModel3D>です。</span><span class="sxs-lookup"><span data-stu-id="45881-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="45881-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>このプロパティ<xref:System.Windows.Media.Media3D.TranslateTransform3D>次のコードを使用してオブジェクトをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="45881-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="45881-106">例</span><span class="sxs-lookup"><span data-stu-id="45881-106">Example</span></span>  
 <span data-ttu-id="45881-107">次のコードでは、全体のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="45881-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="45881-108">参照</span><span class="sxs-lookup"><span data-stu-id="45881-108">See Also</span></span>  
 [<span data-ttu-id="45881-109">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="45881-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="45881-110">3-D シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="45881-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="45881-111">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="45881-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="45881-112">変換の概要</span><span class="sxs-lookup"><span data-stu-id="45881-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
