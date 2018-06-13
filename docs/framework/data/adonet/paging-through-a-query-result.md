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
# <a name="paging-through-a-query-result"></a>クエリ結果のページング
クエリ結果のページングとは、クエリ結果をデータの小さなサブセット、つまりページに分けて返すプロセスです。 クエリ結果のページングは、結果を管理しやすい小さな単位でユーザーに表示するために行われる一般的な処理です。  
  
 **DataAdapter**のオーバー ロードによって、データのページのみを返すための機能を提供、**塗りつぶし**メソッドです。 ただし、このできない可能性がありますので、大規模なクエリ結果のページングに最適な選択肢ですが、 **DataAdapter**塗りつぶしますターゲット<xref:System.Data.DataTable>または<xref:System.Data.DataSet>のみ、要求されたレコードを返すリソースで、クエリ全体が引き続き使用されます。 クエリ全体を返す必要があるリソースを使用せずにデータ ソースから 1 ページ分のデータを返すには、必要な行だけ返すように限定する抽出条件をクエリに追加します。  
  
 使用する、**塗りつぶし**、データのページを返す方法を指定する、 **startRecord**最初のレコードのデータのページで、パラメーター、および**maxRecords**の数のパラメーターデータのページのレコードです。  
  
 次のコード例を使用する方法を示しています、**塗りつぶし**ページ サイズが 5 つのレコードは、クエリ結果の最初のページを返すメソッドをします。  
  
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
  
 前の例で、**データセット**で 5 つのレコードが全体が入力のみ**Orders**テーブルが返されます。 入力する、**データセット**これら同じ 5 つのレコードが 5 つのレコードだけを返すは、TOP を使用して、次のコード例のように、SQL ステートメントの WHERE 句です。  
  
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
  
 この方法でクエリ結果をページングするときは、次のレコード ページを返すコマンドに一意の ID を渡すために、行を順序付けする固有の識別子を保存する必要があります。次のコード サンプルで示します。  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 オーバー ロードを使用してレコードの次のページを返す、**塗りつぶし**を受け取るメソッド、 **startRecord**と**maxRecords**パラメーター、インクリメントでは、現在のレコード インデックスページ サイズと塗りつぶしテーブル。 レコードの 1 つだけのページに追加される場合でも、データベース サーバーがクエリ全体結果を返すことに注意してください、**データセット**です。 次のデータ ページを格納する前にテーブル行をクリアするコード サンプルを次に示します。 データベース サーバーとのやり取りを減らすために、ローカルのキャッシュに、返された一定数の行を保存することもできます。  
  
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
  
 データベース サーバーによってクエリ全体を返さずに次のレコード ページを返すには、SELECT ステートメントに限定的な抽出条件を指定します。 上の例では最後に返されたレコードが保存されますが、次のコード サンプルに示すようにそのレコードを WHERE 句で使用するとクエリの開始点を指定できます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
