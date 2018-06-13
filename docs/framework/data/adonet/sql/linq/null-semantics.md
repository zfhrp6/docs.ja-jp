---
title: null セマンティクス
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: b80d198b81e28b0fe1d0107dd04a9694c3069868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357703"
---
# <a name="null-semantics"></a><span data-ttu-id="24068-102">null セマンティクス</span><span class="sxs-lookup"><span data-stu-id="24068-102">Null Semantics</span></span>
<span data-ttu-id="24068-103">次の表のさまざまな部分へのリンクを提供する、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメント場所`null`(`Nothing` Visual Basic で) の問題が説明されています。</span><span class="sxs-lookup"><span data-stu-id="24068-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="24068-104">トピック</span><span class="sxs-lookup"><span data-stu-id="24068-104">Topic</span></span>|<span data-ttu-id="24068-105">説明</span><span class="sxs-lookup"><span data-stu-id="24068-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="24068-106">SQL と CLR の型の不一致</span><span class="sxs-lookup"><span data-stu-id="24068-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="24068-107">このトピックの「Null セマンティクス」セクションには、3 つの状態 SQL のブール値と 2 つの状態共通言語ランタイム (CLR) 説明が含まれています<xref:System.Boolean>、リテラル`Nothing`(Visual Basic の場合) と`null`(c#)、およびその他の同様の問題です。</span><span class="sxs-lookup"><span data-stu-id="24068-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="24068-108">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="24068-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="24068-109">このトピックの「null セマンティクス」セクションでは、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]での null の比較のセマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="24068-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="24068-110">System.String メソッド</span><span class="sxs-lookup"><span data-stu-id="24068-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="24068-111">このトピックの「.NET との相違」セクションでは、 <xref:System.String.LastIndexOf%2A> の戻り値が 0 の場合に、文字列が null の場合と、見つかった位置が 0 の場合の両方があることについて説明します。</span><span class="sxs-lookup"><span data-stu-id="24068-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="24068-112">数値のシーケンスの合計の計算</span><span class="sxs-lookup"><span data-stu-id="24068-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="24068-113">について説明しますが、どのように<xref:System.Linq.Enumerable.Sum%2A>に演算子が評価`null`(`Nothing` Visual Basic で) 0 null のみを含むシーケンスまたは空のシーケンスではなくです。</span><span class="sxs-lookup"><span data-stu-id="24068-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24068-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="24068-114">See Also</span></span>  
 [<span data-ttu-id="24068-115">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="24068-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
