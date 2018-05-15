---
title: DataSet への既存の制約の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: c3c28392a9e4bee0e2f9e0dcf553e13b67c378dd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="41130-102">DataSet への既存の制約の追加</span><span class="sxs-lookup"><span data-stu-id="41130-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="41130-103">**塗りつぶし**のメソッド、 **DataAdapter**塗りつぶします、<xref:System.Data.DataSet>のみテーブルの列およびデータ ソースからの行も制約は一般設定、データ ソースによって、 **を塗りつぶす**メソッドでは、このスキーマ情報には追加されません、**データセット**既定です。</span><span class="sxs-lookup"><span data-stu-id="41130-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="41130-104">設定する、**データセット**呼び出すかを使用してデータ ソースから既存の主キー制約情報できます、 **FillSchema**のメソッド、 **DataAdapter**、設定や、**MissingSchemaAction**のプロパティ、 **DataAdapter**に**AddWithKey**呼び出す前に**塗りつぶし**です。</span><span class="sxs-lookup"><span data-stu-id="41130-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="41130-105">これが主キーをにより、内の制約、**データセット**データ ソースに反映します。</span><span class="sxs-lookup"><span data-stu-id="41130-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="41130-106">外部キー制約情報が含まれていないのように、明示的に作成する必要があります[DataTable の制約](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)です。</span><span class="sxs-lookup"><span data-stu-id="41130-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="41130-107">スキーマ情報を追加する、**データセット**主キー制約に含まれているようにデータを設定する前に、<xref:System.Data.DataTable>内のオブジェクト、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="41130-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="41130-108">その結果、追加時に入力への呼び出し、**データセット**が行われますが、プライマリ キー列情報を使用して、現在の行の各データ ソースから新しい行と一致**DataTable**との現在のデータテーブルは、データ ソースのデータで上書きされます。</span><span class="sxs-lookup"><span data-stu-id="41130-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="41130-109">スキーマ情報がない場合、新しいデータ ソースから行が、**データセット**、その結果が重複する行にします。</span><span class="sxs-lookup"><span data-stu-id="41130-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41130-110">データ ソース内の列が自動インクリメントとして識別された場合、 **FillSchema**メソッド、または**塗りつぶし**メソッドを**MissingSchemaAction**の**AddWithKey**、作成、 **DataColumn**で、 **AutoIncrement**プロパティに設定`true`です。</span><span class="sxs-lookup"><span data-stu-id="41130-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="41130-111">ただしを設定する必要がありますには、 **AutoIncrementStep**と**AutoIncrementSeed**値を自分でします。</span><span class="sxs-lookup"><span data-stu-id="41130-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="41130-112">自動インクリメント列の詳細については、次を参照してください。 [AutoIncrement 列の作成](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)です。</span><span class="sxs-lookup"><span data-stu-id="41130-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="41130-113">使用して**FillSchema**またはの設定、 **MissingSchemaAction**に**AddWithKey**主キー列情報を確認するのにはデータ ソースで余分な処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="41130-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="41130-114">この追加の処理によりパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="41130-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="41130-115">デザイン時に主キー情報がわかっている場合は、最適のパフォーマンスを得るために主キー列 (複数の場合もある) を明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="41130-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="41130-116">テーブルの主キーの情報を明示的に設定については、次を参照してください。[主キーを定義する](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)です。</span><span class="sxs-lookup"><span data-stu-id="41130-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="41130-117">次のコード例は、スキーマ情報を追加する方法を示しています、**データセット**を使用して**FillSchema**です。</span><span class="sxs-lookup"><span data-stu-id="41130-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="41130-118">次のコード例は、スキーマ情報を追加する方法を示しています、**データセット**を使用して、 **MissingSchemaAction.AddWithKey**のプロパティ、**塗りつぶし**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41130-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="41130-119">複数の結果セットの処理</span><span class="sxs-lookup"><span data-stu-id="41130-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="41130-120">場合、 **DataAdapter**から返された複数の結果セットが発生した、 **SelectCommand**、複数のテーブルが作成されます、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="41130-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="41130-121">テーブルが、0 から始まるインクリメンタル既定名を指定する**テーブル** *N*以降で、**テーブル**したがって"Table0"の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="41130-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="41130-122">テーブル名がへの引数として渡されたかどうか、 **FillSchema**メソッド、テーブルがある、0 から始まるインクリメンタル名**TableName** *N*始まる**TableName** "TableName0"ではなくです。</span><span class="sxs-lookup"><span data-stu-id="41130-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41130-123">場合、 **FillSchema**のメソッド、 **OleDbDataAdapter**を複数の結果セットを返すコマンドのオブジェクトが呼び出されると、最初の結果セットからスキーマ情報のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="41130-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="41130-124">ときに複数の結果のスキーマ情報セットを返すを使用して、 **OleDbDataAdapter**を指定することをお勧め、 **MissingSchemaAction**の**AddWithKey**呼び出すときに、スキーマ情報を取得し、**塗りつぶし**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41130-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41130-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="41130-125">See Also</span></span>  
 [<span data-ttu-id="41130-126">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="41130-126">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="41130-127">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="41130-127">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="41130-128">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="41130-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="41130-129">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="41130-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
