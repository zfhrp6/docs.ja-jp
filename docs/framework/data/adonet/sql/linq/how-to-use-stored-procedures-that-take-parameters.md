---
title: '方法 : パラメーターを受け取るストアド プロシージャを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: d1c9337f59b8cf218b9d2ab8fe4cf21afd2da689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353512"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="b784c-102">方法 : パラメーターを受け取るストアド プロシージャを使用する</span><span class="sxs-lookup"><span data-stu-id="b784c-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b784c-103"> は、出力パラメーターを参照パラメーターに対応付け、値型はパラメーターを null 許容型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="b784c-103"> maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="b784c-104">行セットを返すクエリで、入力パラメーターを使用する方法の例は、次を参照してください。[する方法: 行セットを返す](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)です。</span><span class="sxs-lookup"><span data-stu-id="b784c-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b784c-105">例</span><span class="sxs-lookup"><span data-stu-id="b784c-105">Example</span></span>  
 <span data-ttu-id="b784c-106">次の例は、単一の入力パラメーター (顧客 ID) を受け取り、出力パラメーター (その顧客の売上合計) を返します。</span><span class="sxs-lookup"><span data-stu-id="b784c-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="b784c-107">例</span><span class="sxs-lookup"><span data-stu-id="b784c-107">Example</span></span>  
 <span data-ttu-id="b784c-108">このストアド プロシージャは次のように呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b784c-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b784c-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b784c-109">See Also</span></span>  
 [<span data-ttu-id="b784c-110">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b784c-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [<span data-ttu-id="b784c-111">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="b784c-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="b784c-112">Null 許容型の使用</span><span class="sxs-lookup"><span data-stu-id="b784c-112">Using Nullable Types</span></span>](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [<span data-ttu-id="b784c-113">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="b784c-113">Nullable Value Types</span></span>](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
