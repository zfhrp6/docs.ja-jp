---
title: LINQ to DataSet の例
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: f0b836e4f19011dc3d75f0681f7205cec6cb9110
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="97279-102">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="97279-102">LINQ to DataSet Examples</span></span>
<span data-ttu-id="97279-103">このセクションでは[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]プログラミングの標準クエリ演算子を使用する例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="97279-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples that use the standard query operators.</span></span> <span data-ttu-id="97279-104"><xref:System.Data.DataSet>これらの例で使用されるを使用して設定されます、`FillDataSet`で指定されているメソッド[、データセットにデータを読み込む](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)します。</span><span class="sxs-lookup"><span data-stu-id="97279-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="97279-105">詳細については、次を参照してください。[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)です。</span><span class="sxs-lookup"><span data-stu-id="97279-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97279-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="97279-106">In This Section</span></span>  
 [<span data-ttu-id="97279-107">クエリ式の例</span><span class="sxs-lookup"><span data-stu-id="97279-107">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="97279-108">次の例があります。</span><span class="sxs-lookup"><span data-stu-id="97279-108">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="97279-109">射影</span><span class="sxs-lookup"><span data-stu-id="97279-109">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
-   [<span data-ttu-id="97279-110">制限</span><span class="sxs-lookup"><span data-stu-id="97279-110">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
-   [<span data-ttu-id="97279-111">パーティション分割</span><span class="sxs-lookup"><span data-stu-id="97279-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="97279-112">順序付け</span><span class="sxs-lookup"><span data-stu-id="97279-112">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="97279-113">要素演算子</span><span class="sxs-lookup"><span data-stu-id="97279-113">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="97279-114">集計演算子</span><span class="sxs-lookup"><span data-stu-id="97279-114">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="97279-115">結合演算子</span><span class="sxs-lookup"><span data-stu-id="97279-115">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="97279-116">メソッド ベースのクエリ例</span><span class="sxs-lookup"><span data-stu-id="97279-116">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="97279-117">次の例があります。</span><span class="sxs-lookup"><span data-stu-id="97279-117">Contains the following examples:</span></span>  
  
-   [<span data-ttu-id="97279-118">射影</span><span class="sxs-lookup"><span data-stu-id="97279-118">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="97279-119">パーティション分割</span><span class="sxs-lookup"><span data-stu-id="97279-119">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
  
-   [<span data-ttu-id="97279-120">順序付け</span><span class="sxs-lookup"><span data-stu-id="97279-120">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
-   [<span data-ttu-id="97279-121">集合演算子</span><span class="sxs-lookup"><span data-stu-id="97279-121">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
  
-   [<span data-ttu-id="97279-122">変換演算子</span><span class="sxs-lookup"><span data-stu-id="97279-122">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
  
-   [<span data-ttu-id="97279-123">要素演算子</span><span class="sxs-lookup"><span data-stu-id="97279-123">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="97279-124">集計演算子</span><span class="sxs-lookup"><span data-stu-id="97279-124">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="97279-125">Join</span><span class="sxs-lookup"><span data-stu-id="97279-125">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="97279-126">DataSet 固有の演算子の例</span><span class="sxs-lookup"><span data-stu-id="97279-126">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="97279-127"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドおよび <xref:System.Data.DataRowComparer> クラスの使用例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="97279-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97279-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="97279-128">See Also</span></span>  
 [<span data-ttu-id="97279-129">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="97279-129">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [<span data-ttu-id="97279-130">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="97279-130">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
