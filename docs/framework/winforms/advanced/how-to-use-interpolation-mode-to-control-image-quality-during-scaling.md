---
title: "方法 : 補間モードを使用してスケーリング時の画質を制御する"
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
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8bbc17b8344fca496dcf8f4077a69b6db1453c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="e4210-102">方法 : 補間モードを使用してスケーリング時の画質を制御する</span><span class="sxs-lookup"><span data-stu-id="e4210-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="e4210-103">補間モード、<xref:System.Drawing.Graphics>オブジェクト方法に影響を与えます[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]スケール (拡大および縮小) イメージ。</span><span class="sxs-lookup"><span data-stu-id="e4210-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="e4210-104"><xref:System.Drawing.Drawing2D.InterpolationMode>列挙体は、以下のうち一部を示しています、いくつかの補間モードを定義します。</span><span class="sxs-lookup"><span data-stu-id="e4210-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="e4210-105">イメージを拡大するには、大きいイメージのピクセルのグループに、元のイメージ内の各ピクセルをマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4210-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="e4210-106">イメージを縮小するより小さなイメージの単一のピクセルに元のイメージのピクセルのグループをマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4210-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="e4210-107">これらのマッピングを実行するアルゴリズムの有効性は、スケーリングされたイメージの品質を決定します。</span><span class="sxs-lookup"><span data-stu-id="e4210-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="e4210-108">高品質のスケーリングされたイメージを生成するアルゴリズムは、処理時間を必要とする傾向があります。</span><span class="sxs-lookup"><span data-stu-id="e4210-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="e4210-109">上記の一覧で<xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>が最も低い品質モードと<xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>最高品質のモードします。</span><span class="sxs-lookup"><span data-stu-id="e4210-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="e4210-110">補間モードを設定するには、メンバーのいずれかを割り当てる、<xref:System.Drawing.Drawing2D.InterpolationMode>列挙型を<xref:System.Drawing.Graphics.InterpolationMode%2A>のプロパティ、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e4210-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4210-111">例</span><span class="sxs-lookup"><span data-stu-id="e4210-111">Example</span></span>  
 <span data-ttu-id="e4210-112">次の例では、イメージを描画し、次の 3 つの異なる補間モードとイメージが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="e4210-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="e4210-113">次の図は、元のイメージと 3 つの小さいイメージを示します。</span><span class="sxs-lookup"><span data-stu-id="e4210-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 <span data-ttu-id="e4210-114">![さまざまな補間設定でイメージ](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span><span class="sxs-lookup"><span data-stu-id="e4210-114">![Image with Varied Interpolation Settings](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4210-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e4210-115">Compiling the Code</span></span>  
 <span data-ttu-id="e4210-116">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="e4210-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4210-117">参照</span><span class="sxs-lookup"><span data-stu-id="e4210-117">See Also</span></span>  
 [<span data-ttu-id="e4210-118">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="e4210-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="e4210-119">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="e4210-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
