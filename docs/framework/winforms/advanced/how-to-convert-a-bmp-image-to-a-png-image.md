---
title: "方法 : BMP イメージから PNG イメージへの変換"
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
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 542dd132ece543b6a53a9e6d867b49fce4d15a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="c7980-102">方法 : BMP イメージから PNG イメージへの変換</span><span class="sxs-lookup"><span data-stu-id="c7980-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="c7980-103">多くの場合、1 つのイメージ ファイル形式から別の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="c7980-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="c7980-104">この変換は、<xref:System.Drawing.Image> クラスの <xref:System.Drawing.Image.Save%2A> のメソッドを呼び出して、必要なイメージ ファイル形式に対して <xref:System.Drawing.Imaging.ImageFormat> を指定することで簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="c7980-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7980-105">例</span><span class="sxs-lookup"><span data-stu-id="c7980-105">Example</span></span>  
 <span data-ttu-id="c7980-106">次の例では、型から BMP イメージを読み込み、PNG 形式で画像を保存します。</span><span class="sxs-lookup"><span data-stu-id="c7980-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7980-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c7980-107">Compiling the Code</span></span>  
 <span data-ttu-id="c7980-108">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c7980-108">This example requires:</span></span>  
  
-   <span data-ttu-id="c7980-109">Windows フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c7980-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="c7980-110">`System.Drawing.Imaging` 名前空間への参照</span><span class="sxs-lookup"><span data-stu-id="c7980-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7980-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7980-111">See Also</span></span>  
 [<span data-ttu-id="c7980-112">方法: インストールされたエンコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="c7980-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="c7980-113">マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用</span><span class="sxs-lookup"><span data-stu-id="c7980-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [<span data-ttu-id="c7980-114">ビットマップの種類</span><span class="sxs-lookup"><span data-stu-id="c7980-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
