---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 3b63ca6ade93331b9d1c3ef3e8de15ed520864dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="skip-entity-sql"></a><span data-ttu-id="14e23-102">SKIP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="14e23-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="14e23-103">物理的なページングは、ORDER BY 句の SKIP サブ句を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="14e23-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="14e23-104">SKIP を ORDER BY 句と切り離して使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="14e23-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e23-105">構文</span><span class="sxs-lookup"><span data-stu-id="14e23-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="14e23-106">引数</span><span class="sxs-lookup"><span data-stu-id="14e23-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="14e23-107">スキップするアイテムの数。</span><span class="sxs-lookup"><span data-stu-id="14e23-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14e23-108">コメント</span><span class="sxs-lookup"><span data-stu-id="14e23-108">Remarks</span></span>  
 <span data-ttu-id="14e23-109">SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="14e23-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="14e23-110">たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。</span><span class="sxs-lookup"><span data-stu-id="14e23-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14e23-111">TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは無効です。</span><span class="sxs-lookup"><span data-stu-id="14e23-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="14e23-112">TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="14e23-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14e23-113">[!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]では、キー以外の列で ORDER BY と共に SKIP を使用すると、不適切な結果が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="14e23-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="14e23-114">キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="14e23-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="14e23-115">これは、 [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]用に SKIP が変換される方法によるものです。</span><span class="sxs-lookup"><span data-stu-id="14e23-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="14e23-116">たとえば、次のコードでは、 `E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="14e23-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="14e23-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] この [例の中の](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) クエリでは、SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を SKIP と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="14e23-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [this](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) example uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e23-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="14e23-118">See Also</span></span>  
 [<span data-ttu-id="14e23-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="14e23-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="14e23-120">方法: 結果をクエリ ページング</span><span class="sxs-lookup"><span data-stu-id="14e23-120">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="14e23-121">ページング</span><span class="sxs-lookup"><span data-stu-id="14e23-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="14e23-122">TOP</span><span class="sxs-lookup"><span data-stu-id="14e23-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
