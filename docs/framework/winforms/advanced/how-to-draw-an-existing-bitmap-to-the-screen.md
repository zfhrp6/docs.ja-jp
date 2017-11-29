---
title: "方法: 既存のビットマップを画面に描画する"
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
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f435c397832e8f64b2bf911a59aae7578ffd3bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="c36cc-102">方法: 既存のビットマップを画面に描画する</span><span class="sxs-lookup"><span data-stu-id="c36cc-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="c36cc-103">画面で、既存のイメージを簡単に描画できます。</span><span class="sxs-lookup"><span data-stu-id="c36cc-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="c36cc-104">最初に作成する必要があります、<xref:System.Drawing.Bitmap>オブジェクトは、ファイル名を受け取り、ビットマップ コンス トラクターを使用して<xref:System.Drawing.Bitmap.%23ctor%28System.String%29>です。</span><span class="sxs-lookup"><span data-stu-id="c36cc-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="c36cc-105">このコンス トラクターは、BMP、GIF、JPEG、PNG、TIFF を含め、いくつかの異なるファイル形式で画像を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c36cc-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="c36cc-106">作成した後、<xref:System.Drawing.Bitmap>オブジェクトを渡す<xref:System.Drawing.Bitmap>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c36cc-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c36cc-107">例</span><span class="sxs-lookup"><span data-stu-id="c36cc-107">Example</span></span>  
 <span data-ttu-id="c36cc-108">この例で作成、 <xref:System.Drawing.Bitmap> JPEG ファイルからオブジェクトで、左上隅のビットマップを描画と (60, 10)。</span><span class="sxs-lookup"><span data-stu-id="c36cc-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="c36cc-109">次の図は、指定した位置に描画されるビットマップを示します。</span><span class="sxs-lookup"><span data-stu-id="c36cc-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="c36cc-110">![画像の位置](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="c36cc-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c36cc-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c36cc-111">Compiling the Code</span></span>  
 <span data-ttu-id="c36cc-112">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="c36cc-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36cc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c36cc-113">See Also</span></span>  
 [<span data-ttu-id="c36cc-114">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="c36cc-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="c36cc-115">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="c36cc-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
