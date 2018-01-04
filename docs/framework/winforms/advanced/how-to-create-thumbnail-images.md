---
title: "方法 : サムネイル イメージを作成する"
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
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8eeb856fabd895e171c0ad8739ae6a63b5c7065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="c1a92-102">方法 : サムネイル イメージを作成する</span><span class="sxs-lookup"><span data-stu-id="c1a92-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="c1a92-103">サムネイル イメージとは、画像の縮小版です。</span><span class="sxs-lookup"><span data-stu-id="c1a92-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="c1a92-104">サムネイル イメージを作成するには呼び出すことによって、<xref:System.Drawing.Image.GetThumbnailImage%2A>のメソッド、<xref:System.Drawing.Image>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c1a92-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1a92-105">例</span><span class="sxs-lookup"><span data-stu-id="c1a92-105">Example</span></span>  
 <span data-ttu-id="c1a92-106">次の例の構築、 <xref:System.Drawing.Image> JPG ファイルからオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c1a92-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="c1a92-107">元のイメージは、640 ピクセル幅および 479 ピクセルの高さを持ちます。</span><span class="sxs-lookup"><span data-stu-id="c1a92-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="c1a92-108">コードでは、100 ピクセルの幅と高さ 100 ピクセルを持つサムネイル イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1a92-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="c1a92-109">次の図は、サムネイル画像を示します。</span><span class="sxs-lookup"><span data-stu-id="c1a92-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="c1a92-110">![サムネイル画像](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="c1a92-110">![Thumbnail Image](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1a92-111">この例では、コールバック メソッドは宣言されている、使用されていません。</span><span class="sxs-lookup"><span data-stu-id="c1a92-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="c1a92-112">これには、GDI + のすべてのバージョンがサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c1a92-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1a92-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c1a92-113">Compiling the Code</span></span>  
 <span data-ttu-id="c1a92-114">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="c1a92-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="c1a92-115">例を実行するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c1a92-115">To run the example, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c1a92-116">新しい Windows フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1a92-116">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="c1a92-117">例のコードをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="c1a92-117">Add the example code to the form.</span></span>  
  
3.  <span data-ttu-id="c1a92-118">フォームのハンドラーを作成<xref:System.Windows.Forms.Control.Paint>イベント</span><span class="sxs-lookup"><span data-stu-id="c1a92-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4.  <span data-ttu-id="c1a92-119"><xref:System.Windows.Forms.Control.Paint>ハンドラーを呼び出し、`GetThumbnail`メソッドを渡します`e`の<xref:System.Windows.Forms.PaintEventArgs>します。</span><span class="sxs-lookup"><span data-stu-id="c1a92-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5.  <span data-ttu-id="c1a92-120">サムネイルを作成するイメージ ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="c1a92-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6.  <span data-ttu-id="c1a92-121">`GetThumbnail`メソッドは、パスを指定し、ファイルをイメージ名。</span><span class="sxs-lookup"><span data-stu-id="c1a92-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7.  <span data-ttu-id="c1a92-122">F5 キーを押して、例を実行します。</span><span class="sxs-lookup"><span data-stu-id="c1a92-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="c1a92-123">100 × 100 のサムネイル画像は、フォームに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1a92-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a92-124">参照</span><span class="sxs-lookup"><span data-stu-id="c1a92-124">See Also</span></span>  
 [<span data-ttu-id="c1a92-125">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="c1a92-125">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="c1a92-126">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="c1a92-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
