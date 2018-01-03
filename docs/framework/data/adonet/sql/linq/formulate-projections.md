---
title: "射影の作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bb22ddd4882d9885c55301a6fdc6a0eb336b49af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="formulate-projections"></a><span data-ttu-id="e8870-102">射影の作成</span><span class="sxs-lookup"><span data-stu-id="e8870-102">Formulate Projections</span></span>
<span data-ttu-id="e8870-103">以下の例は、C# の `select` ステートメントおよび `Select` の [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ステートメントを他の機能と組み合わせて、クエリの射影を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e8870-103">The following examples show how the `select` statement in C# and `Select` statement in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8870-104">例</span><span class="sxs-lookup"><span data-stu-id="e8870-104">Example</span></span>  
 <span data-ttu-id="e8870-105">次の例で、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) を連絡先の名前のシーケンスを返す`Customers`です。</span><span class="sxs-lookup"><span data-stu-id="e8870-105">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="e8870-106">例</span><span class="sxs-lookup"><span data-stu-id="e8870-106">Example</span></span>  
 <span data-ttu-id="e8870-107">次の例では、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*連絡先の名前のシーケンスを返すし、電話の番号を`Customers`です。</span><span class="sxs-lookup"><span data-stu-id="e8870-107">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="e8870-108">例</span><span class="sxs-lookup"><span data-stu-id="e8870-108">Example</span></span>  
 <span data-ttu-id="e8870-109">次の例では、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*名前のシーケンスを返すし、従業員の電話番号にします。</span><span class="sxs-lookup"><span data-stu-id="e8870-109">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="e8870-110">`FirstName`と`LastName`フィールドが 1 つのフィールドに結合されます (`Name`)、および`HomePhone`フィールドの名前を変更する`Phone`結果のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="e8870-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="e8870-111">例</span><span class="sxs-lookup"><span data-stu-id="e8870-111">Example</span></span>  
 <span data-ttu-id="e8870-112">次の例では、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*すべてのシーケンスを返します`ProductID`s とという名前の計算値`HalfPrice`です。</span><span class="sxs-lookup"><span data-stu-id="e8870-112">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="e8870-113">この値は、`UnitPrice` を 2 で割った値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e8870-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="e8870-114">例</span><span class="sxs-lookup"><span data-stu-id="e8870-114">Example</span></span>  
 <span data-ttu-id="e8870-115">次の例で、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select` (C#) 句) および*条件付きステートメント*製品名および製品の可用性のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="e8870-115">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="e8870-116">例</span><span class="sxs-lookup"><span data-stu-id="e8870-116">Example</span></span>  
 <span data-ttu-id="e8870-117">次の例では、 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select`句 (`select` (C#) 句) および*既知の型*従業員の名前のシーケンスを返します (名前)。</span><span class="sxs-lookup"><span data-stu-id="e8870-117">The following example uses a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="e8870-118">例</span><span class="sxs-lookup"><span data-stu-id="e8870-118">Example</span></span>  
 <span data-ttu-id="e8870-119">次の例で`Select`と`Where`で[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`と`where`C# の場合) を返す、*フィルター処理されたシーケンス*ロンドンの顧客の連絡先の名前のです。</span><span class="sxs-lookup"><span data-stu-id="e8870-119">The following example uses `Select` and `Where` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="e8870-120">例</span><span class="sxs-lookup"><span data-stu-id="e8870-120">Example</span></span>  
 <span data-ttu-id="e8870-121">次の例で、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*を返す、*成型されたサブセット*の顧客に関するデータ。</span><span class="sxs-lookup"><span data-stu-id="e8870-121">The following example uses a `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="e8870-122">例</span><span class="sxs-lookup"><span data-stu-id="e8870-122">Example</span></span>  
 <span data-ttu-id="e8870-123">次の例では、入れ子になったクエリを使用して以下の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="e8870-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="e8870-124">すべての注文および対応する `OrderID` のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="e8870-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="e8870-125">注文内で割引のある項目から成るサブシーケンス。</span><span class="sxs-lookup"><span data-stu-id="e8870-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="e8870-126">出荷コストが含まれない場合に節約される費用。</span><span class="sxs-lookup"><span data-stu-id="e8870-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="e8870-127">参照</span><span class="sxs-lookup"><span data-stu-id="e8870-127">See Also</span></span>  
 [<span data-ttu-id="e8870-128">クエリの例</span><span class="sxs-lookup"><span data-stu-id="e8870-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
