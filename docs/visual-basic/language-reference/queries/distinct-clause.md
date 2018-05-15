---
title: Distinct 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="d0768-102">Distinct 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0768-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="d0768-103">次のクエリ句で、重複を回避するのには、現在の範囲変数の値を制限します。</span><span class="sxs-lookup"><span data-stu-id="d0768-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0768-104">構文</span><span class="sxs-lookup"><span data-stu-id="d0768-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="d0768-105">コメント</span><span class="sxs-lookup"><span data-stu-id="d0768-105">Remarks</span></span>  
 <span data-ttu-id="d0768-106">使用することができます、`Distinct`句に固有のアイテムの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="d0768-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="d0768-107">`Distinct`句によって重複するクエリの結果を無視するクエリ。</span><span class="sxs-lookup"><span data-stu-id="d0768-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="d0768-108">`Distinct`句は、すべてで指定されたフィールドの戻り値の重複する値に適用されます、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="d0768-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="d0768-109">ない場合は`Select`句を指定する、`Distinct`句は、クエリで特定の範囲変数に適用、`From`句。</span><span class="sxs-lookup"><span data-stu-id="d0768-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="d0768-110">範囲変数が、不変の型でない場合は、型のすべてのメンバーには、既存のクエリ結果が一致する場合、クエリはのみ、クエリ結果が無視されます。</span><span class="sxs-lookup"><span data-stu-id="d0768-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0768-111">例</span><span class="sxs-lookup"><span data-stu-id="d0768-111">Example</span></span>  
 <span data-ttu-id="d0768-112">次のクエリ式は、顧客注文のリストと顧客のリストを結合します。</span><span class="sxs-lookup"><span data-stu-id="d0768-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="d0768-113">`Distinct`句は一意の顧客名のリストを返し、注文日に含まれています。</span><span class="sxs-lookup"><span data-stu-id="d0768-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d0768-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0768-114">See Also</span></span>  
 [<span data-ttu-id="d0768-115">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="d0768-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d0768-116">クエリ</span><span class="sxs-lookup"><span data-stu-id="d0768-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d0768-117">From 句</span><span class="sxs-lookup"><span data-stu-id="d0768-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d0768-118">Select 句</span><span class="sxs-lookup"><span data-stu-id="d0768-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d0768-119">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="d0768-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
