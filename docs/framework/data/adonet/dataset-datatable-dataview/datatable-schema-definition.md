---
title: "DataTable スキーマの定義"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ae4d5af0238108d0f309ae311e172450bf226c23
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="adb46-102">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="adb46-102">DataTable Schema Definition</span></span>
<span data-ttu-id="adb46-103">テーブルのスキーマ (構造) は、列と制約で表されます。</span><span class="sxs-lookup"><span data-stu-id="adb46-103">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="adb46-104"><xref:System.Data.DataTable> のスキーマは、<xref:System.Data.DataColumn>、<xref:System.Data.ForeignKeyConstraint>、<xref:System.Data.UniqueConstraint> の各オブジェクトを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="adb46-104">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="adb46-105">テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。</span><span class="sxs-lookup"><span data-stu-id="adb46-105">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="adb46-106">テーブルの列、リレーション、および制約を名前で参照する場合は、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="adb46-106">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="adb46-107">複数の列、リレーション、または制約の名前が同じであっても、大文字と小文字が異なっていれば、1 つのテーブルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="adb46-107">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="adb46-108">たとえば、ことが**Col1**と**col1**です。</span><span class="sxs-lookup"><span data-stu-id="adb46-108">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="adb46-109">この場合、列を名前で参照するときは、列名の大文字と小文字を正確に指定する必要があります。正確に指定しない場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="adb46-109">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="adb46-110">たとえば場合の表に、 **myTable**列を含む**Col1**と**col1**を参照する**Col1**と名前で**myTable.Columns["Col1"]**、および**col1**として**myTable.Columns["col1"]**です。</span><span class="sxs-lookup"><span data-stu-id="adb46-110">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="adb46-111">として列のいずれかを参照しようとして**myTable.Columns["COL1"]**例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="adb46-111">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="adb46-112">大文字と小文字の区別の規則は、特定の名前の列、リレーション、または制約が 1 つしかない場合には適用されません。</span><span class="sxs-lookup"><span data-stu-id="adb46-112">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="adb46-113">つまり、特定の列、リレーション、または制約オブジェクトと名前が一致する列、リレーション、または制約オブジェクトがテーブルに存在しない場合は、大文字と小文字を区別せずにそのオブジェクトを名前で参照することができます。このとき、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="adb46-113">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="adb46-114">たとえば、テーブルにのみ**Col1**を使用してそれを参照することができます**my です。列 ["COL1"]**です。</span><span class="sxs-lookup"><span data-stu-id="adb46-114">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adb46-115"><xref:System.Data.DataTable.CaseSensitive%2A>のプロパティ、 **DataTable**この動作には影響しません。</span><span class="sxs-lookup"><span data-stu-id="adb46-115">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="adb46-116">**CaseSensitive**プロパティは、列、リレーション、および制約への参照ではなく、テーブルや並べ替え、検索、フィルター処理、制約の適用などのデータに適用されます。</span><span class="sxs-lookup"><span data-stu-id="adb46-116">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="adb46-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="adb46-117">In This Section</span></span>  
 [<span data-ttu-id="adb46-118">DataTable への列の追加</span><span class="sxs-lookup"><span data-stu-id="adb46-118">Adding Columns to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 <span data-ttu-id="adb46-119">使用してテーブルの列を定義する方法について説明**DataColumn**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="adb46-119">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="adb46-120">式列の作成</span><span class="sxs-lookup"><span data-stu-id="adb46-120">Creating Expression Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 <span data-ttu-id="adb46-121">について説明しますが、どのように**式**列のプロパティは、行の他の列の値に基づいて値を計算に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="adb46-121">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="adb46-122">AutoIncrement 列の作成</span><span class="sxs-lookup"><span data-stu-id="adb46-122">Creating AutoIncrement Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 <span data-ttu-id="adb46-123">数値を自動的にインクリメントして行ごとに一意の列値が割り当てられるように列を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="adb46-123">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="adb46-124">主キーの定義</span><span class="sxs-lookup"><span data-stu-id="adb46-124">Defining Primary Keys</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 <span data-ttu-id="adb46-125">1 つ以上のテーブルの主キーを指定する方法について説明**DataColumn**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="adb46-125">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="adb46-126">DataTable の制約</span><span class="sxs-lookup"><span data-stu-id="adb46-126">DataTable Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 <span data-ttu-id="adb46-127">テーブルの列の外部キー制約と UNIQUE 制約を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="adb46-127">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb46-128">参照</span><span class="sxs-lookup"><span data-stu-id="adb46-128">See Also</span></span>  
 [<span data-ttu-id="adb46-129">DataTables</span><span class="sxs-lookup"><span data-stu-id="adb46-129">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="adb46-130">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="adb46-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
