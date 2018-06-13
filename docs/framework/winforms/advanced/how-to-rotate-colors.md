---
title: '方法 : 色を回転させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 258ef9cd5eb8d569b2982614e3087df730a18c57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522396"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="fd4c8-102">方法 : 色を回転させる</span><span class="sxs-lookup"><span data-stu-id="fd4c8-102">How to: Rotate Colors</span></span>
<span data-ttu-id="fd4c8-103">4 次元の色領域の回転は、視覚化するが困難です。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="fd4c8-104">おやすくをいずれかの色要素を固定に同意することにより回転を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="fd4c8-105">たとえば、アルファ コンポーネントを 1 に固定の (完全に不透明) を保持することに同意します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="fd4c8-106">次の図に示すように赤、緑、および青の軸を持つ 3 次元のカラー スペースを視覚化できます。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fd4c8-107">![色の変更](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="fd4c8-107">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="fd4c8-108">色は、3-D 空間内のポイントと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="fd4c8-109">たとえば、領域で、ポイント (1, 0, 0) は色が赤を表し領域で、ポイント (0, 1, 0) が緑色の色を表します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="fd4c8-110">次の図は、(1, 0, 0) の色を回転する意味を示します、赤、緑の平面に 60 度の角度をします。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="fd4c8-111">赤、緑の平面に平行な平面の回転は、青の軸を中心に回転と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="fd4c8-112">![色の変更](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="fd4c8-112">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="fd4c8-113">次の図は、各 (赤、緑、青) の 3 つの座標の軸の回転を実行するカラー行列を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="fd4c8-114">![色の変更](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="fd4c8-114">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd4c8-115">例</span><span class="sxs-lookup"><span data-stu-id="fd4c8-115">Example</span></span>  
 <span data-ttu-id="fd4c8-116">次の例は、イメージを 1 つのすべての色 (1, 0, 0.6) は、青軸を中心 60 度回転を適用します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="fd4c8-117">回転の角度は赤、緑の平面に並列では、平面内をスイープします。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="fd4c8-118">次の図は、左側と右側の色の回転後イメージの元のイメージを示します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="fd4c8-119">![色の回転](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="fd4c8-119">![Rotate Colors](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="fd4c8-120">次の図は、次のコードで実行される色の回転の視覚エフェクトを示します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="fd4c8-121">![色の変更](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="fd4c8-121">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd4c8-122">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="fd4c8-122">Compiling the Code</span></span>  
 <span data-ttu-id="fd4c8-123">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="fd4c8-124">置き換える`RotationInput.bmp`イメージのファイル名と、システム上で有効なパスを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd4c8-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4c8-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd4c8-125">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="fd4c8-126">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="fd4c8-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="fd4c8-127">イメージの色の変更</span><span class="sxs-lookup"><span data-stu-id="fd4c8-127">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
