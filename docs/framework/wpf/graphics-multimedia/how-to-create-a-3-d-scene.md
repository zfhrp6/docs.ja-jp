---
title: '方法 : 3-D シーンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: e3c2ea803961ca57606f8ea8bec21d50a38dbe1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559527"
---
# <a name="how-to-create-a-3-d-scene"></a><span data-ttu-id="399c4-102">方法 : 3-D シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="399c4-102">How to: Create a 3-D Scene</span></span>
<span data-ttu-id="399c4-103">この例では、回転されているフラットな用紙のような 3d オブジェクトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="399c4-103">This example shows how to create a 3-D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="399c4-104">A<xref:System.Windows.Controls.Viewport3D>次のコンポーネントと共にこの単純な 3-D シーンの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="399c4-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3-D scene:</span></span>  
  
-   <span data-ttu-id="399c4-105">使用して、カメラを作成、<xref:System.Windows.Media.Media3D.PerspectiveCamera>です。</span><span class="sxs-lookup"><span data-stu-id="399c4-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="399c4-106">カメラでは、3-D シーンのどの部分が表示可能なを指定します。</span><span class="sxs-lookup"><span data-stu-id="399c4-106">The camera specifies what part of the 3-D scene is viewable.</span></span>  
  
-   <span data-ttu-id="399c4-107">使用して 3-D オブジェクト (枚の用紙) の形状を指定するメッシュが作成、<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>プロパティ<xref:System.Windows.Media.Media3D.GeometryModel3D>です。</span><span class="sxs-lookup"><span data-stu-id="399c4-107">A mesh is created to specify the shape of 3-D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="399c4-108">使用して、オブジェクト (このサンプルでの線形グラデーション) の画面に表示される材料が指定されている、<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>プロパティ<xref:System.Windows.Media.Media3D.GeometryModel3D>です。</span><span class="sxs-lookup"><span data-stu-id="399c4-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="399c4-109">使用してオブジェクトに当てるライトが作成された<xref:System.Windows.Media.Media3D.DirectionalLight>です。</span><span class="sxs-lookup"><span data-stu-id="399c4-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="399c4-110">例</span><span class="sxs-lookup"><span data-stu-id="399c4-110">Example</span></span>  
 <span data-ttu-id="399c4-111">次のコードでは、XAML で 3-D シーンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="399c4-111">The code below shows how to create a 3-D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="399c4-112">例</span><span class="sxs-lookup"><span data-stu-id="399c4-112">Example</span></span>  
 <span data-ttu-id="399c4-113">次のコードでは、手続き型コードで同じ 3-D シーンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="399c4-113">The code below shows how to create the same 3-D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="399c4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="399c4-114">See Also</span></span>  
 [<span data-ttu-id="399c4-115">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="399c4-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
