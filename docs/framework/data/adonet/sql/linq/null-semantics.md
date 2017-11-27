---
title: "null セマンティクス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3820b1282dda4155946ff22784e5ebe18525b45c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="null-semantics"></a><span data-ttu-id="a153c-102">null セマンティクス</span><span class="sxs-lookup"><span data-stu-id="a153c-102">Null Semantics</span></span>
<span data-ttu-id="a153c-103">次の表では、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ドキュメントで `null` (`Nothing` では [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) について説明している各部分へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="a153c-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="a153c-104">トピック</span><span class="sxs-lookup"><span data-stu-id="a153c-104">Topic</span></span>|<span data-ttu-id="a153c-105">説明</span><span class="sxs-lookup"><span data-stu-id="a153c-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a153c-106">SQL CLR 型の不一致</span><span class="sxs-lookup"><span data-stu-id="a153c-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="a153c-107">このトピックの「null セマンティクス」セクションでは、3 つの状態を持つ SQL のブール値と、2 つの状態を持つ共通言語ランタイム (CLR: Common Language Runtime) の <xref:System.Boolean>、 `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)])、 `null` (C#)、および関連するその他の話題について説明します。</span><span class="sxs-lookup"><span data-stu-id="a153c-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="a153c-108">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="a153c-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="a153c-109">このトピックの「null セマンティクス」セクションでは、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]での null の比較のセマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a153c-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="a153c-110">System.String メソッド</span><span class="sxs-lookup"><span data-stu-id="a153c-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="a153c-111">このトピックの「.NET との相違」セクションでは、 <xref:System.String.LastIndexOf%2A> の戻り値が 0 の場合に、文字列が null の場合と、見つかった位置が 0 の場合の両方があることについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a153c-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="a153c-112">数値のシーケンス値の合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="a153c-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="a153c-113">null のみを含むシーケンス、または空のシーケンスの場合に、 <xref:System.Linq.Enumerable.Sum%2A> 演算子が 0 ではなく `null` (`Nothing` では [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) に評価されることについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a153c-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a153c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a153c-114">See Also</span></span>  
 [<span data-ttu-id="a153c-115">データ型および関数</span><span class="sxs-lookup"><span data-stu-id="a153c-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
