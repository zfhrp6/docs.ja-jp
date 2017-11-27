---
title: "GDI+ でのメタファイル"
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
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b75ceb08df0454172a000d5d1ad15445f685ddf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="14a46-102">GDI+ でのメタファイル</span><span class="sxs-lookup"><span data-stu-id="14a46-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="14a46-103">提供、<xref:System.Drawing.Imaging.Metafile>クラスを記録してメタファイルを表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="14a46-103"> provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="14a46-104">ベクター イメージとも呼ばれる、メタファイルは、コマンドと設定の描画のシーケンスとして格納されているイメージです。</span><span class="sxs-lookup"><span data-stu-id="14a46-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="14a46-105">コマンドと設定に記録、<xref:System.Drawing.Imaging.Metafile>オブジェクトをメモリに格納されているか、ファイルまたはストリームに保存します。</span><span class="sxs-lookup"><span data-stu-id="14a46-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="14a46-106">メタファイルの形式</span><span class="sxs-lookup"><span data-stu-id="14a46-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="14a46-107">次の形式で格納されているメタファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="14a46-107"> can display metafiles that have been stored in the following formats:</span></span>  
  
-   <span data-ttu-id="14a46-108">Windows のメタファイル (WMF)</span><span class="sxs-lookup"><span data-stu-id="14a46-108">Windows Metafile (WMF)</span></span>  
  
-   <span data-ttu-id="14a46-109">拡張メタファイル (EMF)</span><span class="sxs-lookup"><span data-stu-id="14a46-109">Enhanced Metafile (EMF)</span></span>  
  
-   <span data-ttu-id="14a46-110">EMF +</span><span class="sxs-lookup"><span data-stu-id="14a46-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="14a46-111">WMF の形式ではなく、EMF と EMF + の形式で、メタファイルを記録できます。</span><span class="sxs-lookup"><span data-stu-id="14a46-111"> can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="14a46-112">EMF + は、拡張機能により、EMF[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]レコードが格納されます。</span><span class="sxs-lookup"><span data-stu-id="14a46-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="14a46-113">EMF + 形式に 2 つのバリエーションがあります: EMF + デュアルと EMF + のみです。</span><span class="sxs-lookup"><span data-stu-id="14a46-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="14a46-114">メタファイル EMF + だけのみを含める[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]レコード。</span><span class="sxs-lookup"><span data-stu-id="14a46-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="14a46-115">このようなメタファイルはによって表示されることができます[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]がなく、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="14a46-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="14a46-116">EMF + デュアル メタファイルを含む[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]レコード。</span><span class="sxs-lookup"><span data-stu-id="14a46-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="14a46-117">各[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]EMF + デュアルでレコード メタファイルとペアになる代替[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]レコード。</span><span class="sxs-lookup"><span data-stu-id="14a46-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="14a46-118">このようなメタファイルはによって表示されることができます[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]または[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="14a46-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="14a46-119">次の例では、ファイルとして保存されているメタファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="14a46-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="14a46-120">左上隅のメタファイルが表示されます (100, 100)。</span><span class="sxs-lookup"><span data-stu-id="14a46-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="14a46-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="14a46-121">See Also</span></span>  
 [<span data-ttu-id="14a46-122">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="14a46-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
