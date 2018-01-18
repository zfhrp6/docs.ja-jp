---
title: "式列の作成"
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
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 03c049ea3fb4b0f75418de4f9e8318512c198f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="creating-expression-columns"></a><span data-ttu-id="873e0-102">式列の作成</span><span class="sxs-lookup"><span data-stu-id="873e0-102">Creating Expression Columns</span></span>
<span data-ttu-id="873e0-103">列の式を定義すると、同じ行の他の列値またはテーブル内の複数の行の列値に基づいて計算した値を、その列に格納できます。</span><span class="sxs-lookup"><span data-stu-id="873e0-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="873e0-104">評価する式を定義するには、対象の列の <xref:System.Data.DataColumn.Expression%2A> プロパティを使用し、その式で <xref:System.Data.DataColumn.ColumnName%2A> プロパティを使用して他の列を参照します。</span><span class="sxs-lookup"><span data-stu-id="873e0-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="873e0-105">式列の <xref:System.Data.DataColumn.DataType%2A> は、その式が返す値に適した型であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="873e0-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="873e0-106">テーブル内の式列で使用できるいくつかの式の種類を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="873e0-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="873e0-107">式の種類</span><span class="sxs-lookup"><span data-stu-id="873e0-107">Expression type</span></span>|<span data-ttu-id="873e0-108">例</span><span class="sxs-lookup"><span data-stu-id="873e0-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="873e0-109">比較</span><span class="sxs-lookup"><span data-stu-id="873e0-109">Comparison</span></span>|<span data-ttu-id="873e0-110">"Total >= 500"</span><span class="sxs-lookup"><span data-stu-id="873e0-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="873e0-111">計算</span><span class="sxs-lookup"><span data-stu-id="873e0-111">Computation</span></span>|<span data-ttu-id="873e0-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="873e0-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="873e0-113">集約</span><span class="sxs-lookup"><span data-stu-id="873e0-113">Aggregation</span></span>|<span data-ttu-id="873e0-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="873e0-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="873e0-115">設定することができます、**式**、既存のプロパティ**DataColumn**オブジェクトを使用したりできますプロパティに渡される 3 番目の引数として、<xref:System.Data.DataColumn>コンス トラクターは、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="873e0-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="873e0-116">式は他の式列を参照できます。ただし、2 つの式が相互に参照し合う循環参照の場合は、例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="873e0-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="873e0-117">式の作成に関する規則は、次を参照してください。、<xref:System.Data.DataColumn.Expression%2A>のプロパティ、 **DataColumn**クラスです。</span><span class="sxs-lookup"><span data-stu-id="873e0-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873e0-118">参照</span><span class="sxs-lookup"><span data-stu-id="873e0-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="873e0-119">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="873e0-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="873e0-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="873e0-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="873e0-121">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="873e0-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
