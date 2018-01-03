---
title: "非同期操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6f631d785698ae59370053c4e35307514c44087c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-operations"></a><span data-ttu-id="a3a6a-102">非同期操作</span><span class="sxs-lookup"><span data-stu-id="a3a6a-102">Asynchronous Operations</span></span>
<span data-ttu-id="a3a6a-103">コマンドの実行など、データベースでの一部の操作は、完了までに長時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-103">Some database operations, such as command executions, can take significant time to complete.</span></span> <span data-ttu-id="a3a6a-104">そのような場合、シングルスレッドのアプリケーションでは、他の操作をブロックして、コマンドが終了するまで待機しなければ操作を続行できません。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-104">In such a case, single-threaded applications must block other operations and wait for the command to finish before they can continue their own operations.</span></span> <span data-ttu-id="a3a6a-105">これに対して、長時間にわたる操作をバックグラウンド スレッドに割り当てることができれば、フォアグラウンド スレッドがアクティブなまま操作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-105">In contrast, being able to assign the long-running operation to a background thread allows the foreground thread to remain active throughout the operation.</span></span> <span data-ttu-id="a3a6a-106">たとえば、Windows アプリケーションでは、操作を実行中のユーザー インターフェイス スレッドの応答性を維持しながら、時間のかかる操作をバックグラウンド スレッドに委任することができます。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-106">In a Windows application, for example, delegating the long-running operation to a background thread allows the user interface thread to remain responsive while the operation is executing.</span></span>  
  
 <span data-ttu-id="a3a6a-107">.NET Framework では、複数の標準的な非同期デザイン パターンが用意されており、バックグラウンド スレッドを利用して、その他の操作を完了するためにユーザー インターフェイスまたは優先順位の高いスレッドを解放できます。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-107">The .NET Framework provides several standard asynchronous design patterns that developers can use to take advantage of background threads and free the user interface or high-priority threads to complete other operations.</span></span> <span data-ttu-id="a3a6a-108">ADO.NET では、<xref:System.Data.SqlClient.SqlCommand> クラスでこれらと同じデザイン パターンがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-108">ADO.NET supports these same design patterns in its <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="a3a6a-109">特に、<xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>、および <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> メソッドと、<xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>、および <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> メソッドとのペアによって、非同期動作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-109">Specifically, the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, and <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> methods, paired with the <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, and <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> methods, provide the asynchronous support.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3a6a-110">非同期プログラミングは .NET Framework の中心的な機能であり、ADO.NET では標準のデザイン パターンが活用されます。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-110">Asynchronous programming is a core feature of the .NET Framework, and ADO.NET takes full advantage of the standard design patterns.</span></span> <span data-ttu-id="a3a6a-111">開発者が利用できる別の非同期技法の詳細については、次を参照してください。[同期のメソッドを非同期に呼び出す](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)です。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-111">For more information about the different asynchronous techniques available to developers, see [Calling Synchronous Methods Asynchronously](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
 <span data-ttu-id="a3a6a-112">ADO.NET 機能での非同期技法の使用に伴う特別な考慮事項はありませんが、非同期機能は、.NET Framework のその他の領域よりも ADO.NET で使用する場合が多いと思われます。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-112">Although using asynchronous techniques with ADO.NET features does not add any special considerations, it is likely that more developers will use asynchronous features in ADO.NET than in other areas of the .NET Framework.</span></span> <span data-ttu-id="a3a6a-113">マルチスレッドのアプリケーションは、その利点と問題点を認識した上で作成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-113">It is important to be aware of the benefits and pitfalls of creating multithreaded applications.</span></span> <span data-ttu-id="a3a6a-114">このセクションに示す例は、マルチスレッド機能を組み込むアプリケーションを構築する際に考慮すべき重要な問題を提示しています。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-114">The examples that follow in this section point out several important issues that developers will need to take into account when building applications that incorporate multithreaded functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a3a6a-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a3a6a-115">In This Section</span></span>  
 [<span data-ttu-id="a3a6a-116">コールバックを使用した Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="a3a6a-116">Windows Applications Using Callbacks</span></span>](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 <span data-ttu-id="a3a6a-117">この例では、非同期コマンドを安全に実行し、異なるスレッドのフォームと内容との対話を正しく処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-117">Provides an example demonstrating how to execute an asynchronous command safely, correctly handling interaction with a form and its contents from a separate thread.</span></span>  
  
 [<span data-ttu-id="a3a6a-118">待機ハンドルを使用した ASP.NET アプリケーション</span><span class="sxs-lookup"><span data-stu-id="a3a6a-118">ASP.NET Applications Using Wait Handles</span></span>](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 <span data-ttu-id="a3a6a-119">この例では、ASP.NET ページから複数の同時実行コマンドを実行し、すべてのコマンドの終了時に Wait ハンドルを使用して操作を管理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-119">Provides an example demonstrating how to execute multiple concurrent commands from an ASP.NET page, using Wait handles to manage the operation at completion of all the commands.</span></span>  
  
 [<span data-ttu-id="a3a6a-120">コンソール アプリケーションでのポーリング</span><span class="sxs-lookup"><span data-stu-id="a3a6a-120">Polling in Console Applications</span></span>](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 <span data-ttu-id="a3a6a-121">この例では、ポーリングを使用して非同期コマンドの実行をコンソール アプリケーションで待機する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-121">Provides an example demonstrating the use of polling to wait for the completion of an asynchronous command execution from a console application.</span></span> <span data-ttu-id="a3a6a-122">この技法は、クラス ライブラリまたはユーザー インターフェイスを持たないその他のアプリケーションでも有効です。</span><span class="sxs-lookup"><span data-stu-id="a3a6a-122">This technique is also valid in a class library or other application without a user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a6a-123">参照</span><span class="sxs-lookup"><span data-stu-id="a3a6a-123">See Also</span></span>  
 [<span data-ttu-id="a3a6a-124">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a3a6a-124">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="a3a6a-125">同期メソッドの非同期呼び出し</span><span class="sxs-lookup"><span data-stu-id="a3a6a-125">Calling Synchronous Methods Asynchronously</span></span>](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [<span data-ttu-id="a3a6a-126">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="a3a6a-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
