---
title: "方法 : 色を傾斜する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a32e6c1901f84c276c071402dac641d45566717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="c9a6d-102">方法 : 色を傾斜する</span><span class="sxs-lookup"><span data-stu-id="c9a6d-102">How to: Shear Colors</span></span>
<span data-ttu-id="c9a6d-103">傾斜だけ増加または減少色要素の色の別のコンポーネントに比例した量。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="c9a6d-104">たとえば、赤の要素は青の要素の値の半分ずつ増加する、変換があるとします。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="c9a6d-105">このような変換は、下にある色 (0.2、0.5, 1) になります (0.7, 0.5, 1)。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="c9a6d-106">新しい赤の要素が 0.2 + (1/2)(1) 0.7 を = です。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9a6d-107">例</span><span class="sxs-lookup"><span data-stu-id="c9a6d-107">Example</span></span>  
 <span data-ttu-id="c9a6d-108">次の例の構築、 <xref:System.Drawing.Image> ColorBars4.bmp ファイルからオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="c9a6d-109">コードは、イメージ内の各ピクセルに前の段落で説明した傾斜変換を適用します。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="c9a6d-110">次の図は、右側の左側に元のイメージと傾斜されたイメージを示します。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="c9a6d-111">![色を傾斜](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="c9a6d-111">![Shear Colors](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="c9a6d-112">次の表では、および傾斜変換を実行後する前に、4 つのバーの色のベクターが一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="c9a6d-113">元</span><span class="sxs-lookup"><span data-stu-id="c9a6d-113">Original</span></span>|<span data-ttu-id="c9a6d-114">傾斜</span><span class="sxs-lookup"><span data-stu-id="c9a6d-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="c9a6d-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="c9a6d-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="c9a6d-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="c9a6d-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="c9a6d-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="c9a6d-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="c9a6d-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="c9a6d-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="c9a6d-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c9a6d-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c9a6d-123">Compiling the Code</span></span>  
 <span data-ttu-id="c9a6d-124">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="c9a6d-125">置き換える`ColorBars.bmp`イメージの名前とパスがシステム上で有効にします。</span><span class="sxs-lookup"><span data-stu-id="c9a6d-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a6d-126">参照</span><span class="sxs-lookup"><span data-stu-id="c9a6d-126">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="c9a6d-127">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="c9a6d-127">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="c9a6d-128">イメージの色の変更</span><span class="sxs-lookup"><span data-stu-id="c9a6d-128">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
