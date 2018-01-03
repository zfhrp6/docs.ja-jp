---
title: "ADO.NET での接続文字列"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a20061c551f5cb1a19c64a2f92b8180465f58eb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="f304b-102">ADO.NET での接続文字列</span><span class="sxs-lookup"><span data-stu-id="f304b-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="f304b-103">.NET Framework 2.0 では、接続文字列を扱う新しい機能が導入されました。接続文字列ビルダー クラスに追加された新しいキーワードもその 1 つであり、有効な接続文字列を実行時に簡単に作成できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="f304b-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
 <span data-ttu-id="f304b-104">接続文字列には、データ プロバイダーからデータ ソースにパラメーターとして渡す初期化情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f304b-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="f304b-105">接続文字列は接続を開くときに解析され、その構文はデータ プロバイダーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f304b-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="f304b-106">構文エラーの場合はランタイム例外が生成されますが、その他のエラーは、データ ソースが接続情報を受け取った後でのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="f304b-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="f304b-107">いったん接続文字列が検証されると、接続文字列に指定されたオプションがデータ ソースによって適用されて接続が開かれます。</span><span class="sxs-lookup"><span data-stu-id="f304b-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>  
  
 <span data-ttu-id="f304b-108">接続文字列の形式は、キーと値パラメーターのペアをセミコロンで区切ったリストです。</span><span class="sxs-lookup"><span data-stu-id="f304b-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>  
  
 `keyword1=value; keyword2=value;`  
  
 <span data-ttu-id="f304b-109">キーワードの大文字と小文字は区別されません。また、キーと値のペア間のスペースは無視されます。</span><span class="sxs-lookup"><span data-stu-id="f304b-109">Keywords are not case sensitive, and spaces between key/value pairs are ignored.</span></span> <span data-ttu-id="f304b-110">ただし、値の大文字と小文字を区別するかどうかはデータ ソースにより異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f304b-110">However, values may be case sensitive, depending on the data source.</span></span> <span data-ttu-id="f304b-111">値にセミコロン、単一引用符、または二重引用符が含まれている場合は、必ず二重引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="f304b-111">Any values containing a semicolon, single quotation marks, or double quotation marks must be enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="f304b-112">有効な接続文字列の構文はプロバイダーによって異なり、ODBC のような初期の API から長年にわたって進化しています。</span><span class="sxs-lookup"><span data-stu-id="f304b-112">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="f304b-113">.NET Framework Data Provider for SQL Server (SqlClient) には、古い構文の要素が多数組み込まれており、一般的に、共通の接続文字列の構文に対しては柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="f304b-113">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="f304b-114">多くの場合、接続文字列の構文要素には同等として扱われる有効なシノニムが存在しますが、構文やスペルの誤りによって問題が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f304b-114">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="f304b-115">たとえば、"`Integrated Security=true`" は有効ですが、"`IntegratedSecurity=true`" ではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f304b-115">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="f304b-116">また、ユーザー入力を基にして接続文字列を実行時に構築する場合、入力された文字列を検証しないと、文字列のインジェクション攻撃を招き、データ ソースのセキュリティが脅かされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f304b-116">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>  
  
 <span data-ttu-id="f304b-117">こうした問題に対処するため、ADO.NET 2.0 では、各 .NET Framework データ プロバイダー用の新しい接続文字列ビルダーが導入されました。</span><span class="sxs-lookup"><span data-stu-id="f304b-117">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="f304b-118">キーワードがプロパティとして公開され、接続文字列をデータ ソースに送信する前に、その構文を検証できます。</span><span class="sxs-lookup"><span data-stu-id="f304b-118">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f304b-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f304b-119">In This Section</span></span>  
 [<span data-ttu-id="f304b-120">接続文字列ビルダー</span><span class="sxs-lookup"><span data-stu-id="f304b-120">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="f304b-121">`ConnectionStringBuilder` クラスを使用して、有効な接続文字列を実行時に作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f304b-121">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>  
  
 [<span data-ttu-id="f304b-122">接続文字列と構成ファイル</span><span class="sxs-lookup"><span data-stu-id="f304b-122">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="f304b-123">構成ファイルを使用した接続文字列の格納と取得の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f304b-123">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>  
  
 [<span data-ttu-id="f304b-124">接続文字列の構文</span><span class="sxs-lookup"><span data-stu-id="f304b-124">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="f304b-125">`SqlClient`、`OracleClient`、`OleDb`、`Odbc` の各プロバイダーに固有の接続文字列を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f304b-125">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>  
  
 [<span data-ttu-id="f304b-126">接続情報の保護</span><span class="sxs-lookup"><span data-stu-id="f304b-126">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="f304b-127">データ ソースへの接続に使用する情報を保護する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f304b-127">Demonstrates techniques for protecting information used to connect to a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f304b-128">参照</span><span class="sxs-lookup"><span data-stu-id="f304b-128">See Also</span></span>  
 [<span data-ttu-id="f304b-129">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="f304b-129">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="f304b-130">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="f304b-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
