---
title: "方法 : イメージをトリミングおよびスケーリングする"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de905cf70013098a4282e3f4af092ccbea16ccfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="6ccbd-102">方法 : イメージをトリミングおよびスケーリングする</span><span class="sxs-lookup"><span data-stu-id="6ccbd-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="6ccbd-103"><xref:System.Drawing.Graphics>クラスには、いくつか用意されて<xref:System.Drawing.Graphics.DrawImage%2A>トリミングおよびスケール イメージに使用できる元とコピー先の四角形のパラメーターを持つこれらのいくつかの方法です。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ccbd-104">例</span><span class="sxs-lookup"><span data-stu-id="6ccbd-104">Example</span></span>  
 <span data-ttu-id="6ccbd-105">次の例の構築、 <xref:System.Drawing.Image> Apple.gif ディスク ファイルからのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="6ccbd-106">コードは、元のサイズでリンゴのイメージ全体を描画します。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="6ccbd-107">コードを呼び出し、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>が元の apple イメージよりも大きい先の四角形の apple のイメージの部分を描画するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="6ccbd-108"><xref:System.Drawing.Graphics.DrawImage%2A>メソッドが指定された、3 番目、4 番目に、元の四角形、5 番目と 6 番目の引数を確認して描画する apple のどの部分を決定します。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="6ccbd-109">この場合、幅の 75% を高さの 75%、apple がトリミングされます。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="6ccbd-110"><xref:System.Drawing.Graphics.DrawImage%2A>メソッドを調べ、トリミング apple を描画する場所を先の四角形を確認して、トリミングされた apple 大きさ、これは 2 番目の引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="6ccbd-111">この例では、先の四角形は、30% の幅と、元の画像を縦長の 30% です。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="6ccbd-112">次の図元の apple および、スケーリング apple をトリミングします。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 <span data-ttu-id="6ccbd-113">![トリミング & スケール](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span><span class="sxs-lookup"><span data-stu-id="6ccbd-113">![Crop & Scale](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6ccbd-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6ccbd-114">Compiling the Code</span></span>  
 <span data-ttu-id="6ccbd-115">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="6ccbd-116">必ず置き換えて`Apple.gif`イメージのファイル名と、システムで有効なパスを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ccbd-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ccbd-117">参照</span><span class="sxs-lookup"><span data-stu-id="6ccbd-117">See Also</span></span>  
 [<span data-ttu-id="6ccbd-118">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="6ccbd-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="6ccbd-119">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="6ccbd-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
