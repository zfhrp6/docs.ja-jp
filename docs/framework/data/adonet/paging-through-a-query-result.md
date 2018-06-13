---
title: クエリ結果のページング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 73475f8521b4112929339cc7f1116e36ffebedb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358969"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="af83f-102">クエリ結果のページング</span><span class="sxs-lookup"><span data-stu-id="af83f-102">Paging Through a Query Result</span></span>
<span data-ttu-id="af83f-103">クエリ結果のページングとは、クエリ結果をデータの小さなサブセット、つまりページに分けて返すプロセスです。</span><span class="sxs-lookup"><span data-stu-id="af83f-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="af83f-104">クエリ結果のページングは、結果を管理しやすい小さな単位でユーザーに表示するために行われる一般的な処理です。</span><span class="sxs-lookup"><span data-stu-id="af83f-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="af83f-105">**DataAdapter**のオーバー ロードによって、データのページのみを返すための機能を提供、**塗りつぶし**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="af83f-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="af83f-106">ただし、このできない可能性がありますので、大規模なクエリ結果のページングに最適な選択肢ですが、 **DataAdapter**塗りつぶしますターゲット<xref:System.Data.DataTable>または<xref:System.Data.DataSet>のみ、要求されたレコードを返すリソースで、クエリ全体が引き続き使用されます。</span><span class="sxs-lookup"><span data-stu-id="af83f-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="af83f-107">クエリ全体を返す必要があるリソースを使用せずにデータ ソースから 1 ページ分のデータを返すには、必要な行だけ返すように限定する抽出条件をクエリに追加します。</span><span class="sxs-lookup"><span data-stu-id="af83f-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="af83f-108">使用する、**塗りつぶし**、データのページを返す方法を指定する、 **startRecord**最初のレコードのデータのページで、パラメーター、および**maxRecords**の数のパラメーターデータのページのレコードです。</span><span class="sxs-lookup"><span data-stu-id="af83f-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="af83f-109">次のコード例を使用する方法を示しています、**塗りつぶし**ページ サイズが 5 つのレコードは、クエリ結果の最初のページを返すメソッドをします。</span><span class="sxs-lookup"><span data-stu-id="af83f-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="af83f-110">前の例で、**データセット**で 5 つのレコードが全体が入力のみ**Orders**テーブルが返されます。</span><span class="sxs-lookup"><span data-stu-id="af83f-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="af83f-111">入力する、**データセット**これら同じ 5 つのレコードが 5 つのレコードだけを返すは、TOP を使用して、次のコード例のように、SQL ステートメントの WHERE 句です。</span><span class="sxs-lookup"><span data-stu-id="af83f-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")   
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 <span data-ttu-id="af83f-112">この方法でクエリ結果をページングするときは、次のレコード ページを返すコマンドに一意の ID を渡すために、行を順序付けする固有の識別子を保存する必要があります。次のコード サンプルで示します。</span><span class="sxs-lookup"><span data-stu-id="af83f-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="af83f-113">オーバー ロードを使用してレコードの次のページを返す、**塗りつぶし**を受け取るメソッド、 **startRecord**と**maxRecords**パラメーター、インクリメントでは、現在のレコード インデックスページ サイズと塗りつぶしテーブル。</span><span class="sxs-lookup"><span data-stu-id="af83f-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="af83f-114">レコードの 1 つだけのページに追加される場合でも、データベース サーバーがクエリ全体結果を返すことに注意してください、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="af83f-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="af83f-115">次のデータ ページを格納する前にテーブル行をクリアするコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="af83f-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="af83f-116">データベース サーバーとのやり取りを減らすために、ローカルのキャッシュに、返された一定数の行を保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="af83f-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="af83f-117">データベース サーバーによってクエリ全体を返さずに次のレコード ページを返すには、SELECT ステートメントに限定的な抽出条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="af83f-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="af83f-118">上の例では最後に返されたレコードが保存されますが、次のコード サンプルに示すようにそのレコードを WHERE 句で使用するとクエリの開始点を指定できます。</span><span class="sxs-lookup"><span data-stu-id="af83f-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="af83f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="af83f-119">See Also</span></span>  
 [<span data-ttu-id="af83f-120">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="af83f-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="af83f-121">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="af83f-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
