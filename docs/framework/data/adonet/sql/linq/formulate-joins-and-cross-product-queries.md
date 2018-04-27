---
title: 結合およびクロス積クエリの作成
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 468ee54b0936afcbb548249bc714ea4b04abd3de
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="4bfeb-102">結合およびクロス積クエリの作成</span><span class="sxs-lookup"><span data-stu-id="4bfeb-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="4bfeb-103">次の例は、複数のテーブルからの結果を組み合わせる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bfeb-104">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-104">Example</span></span>  
 <span data-ttu-id="4bfeb-105">次の例で外部キー ナビゲーションを使用して、 `From` Visual Basic での句 (`from`句 (C#)) をロンドンの顧客のすべての注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-106">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-106">Example</span></span>  
 <span data-ttu-id="4bfeb-107">次の例で外部キー ナビゲーションを使用して、 `Where` Visual Basic での句 (`where`句 (C#)) を在庫切れのフィルター処理する`Products`が`Supplier`米国の州がします。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-108">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-108">Example</span></span>  
 <span data-ttu-id="4bfeb-109">次の例で外部キー ナビゲーションを使用して、 `From` Visual Basic での句 (`from`句 (C#)) シアトルの従業員をフィルター処理し、その担当区域の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-110">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-110">Example</span></span>  
 <span data-ttu-id="4bfeb-111">次の例で外部キー ナビゲーションを使用して、 `Select` Visual Basic での句 (`select`句 (C#)) を 1 人の従業員が、他のレポート、および、両方の従業員は同じ従業員の組み合わせをフィルター処理する`City`です。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-112">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-112">Example</span></span>  
 <span data-ttu-id="4bfeb-113">Visual Basic の例を次すべての顧客と注文を検索、注文が、顧客に一致することを確認して行いリスト内のすべての顧客の連絡先の名前が指定されていることを保証します。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-114">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-114">Example</span></span>  
 <span data-ttu-id="4bfeb-115">次の例は、2 つのテーブルを明示的に結合し、両方のテーブルからの結果を投影します。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-116">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-116">Example</span></span>  
 <span data-ttu-id="4bfeb-117">次の例は、3 つのテーブルを明示的に結合し、各テーブルからの結果を投影します。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-118">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-118">Example</span></span>  
 <span data-ttu-id="4bfeb-119">次の例は、`LEFT OUTER JOIN` を使用して、`DefaultIfEmpty()` を実現する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="4bfeb-120">`DefaultIfEmpty()` に `Order` がない場合は、`Employee` メソッドから null が返されます。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-121">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-121">Example</span></span>  
 <span data-ttu-id="4bfeb-122">次の例は、結合の結果の `let` 式を投影します。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-123">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-123">Example</span></span>  
 <span data-ttu-id="4bfeb-124">次の例は、複合キーを使用する `join` を示しています。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="4bfeb-125">例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-125">Example</span></span>  
 <span data-ttu-id="4bfeb-126">次の例は、一方が null 許容で他方がそうでない `join` の作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4bfeb-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="4bfeb-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bfeb-127">See Also</span></span>  
 [<span data-ttu-id="4bfeb-128">クエリの例</span><span class="sxs-lookup"><span data-stu-id="4bfeb-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
