---
title: "コンテキスト接続"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 40aa71a16c7a0616cfcf318901858da7587fa20b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="the-context-connection"></a><span data-ttu-id="e4acc-102">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="e4acc-102">The Context Connection</span></span>
<span data-ttu-id="e4acc-103">内部データ アクセスの問題は、非常に一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="e4acc-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="e4acc-104">つまり、共通言語ランタイム (CLR) ストアド プロシージャまたは関数を実行しているサーバーにアクセスする場合の問題です。</span><span class="sxs-lookup"><span data-stu-id="e4acc-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="e4acc-105">1 つの解決方法は、<xref:System.Data.SqlClient.SqlConnection> を使用して接続文字列を作成し、ローカル サーバーをポイントするように接続文字列で指定して、接続を開くことです。</span><span class="sxs-lookup"><span data-stu-id="e4acc-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="e4acc-106">これを行うには、ログインするための資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4acc-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="e4acc-107">接続がストアド プロシージャまたは関数とは別のデータベース セッションにある場合や、異なる `SET` オプションが指定されている場合があります。また、別のトランザクション内にある場合や、一時テーブルを参照していない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e4acc-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="e4acc-108">マネージ ストアド プロシージャまたは関数コードが SQL Server プロセス内で実行されている場合、別のユーザーがサーバーに接続して、そのマネージ ストアド プロシージャまたは関数コードを起動する SQL ステートメントを実行していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e4acc-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="e4acc-109">接続のコンテキスト内で、ストアド プロシージャまたは関数をトランザクションや `SET` オプションなどと共に実行する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e4acc-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="e4acc-110">これは、コンテキスト接続と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e4acc-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="e4acc-111">コンテキスト接続を使用すると、コードが初めに起動されたコンテキスト内で Transact-SQL ステートメントを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="e4acc-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="e4acc-112">詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4acc-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e4acc-113">**SQL Server オンライン ブック**</span><span class="sxs-lookup"><span data-stu-id="e4acc-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="e4acc-114">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="e4acc-114">The Context Connection</span></span>](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a><span data-ttu-id="e4acc-115">参照</span><span class="sxs-lookup"><span data-stu-id="e4acc-115">See Also</span></span>  
 [<span data-ttu-id="e4acc-116">マネージ コードでの SQL Server 2005 のオブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="e4acc-116">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="e4acc-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="e4acc-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
