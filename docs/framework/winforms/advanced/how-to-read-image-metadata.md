---
title: "方法 : イメージ メタデータを読み取る"
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
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9df2866251e08b8989f8550d045b587c9de8d2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="a6681-102">方法 : イメージ メタデータを読み取る</span><span class="sxs-lookup"><span data-stu-id="a6681-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="a6681-103">一部のイメージ ファイルには、イメージの機能を決定するために読み取ることができますメタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6681-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="a6681-104">たとえば、デジタル写真には、make とイメージをキャプチャするために使用する、カメラのモデルを決定するために読み取ることができますメタデータが含まれます可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6681-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="a6681-105">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]既存のメタデータを読み取ることができます、およびイメージ ファイルに新しいメタデータを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="a6681-105">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a6681-106">内のメタデータの個々 の部分を格納、<xref:System.Drawing.Imaging.PropertyItem>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a6681-106"> stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="a6681-107">読み取ることができます、<xref:System.Drawing.Image.PropertyItems%2A>のプロパティ、<xref:System.Drawing.Image>ファイルからすべてのメタデータを取得するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a6681-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="a6681-108"><xref:System.Drawing.Image.PropertyItems%2A>プロパティの配列を返します<xref:System.Drawing.Imaging.PropertyItem>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a6681-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="a6681-109">A<xref:System.Drawing.Imaging.PropertyItem>オブジェクトには次の 4 つのプロパティ: `Id`、 `Value`、 `Len`、および`Type`です。</span><span class="sxs-lookup"><span data-stu-id="a6681-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="a6681-110">ID</span><span class="sxs-lookup"><span data-stu-id="a6681-110">Id</span></span>  
 <span data-ttu-id="a6681-111">メタデータ アイテムを識別するタグです。</span><span class="sxs-lookup"><span data-stu-id="a6681-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="a6681-112">いくつかの値を割り当てることのできる<xref:System.Drawing.Imaging.PropertyItem.Id%2A>次の表に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6681-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="a6681-113">16 進値</span><span class="sxs-lookup"><span data-stu-id="a6681-113">Hexadecimal value</span></span>|<span data-ttu-id="a6681-114">説明</span><span class="sxs-lookup"><span data-stu-id="a6681-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="a6681-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="a6681-115">0x0320</span></span><br /><br /> <span data-ttu-id="a6681-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="a6681-116">0x010F</span></span><br /><br /> <span data-ttu-id="a6681-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="a6681-117">0x0110</span></span><br /><br /> <span data-ttu-id="a6681-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="a6681-118">0x9003</span></span><br /><br /> <span data-ttu-id="a6681-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="a6681-119">0x829A</span></span><br /><br /> <span data-ttu-id="a6681-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="a6681-120">0x5090</span></span><br /><br /> <span data-ttu-id="a6681-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="a6681-121">0x5091</span></span>|<span data-ttu-id="a6681-122">イメージのタイトル</span><span class="sxs-lookup"><span data-stu-id="a6681-122">Image title</span></span><br /><br /> <span data-ttu-id="a6681-123">相手先ブランド供給</span><span class="sxs-lookup"><span data-stu-id="a6681-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="a6681-124">機器のモデル</span><span class="sxs-lookup"><span data-stu-id="a6681-124">Equipment model</span></span><br /><br /> <span data-ttu-id="a6681-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="a6681-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="a6681-126">Exif 露出時間</span><span class="sxs-lookup"><span data-stu-id="a6681-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="a6681-127">輝度テーブル</span><span class="sxs-lookup"><span data-stu-id="a6681-127">Luminance table</span></span><br /><br /> <span data-ttu-id="a6681-128">色光度テーブル</span><span class="sxs-lookup"><span data-stu-id="a6681-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="a6681-129">値</span><span class="sxs-lookup"><span data-stu-id="a6681-129">Value</span></span>  
 <span data-ttu-id="a6681-130">値の配列。</span><span class="sxs-lookup"><span data-stu-id="a6681-130">An array of values.</span></span> <span data-ttu-id="a6681-131">値の形式はによって決まります、<xref:System.Drawing.Imaging.PropertyItem.Type%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a6681-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="a6681-132">Len</span><span class="sxs-lookup"><span data-stu-id="a6681-132">Len</span></span>  
 <span data-ttu-id="a6681-133">値の配列の長さ (バイト) を指す、<xref:System.Drawing.Imaging.PropertyItem.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a6681-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="a6681-134">型</span><span class="sxs-lookup"><span data-stu-id="a6681-134">Type</span></span>  
 <span data-ttu-id="a6681-135">配列内の値のデータ型を指す、`Value`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a6681-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="a6681-136">によって示される形式、`Type`プロパティの値は次の表に表示されます</span><span class="sxs-lookup"><span data-stu-id="a6681-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="a6681-137">数値の値</span><span class="sxs-lookup"><span data-stu-id="a6681-137">Numeric value</span></span>|<span data-ttu-id="a6681-138">説明</span><span class="sxs-lookup"><span data-stu-id="a6681-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="a6681-139">1</span><span class="sxs-lookup"><span data-stu-id="a6681-139">1</span></span>|<span data-ttu-id="a6681-140">`Byte`。</span><span class="sxs-lookup"><span data-stu-id="a6681-140">A `Byte`</span></span>|  
|<span data-ttu-id="a6681-141">2</span><span class="sxs-lookup"><span data-stu-id="a6681-141">2</span></span>|<span data-ttu-id="a6681-142">配列`Byte`ascii 形式でエンコードされたオブジェクト</span><span class="sxs-lookup"><span data-stu-id="a6681-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="a6681-143">3</span><span class="sxs-lookup"><span data-stu-id="a6681-143">3</span></span>|<span data-ttu-id="a6681-144">16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="a6681-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="a6681-145">4</span><span class="sxs-lookup"><span data-stu-id="a6681-145">4</span></span>|<span data-ttu-id="a6681-146">32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="a6681-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="a6681-147">5</span><span class="sxs-lookup"><span data-stu-id="a6681-147">5</span></span>|<span data-ttu-id="a6681-148">2 つの配列`Byte`有理数を表すオブジェクト</span><span class="sxs-lookup"><span data-stu-id="a6681-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="a6681-149">6</span><span class="sxs-lookup"><span data-stu-id="a6681-149">6</span></span>|<span data-ttu-id="a6681-150">未使用</span><span class="sxs-lookup"><span data-stu-id="a6681-150">Not used</span></span>|  
|<span data-ttu-id="a6681-151">7</span><span class="sxs-lookup"><span data-stu-id="a6681-151">7</span></span>|<span data-ttu-id="a6681-152">未定義</span><span class="sxs-lookup"><span data-stu-id="a6681-152">Undefined</span></span>|  
|<span data-ttu-id="a6681-153">9</span><span class="sxs-lookup"><span data-stu-id="a6681-153">8</span></span>|<span data-ttu-id="a6681-154">未使用</span><span class="sxs-lookup"><span data-stu-id="a6681-154">Not used</span></span>|  
|<span data-ttu-id="a6681-155">9</span><span class="sxs-lookup"><span data-stu-id="a6681-155">9</span></span>|`SLong`|  
|<span data-ttu-id="a6681-156">10</span><span class="sxs-lookup"><span data-stu-id="a6681-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="a6681-157">例</span><span class="sxs-lookup"><span data-stu-id="a6681-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a6681-158">説明</span><span class="sxs-lookup"><span data-stu-id="a6681-158">Description</span></span>  
 <span data-ttu-id="a6681-159">次のコード例を読み取ったり、ファイルのメタデータの 7 つの部分を表示`FakePhoto.jpg`です。</span><span class="sxs-lookup"><span data-stu-id="a6681-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="a6681-160">リストの 2 つ目 (インデックス 1) プロパティ項目が<xref:System.Drawing.Imaging.PropertyItem.Id%2A>0x010F (供給) および<xref:System.Drawing.Imaging.PropertyItem.Type%2A>2 (ASCII エンコードのバイト配列)。</span><span class="sxs-lookup"><span data-stu-id="a6681-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="a6681-161">コード例では、そのプロパティ項目の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6681-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="a6681-162">コードには、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6681-162">The code produces output similar to the following:</span></span>  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a><span data-ttu-id="a6681-163">コード</span><span class="sxs-lookup"><span data-stu-id="a6681-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6681-164">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a6681-164">Compiling the Code</span></span>  
 <span data-ttu-id="a6681-165">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="a6681-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="a6681-166">フォームの処理<xref:System.Windows.Forms.Control.Paint>イベントとペイントのイベント ハンドラーに次のコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a6681-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="a6681-167">置き換える必要があります`FakePhoto.jpg`イメージの名前と、システムとインポートの有効なパスと、`System.Drawing.Imaging`名前空間。</span><span class="sxs-lookup"><span data-stu-id="a6681-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6681-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6681-168">See Also</span></span>  
 [<span data-ttu-id="a6681-169">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="a6681-169">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="a6681-170">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="a6681-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
