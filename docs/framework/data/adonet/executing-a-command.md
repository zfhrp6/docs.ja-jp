---
title: "コマンドの実行"
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
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 43fb2d8e42aeae5340874ab082f33257b197eac3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="executing-a-command"></a><span data-ttu-id="700df-102">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="700df-102">Executing a Command</span></span>
<span data-ttu-id="700df-103">.NET Framework に含まれている各 .NET Framework データ プロバイダーは、それぞれ <xref:System.Data.Common.DbCommand> を継承する固有のコマンド オブジェクトを持ちます。</span><span class="sxs-lookup"><span data-stu-id="700df-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="700df-104">.NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbCommand> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlCommand> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcCommand> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleCommand> があります。</span><span class="sxs-lookup"><span data-stu-id="700df-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="700df-105">次の表に示したように、各オブジェクトはコマンドを実行するための各種のメソッドを公開しており、コマンドの種類と適切な戻り値に基づいて使い分けることになります。</span><span class="sxs-lookup"><span data-stu-id="700df-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="700df-106">コマンド</span><span class="sxs-lookup"><span data-stu-id="700df-106">Command</span></span>|<span data-ttu-id="700df-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="700df-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="700df-108">`DataReader` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="700df-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="700df-109">単一のスカラー値を返します。</span><span class="sxs-lookup"><span data-stu-id="700df-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="700df-110">行を一切返さないコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="700df-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="700df-111"><xref:System.Xml.XmlReader> を返します。</span><span class="sxs-lookup"><span data-stu-id="700df-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="700df-112">`SqlCommand` オブジェクトでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="700df-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="700df-113">厳密に型指定された各コマンド オブジェクトは、次の表に示す <xref:System.Data.CommandType> 列挙値をサポートしています。これらの列挙値を使用してコマンド文字列の解釈方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="700df-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="700df-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="700df-114">CommandType</span></span>|<span data-ttu-id="700df-115">説明</span><span class="sxs-lookup"><span data-stu-id="700df-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="700df-116">データ ソース側で実行されるステートメントを定義する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="700df-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="700df-117">ストアド プロシージャの名前。</span><span class="sxs-lookup"><span data-stu-id="700df-117">The name of the stored procedure.</span></span> <span data-ttu-id="700df-118">呼び出す `Parameters` メソッドに関係なく、コマンドの `Execute` プロパティを使用して入力パラメーターと出力パラメーターにアクセスし、戻り値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="700df-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="700df-119">`ExecuteReader` を使用した場合は、`DataReader` を閉じるまで戻り値および出力パラメーターにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="700df-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="700df-120">テーブルの名前。</span><span class="sxs-lookup"><span data-stu-id="700df-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="700df-121">例</span><span class="sxs-lookup"><span data-stu-id="700df-121">Example</span></span>  
 <span data-ttu-id="700df-122"><xref:System.Data.SqlClient.SqlCommand> オブジェクトを作成し、そのプロパティを設定することによってストアド プロシージャを実行するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="700df-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="700df-123">ストアド プロシージャへの入力パラメーターは、<xref:System.Data.SqlClient.SqlParameter> オブジェクトを使って指定します。</span><span class="sxs-lookup"><span data-stu-id="700df-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="700df-124">このコマンドを <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> メソッドで実行し、<xref:System.Data.SqlClient.SqlDataReader> からの出力をコンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="700df-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="700df-125">コマンドのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="700df-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="700df-126">.NET Framework Data Provider for SQL Server には、失敗したコマンド実行に関連して断続的に発生する問題を検出できるパフォーマンス カウンターが追加されています。</span><span class="sxs-lookup"><span data-stu-id="700df-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="700df-127">詳細については、次を参照してください。[パフォーマンス カウンター](../../../../docs/framework/data/adonet/performance-counters.md)です。</span><span class="sxs-lookup"><span data-stu-id="700df-127">For more information see [Performance Counters](../../../../docs/framework/data/adonet/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700df-128">参照</span><span class="sxs-lookup"><span data-stu-id="700df-128">See Also</span></span>  
 [<span data-ttu-id="700df-129">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="700df-129">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="700df-130">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="700df-130">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="700df-131">Datareader の操作</span><span class="sxs-lookup"><span data-stu-id="700df-131">Working with DataReaders</span></span>](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="700df-132">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="700df-132">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
