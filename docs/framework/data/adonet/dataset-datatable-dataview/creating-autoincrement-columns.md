---
title: "AutoIncrement 列の作成"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7bc71e3ae817bbdaf5dc14f22041e297cab949b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="3904d-102">AutoIncrement 列の作成</span><span class="sxs-lookup"><span data-stu-id="3904d-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="3904d-103">列値を一意にするために、新しい行がテーブルに追加されたときに列値が自動的にインクリメントされるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="3904d-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="3904d-104">自動インクリメントを作成する<xref:System.Data.DataColumn>、設定、<xref:System.Data.DataColumn.AutoIncrement%2A>する列のプロパティ**true**です。</span><span class="sxs-lookup"><span data-stu-id="3904d-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="3904d-105"><xref:System.Data.DataColumn>で定義された値を使用して起動、<xref:System.Data.DataColumn.AutoIncrementSeed%2A>プロパティ、各行の値を追加し、 **AutoIncrement**列で定義されている値が加算、<xref:System.Data.DataColumn.AutoIncrementStep%2A>列のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="3904d-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="3904d-106">**AutoIncrement**列、ことをお勧め、<xref:System.Data.DataColumn.ReadOnly%2A>のプロパティ、 **DataColumn**に設定されている**true**です。</span><span class="sxs-lookup"><span data-stu-id="3904d-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="3904d-107">値 200 から開始して 3 ずつインクリメントする列を作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3904d-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3904d-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="3904d-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="3904d-109">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="3904d-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="3904d-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="3904d-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="3904d-111">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="3904d-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
