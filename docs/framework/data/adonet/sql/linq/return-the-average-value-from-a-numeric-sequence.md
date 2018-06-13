---
title: 一連の数値の平均値の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 3e808b836183a23fa6bd80faeb0d3cfc5921f4cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358857"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="bc9c6-102">一連の数値の平均値の取得</span><span class="sxs-lookup"><span data-stu-id="bc9c6-102">Return the Average Value From a Numeric Sequence</span></span>
<span data-ttu-id="bc9c6-103"><xref:System.Linq.Enumerable.Average%2A> 演算子は、一連の数値の平均値を計算します。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-103">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc9c6-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で整数値の `Average` が変換されるときには、倍精度浮動小数点数ではなく整数として計算されます。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-104">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9c6-105">例</span><span class="sxs-lookup"><span data-stu-id="bc9c6-105">Example</span></span>  
 <span data-ttu-id="bc9c6-106">次の例は、`Freight` テーブルの `Orders` の平均値を返します。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-106">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="bc9c6-107">Northwind サンプル データベースでは、結果は `78.2442` になります。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-107">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bc9c6-108">例</span><span class="sxs-lookup"><span data-stu-id="bc9c6-108">Example</span></span>  
 <span data-ttu-id="bc9c6-109">次の例は、`Products` テーブルのすべての `Products` の単価の平均値を返します。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-109">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="bc9c6-110">Northwind サンプル データベースでは、結果は `28.8663` になります。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-110">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="bc9c6-111">例</span><span class="sxs-lookup"><span data-stu-id="bc9c6-111">Example</span></span>  
 <span data-ttu-id="bc9c6-112">次の例は、`Average` 演算子を使用して、カテゴリ内の平均単価よりも単価が高い `Products` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-112">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="bc9c6-113">その後、結果をグループ別に表示します。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-113">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="bc9c6-114">この例の戻り値は匿名型なので、C# で `var` キーワードを使用する必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-114">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="bc9c6-115">Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bc9c6-115">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="bc9c6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc9c6-116">See Also</span></span>  
 [<span data-ttu-id="bc9c6-117">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="bc9c6-117">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
