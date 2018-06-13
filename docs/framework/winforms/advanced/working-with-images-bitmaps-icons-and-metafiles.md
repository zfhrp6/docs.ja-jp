---
title: イメージ、ビットマップ、アイコン、およびメタファイルの操作
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
ms.openlocfilehash: 6d2f0a2f4acebaac59f2d8180f2de4ccb88b2965
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526836"
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="49b03-102">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="49b03-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="49b03-103"> は、ラスター イメージを操作するための `Bitmap` クラスと、ベクター イメージを操作するための `Metafile` クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="49b03-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="49b03-104">`Bitmap` クラスおよび `Metafile` クラスは、どちらも `Image` クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="49b03-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49b03-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="49b03-105">In This Section</span></span>  
 [<span data-ttu-id="49b03-106">方法: 既存のビットマップを画面に描画する</span><span class="sxs-lookup"><span data-stu-id="49b03-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="49b03-107">ビットマップを読み込んで描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49b03-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="49b03-108">方法: メタファイルを読み込んで表示する</span><span class="sxs-lookup"><span data-stu-id="49b03-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="49b03-109">メタファイルを読み込んで描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49b03-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="49b03-110">GDI+ でのイメージのトリミングおよびスケーリング</span><span class="sxs-lookup"><span data-stu-id="49b03-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="49b03-111">ベクター イメージおよびラスター イメージをトリミングしてスケールを調整する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49b03-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="49b03-112">方法: イメージを回転、反転、および傾斜させる</span><span class="sxs-lookup"><span data-stu-id="49b03-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="49b03-113">回転、反転、および傾斜したイメージを描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49b03-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="49b03-114">方法: 補間モードを使用してスケーリング時の画質を制御する</span><span class="sxs-lookup"><span data-stu-id="49b03-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="49b03-115"><xref:System.Drawing.Drawing2D.InterpolationMode> 列挙体を使用してイメージ品質を変更する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="49b03-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="49b03-116">方法: サムネイル イメージを作成する</span><span class="sxs-lookup"><span data-stu-id="49b03-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="49b03-117">サムネイル イメージを作成する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="49b03-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="49b03-118">方法: 自動スケーリングを解除してパフォーマンスを向上させる</span><span class="sxs-lookup"><span data-stu-id="49b03-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="49b03-119">自動スケーリングなしでイメージを描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49b03-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="49b03-120">方法: イメージ メタデータを読み取る</span><span class="sxs-lookup"><span data-stu-id="49b03-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="49b03-121">イメージからメタデータを読み取る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49b03-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="49b03-122">方法: 実行時にビットマップを作成する</span><span class="sxs-lookup"><span data-stu-id="49b03-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="49b03-123">実行時にビットマップを描画する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="49b03-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="49b03-124">方法: Windows フォームでファイルに関連付けられているアイコンを抽出する</span><span class="sxs-lookup"><span data-stu-id="49b03-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="49b03-125">ファイルの埋め込みリソースであるアイコンを抽出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49b03-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="49b03-126">参照</span><span class="sxs-lookup"><span data-stu-id="49b03-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="49b03-127">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="49b03-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="49b03-128">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="49b03-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="49b03-129">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="49b03-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49b03-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="49b03-130">Related Sections</span></span>  
 [<span data-ttu-id="49b03-131">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="49b03-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="49b03-132">さまざまな種類のビットマップと、アプリケーションでこれらを操作する方法について説明するトピックへのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="49b03-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
