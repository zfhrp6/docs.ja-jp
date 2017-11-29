---
title: "ワールド変換の使用"
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
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5b2a8de0644e71a5e6ae1a5ca796f580f0c4f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="fd57a-102">ワールド変換の使用</span><span class="sxs-lookup"><span data-stu-id="fd57a-102">Using the World Transformation</span></span>
<span data-ttu-id="fd57a-103">ワールド変換のプロパティは、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="fd57a-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="fd57a-104">ワールド変換を指定する数値に格納されている、 <xref:System.Drawing.Drawing2D.Matrix> 3 × 3 行列を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fd57a-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="fd57a-105"><xref:System.Drawing.Drawing2D.Matrix>と<xref:System.Drawing.Graphics>クラス ワールド変換行列の数値を設定するためのいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="fd57a-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="fd57a-106">異なる種類の変換</span><span class="sxs-lookup"><span data-stu-id="fd57a-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="fd57a-107">次の例では、コードはまず 50 × 50 四角形を作成し、原点 (0, 0) を検索します。</span><span class="sxs-lookup"><span data-stu-id="fd57a-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="fd57a-108">原点は、クライアント領域の左上隅にあること。</span><span class="sxs-lookup"><span data-stu-id="fd57a-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="fd57a-109">次のコードを 1.75 x 軸方向の四角形を拡張し、y 軸方向 0.5 の四角形を縮小する拡大縮小変換が適用されます。</span><span class="sxs-lookup"><span data-stu-id="fd57a-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="fd57a-110">X 方向に長いと、元のより短い y 方向の四角形になります。</span><span class="sxs-lookup"><span data-stu-id="fd57a-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="fd57a-111">スケーリングすることではなく四角形を回転するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd57a-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="fd57a-112">四角形を変換するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd57a-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="fd57a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd57a-113">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [<span data-ttu-id="fd57a-114">座標系と変換</span><span class="sxs-lookup"><span data-stu-id="fd57a-114">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="fd57a-115">マネージ GDI+ での変換の使用</span><span class="sxs-lookup"><span data-stu-id="fd57a-115">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
