---
title: '方法 : 3-D モデルのスケールを変換する'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 3cca1a210a7dbe410ebaacaaf89c08de8c31c40e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561099"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="bf828-102">方法 : 3-D モデルのスケールを変換する</span><span class="sxs-lookup"><span data-stu-id="bf828-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="bf828-103">この例では、3-D オブジェクトをスケーリングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bf828-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="bf828-104">する 3d オブジェクトを拡張するを使用して、<xref:System.Windows.Media.Media3D.ScaleTransform3D>です。</span><span class="sxs-lookup"><span data-stu-id="bf828-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="bf828-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>、 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>、および<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>プロパティを指定する係数で要素のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="bf828-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="bf828-106">たとえば、 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> 1.5 の値が元の幅の 150% にオブジェクトを拡大します。</span><span class="sxs-lookup"><span data-stu-id="bf828-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="bf828-107">A<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>値 0.5 は 50% でオブジェクトの高さを縮小します。</span><span class="sxs-lookup"><span data-stu-id="bf828-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="bf828-108">次のコードを使用して、<xref:System.Windows.Media.Media3D.ScaleTransform3D>に対して変換として、<xref:System.Windows.Media.Media3D.GeometryModel3D>です。</span><span class="sxs-lookup"><span data-stu-id="bf828-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="bf828-109">例</span><span class="sxs-lookup"><span data-stu-id="bf828-109">Example</span></span>  
 <span data-ttu-id="bf828-110">次のコードでは、全体のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="bf828-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bf828-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf828-111">See Also</span></span>  
 [<span data-ttu-id="bf828-112">3-D 変換をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="bf828-112">Animate 3-D Translations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [<span data-ttu-id="bf828-113">3-D シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="bf828-113">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="bf828-114">3-D グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="bf828-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
