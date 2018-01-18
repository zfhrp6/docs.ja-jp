---
title: "DbConnection、DbCommand、および DbException"
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
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a79587762ec9b69bcc580af63fc1db19e491dec
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="d4cd3-102">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="d4cd3-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="d4cd3-103"><xref:System.Data.Common.DbProviderFactory> および <xref:System.Data.Common.DbConnection> を作成すると、コマンドおよびデータ リーダーを使用してデータ ソースからデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="d4cd3-104">データの取得例</span><span class="sxs-lookup"><span data-stu-id="d4cd3-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="d4cd3-105">次のコード例は、`DbConnection` オブジェクトを引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="d4cd3-106"><xref:System.Data.Common.DbCommand> に SQL SELECT ステートメントを設定することによって、Categories テーブルからデータを検索するための <xref:System.Data.Common.DbCommand.CommandText%2A> を作成します。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="d4cd3-107">このコードを実行するには、データ ソースに Categories テーブルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="d4cd3-108">接続を開いた後、<xref:System.Data.Common.DbDataReader> を使用してデータが取得されます。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="d4cd3-109">コマンド実行例</span><span class="sxs-lookup"><span data-stu-id="d4cd3-109">Executing a Command Example</span></span>  
 <span data-ttu-id="d4cd3-110">次のコード例は、`DbConnection` オブジェクトを引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="d4cd3-111">`DbConnection` が有効である場合、接続が開かれ、<xref:System.Data.Common.DbCommand> が作成されて実行されます。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="d4cd3-112"><xref:System.Data.Common.DbCommand.CommandText%2A> には、Northwind データベースの Categories テーブルへの挿入操作を実行する SQL INSERT ステートメントが設定されています。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="d4cd3-113">このコードを実行するには、データ ソースに Northwind データベースが存在すること、および、指定されたプロバイダーの有効な SQL 構文が INSERT ステートメントに使用されていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="d4cd3-114">データ ソースで発生したエラーは <xref:System.Data.Common.DbException> コード ブロックで処理され、それ以外のすべての例外は <xref:System.Exception> ブロックで処理されます。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="d4cd3-115">DbException でのデータ エラーの処理</span><span class="sxs-lookup"><span data-stu-id="d4cd3-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="d4cd3-116"><xref:System.Data.Common.DbException> クラスは、データ ソースでスローされるすべての例外の基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="d4cd3-117">このクラスを例外処理コードに使用することで、プロバイダーに固有の例外クラスを参照することなく、各種のプロバイダーによってスローされる例外を処理できます。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="d4cd3-118">次のコード フラグメントでは、<xref:System.Data.Common.DbException> の各プロパティ (<xref:System.Exception.GetType%2A>、<xref:System.Exception.Source%2A>、<xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>、および <xref:System.Exception.Message%2A>) を使って、データ ソースから返されたエラー情報を表示しています。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="d4cd3-119">出力結果には、エラーの種類、エラーの発生元 (プロバイダー名)、エラー コード、および、エラーに関連付けられたメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4cd3-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4cd3-120">参照</span><span class="sxs-lookup"><span data-stu-id="d4cd3-120">See Also</span></span>  
 [<span data-ttu-id="d4cd3-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="d4cd3-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="d4cd3-122">DbProviderFactory の取得</span><span class="sxs-lookup"><span data-stu-id="d4cd3-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="d4cd3-123">DbDataAdapter を使用したデータの変更</span><span class="sxs-lookup"><span data-stu-id="d4cd3-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="d4cd3-124">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="d4cd3-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
