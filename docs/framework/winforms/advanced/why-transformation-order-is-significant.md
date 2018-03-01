---
title: "変換順序が重要となる理由"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd3363a1afb8658ed3bb27359259cb752464507d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="why-transformation-order-is-significant"></a><span data-ttu-id="82ba9-102">変換順序が重要となる理由</span><span class="sxs-lookup"><span data-stu-id="82ba9-102">Why Transformation Order Is Significant</span></span>
<span data-ttu-id="82ba9-103">1 つ<xref:System.Drawing.Drawing2D.Matrix>オブジェクトは、単一の変換または変換のシーケンスを格納できます。</span><span class="sxs-lookup"><span data-stu-id="82ba9-103">A single <xref:System.Drawing.Drawing2D.Matrix> object can store a single transformation or a sequence of transformations.</span></span> <span data-ttu-id="82ba9-104">後者を複合変換と呼びます。</span><span class="sxs-lookup"><span data-stu-id="82ba9-104">The latter is called a composite transformation.</span></span> <span data-ttu-id="82ba9-105">複合変換のマトリックスは、個々 の変換行列を乗算することによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="82ba9-105">The matrix of a composite transformation is obtained by multiplying the matrices of individual transformations.</span></span>  
  
## <a name="composite-transform-examples"></a><span data-ttu-id="82ba9-106">複合変換の例</span><span class="sxs-lookup"><span data-stu-id="82ba9-106">Composite Transform Examples</span></span>  
 <span data-ttu-id="82ba9-107">複合変換では、個々 の変換の順序が重要です。</span><span class="sxs-lookup"><span data-stu-id="82ba9-107">In a composite transformation, the order of individual transformations is important.</span></span> <span data-ttu-id="82ba9-108">など、回転、まずしてから、スケール、変換、最初に変換する場合、回転し、スケールよりも異なる結果が得です。</span><span class="sxs-lookup"><span data-stu-id="82ba9-108">For example, if you first rotate, then scale, then translate, you get a different result than if you first translate, then rotate, then scale.</span></span> <span data-ttu-id="82ba9-109">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、複合変換は、左から右に構築されます。</span><span class="sxs-lookup"><span data-stu-id="82ba9-109">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], composite transformations are built from left to right.</span></span> <span data-ttu-id="82ba9-110">S、R、T は、スケール、回転、および平行移動行列をそれぞれが場合、し、製品 (その順序で) SRT 複合変換のマトリックスを最初にスケーリングは回転し、変換します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-110">If S, R, and T are scale, rotation, and translation matrices respectively, then the product SRT (in that order) is the matrix of the composite transformation that first scales, then rotates, then translates.</span></span> <span data-ttu-id="82ba9-111">製品によって生成されるマトリックス SRT は、製品 TRS によって生成されるマトリックスと異なります。</span><span class="sxs-lookup"><span data-stu-id="82ba9-111">The matrix produced by the product SRT is different from the matrix produced by the product TRS.</span></span>  
  
 <span data-ttu-id="82ba9-112">順序は重要な理由の 1 つは、座標系の原点を基準の回転とスケーリングのような変換を行うことです。</span><span class="sxs-lookup"><span data-stu-id="82ba9-112">One reason order is significant is that transformations like rotation and scaling are done with respect to the origin of the coordinate system.</span></span> <span data-ttu-id="82ba9-113">原点を中心とするオブジェクトをスケーリングすると、原点から離れているオブジェクトをスケーリング異なる結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="82ba9-113">Scaling an object that is centered at the origin produces a different result than scaling an object that has been moved away from the origin.</span></span> <span data-ttu-id="82ba9-114">同様に、原点を中心とするオブジェクトを回転させるには、原点から離れているオブジェクトを回転異なる結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="82ba9-114">Similarly, rotating an object that is centered at the origin produces a different result than rotating an object that has been moved away from the origin.</span></span>  
  
 <span data-ttu-id="82ba9-115">次の例では、複合変換を拡大/縮小、回転、およびその順序で翻訳を結合します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-115">The following example combines scaling, rotation and translation (in that order) to form a composite transformation.</span></span> <span data-ttu-id="82ba9-116">引数<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に渡される、<xref:System.Drawing.Graphics.RotateTransform%2A>メソッドでは、拡大/縮小、回転を従うことを示します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-116">The argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passed to the <xref:System.Drawing.Graphics.RotateTransform%2A> method indicates that the rotation will follow the scaling.</span></span> <span data-ttu-id="82ba9-117">同様に、引数<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に渡される、<xref:System.Drawing.Graphics.TranslateTransform%2A>メソッドは、翻訳は、回転に従うことを示します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-117">Likewise, the argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passed to the <xref:System.Drawing.Graphics.TranslateTransform%2A> method indicates that the translation will follow the rotation.</span></span> <span data-ttu-id="82ba9-118"><xref:System.Drawing.Drawing2D.MatrixOrder.Append>および<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>のメンバーである、<xref:System.Drawing.Drawing2D.MatrixOrder>列挙します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-118"><xref:System.Drawing.Drawing2D.MatrixOrder.Append> and <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> are members of the <xref:System.Drawing.Drawing2D.MatrixOrder> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 <span data-ttu-id="82ba9-119">次の例で、前の例と同じメソッドを呼び出してが、呼び出しの順序を反転します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-119">The following example makes the same method calls as the preceding example, but the order of the calls is reversed.</span></span> <span data-ttu-id="82ba9-120">操作の結果として得られる順序が最初に平行移動、回転、最初の小数点以下桁数よりも大幅に異なる結果を生成するには、小数点以下桁数を回転させて、し、変換します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-120">The resulting order of operations is first translate, then rotate, then scale, which produces a very different result than first scale, then rotate, then translate.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 <span data-ttu-id="82ba9-121">複合変換の個々 の変換の順序を反転させる 1 つの方法は、一連のメソッド呼び出しの順序を逆です。</span><span class="sxs-lookup"><span data-stu-id="82ba9-121">One way to reverse the order of individual transformations in a composite transformation is to reverse the order of a sequence of method calls.</span></span> <span data-ttu-id="82ba9-122">操作の順序を制御する 2 番目の方法では、マトリックスの order 引数を変更します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-122">A second way to control the order of operations is to change the matrix order argument.</span></span> <span data-ttu-id="82ba9-123">次の例は、点を除いて、上記の例と同じ<xref:System.Drawing.Drawing2D.MatrixOrder.Append>に変わりました<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>です。</span><span class="sxs-lookup"><span data-stu-id="82ba9-123">The following example is the same as the preceding example, except that <xref:System.Drawing.Drawing2D.MatrixOrder.Append> has been changed to <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>.</span></span> <span data-ttu-id="82ba9-124">SRT、S、R、T があるスケールのマトリックスの順序では、行列乗算を実行してください。、回転、および翻訳に、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="82ba9-124">The matrix multiplication is done in the order SRT, where S, R, and T are the matrices for scale, rotate, and translate, respectively.</span></span> <span data-ttu-id="82ba9-125">複合変換の順序は最初の小数点以下桁数、回転、変換します。</span><span class="sxs-lookup"><span data-stu-id="82ba9-125">The order of the composite transformation is first scale, then rotate, then translate.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 <span data-ttu-id="82ba9-126">直前の例の結果は、このトピックの最初の例の結果と同じです。</span><span class="sxs-lookup"><span data-stu-id="82ba9-126">The result of the immediately preceding example is the same as the result of the first example in this topic.</span></span> <span data-ttu-id="82ba9-127">これは、メソッド呼び出しの順序と行列乗算の順序の両方は元に戻すためにです。</span><span class="sxs-lookup"><span data-stu-id="82ba9-127">This is because we reversed both the order of the method calls and the order of the matrix multiplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ba9-128">参照</span><span class="sxs-lookup"><span data-stu-id="82ba9-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [<span data-ttu-id="82ba9-129">座標系と変換</span><span class="sxs-lookup"><span data-stu-id="82ba9-129">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="82ba9-130">マネージ GDI+ での変換の使用</span><span class="sxs-lookup"><span data-stu-id="82ba9-130">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
