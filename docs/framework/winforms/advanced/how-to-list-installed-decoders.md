---
title: "方法 : インストールされたデコーダーの一覧"
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
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17cbdebfa6cbb0cacacd923de4bd22125c812938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="bb7f3-102">方法 : インストールされたデコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="bb7f3-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="bb7f3-103">アプリケーションが特定のイメージ ファイル形式を読み取るかどうかを決定するコンピューターでは、使用可能なイメージ デコーダーの一覧を表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="bb7f3-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="bb7f3-104"><xref:System.Drawing.Imaging.ImageCodecInfo>クラスを提供、<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>静的メソッドどのイメージ デコーダーが使用できるかを判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bb7f3-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="bb7f3-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>配列を返します<xref:System.Drawing.Imaging.ImageCodecInfo>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bb7f3-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb7f3-106">例</span><span class="sxs-lookup"><span data-stu-id="bb7f3-106">Example</span></span>  
 <span data-ttu-id="bb7f3-107">次のコード例では、インストールされているデコーダーの一覧とそのプロパティ値を出力します。</span><span class="sxs-lookup"><span data-stu-id="bb7f3-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb7f3-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bb7f3-108">Compiling the Code</span></span>  
 <span data-ttu-id="bb7f3-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bb7f3-109">This example requires:</span></span>  
  
-   <span data-ttu-id="bb7f3-110">Windows フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="bb7f3-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="bb7f3-111">A <xref:System.Windows.Forms.PaintEventArgs>、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="bb7f3-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb7f3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb7f3-112">See Also</span></span>  
 [<span data-ttu-id="bb7f3-113">方法: インストールされたエンコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="bb7f3-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="bb7f3-114">マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用</span><span class="sxs-lookup"><span data-stu-id="bb7f3-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
