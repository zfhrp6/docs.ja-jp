---
title: マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524502"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="50e54-102">マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用</span><span class="sxs-lookup"><span data-stu-id="50e54-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="50e54-103"><xref:System.Drawing>名前空間には、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>を格納して、画像を操作するためのクラスです。</span><span class="sxs-lookup"><span data-stu-id="50e54-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="50e54-104">イメージ エンコーダーを使用して、 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、メモリからディスク イメージを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="50e54-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="50e54-105">イメージのデコーダーを使用して、 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、ディスクからイメージをメモリに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="50e54-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="50e54-106">内のデータを変換するエンコーダー、<xref:System.Drawing.Image>または<xref:System.Drawing.Bitmap>オブジェクト、指定されたディスク ファイル形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="50e54-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="50e54-107">必要な形式にディスク ファイル内のデータを変換するデコーダー、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="50e54-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="50e54-108"> 組み込みエンコーダーとデコーダー ファイルの種類をサポートするにがあります。</span><span class="sxs-lookup"><span data-stu-id="50e54-108"> has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="50e54-109">BMP</span><span class="sxs-lookup"><span data-stu-id="50e54-109">BMP</span></span>  
  
-   <span data-ttu-id="50e54-110">GIF</span><span class="sxs-lookup"><span data-stu-id="50e54-110">GIF</span></span>  
  
-   <span data-ttu-id="50e54-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="50e54-111">JPEG</span></span>  
  
-   <span data-ttu-id="50e54-112">PNG</span><span class="sxs-lookup"><span data-stu-id="50e54-112">PNG</span></span>  
  
-   <span data-ttu-id="50e54-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="50e54-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="50e54-114"> 次のファイルの種類をサポートする組み込みのデコーダーがあります。</span><span class="sxs-lookup"><span data-stu-id="50e54-114"> also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="50e54-115">WMF</span><span class="sxs-lookup"><span data-stu-id="50e54-115">WMF</span></span>  
  
-   <span data-ttu-id="50e54-116">EMF</span><span class="sxs-lookup"><span data-stu-id="50e54-116">EMF</span></span>  
  
-   <span data-ttu-id="50e54-117">アイコン</span><span class="sxs-lookup"><span data-stu-id="50e54-117">ICON</span></span>  
  
 <span data-ttu-id="50e54-118">次のトピックでは、エンコーダーとデコーダーの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="50e54-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50e54-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="50e54-119">In This Section</span></span>  
 [<span data-ttu-id="50e54-120">方法: インストールされたエンコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="50e54-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="50e54-121">コンピューターで使用可能なエンコーダーの一覧を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50e54-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="50e54-122">方法: インストールされたデコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="50e54-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="50e54-123">コンピューターで使用できるデコーダーの一覧を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50e54-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="50e54-124">方法: エンコーダーがサポートするパラメーターの確認</span><span class="sxs-lookup"><span data-stu-id="50e54-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="50e54-125">一覧表示する方法について説明します、<xref:System.Drawing.Imaging.EncoderParameters>エンコーダーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="50e54-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="50e54-126">方法: BMP イメージから PNG イメージへの変換</span><span class="sxs-lookup"><span data-stu-id="50e54-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="50e54-127">さまざまなイメージ形式で、イメージを保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50e54-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="50e54-128">方法: JPEG 圧縮レベルの設定</span><span class="sxs-lookup"><span data-stu-id="50e54-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="50e54-129">イメージの品質レベルを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50e54-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="50e54-130">参照</span><span class="sxs-lookup"><span data-stu-id="50e54-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="50e54-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="50e54-131">Related Sections</span></span>  
 [<span data-ttu-id="50e54-132">GDI+ マネージ コードについて</span><span class="sxs-lookup"><span data-stu-id="50e54-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="50e54-133">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="50e54-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
