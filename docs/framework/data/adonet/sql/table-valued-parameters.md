---
title: "テーブル値パラメーター"
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
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e881213979d32cb9335f01d2804c35c19856b5e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="table-valued-parameters"></a><span data-ttu-id="adb7f-102">テーブル値パラメーター</span><span class="sxs-lookup"><span data-stu-id="adb7f-102">Table-Valued Parameters</span></span>
<span data-ttu-id="adb7f-103">テーブル値パラメーターを使用すると、ラウンド トリップを何度も繰り返したり、サーバー側にデータを処理するための特殊なロジックを組み込んだりすることなく、複数行のデータをクライアント アプリケーションから [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] へと簡単にマーシャリングできます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="adb7f-104">テーブル値パラメーターを使用すると、クライアント アプリケーションのデータ行をカプセル化して単一のパラメーター化コマンドでサーバーに送ることができます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="adb7f-105">受信データ行はテーブル変数に格納され、[!INCLUDE[tsql](../../../../../includes/tsql-md.md)] によって操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="adb7f-106">テーブル値パラメーターの列値には、[!INCLUDE[tsql](../../../../../includes/tsql-md.md)] の標準的な SELECT ステートメントを使ってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="adb7f-107">テーブル値パラメーターは厳密に型指定されており、その構造は自動的に検証されます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="adb7f-108">テーブル値パラメーターのサイズは、サーバーのメモリによってのみ制限されます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adb7f-109">テーブル値パラメーターにデータを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="adb7f-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="adb7f-110">テーブル値パラメーターは入力専用です。OUTPUT キーワードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="adb7f-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="adb7f-111">テーブル値パラメーターの詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="adb7f-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="adb7f-112">リソース</span><span class="sxs-lookup"><span data-stu-id="adb7f-112">Resource</span></span>|<span data-ttu-id="adb7f-113">説明</span><span class="sxs-lookup"><span data-stu-id="adb7f-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="adb7f-114">[テーブル値パラメーター (データベース エンジン)](http://go.microsoft.com/fwlink/?LinkId=98363)で[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="adb7f-114">[Table-Valued Parameters (Database Engine)](http://go.microsoft.com/fwlink/?LinkId=98363) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="adb7f-115">テーブル値パラメーターの作成方法および使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="adb7f-116">[ユーザー定義テーブル型](http://go.microsoft.com/fwlink/?LinkId=98364)で[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="adb7f-116">[User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkId=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="adb7f-117">テーブル値パラメーターを宣言する際に使用するユーザー定義テーブル型について説明します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="adb7f-118">旧バージョンの SQL Server での複数行の受け渡し</span><span class="sxs-lookup"><span data-stu-id="adb7f-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="adb7f-119">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008 にテーブル値パラメーターが導入されるまでは、複数行データをストアド プロシージャまたはパラメーター化 SQL コマンドに渡す方法は限られていました。</span><span class="sxs-lookup"><span data-stu-id="adb7f-119">Before table-valued parameters were introduced to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="adb7f-120">複数行をサーバーに渡す方法には、次のオプションがありました。</span><span class="sxs-lookup"><span data-stu-id="adb7f-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="adb7f-121">複数のデータ列およびデータ行の値を表す一連の個別パラメーターを使用する。</span><span class="sxs-lookup"><span data-stu-id="adb7f-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="adb7f-122">この方法で渡すことのできるデータの量は、使用可能なパラメーターの数によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="adb7f-123"> プロシージャが持つことのできるパラメーター数は最大 2,100 です。</span><span class="sxs-lookup"><span data-stu-id="adb7f-123"> procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="adb7f-124">これらの個々の値をテーブル変数または一時テーブルにまとめて処理するには、サーバー側のロジックが必要です。</span><span class="sxs-lookup"><span data-stu-id="adb7f-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="adb7f-125">複数のデータを区切られた文字列または XML ドキュメントとしてまとめ、そのテキスト値をプロシージャまたはステートメントに渡す。</span><span class="sxs-lookup"><span data-stu-id="adb7f-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="adb7f-126">これには、データ構造を検証して値を処理するためのロジックをプロシージャまたはステートメントに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="adb7f-127">複数の行に影響を与えるデータ変更のための一連の SQL ステートメントを作成する。たとえば、`Update` の <xref:System.Data.SqlClient.SqlDataAdapter> メソッドを呼び出すことによって作成できます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="adb7f-128">変更はサーバーに個別に送ることもグループにまとめて送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="adb7f-129">ただし、複数のステートメントを含むバッチを送信しても、サーバーでは個々のステートメントが別々に実行されます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="adb7f-130">`bcp` ユーティリティ プログラムまたは <xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを使用して、多数行のデータをテーブルに読み込む。</span><span class="sxs-lookup"><span data-stu-id="adb7f-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="adb7f-131">この方法は効率的ですが、データが一時テーブルまたはテーブル変数に読み込まれなければ、サーバー側での処理がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="adb7f-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="adb7f-132">テーブル値パラメーター型の作成</span><span class="sxs-lookup"><span data-stu-id="adb7f-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="adb7f-133">テーブル値パラメーターは、[!INCLUDE[tsql](../../../../../includes/tsql-md.md)] の CREATE TYPE ステートメントを使用して定義された厳密に型指定されたテーブルの構造に基づいています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="adb7f-134">クライアント アプリケーションでテーブル値パラメーターを使用するには、まず [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] でテーブル型を作成し、その構造を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-134">You have to create a table type and define the structure in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="adb7f-135">テーブルの種類の作成の詳細については、次を参照してください。[ユーザー定義テーブル型](http://go.microsoft.com/fwlink/?LinkID=98364)で[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]オンライン ブック。</span><span class="sxs-lookup"><span data-stu-id="adb7f-135">For more information about creating table types, see [User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkID=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="adb7f-136">次のステートメントは、CategoryID と CategoryName 列から成る CategoryTableType というテーブル型を作成します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="adb7f-137">テーブル型を作成したら、その型に基づいてテーブル値パラメーターを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="adb7f-138">次の [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] フラグメントは、ストアド プロシージャ定義の中でテーブル値パラメーターを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="adb7f-139">テーブル値パラメーターの宣言には READONLY キーワードが必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="adb7f-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="adb7f-140">テーブル値パラメーターによるデータの変更 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="adb7f-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="adb7f-141">テーブル値パラメーターは、単一のステートメントを実行して複数行を操作する、セット ベースのデータ変更の中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="adb7f-142">たとえば、テーブル値パラメーターのすべての行を選択し、それらをデータベース テーブルに挿入できます。また、テーブル値パラメーターを更新対象のテーブルに結合する更新ステートメントを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="adb7f-143">次の [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE ステートメントは、テーブル値パラメーターを Categories テーブルに結合して使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="adb7f-144">テーブル値パラメーターを FROM 句の JOIN で使用するときは、エイリアスを使用する必要があります。この例ではテーブル値パラメーターに "ec" というエイリアスが使用されています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="adb7f-145">この [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] の例は、単一のセット ベース操作で INSERT を実行するためにテーブル値パラメーターから行を選択する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="adb7f-146">テーブル値パラメーターの制限</span><span class="sxs-lookup"><span data-stu-id="adb7f-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="adb7f-147">テーブル値パラメーターにはいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="adb7f-148">テーブル値パラメーターを渡すことはできません[CLR ユーザー定義関数](http://msdn.microsoft.com/library/ms131077.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="adb7f-148">You cannot pass table-valued parameters to [CLR user-defined functions](http://msdn.microsoft.com/library/ms131077.aspx).</span></span>  
  
-   <span data-ttu-id="adb7f-149">テーブル値パラメーターでは、UNIQUE 制約または PRIMARY KEY 制約をサポートするためにのみ、インデックスを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="adb7f-150"> はテーブル値パラメーターの統計を保持しません。</span><span class="sxs-lookup"><span data-stu-id="adb7f-150"> does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="adb7f-151">テーブル値パラメーターは [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] コードの中では読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="adb7f-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="adb7f-152">テーブル値パラメーターの行内の列の値は更新できません。行を挿入することも削除することもできません。</span><span class="sxs-lookup"><span data-stu-id="adb7f-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="adb7f-153">テーブル値パラメーター内のストアド プロシージャやパラメーター化ステートメントに渡すデータを変更するには、一時テーブルまたはテーブル変数にデータを挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="adb7f-154">ALTER TABLE ステートメントをテーブル値パラメーターの設計変更に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="adb7f-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="adb7f-155">SqlParameter の構成例</span><span class="sxs-lookup"><span data-stu-id="adb7f-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="adb7f-156"><xref:System.Data.SqlClient>テーブル値パラメーターの設定をサポートしている<xref:System.Data.DataTable>、<xref:System.Data.Common.DbDataReader>または<xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="adb7f-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="adb7f-157"><xref:System.Data.SqlClient.SqlParameter.TypeName%2A> の <xref:System.Data.SqlClient.SqlParameter> プロパティを使用して、テーブル値パラメーターの型名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="adb7f-158">`TypeName` は、既にサーバー上に作成されている、互換性のある型の名前と一致していることが必要です。</span><span class="sxs-lookup"><span data-stu-id="adb7f-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="adb7f-159">次のコード フラグメントは、データを挿入するための <xref:System.Data.SqlClient.SqlParameter> の構成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
  
```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="adb7f-160"><xref:System.Data.Common.DbDataReader> から派生した任意のオブジェクトを使用して、一連の行データをテーブル値パラメーターに挿入することもできます。その方法を次のフラグメントに示します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-160">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><span data-ttu-id="adb7f-161">ストアド プロシージャへのテーブル値パラメーターの受け渡し</span><span class="sxs-lookup"><span data-stu-id="adb7f-161">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="adb7f-162">この例は、テーブル値パラメーターのデータをストアド プロシージャに渡す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-162">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="adb7f-163">このコードは、<xref:System.Data.DataTable> メソッドを使用して、追加された行を新しい <xref:System.Data.DataTable.GetChanges%2A> に抽出します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-163">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="adb7f-164">次に <xref:System.Data.SqlClient.SqlCommand> を定義し、<xref:System.Data.SqlClient.SqlCommand.CommandType%2A> プロパティを <xref:System.Data.CommandType.StoredProcedure> に設定します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-164">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="adb7f-165"><xref:System.Data.SqlClient.SqlParameter> へのデータ入力には <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> メソッドが使用され、<xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> は `Structured` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-165">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="adb7f-166">次に <xref:System.Data.SqlClient.SqlCommand> メソッドを使用して <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> が実行されます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-166">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="adb7f-167">パラメーター化 SQL ステートメントへのテーブル値パラメーターの受け渡し</span><span class="sxs-lookup"><span data-stu-id="adb7f-167">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="adb7f-168">次の例は、データ ソースとしてテーブル値パラメーターを持つ SELECT サブクエリ付きの INSERT ステートメントを使用して、dbo.Categories テーブルにデータを挿入する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-168">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="adb7f-169">テーブル値パラメーターをパラメーター化 SQL ステートメントに渡すときは、<xref:System.Data.SqlClient.SqlParameter.TypeName%2A> の新しい <xref:System.Data.SqlClient.SqlParameter> プロパティを使用して、テーブル値パラメーターの型名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-169">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="adb7f-170">この `TypeName` は、既にサーバー上に作成されている、互換性のある型の名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-170">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="adb7f-171">このコード例では、dbo.CategoryTableType で定義されている型の構造を参照するために `TypeName` プロパティが使用されています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-171">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adb7f-172">テーブル値パラメーターで ID 列の値を指定する場合は、そのセッションの SET IDENTITY_INSERT ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adb7f-172">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="adb7f-173">DataReader による行のストリーミング</span><span class="sxs-lookup"><span data-stu-id="adb7f-173">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="adb7f-174">テーブル値パラメーターにデータ行をストリーム出力するには、<xref:System.Data.Common.DbDataReader> から派生したオブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-174">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="adb7f-175">次のコード フラグメントは、<xref:System.Data.OracleClient.OracleCommand> と <xref:System.Data.OracleClient.OracleDataReader> を使用して Oracle データベースからデータを取り出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="adb7f-175">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="adb7f-176">このコードは次に、単一の入力パラメーターを持つストアド プロシージャを呼び出すように <xref:System.Data.SqlClient.SqlCommand> を構成します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-176">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="adb7f-177"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> の <xref:System.Data.SqlClient.SqlParameter> プロパティが `Structured` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="adb7f-177">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="adb7f-178"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> は `OracleDataReader` の結果セットをテーブル値パラメーターとしてストアド プロシージャに渡します。</span><span class="sxs-lookup"><span data-stu-id="adb7f-178">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="adb7f-179">参照</span><span class="sxs-lookup"><span data-stu-id="adb7f-179">See Also</span></span>  
 [<span data-ttu-id="adb7f-180">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="adb7f-180">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="adb7f-181">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="adb7f-181">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="adb7f-182">DataAdapter パラメーター</span><span class="sxs-lookup"><span data-stu-id="adb7f-182">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="adb7f-183">ADO.NET における SQL Server データ操作</span><span class="sxs-lookup"><span data-stu-id="adb7f-183">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="adb7f-184">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="adb7f-184">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
