---
title: "DataTable の作成"
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 68f8272aa0f525c04120f129057e6151e42ffee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datatable"></a><span data-ttu-id="b5921-102">DataTable の作成</span><span class="sxs-lookup"><span data-stu-id="b5921-102">Creating a DataTable</span></span>
<span data-ttu-id="b5921-103"><xref:System.Data.DataTable> は 1 つのインメモリ リレーショナル データのテーブルを表します。DataTable は単独で作成および使用することも、他の .NET Framework オブジェクトから <xref:System.Data.DataSet> のメンバーとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b5921-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="b5921-104">作成することができます、 **DataTable** 、適切なを使用してオブジェクト**DataTable**コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="b5921-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="b5921-105">追加することができます、**データセット**を使用して、**追加**に追加する方法、 **DataTable**オブジェクトの**テーブル**コレクション。</span><span class="sxs-lookup"><span data-stu-id="b5921-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="b5921-106">作成することも**DataTable**内のオブジェクトは、**データセット**を使用して、**塗りつぶし**または**FillSchema**のメソッド、 **DataAdapter**オブジェクト、または、定義済みまたは推論されたスキーマを使用して XML から、 **ReadXml**、 **ReadXmlSchema**、または**InferXmlSchema**メソッド、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="b5921-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="b5921-107">追加した後に注意してください、 **DataTable**のメンバーとして、**テーブル**いずれかのコレクション**データセット**、他の任意ののテーブルのコレクションに追加することはできません**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="b5921-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="b5921-108">作成する場合、 **DataTable**スキーマ (つまり、構造体) はありません。</span><span class="sxs-lookup"><span data-stu-id="b5921-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="b5921-109">テーブルのスキーマを定義するのには必要がありますを作成し、追加<xref:System.Data.DataColumn>オブジェクトを**列**テーブルのコレクション。</span><span class="sxs-lookup"><span data-stu-id="b5921-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="b5921-110">テーブルの主キー列を定義し、作成して追加**制約**オブジェクトを**制約**テーブルのコレクション。</span><span class="sxs-lookup"><span data-stu-id="b5921-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="b5921-111">スキーマを定義した後、 **DataTable**、行のデータをテーブルに追加するには追加することによって**DataRow**オブジェクトを**行**テーブルのコレクション。</span><span class="sxs-lookup"><span data-stu-id="b5921-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="b5921-112">値を指定する必要はありません、<xref:System.Data.DataTable.TableName%2A>プロパティを作成するとき、 **DataTable**; プロパティを指定するには、いつでもまたはすることが空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="b5921-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="b5921-113">ただし、せず、テーブルを追加する、 **TableName**値を**データセット**、テーブルがテーブルの増分の既定の名前を指定する*N*、table0"Table"で開始します。</span><span class="sxs-lookup"><span data-stu-id="b5921-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5921-114">避けることをお勧め、"テーブル*N*"名前付け規則を指定するときに、 **TableName**値、指定した名前の既存の既定のテーブル名と競合する場合もあるため、**データセット**.</span><span class="sxs-lookup"><span data-stu-id="b5921-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="b5921-115">指定した名前が既に存在する場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b5921-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="b5921-116">次の例のインスタンスを作成する、 **DataTable**オブジェクトし、"Customers"という名前を割り当てる</span><span class="sxs-lookup"><span data-stu-id="b5921-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="b5921-117">次の例のインスタンスを作成する、 **DataTable**に追加することによって、**テーブル**のコレクション、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="b5921-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5921-118">参照</span><span class="sxs-lookup"><span data-stu-id="b5921-118">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [<span data-ttu-id="b5921-119">DataTables</span><span class="sxs-lookup"><span data-stu-id="b5921-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="b5921-120">DataAdapter からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="b5921-120">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="b5921-121">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="b5921-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="b5921-122">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="b5921-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="b5921-123">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="b5921-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
