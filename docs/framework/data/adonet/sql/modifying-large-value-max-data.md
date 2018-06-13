---
title: ADO.NET での大きい値 (max) データの変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 285803d92474efd3268816d1af06eb3ff4abbc79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365593"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="fdd68-102">ADO.NET での大きい値 (max) データの変更</span><span class="sxs-lookup"><span data-stu-id="fdd68-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="fdd68-103">ラージ オブジェクト (LOB) データ型は、最大行サイズが 8 KB を超えるデータ型です。</span><span class="sxs-lookup"><span data-stu-id="fdd68-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="fdd68-104">SQL Server では、`max`、`varchar`、および `nvarchar` の各データ型に `varbinary` 指定子が用意されており、2^32 バイトの値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="fdd68-105">テーブル列および Transact-SQL 変数により、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` データ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="fdd68-106">ADO.NET では、`max` データ型は、`DataReader` によってフェッチすることができ、特殊な処理を行うことなく入力パラメーターと出力パラメーター両方の値として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="fdd68-107">サイズの大きい `varchar` データ型の場合は、データを段階的に取得および更新できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="fdd68-108">`max` データ型は、Transact-SQL 変数として比較に使用したり、連結に使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="fdd68-109">これらは SELECT ステートメントの DISTINCT 句、ORDER BY 句、GROUP BY 句で使用できるほか、集約、結合、サブクエリでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="fdd68-110">次の表は、SQL Server オンライン ブックのドキュメントへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="fdd68-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="fdd68-111">**SQL Server オンライン ブック**</span><span class="sxs-lookup"><span data-stu-id="fdd68-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="fdd68-112">大きな値データ型の使用</span><span class="sxs-lookup"><span data-stu-id="fdd68-112">Using Large-Value Data Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="fdd68-113">大きい値型の制限事項</span><span class="sxs-lookup"><span data-stu-id="fdd68-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="fdd68-114">`max` データ型には、小さいデータ型にはない、次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
-   <span data-ttu-id="fdd68-115">`sql_variant` に大きい `varchar` データ型を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fdd68-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
-   <span data-ttu-id="fdd68-116">大きい `varchar` 列はインデックス内のキー列として指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="fdd68-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="fdd68-117">非クラスター化インデックスに含まれる列で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
-   <span data-ttu-id="fdd68-118">大きい `varchar` 列はパーティション分割のキー列として使用できません。</span><span class="sxs-lookup"><span data-stu-id="fdd68-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="fdd68-119">Transact-SQL での大きい値型の使用</span><span class="sxs-lookup"><span data-stu-id="fdd68-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="fdd68-120">Transact-SQL の `OPENROWSET` 関数は、リモート データへの接続およびアクセスに 1 回だけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="fdd68-121">この関数には、OLE DB データ ソースからリモート データにアクセスするために必要な、すべての接続情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="fdd68-122">`OPENROWSET` は、クエリの FROM 句でテーブル名と同様に参照できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="fdd68-123">OLE DB プロバイダーの機能に従って、INSERT、UPDATE、または DELETE ステートメントのターゲット テーブルとして参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="fdd68-124">`OPENROWSET` 関数には、`BULK` 行セット プロバイダーが含まれており、データをターゲット テーブルに読み込むことなく、ファイルから直接読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="fdd68-125">これにより、`OPENROWSET` を単純な INSERT SELECT ステートメントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="fdd68-126">`OPENROWSET``BULK`オプション引数により、開始およびデータの読み取りを終了する場所、エラーに対処する方法、およびデータを解釈する方法に大幅な制御。</span><span class="sxs-lookup"><span data-stu-id="fdd68-126">The `OPENROWSET``BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="fdd68-127">たとえば、データ ファイルを 1 行として、あるいは `varbinary`、`varchar`、または `nvarchar` 型の 1 列の行セットとして読み取るように指定できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="fdd68-128">完全な構文とオプションについては、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdd68-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="fdd68-129">次の例では、AdventureWorks サンプル データベースの ProductPhoto テーブルに写真を挿入しています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="fdd68-130">使用する場合、`BULK``OPENROWSET`プロバイダー、すべての列に値を挿入しない場合でも、列の名前付きの一覧を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdd68-130">When using the `BULK``OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="fdd68-131">この場合の主キーは ID 列として定義され、列リストから省略することもできます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="fdd68-132">ただし、`OPENROWSET` ステートメントの最後に相関関係名 (この場合は ThumbnailPhoto) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdd68-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="fdd68-133">これにより、ファイルが読み込まれる `ProductPhoto` テーブルの列との相関関係が定義されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
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
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="fdd68-134">UPDATE .WRITE を使用したデータの更新</span><span class="sxs-lookup"><span data-stu-id="fdd68-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="fdd68-135">Transact-SQL の UPDATE ステートメントでは、`varchar(max)`、`nvarchar(max)`、または `varbinary(max)` 列の内容を変更するための、新しい WRITE 構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="fdd68-136">これにより、データの部分的な更新が可能になります。</span><span class="sxs-lookup"><span data-stu-id="fdd68-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="fdd68-137">次に UPDATE .WRITE 構文を省略形で示します。</span><span class="sxs-lookup"><span data-stu-id="fdd68-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="fdd68-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="fdd68-138">UPDATE</span></span>  
  
 <span data-ttu-id="fdd68-139">{ *\<object>* }</span><span class="sxs-lookup"><span data-stu-id="fdd68-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="fdd68-140">SET</span><span class="sxs-lookup"><span data-stu-id="fdd68-140">SET</span></span>  
  
 <span data-ttu-id="fdd68-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span><span class="sxs-lookup"><span data-stu-id="fdd68-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="fdd68-142">WRITE メソッドには、ことを指定の値のセクションで、 *column_name*が変更されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="fdd68-143">式が値をコピーする、 *column_name*、`@Offset`に式が書き込まれたが、開始点は、および`@Length`引数は、列のセクションの長さ。</span><span class="sxs-lookup"><span data-stu-id="fdd68-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="fdd68-144">If</span><span class="sxs-lookup"><span data-stu-id="fdd68-144">If</span></span>|<span data-ttu-id="fdd68-145">Then</span><span class="sxs-lookup"><span data-stu-id="fdd68-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="fdd68-146">expression が NULL</span><span class="sxs-lookup"><span data-stu-id="fdd68-146">The expression is set to NULL</span></span>|<span data-ttu-id="fdd68-147">`@Length` 無視されますとで値*column_name*は切り捨てられます内の指定した`@Offset`です。</span><span class="sxs-lookup"><span data-stu-id="fdd68-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="fdd68-148">`@Offset` が NULL</span><span class="sxs-lookup"><span data-stu-id="fdd68-148">`@Offset` is NULL</span></span>|<span data-ttu-id="fdd68-149">更新操作では、既存の最後に式を追加します。 *column_name*値および`@Length`は無視されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="fdd68-150">`@Offset` が column_name の値の長さより長い</span><span class="sxs-lookup"><span data-stu-id="fdd68-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="fdd68-151">SQL Server からエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="fdd68-152">`@Length` が NULL</span><span class="sxs-lookup"><span data-stu-id="fdd68-152">`@Length` is NULL</span></span>|<span data-ttu-id="fdd68-153">更新操作により `@Offset` の値の `column_name` から最後までのすべてのデータが削除されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="fdd68-154">`@Offset` または `@Length` のいずれにも負数を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="fdd68-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdd68-155">例</span><span class="sxs-lookup"><span data-stu-id="fdd68-155">Example</span></span>  
 <span data-ttu-id="fdd68-156">この Transact-SQL の例では、AdventureWorks データベースの Document テーブルの `nvarchar(max)` 列である DocumentSummary の値の一部が更新されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="fdd68-157">置換後の単語、置換する単語の既存データ内での開始位置 (オフセット)、置換する文字数 (長さ) を指定することで、'components' という単語が 'features' という単語に置換されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="fdd68-158">この例では、結果を比較するために、UPDATE ステートメントの前後に SELECT ステートメントを指定しています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="fdd68-159">ADO.NET での大きい値型の使用</span><span class="sxs-lookup"><span data-stu-id="fdd68-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="fdd68-160">ADO.NET での大きな値の型を使用するには、大きな値の型として指定することによって<xref:System.Data.SqlClient.SqlParameter>内のオブジェクト、<xref:System.Data.SqlClient.SqlDataReader>の結果を返すセット、またはを使用して、<xref:System.Data.SqlClient.SqlDataAdapter>を埋める、 `DataSet` /`DataTable`です。</span><span class="sxs-lookup"><span data-stu-id="fdd68-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="fdd68-161">大きい値型と、関連する小さい値型の使用方法に違いはありません。</span><span class="sxs-lookup"><span data-stu-id="fdd68-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="fdd68-162">GetSqlBytes を使用したデータの取得</span><span class="sxs-lookup"><span data-stu-id="fdd68-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="fdd68-163">`GetSqlBytes` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varbinary(max)` 列の内容を取得できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="fdd68-164">次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `varbinary(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBytes> として取得されることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="fdd68-165">GetSqlChars を使用したデータの取得</span><span class="sxs-lookup"><span data-stu-id="fdd68-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="fdd68-166">`GetSqlChars` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varchar(max)` または `nvarchar(max)` 列の内容を取得できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="fdd68-167">次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `nvarchar(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが取得されることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="fdd68-168">GetSqlBinary を使用したデータの取得</span><span class="sxs-lookup"><span data-stu-id="fdd68-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="fdd68-169">`GetSqlBinary` の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、`varbinary(max)` 列の内容を取得できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="fdd68-170">次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlCommand> という名前の `cmd` オブジェクトによってテーブルから `varbinary(max)` データが選択され、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが <xref:System.Data.SqlTypes.SqlBinary> ストリームとして取得されることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="fdd68-171">GetBytes を使用したデータの取得</span><span class="sxs-lookup"><span data-stu-id="fdd68-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="fdd68-172">`GetBytes` の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、指定された配列のオフセットから開始するバイト配列に、指定された列のオフセットからバイトのストリームが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="fdd68-173">次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってバイトがバイト配列に読み込まれることが想定されています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="fdd68-174">ただし `GetSqlBytes` とは異なり、`GetBytes` では配列バッファーのサイズを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdd68-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="fdd68-175">GetValue を使用したデータの取得</span><span class="sxs-lookup"><span data-stu-id="fdd68-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="fdd68-176">`GetValue` の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、指定した列オフセットから値が配列に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="fdd68-177">次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによって、最初の列のオフセットからバイナリ データが取得され、2 番目の列のオフセットから文字列データが取得されることが想定されています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="fdd68-178">大きい値型から CLR 型への変換</span><span class="sxs-lookup"><span data-stu-id="fdd68-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="fdd68-179">`varchar(max)` などの任意の文字列変換メソッドを使用して、`nvarchar(max)` または `ToString` 列の内容を変換できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="fdd68-180">次のコード フラグメントでは、<xref:System.Data.SqlClient.SqlDataReader> という名前の `reader` オブジェクトによってデータが取得されることが想定されています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="fdd68-181">例</span><span class="sxs-lookup"><span data-stu-id="fdd68-181">Example</span></span>  
 <span data-ttu-id="fdd68-182">次のコードでは、`LargePhoto` データベースの `ProductPhoto` テーブルから名前と `AdventureWorks` オブジェクトが取得され、ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="fdd68-183">このアセンブリは、<xref:System.Drawing> 名前空間への参照を指定してコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdd68-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="fdd68-184"><xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> の <xref:System.Data.SqlClient.SqlDataReader> メソッドにより、<xref:System.Data.SqlTypes.SqlBytes> プロパティを公開する `Stream` オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="fdd68-185">コードでは、これを使用して、新しい`Bitmap`オブジェクト、および、Gif を保存し、`ImageFormat`です。</span><span class="sxs-lookup"><span data-stu-id="fdd68-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="fdd68-186">大きな値型パラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="fdd68-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="fdd68-187">大きい値型は、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内の小さい値型と同じ方法で、<xref:System.Data.SqlClient.SqlParameter> オブジェクト内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="fdd68-188">として大きな値の型を取得する<xref:System.Data.SqlClient.SqlParameter>値は、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="fdd68-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="fdd68-189">このコードでは、次の GetDocumentSummary ストアド プロシージャが、AdventureWorks サンプル データベースに存在することが想定されています。</span><span class="sxs-lookup"><span data-stu-id="fdd68-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="fdd68-190">ストアド プロシージャでは、という名前の入力パラメーター@DocumentIDである DocumentSummary 列の内容を返します、@DocumentSummary出力パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="fdd68-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="fdd68-191">例</span><span class="sxs-lookup"><span data-stu-id="fdd68-191">Example</span></span>  
 <span data-ttu-id="fdd68-192">ADO.NET コードにより、<xref:System.Data.SqlClient.SqlConnection> および <xref:System.Data.SqlClient.SqlCommand> オブジェクトが作成され、GetDocumentSummary ストアド プロシージャが実行されることで、ドキュメントの概要が取得され、大きい値型として格納されます。</span><span class="sxs-lookup"><span data-stu-id="fdd68-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="fdd68-193">コード値を渡す、@DocumentID入力パラメーター、およびに渡された結果が表示されます、@DocumentSummaryコンソール ウィンドウでパラメーターを出力します。</span><span class="sxs-lookup"><span data-stu-id="fdd68-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fdd68-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdd68-194">See Also</span></span>  
 [<span data-ttu-id="fdd68-195">SQL Server のバイナリ データと大きな値のデータ</span><span class="sxs-lookup"><span data-stu-id="fdd68-195">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="fdd68-196">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="fdd68-196">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="fdd68-197">ADO.NET における SQL Server データ操作</span><span class="sxs-lookup"><span data-stu-id="fdd68-197">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="fdd68-198">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="fdd68-198">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
