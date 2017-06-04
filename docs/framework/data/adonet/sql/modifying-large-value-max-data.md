---
title: "ADO.NET での大きい値 (max) データの変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# ADO.NET での大きい値 (max) データの変更
ラージ オブジェクト \(LOB\) データ型は、最大行サイズが 8 KB を超えるデータ型です。  SQL Server では、`varchar`、`nvarchar`、および `varbinary` の各データ型に `max` 指定子が用意されており、2^32 バイトの値を格納できます。  テーブル列および Transact\-SQL 変数により、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` データ型を指定できます。  ADO.NET では、`max` データ型は、`DataReader` によってフェッチすることができ、特殊な処理を行うことなく入力パラメーターと出力パラメーター両方の値として指定することもできます。  サイズの大きい `varchar` データ型の場合は、データを段階的に取得および更新できます。  
  
 `max` データ型は、Transact\-SQL 変数として比較に使用したり、連結に使用したりできます。  これらは SELECT ステートメントの DISTINCT 句、ORDER BY 句、GROUP BY 句で使用できるほか、集約、結合、サブクエリでも使用できます。  
  
 次の表は、SQL Server オンライン ブックのドキュメントへのリンクを提供します。  
  
 **SQL Server オンライン ブック**  
  
1.  [大きい値のデータ型の使用](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## 大きい値型の制限事項  
 `max` データ型には、小さいデータ型にはない、次の制限事項が適用されます。  
  
-   `sql_variant` に大きい `varchar` データ型を含めることはできません。  
  
-   大きい `varchar` 列はインデックス内のキー列として指定することはできません。  非クラスター化インデックスに含まれる列で使用できます。  
  
-   大きい `varchar` 列はパーティション分割のキー列として使用できません。  
  
## Transact\-SQL での大きい値型の使用  
 Transact\-SQL の `OPENROWSET` 関数は、リモート データへの接続およびアクセスに 1 回だけ使用できます。  この関数には、OLE DB データ ソースからリモート データにアクセスするために必要な、すべての接続情報が含まれています。  `OPENROWSET` は、クエリの FROM 句でテーブル名と同様に参照できます。  OLE DB プロバイダーの機能に従って、INSERT、UPDATE、または DELETE ステートメントのターゲット テーブルとして参照することもできます。  
  
 `OPENROWSET` 関数には、`BULK` 行セット プロバイダーが含まれており、データをターゲット テーブルに読み込むことなく、ファイルから直接読み取ることができます。  これにより、`OPENROWSET` を単純な INSERT SELECT ステートメントで使用できます。  
  
 `OPENROWSET`  `BULK` オプション引数により、データの読み取りの開始位置および終了位置、エラーの処理、データの解釈の制御が大幅に容易になります。  たとえば、データ ファイルを 1 行として、あるいは `varbinary`、`varchar`、または `nvarchar` 型の 1 列の行セットとして読み取るように指定できます。  完全な構文とオプションについては、SQL Server オンライン ブックを参照してください。  
  
 次の例では、AdventureWorks サンプル データベースの ProductPhoto テーブルに写真を挿入しています。  `BULK``OPENROWSET` プロバイダーを使用する場合は、すべての列に値を挿入しない場合でも、列名を挙げてリストを作成する必要があります。  この場合の主キーは ID 列として定義され、列リストから省略することもできます。  ただし、`OPENROWSET` ステートメントの最後に相関関係名 \(この場合は ThumbnailPhoto\) を指定する必要があります。  これにより、ファイルが読み込まれる `ProductPhoto` テーブルの列との相関関係が定義されます。  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## UPDATE .WRITE を使用したデータの更新  
 Transact\-SQL の UPDATE ステートメントでは、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` 列の内容を変更するための、新しい WRITE 構文を使用できます。  これにより、データの部分的な更新が可能になります。  次に UPDATE .WRITE 構文を省略形で示します。  
  
 UPDATE  
  
 { *\<object\>* }  
  
 SET  
  
 { *column\_name* \= { .WRITE \( *expression* , @Offset , @Length \) }  
  
 WRITE メソッドは、*column\_name* の値のセクションが変更されることを指定します。  この式は *column\_name* にコピーされる値で、`@Offset` は式が記述される開始位置であり、`@Length` 引数は列のセクションの長さを示します。  
  
|If|Then|  
|--------|----------|  
|expression が NULL|`@Length` は無視され、*column\_name* の値は指定された `@Offset` で切り捨てられます。|  
|`@Offset` が NULL|更新操作によって既存の *column\_name* の値の最後に式が追加され、`@Length` が無視されます。|  
|`@Offset` が column\_name の値の長さより長い|SQL Server からエラーが返されます。|  
|`@Length` が NULL|更新操作により `column_name` の値の `@Offset` から最後までのすべてのデータが削除されます。|  
  
> [!NOTE]
>  `@Offset` または `@Length` のいずれにも負数を指定することはできません。  
  
## 例  
 この Transact\-SQL の例では、AdventureWorks データベースの Document テーブルの `nvarchar(max)` 列である DocumentSummary の値の一部が更新されます。  置換後の単語、置換する単語の既存データ内での開始位置 \(オフセット\)、置換する文字数 \(長さ\) を指定することで、'components' という単語が 'features' という単語に置換されます。  この例では、結果を比較するために、UPDATE ステートメントの前後に SELECT ステートメントを指定しています。  
  
```  
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## ADO.NET での大きい値型の使用  
 大きい値型を ADO.NET で使用するには、大きい値型を <xref:System.Data.SqlClient.SqlDataReader> で <xref:System.Data.SqlClient.SqlParameter> オブジェクトとして指定して結果セットを返すようにするか、または <xref:System.Data.SqlClient.SqlDataAdapter> を使用して `DataSet`\/`DataTable` に入力します。  大きい値型と、関連する小さい値型の使用方法に違いはありません。  
  
### GetSqlBytes を使用したデータの取得  
 <xref:System.Data.SqlClient.SqlDataReader> の `GetSqlBytes` メソッドを使用して、`varbinary(max)` 列の内容を取得できます。  次のコード フラグメントでは、`cmd` という名前の <xref:System.Data.SqlClient.SqlCommand> オブジェクトによってテーブルから `varbinary(max)` データが選択され、`reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBytes> として取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### GetSqlChars を使用したデータの取得  
 <xref:System.Data.SqlClient.SqlDataReader> の `GetSqlChars` メソッドを使用して、`varchar(max)` または `nvarchar(max)` 列の内容を取得できます。  次のコード フラグメントでは、`cmd` という名前の <xref:System.Data.SqlClient.SqlCommand> オブジェクトによってテーブルから `nvarchar(max)` データが選択され、`reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトによってデータが取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### GetSqlBinary を使用したデータの取得  
 <xref:System.Data.SqlClient.SqlDataReader> の `GetSqlBinary` メソッドを使用して、`varbinary(max)` 列の内容を取得できます。  次のコード フラグメントでは、`cmd` という名前の <xref:System.Data.SqlClient.SqlCommand> オブジェクトによってテーブルから `varbinary(max)` データが選択され、`reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBinary> ストリームとして取得されることを想定しています。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### GetBytes を使用したデータの取得  
 <xref:System.Data.SqlClient.SqlDataReader> の `GetBytes` メソッドにより、指定された配列のオフセットから開始するバイト配列に、指定された列のオフセットからバイトのストリームが読み込まれます。  次のコード フラグメントでは、`reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトによってバイトがバイト配列に読み込まれることが想定されています。  ただし `GetSqlBytes` とは異なり、`GetBytes` では配列バッファーのサイズを指定する必要があります。  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### GetValue を使用したデータの取得  
 <xref:System.Data.SqlClient.SqlDataReader> の `GetValue` メソッドにより、指定した列オフセットから値が配列に読み込まれます。  次のコード フラグメントでは、`reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトによって、最初の列のオフセットからバイナリ データが取得され、2 番目の列のオフセットから文字列データが取得されることが想定されています。  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## 大きい値型から CLR 型への変換  
 `ToString` などの任意の文字列変換メソッドを使用して、`varchar(max)` または `nvarchar(max)` 列の内容を変換できます。  次のコード フラグメントでは、`reader` という名前の <xref:System.Data.SqlClient.SqlDataReader> オブジェクトによってデータが取得されることが想定されています。  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### 例  
 次のコードでは、`AdventureWorks` データベースの `ProductPhoto` テーブルから名前と `LargePhoto` オブジェクトが取得され、ファイルに保存されます。  このアセンブリは、<xref:System.Drawing> 名前空間への参照を指定してコンパイルする必要があります。  <xref:System.Data.SqlClient.SqlDataReader> の <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> メソッドにより、`Stream` プロパティを公開する <xref:System.Data.SqlTypes.SqlBytes> オブジェクトが返されます。  コードではこのオブジェクトを使用して新しい `Bitmap` オブジェクトが作成され、Gif`ImageFormat` に保存されます。  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## 大きな値型パラメーターの使用  
 大きい値型は、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内の小さい値型と同じ方法で、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内で使用できます。  次の例に示すように、大きい値型は <xref:System.Data.SqlClient.SqlParameter> 値として取得することができます。  このコードでは、次の GetDocumentSummary ストアド プロシージャが、AdventureWorks サンプル データベースに存在することが想定されています。  ストアド プロシージャでは @DocumentID という名前の入力パラメーターを受け取り、@DocumentSummary 出力パラメーターの DocumentSummary 列の内容を返します。  
  
```  
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### 例  
 ADO.NET コードにより、<xref:System.Data.SqlClient.SqlConnection> および <xref:System.Data.SqlClient.SqlCommand> オブジェクトが作成され、GetDocumentSummary ストアド プロシージャが実行されることで、ドキュメントの概要が取得され、大きい値型として格納されます。  このコードによって @DocumentID 入力パラメーターの値が渡され、@DocumentSummary 出力パラメーターに戻された結果がコンソール ウィンドウに表示されます。  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## 参照  
 [SQL Server のバイナリ データと大きな値のデータ](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)   
 [SQL Server データ型のマッピング](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)   
 [ADO.NET における SQL Server データ操作](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)