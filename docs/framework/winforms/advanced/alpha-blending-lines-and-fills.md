---
title: アルファ ブレンドの直線と塗りつぶし
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: f58fa2d105492c6c72d3d6906c3c35f89130fe91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517687"
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="6289f-102">アルファ ブレンドの直線と塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="6289f-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="6289f-103">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]色がそれぞれ 8 ビットでアルファ、赤、緑、および青の 32 ビット値。</span><span class="sxs-lookup"><span data-stu-id="6289f-103">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="6289f-104">アルファ値は、色の透明度を示します: 範囲の色から背景色とブレンドされます。</span><span class="sxs-lookup"><span data-stu-id="6289f-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="6289f-105">アルファ値の範囲は 0 ~ 255, 0 が完全に透明色を表すおよび 255 は、完全に不透明な色を表します。</span><span class="sxs-lookup"><span data-stu-id="6289f-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="6289f-106">アルファ ブレンドは、ソースと背景色データのピクセルごとの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="6289f-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="6289f-107">指定したソースの色の 3 つのコンポーネント (赤、緑、青) は、次の数式に従って背景色の対応するコンポーネントとブレンドされます。</span><span class="sxs-lookup"><span data-stu-id="6289f-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="6289f-108">displayColor sourceColor × アルファを = 255/+ backgroundColor × (255 – alpha)/255</span><span class="sxs-lookup"><span data-stu-id="6289f-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="6289f-109">たとえば、元の色の赤の要素があるとします 150 と背景色の赤の要素は 100 です。</span><span class="sxs-lookup"><span data-stu-id="6289f-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="6289f-110">アルファ値が 200 の場合は、生成される色の赤の要素は次のように計算されます。</span><span class="sxs-lookup"><span data-stu-id="6289f-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="6289f-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="6289f-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6289f-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6289f-112">In This Section</span></span>  
 [<span data-ttu-id="6289f-113">方法: 不透明な直線および半透明な直線を描画する</span><span class="sxs-lookup"><span data-stu-id="6289f-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="6289f-114">アルファ ブレンドの直線を描画する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6289f-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="6289f-115">方法: 不透明ブラシおよび半透明ブラシを使用して描画する</span><span class="sxs-lookup"><span data-stu-id="6289f-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="6289f-116">アルファ ブレンド (ブラシと共に) する方法をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6289f-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="6289f-117">方法: 複合モードを使用してアルファ ブレンドを制御する</span><span class="sxs-lookup"><span data-stu-id="6289f-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="6289f-118">使用してアルファ ブレンドを制御する方法について説明<xref:System.Drawing.Drawing2D.CompositingMode>です。</span><span class="sxs-lookup"><span data-stu-id="6289f-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="6289f-119">方法: カラー行列を使用してイメージのアルファ値を設定する</span><span class="sxs-lookup"><span data-stu-id="6289f-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="6289f-120">使用する方法について説明します、<xref:System.Drawing.Imaging.ColorMatrix>アルファ ブレンドを制御するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6289f-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
