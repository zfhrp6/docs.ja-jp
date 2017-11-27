---
title: "方法 : インストールされたエンコーダーの一覧"
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
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70f913acb2620b5c01e1aec1f1eb98b041b82a59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="93d0a-102">方法 : インストールされたエンコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="93d0a-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="93d0a-103">アプリケーションが特定のイメージ ファイル形式に保存できるかどうかを確認するコンピューターでは、使用可能なイメージ エンコーダーの一覧を表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="93d0a-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="93d0a-104"><xref:System.Drawing.Imaging.ImageCodecInfo>クラスを提供、<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>静的メソッドどのイメージ エンコーダーが使用できるかを判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="93d0a-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="93d0a-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>配列を返します<xref:System.Drawing.Imaging.ImageCodecInfo>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="93d0a-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93d0a-106">例</span><span class="sxs-lookup"><span data-stu-id="93d0a-106">Example</span></span>  
 <span data-ttu-id="93d0a-107">次のコード例では、インストールされているエンコーダーの一覧とそのプロパティ値を出力します。</span><span class="sxs-lookup"><span data-stu-id="93d0a-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93d0a-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="93d0a-108">Compiling the Code</span></span>  
 <span data-ttu-id="93d0a-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="93d0a-109">This example requires:</span></span>  
  
-   <span data-ttu-id="93d0a-110">Windows フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="93d0a-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="93d0a-111">A <xref:System.Windows.Forms.PaintEventArgs>、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="93d0a-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d0a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="93d0a-112">See Also</span></span>  
 [<span data-ttu-id="93d0a-113">方法: インストールされたデコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="93d0a-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="93d0a-114">マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用</span><span class="sxs-lookup"><span data-stu-id="93d0a-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
