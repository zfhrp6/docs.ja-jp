---
title: イメージ、ビットマップ、およびメタファイル
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
ms.openlocfilehash: 30887cd88bc8c08c78eb37c4fe8591ac528e6f01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="f4a01-102">イメージ、ビットマップ、およびメタファイル</span><span class="sxs-lookup"><span data-stu-id="f4a01-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="f4a01-103">`Image` クラスはラスター イメージ (ビットマップ) およびベクター イメージ (メタファイル) を操作するためのメソッドを提供する抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="f4a01-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="f4a01-104">`Bitmap` クラスおよび <xref:System.Drawing.Imaging.Metafile> クラスは、どちらも `Image` クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="f4a01-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="f4a01-105">`Bitmap` クラスは、ラスター イメージの読み込み、保存、および操作のための追加のメソッドを提供することで、`Image` クラスの機能を展開します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="f4a01-106"><xref:System.Drawing.Imaging.Metafile> クラスは、ベクター イメージの記録および検証のための追加のメソッドを提供することで、`Image` クラスの機能を展開します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4a01-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f4a01-107">In This Section</span></span>  
 [<span data-ttu-id="f4a01-108">ビットマップの種類</span><span class="sxs-lookup"><span data-stu-id="f4a01-108">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 <span data-ttu-id="f4a01-109">さまざまなイメージ形式について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="f4a01-110">GDI+ でのメタファイル</span><span class="sxs-lookup"><span data-stu-id="f4a01-110">Metafiles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/metafiles-in-gdi.md)  
 <span data-ttu-id="f4a01-111">メタファイルの [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="f4a01-112">GDI+ でのイメージの描画、配置、およびクローン作成</span><span class="sxs-lookup"><span data-stu-id="f4a01-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="f4a01-113">マネージ コードを使用して、ベクター イメージとラスター イメージを描画するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="f4a01-114">GDI+ でのイメージのトリミングおよびスケーリング</span><span class="sxs-lookup"><span data-stu-id="f4a01-114">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="f4a01-115">マネージ コードを使用して、ベクター イメージとラスター イメージのトリミングとスケーリングのためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f4a01-116">参照</span><span class="sxs-lookup"><span data-stu-id="f4a01-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="f4a01-117">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="f4a01-118">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f4a01-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f4a01-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4a01-119">Related Sections</span></span>  
 [<span data-ttu-id="f4a01-120">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="f4a01-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="f4a01-121">アプリケーションでイメージを使用する方法を説明するトピックへのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f4a01-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
