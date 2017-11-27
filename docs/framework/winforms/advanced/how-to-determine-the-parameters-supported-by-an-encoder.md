---
title: "方法 : エンコーダーがサポートするパラメーターの確認"
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
helpviewer_keywords: encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e041434e9ace24618dbdc45341a0e8468721c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="ac762-102">方法 : エンコーダーがサポートするパラメーターの確認</span><span class="sxs-lookup"><span data-stu-id="ac762-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="ac762-103">イメージなどのパラメーターの品質、および圧縮レベルを調整することができますが、どのパラメーターを指定したイメージ エンコーダーでサポートを特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac762-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="ac762-104"><xref:System.Drawing.Image>クラスを提供、<xref:System.Drawing.Image.GetEncoderParameterList%2A>メソッドどのイメージ パラメーターを特定のエンコーダーのサポートを確認できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ac762-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="ac762-105">エンコーダーを指定するには、GUID を持つ。</span><span class="sxs-lookup"><span data-stu-id="ac762-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="ac762-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A>メソッドの配列を返します<xref:System.Drawing.Imaging.EncoderParameter>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ac762-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac762-107">例</span><span class="sxs-lookup"><span data-stu-id="ac762-107">Example</span></span>  
 <span data-ttu-id="ac762-108">次のコード例では、JPEG エンコーダーでサポートされているパラメーターを出力します。</span><span class="sxs-lookup"><span data-stu-id="ac762-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="ac762-109">パラメーター カテゴリおよびに関連付けられている Guid のリストを使用して、<xref:System.Drawing.Imaging.Encoder>パラメーターごとにカテゴリを確認するクラスの概要です。</span><span class="sxs-lookup"><span data-stu-id="ac762-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac762-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ac762-110">Compiling the Code</span></span>  
 <span data-ttu-id="ac762-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ac762-111">This example requires:</span></span>  
  
-   <span data-ttu-id="ac762-112">Windows フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ac762-112">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="ac762-113">A <xref:System.Windows.Forms.PaintEventArgs>、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="ac762-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac762-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac762-114">See Also</span></span>  
 [<span data-ttu-id="ac762-115">方法: インストールされたエンコーダーの一覧</span><span class="sxs-lookup"><span data-stu-id="ac762-115">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="ac762-116">ビットマップの種類</span><span class="sxs-lookup"><span data-stu-id="ac762-116">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [<span data-ttu-id="ac762-117">マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用</span><span class="sxs-lookup"><span data-stu-id="ac762-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
