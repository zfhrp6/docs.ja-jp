---
title: 変換を使用した色のスケーリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 6cfe90cef42086672990c45c99961db3d29c3ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525968"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="ac862-102">変換を使用した色のスケーリング</span><span class="sxs-lookup"><span data-stu-id="ac862-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="ac862-103">拡大縮小変換は、番号で 4 つの色要素の 1 つ以上を乗算します。</span><span class="sxs-lookup"><span data-stu-id="ac862-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="ac862-104">拡大/縮小を表すカラー マトリックス エントリは、次の表で表されます。</span><span class="sxs-lookup"><span data-stu-id="ac862-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="ac862-105">コンポーネントを拡張します。</span><span class="sxs-lookup"><span data-stu-id="ac862-105">Component to be scaled</span></span>|<span data-ttu-id="ac862-106">マトリックスのエントリ</span><span class="sxs-lookup"><span data-stu-id="ac862-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="ac862-107">赤</span><span class="sxs-lookup"><span data-stu-id="ac862-107">Red</span></span>|<span data-ttu-id="ac862-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="ac862-108">[0][0]</span></span>|  
|<span data-ttu-id="ac862-109">緑</span><span class="sxs-lookup"><span data-stu-id="ac862-109">Green</span></span>|<span data-ttu-id="ac862-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="ac862-110">[1][1]</span></span>|  
|<span data-ttu-id="ac862-111">青</span><span class="sxs-lookup"><span data-stu-id="ac862-111">Blue</span></span>|<span data-ttu-id="ac862-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="ac862-112">[2][2]</span></span>|  
|<span data-ttu-id="ac862-113">[アルファ]</span><span class="sxs-lookup"><span data-stu-id="ac862-113">Alpha</span></span>|<span data-ttu-id="ac862-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="ac862-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="ac862-115">1 つの色のスケーリング</span><span class="sxs-lookup"><span data-stu-id="ac862-115">Scaling One Color</span></span>  
 <span data-ttu-id="ac862-116">次の例の構築、 <xref:System.Drawing.Image> ColorBars2.bmp ファイルからオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ac862-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="ac862-117">コードは、2 倍の図の各ピクセルの青の成分をスケーリングします。</span><span class="sxs-lookup"><span data-stu-id="ac862-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="ac862-118">変換後のイメージが並んで、元の画像が描画されます。</span><span class="sxs-lookup"><span data-stu-id="ac862-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="ac862-119">次の図は、右側の左側に元のイメージとスケーリングされたイメージを示します。</span><span class="sxs-lookup"><span data-stu-id="ac862-119">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="ac862-120">![色をスケーリング](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span><span class="sxs-lookup"><span data-stu-id="ac862-120">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span></span>  
  
 <span data-ttu-id="ac862-121">次の表では、青のスケーリングの前後に、次の 4 つのバーの色ベクターが一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ac862-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="ac862-122">4 番目のカラー バーの青の要素が 0.6 を 0.8 からしたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ac862-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="ac862-123">これはため[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]は、結果の小数部の一部のみが保持されます。</span><span class="sxs-lookup"><span data-stu-id="ac862-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="ac862-124">たとえば、(2)(0.8) = 1.6、1.6 の小数部は 0.6 です。</span><span class="sxs-lookup"><span data-stu-id="ac862-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="ac862-125">小数部分のみを保持とは、結果は、常には [0, 1] 間隔することを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac862-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="ac862-126">元</span><span class="sxs-lookup"><span data-stu-id="ac862-126">Original</span></span>|<span data-ttu-id="ac862-127">拡大/縮小</span><span class="sxs-lookup"><span data-stu-id="ac862-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="ac862-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="ac862-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="ac862-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="ac862-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="ac862-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="ac862-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="ac862-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="ac862-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="ac862-136">複数の色のスケーリング</span><span class="sxs-lookup"><span data-stu-id="ac862-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="ac862-137">次の例の構築、 <xref:System.Drawing.Image> ColorBars2.bmp ファイルからオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ac862-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="ac862-138">コードは、イメージ内の各ピクセルの赤、緑、および青のコンポーネントをスケーリングします。</span><span class="sxs-lookup"><span data-stu-id="ac862-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="ac862-139">赤の要素は、25% に縮小し、緑の要素は 35% に縮小青の要素は、50% に縮小します。</span><span class="sxs-lookup"><span data-stu-id="ac862-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="ac862-140">次の図は、右側の左側に元のイメージとスケーリングされたイメージを示します。</span><span class="sxs-lookup"><span data-stu-id="ac862-140">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="ac862-141">![色をスケーリング](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span><span class="sxs-lookup"><span data-stu-id="ac862-141">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span></span>  
  
 <span data-ttu-id="ac862-142">次の表では、赤、緑、青のスケーリングの前後に、次の 4 つのバーの色ベクターが一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ac862-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="ac862-143">元</span><span class="sxs-lookup"><span data-stu-id="ac862-143">Original</span></span>|<span data-ttu-id="ac862-144">拡大/縮小</span><span class="sxs-lookup"><span data-stu-id="ac862-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="ac862-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="ac862-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="ac862-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="ac862-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="ac862-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="ac862-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="ac862-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="ac862-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="ac862-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac862-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac862-153">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="ac862-154">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="ac862-154">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="ac862-155">イメージの色の変更</span><span class="sxs-lookup"><span data-stu-id="ac862-155">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
