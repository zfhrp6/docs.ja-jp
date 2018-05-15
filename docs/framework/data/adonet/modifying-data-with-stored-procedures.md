---
title: ストアド プロシージャでのデータの変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: d9dcda6b93fbc036818ad2ad43da4bfac95f6833
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="17dd4-102">ストアド プロシージャでのデータの変更</span><span class="sxs-lookup"><span data-stu-id="17dd4-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="17dd4-103">ストアド プロシージャは、入力パラメーターとしてデータを受け取り、出力パラメーター、結果セット、または戻り値としてデータを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="17dd4-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="17dd4-104">以下のサンプルでは、入力パラメーター、出力パラメーター、および戻り値が ADO.NET によってどのようにやり取りされるかを示したものです。</span><span class="sxs-lookup"><span data-stu-id="17dd4-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="17dd4-105">この例では、主キー列が SQL Server データベースの ID 列であるテーブルに新しいレコードを挿入しています。</span><span class="sxs-lookup"><span data-stu-id="17dd4-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17dd4-106">SQL Server のストアド プロシージャで、<xref:System.Data.SqlClient.SqlDataAdapter> を使用してデータを編集または削除する場合、ストアド プロシージャの定義に SET NOCOUNT ON は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="17dd4-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="17dd4-107">処理された行数がゼロとして返され、`DataAdapter` によって同時実行の競合として解釈されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="17dd4-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="17dd4-108">この場合、<xref:System.Data.DBConcurrencyException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="17dd4-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17dd4-109">例</span><span class="sxs-lookup"><span data-stu-id="17dd4-109">Example</span></span>  
 <span data-ttu-id="17dd4-110">このサンプルでは、次のストアド プロシージャを使用してに新しいカテゴリを挿入、 **Northwind** **カテゴリ**テーブル。</span><span class="sxs-lookup"><span data-stu-id="17dd4-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="17dd4-111">ストアド プロシージャ値を受け取り、 **CategoryName** 、SCOPE_IDENTITY() を使用して、入力パラメーターとして列が id フィールドの新しい値を取得する関数**CategoryID**、返す出力パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="17dd4-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="17dd4-112">RETURN ステートメントを使用して、@@ROWCOUNT挿入された行の数を返す関数。</span><span class="sxs-lookup"><span data-stu-id="17dd4-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="17dd4-113">上述の `InsertCategory` ストアド プロシージャを <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> の <xref:System.Data.SqlClient.SqlDataAdapter> のソースとして使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="17dd4-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="17dd4-114">`@Identity` 出力パラメーターは、<xref:System.Data.DataSet> の `Update` メソッドが呼び出され、データベースにレコードが挿入された後で <xref:System.Data.SqlClient.SqlDataAdapter> に反映されます。</span><span class="sxs-lookup"><span data-stu-id="17dd4-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="17dd4-115">戻り値も取得されます。</span><span class="sxs-lookup"><span data-stu-id="17dd4-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17dd4-116">使用する場合、<xref:System.Data.OleDb.OleDbDataAdapter>を持つパラメーターを指定する必要があります、<xref:System.Data.ParameterDirection>の**ReturnValue**他のパラメーターの前にします。</span><span class="sxs-lookup"><span data-stu-id="17dd4-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="17dd4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="17dd4-117">See Also</span></span>  
 [<span data-ttu-id="17dd4-118">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="17dd4-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="17dd4-119">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="17dd4-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="17dd4-120">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="17dd4-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="17dd4-121">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="17dd4-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
