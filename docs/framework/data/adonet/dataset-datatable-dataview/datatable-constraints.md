---
title: "DataTable の制約"
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
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3767467024d6c0d0dfbf1be8829d77ba3f7fa439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-constraints"></a><span data-ttu-id="40fff-102">DataTable の制約</span><span class="sxs-lookup"><span data-stu-id="40fff-102">DataTable Constraints</span></span>
<span data-ttu-id="40fff-103">制約を使用すると、データの整合性を維持するために <xref:System.Data.DataTable> のデータを強制的に制限できます。</span><span class="sxs-lookup"><span data-stu-id="40fff-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="40fff-104">制約は、1 つの列または関連付けられた複数の列に対して自動的に適用される規則であり、行の値がなんらかの方法で変更されたときに実行されるアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="40fff-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="40fff-105">制約が適用時に、`System.Data.DataSet.EnforceConstraints`のプロパティ、<xref:System.Data.DataSet>は**true**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="40fff-106">`EnforceConstraints` プロパティの設定方法のコード例については、<xref:System.Data.DataSet.EnforceConstraints%2A> のリファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40fff-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="40fff-107">ADO.NET には、<xref:System.Data.ForeignKeyConstraint> と <xref:System.Data.UniqueConstraint> の 2 種類の制約があります。</span><span class="sxs-lookup"><span data-stu-id="40fff-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="40fff-108">既定では、両方の制約が自動的に作成を追加して 2 つ以上のテーブル間のリレーションシップを作成するときに、<xref:System.Data.DataRelation>を**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="40fff-109">指定してこの動作を無効にするただし、 **createConstraints** = **false**リレーションシップを作成するときにします。</span><span class="sxs-lookup"><span data-stu-id="40fff-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="40fff-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="40fff-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="40fff-111">A **ForeignKeyConstraint**更新および削除を関連テーブルを反映する方法に関する規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="40fff-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="40fff-112">たとえば、1 つのテーブルの行の値が更新または削除すると同じ値もで使用される 1 つか複数の関連するテーブル、 **ForeignKeyConstraint**関連テーブルでの動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="40fff-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="40fff-113"><xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>と<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>のプロパティ、 **ForeignKeyConstraint**ユーザーを削除するか、関連テーブルの行を更新しようとしたときに実行されるアクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="40fff-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="40fff-114">次の表に、さまざまな設定に使用できる、 **DeleteRule**と**UpdateRule**のプロパティ、 **ForeignKeyConstraint**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="40fff-115">規則の設定</span><span class="sxs-lookup"><span data-stu-id="40fff-115">Rule setting</span></span>|<span data-ttu-id="40fff-116">説明</span><span class="sxs-lookup"><span data-stu-id="40fff-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="40fff-117">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="40fff-117">**Cascade**</span></span>|<span data-ttu-id="40fff-118">関連付けられている行を削除または更新します。</span><span class="sxs-lookup"><span data-stu-id="40fff-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="40fff-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="40fff-119">**SetNull**</span></span>|<span data-ttu-id="40fff-120">関連付けられている行の値を設定**DBNull**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="40fff-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="40fff-121">**SetDefault**</span></span>|<span data-ttu-id="40fff-122">関連付けられている行の値を既定値に設定します。</span><span class="sxs-lookup"><span data-stu-id="40fff-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="40fff-123">**None**</span><span class="sxs-lookup"><span data-stu-id="40fff-123">**None**</span></span>|<span data-ttu-id="40fff-124">関連付けられている行に対してアクションは実行しません。</span><span class="sxs-lookup"><span data-stu-id="40fff-124">Take no action on related rows.</span></span> <span data-ttu-id="40fff-125">既定値です。</span><span class="sxs-lookup"><span data-stu-id="40fff-125">This is the default.</span></span>|  
  
 <span data-ttu-id="40fff-126">A **ForeignKeyConstraint**制限することができますへの変更の反映させたり、関連列です。</span><span class="sxs-lookup"><span data-stu-id="40fff-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="40fff-127">設定されたプロパティによって、 **ForeignKeyConstraint** 、列の場合、 **EnforceConstraints**のプロパティ、**データセット**は**true**、親の行で特定の操作を実行すると、例外。</span><span class="sxs-lookup"><span data-stu-id="40fff-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="40fff-128">たとえば場合、 **DeleteRule**のプロパティ、 **ForeignKeyConstraint**は**None**子行がある場合、親の行を削除できません。</span><span class="sxs-lookup"><span data-stu-id="40fff-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="40fff-129">1 つの列間または配列を使用して列の間の外部キー制約を作成することができます、 **ForeignKeyConstraint**コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="40fff-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="40fff-130">その結果を渡す**ForeignKeyConstraint**オブジェクトを**追加**メソッド テーブルの**制約**プロパティとは、 **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="40fff-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="40fff-131">いくつかのオーバー ロードにコンス トラクターの引数を渡すことも、**追加**のメソッド、 **ConstraintCollection**を作成する、 **ForeignKeyConstraint**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="40fff-132">作成するときに、 **ForeignKeyConstraint**を渡すことができます、 **DeleteRule**と**UpdateRule**するか、引数としてコンス トラクターに値としてのプロパティとして設定できます、次の例 (ここで、 **DeleteRule**に値が設定されている**None**)。</span><span class="sxs-lookup"><span data-stu-id="40fff-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="40fff-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="40fff-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="40fff-134">使用して行への変更を受け入れることができます、 **AcceptChanges**メソッドまたは取り消しを使用して、 **RejectChanges**のメソッド、**データセット**、 **DataTable**、または**DataRow**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="40fff-135">ときに、**データセット**が含まれています**ForeignKeyConstraints**、起動、 **AcceptChanges**または**RejectChanges** を強制する方法**AcceptRejectRule**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="40fff-136">**AcceptRejectRule**のプロパティ、 **ForeignKeyConstraint**子に対して実行されるアクションを決定するときに行**AcceptChanges**または**RejectChanges**は親の行で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="40fff-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="40fff-137">次の表に、利用可能な設定、 **AcceptRejectRule**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="40fff-138">規則の設定</span><span class="sxs-lookup"><span data-stu-id="40fff-138">Rule setting</span></span>|<span data-ttu-id="40fff-139">説明</span><span class="sxs-lookup"><span data-stu-id="40fff-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="40fff-140">**Cascade**</span><span class="sxs-lookup"><span data-stu-id="40fff-140">**Cascade**</span></span>|<span data-ttu-id="40fff-141">子の行への変更を受け入れるかまたは拒否します。</span><span class="sxs-lookup"><span data-stu-id="40fff-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="40fff-142">**None**</span><span class="sxs-lookup"><span data-stu-id="40fff-142">**None**</span></span>|<span data-ttu-id="40fff-143">子の行に対してアクションは実行しません。</span><span class="sxs-lookup"><span data-stu-id="40fff-143">Take no action on child rows.</span></span> <span data-ttu-id="40fff-144">既定値です。</span><span class="sxs-lookup"><span data-stu-id="40fff-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="40fff-145">例</span><span class="sxs-lookup"><span data-stu-id="40fff-145">Example</span></span>  
 <span data-ttu-id="40fff-146">次の例では、<xref:System.Data.ForeignKeyConstraint> を作成し、<xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> を含む複数のプロパティを設定して、<xref:System.Data.ConstraintCollection> オブジェクトの <xref:System.Data.DataTable> に追加します。</span><span class="sxs-lookup"><span data-stu-id="40fff-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="40fff-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="40fff-147">UniqueConstraint</span></span>  
 <span data-ttu-id="40fff-148">**UniqueConstraint**オブジェクト、1 つの列または列の配列のいずれかに割り当てることができます、 **DataTable**、指定された列または列のすべてのデータが行ごとに一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="40fff-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="40fff-149">使用して、列または列の配列に対する unique 制約を作成することができます、 **UniqueConstraint**コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="40fff-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="40fff-150">その結果を渡す**UniqueConstraint**オブジェクトを**追加**メソッド テーブルの**制約**プロパティとは、 **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="40fff-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="40fff-151">いくつかのオーバー ロードにコンス トラクターの引数を渡すことも、**追加**のメソッド、 **ConstraintCollection**を作成する、 **UniqueConstraint**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="40fff-152">作成するときに、 **UniqueConstraint**または複数の列のことができます必要に応じて指定するかどうか、列が主キー。</span><span class="sxs-lookup"><span data-stu-id="40fff-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="40fff-153">設定して、列の unique 制約を作成することも、 **Unique**する列のプロパティ**true**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="40fff-154">または、設定、 **Unique**に単一の列のプロパティ**false**が存在している既存の unique 制約を削除します。</span><span class="sxs-lookup"><span data-stu-id="40fff-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="40fff-155">1 つの列 (または複数の列) をテーブルの主キーとして定義すると、指定した列 (または複数の列) の UNIQUE 制約が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="40fff-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="40fff-156">列を削除する場合、 **PrimaryKey**のプロパティ、 **DataTable**、 **UniqueConstraint**を削除します。</span><span class="sxs-lookup"><span data-stu-id="40fff-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="40fff-157">次の例を作成、 **UniqueConstraint**の 2 つの列に対して、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="40fff-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="40fff-158">参照</span><span class="sxs-lookup"><span data-stu-id="40fff-158">See Also</span></span>  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [<span data-ttu-id="40fff-159">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="40fff-159">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="40fff-160">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="40fff-160">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="40fff-161">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="40fff-161">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
