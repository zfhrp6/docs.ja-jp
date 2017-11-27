---
title: "GDI+ でのイメージのトリミングおよびスケーリング"
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
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63e1e55e57d586cbbca87361b95c18f0f53b8c75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="69b49-102">GDI+ でのイメージのトリミングおよびスケーリング</span><span class="sxs-lookup"><span data-stu-id="69b49-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="69b49-103">使用することができます、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>を描画して、ベクター イメージとラスター イメージを配置するクラス。</span><span class="sxs-lookup"><span data-stu-id="69b49-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="69b49-104"><xref:System.Drawing.Graphics.DrawImage%2A>引数を指定することがいくつかの方法があるため、オーバー ロードされたメソッドは、します。</span><span class="sxs-lookup"><span data-stu-id="69b49-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="69b49-105">DrawImage のバリエーション</span><span class="sxs-lookup"><span data-stu-id="69b49-105">DrawImage Variations</span></span>  
 <span data-ttu-id="69b49-106">1 つのバリエーション、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは受信、<xref:System.Drawing.Bitmap>と<xref:System.Drawing.Rectangle>です。</span><span class="sxs-lookup"><span data-stu-id="69b49-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="69b49-107">四角形を描画操作のシリアル化先を指定しますつまり、イメージを描画する四角形を指定します。</span><span class="sxs-lookup"><span data-stu-id="69b49-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="69b49-108">移行先の四角形のサイズが元のイメージのサイズと異なる場合は、イメージは移行先の四角形に合わせてスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="69b49-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="69b49-109">次のコード例は、3 回、同じイメージを描画する方法を示しています: スケーリングなしで、拡大、および、圧縮を使用します。</span><span class="sxs-lookup"><span data-stu-id="69b49-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="69b49-110">次の図は、3 つの画像を示します。</span><span class="sxs-lookup"><span data-stu-id="69b49-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="69b49-111">![スケーリング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="69b49-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="69b49-112">いくつかのバリエーション、<xref:System.Drawing.Graphics.DrawImage%2A>メソッドは、元の四角形のパラメーターだけでなく、移行先の四角形のパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="69b49-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="69b49-113">元の四角形のパラメーターは、描画する元のイメージの一部を指定します。</span><span class="sxs-lookup"><span data-stu-id="69b49-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="69b49-114">先の四角形は、イメージの部分を描画する四角形を指定します。</span><span class="sxs-lookup"><span data-stu-id="69b49-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="69b49-115">先の四角形のサイズが元の四角形のサイズと異なる場合は、画像は移行先の四角形に合わせてスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="69b49-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="69b49-116">次のコード例を作成する方法を示しています、 <xref:System.Drawing.Bitmap> Runner.jpg ファイルからです。</span><span class="sxs-lookup"><span data-stu-id="69b49-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="69b49-117">位置にスケーリングなしで画像全体が描画された (0, 0) です。</span><span class="sxs-lookup"><span data-stu-id="69b49-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="69b49-118">イメージの一部が 2 回描画し、: 圧縮が 1 回 1 回、および拡大します。</span><span class="sxs-lookup"><span data-stu-id="69b49-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="69b49-119">次の図は、スケールなしのイメージとイメージの圧縮および展開されている部分を示します。</span><span class="sxs-lookup"><span data-stu-id="69b49-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="69b49-120">![トリミングとスケーリング](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="69b49-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b49-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="69b49-121">See Also</span></span>  
 [<span data-ttu-id="69b49-122">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="69b49-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="69b49-123">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="69b49-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
