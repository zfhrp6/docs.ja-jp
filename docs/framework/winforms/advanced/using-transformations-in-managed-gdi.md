---
title: "マネージ GDI+ での変換の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transformations
- examples [Windows Forms], transformations
ms.assetid: 1f8e18d3-d2f5-460e-a8e3-2da891c301de
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 07f10050d669e0de741e8aa1361a078928eebef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-transformations-in-managed-gdi"></a><span data-ttu-id="b64ff-102">マネージ GDI+ での変換の使用</span><span class="sxs-lookup"><span data-stu-id="b64ff-102">Using Transformations in Managed GDI+</span></span>
<span data-ttu-id="b64ff-103">アフィン変換には、回転、拡大/縮小、反転、傾斜、および翻訳が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b64ff-103">Affine transformations include rotating, scaling, reflecting, shearing, and translating.</span></span> <span data-ttu-id="b64ff-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、<xref:System.Drawing.Drawing2D.Matrix>クラスは、ベクター描画、イメージ、およびテキストのアフィン変換を実行するための基盤を提供します。</span><span class="sxs-lookup"><span data-stu-id="b64ff-104">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the <xref:System.Drawing.Drawing2D.Matrix> class provides the foundation for performing affine transformations on vector drawings, images, and text.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b64ff-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b64ff-105">In This Section</span></span>  
 [<span data-ttu-id="b64ff-106">ワールド変換の使用</span><span class="sxs-lookup"><span data-stu-id="b64ff-106">Using the World Transformation</span></span>](../../../../docs/framework/winforms/advanced/using-the-world-transformation.md)  
 <span data-ttu-id="b64ff-107">拡張、およびワールド変換行列を使用してグラフィックスを回転する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64ff-107">Describes how to scale and rotate graphics using a world transformation matrix.</span></span>  
  
 [<span data-ttu-id="b64ff-108">変換順序が重要となる理由</span><span class="sxs-lookup"><span data-stu-id="b64ff-108">Why Transformation Order Is Significant</span></span>](../../../../docs/framework/winforms/advanced/why-transformation-order-is-significant.md)  
 <span data-ttu-id="b64ff-109">変換操作の順序が重要な理由を示します。</span><span class="sxs-lookup"><span data-stu-id="b64ff-109">Demonstrates why the order of transform operations is important.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b64ff-110">参照</span><span class="sxs-lookup"><span data-stu-id="b64ff-110">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.Matrix>  
 <span data-ttu-id="b64ff-111">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b64ff-111">Describes this class and contains links to all of its members.</span></span>
