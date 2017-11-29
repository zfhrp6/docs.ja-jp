---
title: "方法 : イメージを回転、反転、および傾斜させる"
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
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaa6286731d196dad387e1648644ca3e8103da03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="dd36d-102">方法 : イメージを回転、反転、および傾斜させる</span><span class="sxs-lookup"><span data-stu-id="dd36d-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="dd36d-103">回転、反転、および元のイメージの左、右、上および左下コーナーの終点を指定することによって、イメージを傾けることができます。</span><span class="sxs-lookup"><span data-stu-id="dd36d-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="dd36d-104">次の 3 つのターゲット ポイントでは、元の四角形の画像を指定した平行四辺形にマップされるアフィン変換を決定します。</span><span class="sxs-lookup"><span data-stu-id="dd36d-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd36d-105">例</span><span class="sxs-lookup"><span data-stu-id="dd36d-105">Example</span></span>  
 <span data-ttu-id="dd36d-106">たとえば、元のイメージが四角形の左上隅が (0, 0)、右上隅にある (100, 0)、および左下隅にある (0, 50)。</span><span class="sxs-lookup"><span data-stu-id="dd36d-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="dd36d-107">3 つの点を次のようにターゲット ポイントにマップするものとします。</span><span class="sxs-lookup"><span data-stu-id="dd36d-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="dd36d-108">元のポイント</span><span class="sxs-lookup"><span data-stu-id="dd36d-108">Original point</span></span>|<span data-ttu-id="dd36d-109">コピー先のポイント</span><span class="sxs-lookup"><span data-stu-id="dd36d-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="dd36d-110">左上隅 (0, 0)</span><span class="sxs-lookup"><span data-stu-id="dd36d-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="dd36d-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="dd36d-111">(200, 20)</span></span>|  
|<span data-ttu-id="dd36d-112">右 (100, 0)</span><span class="sxs-lookup"><span data-stu-id="dd36d-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="dd36d-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="dd36d-113">(110, 100)</span></span>|  
|<span data-ttu-id="dd36d-114">左下 (0, 50)</span><span class="sxs-lookup"><span data-stu-id="dd36d-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="dd36d-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="dd36d-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="dd36d-116">次の図は、元のイメージと平行四辺形にマップされているイメージを示します。</span><span class="sxs-lookup"><span data-stu-id="dd36d-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="dd36d-117">元のイメージがされて傾斜、反映、回転、および変換します。</span><span class="sxs-lookup"><span data-stu-id="dd36d-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="dd36d-118">元のイメージの上端に沿って、x 軸を実行している行にマップされている (200, 20) と (110, 100)。</span><span class="sxs-lookup"><span data-stu-id="dd36d-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="dd36d-119">元のイメージの左側に y 軸を実行している行にマップされている (200, 20) と (250, 30)。</span><span class="sxs-lookup"><span data-stu-id="dd36d-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="dd36d-120">![ストライプ](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="dd36d-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="dd36d-121">次の図は、写真のイメージに適用されるような変換を示します。</span><span class="sxs-lookup"><span data-stu-id="dd36d-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="dd36d-122">![変換クライマ](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="dd36d-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="dd36d-123">次の図は、同じ変換をメタファイルに適用します。</span><span class="sxs-lookup"><span data-stu-id="dd36d-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="dd36d-124">![変換メタファイル](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="dd36d-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="dd36d-125">次の例では、最初の図に示すようにイメージを生成します。</span><span class="sxs-lookup"><span data-stu-id="dd36d-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd36d-126">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="dd36d-126">Compiling the Code</span></span>  
 <span data-ttu-id="dd36d-127">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。</span><span class="sxs-lookup"><span data-stu-id="dd36d-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="dd36d-128">必ず置き換えて`Stripes.bmp`をシステム上で有効であるイメージへのパス。</span><span class="sxs-lookup"><span data-stu-id="dd36d-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd36d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd36d-129">See Also</span></span>  
 [<span data-ttu-id="dd36d-130">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="dd36d-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
