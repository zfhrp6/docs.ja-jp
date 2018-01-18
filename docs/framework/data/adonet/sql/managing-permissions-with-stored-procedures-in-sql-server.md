---
title: "SQL Server でのストアド プロシージャを使用した権限の管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 38bdc4d41e4b42f2dccaf059d84f6b8b45967ff5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a><span data-ttu-id="3c4c5-102">SQL Server でのストアド プロシージャを使用した権限の管理</span><span class="sxs-lookup"><span data-stu-id="3c4c5-102">Managing Permissions with Stored Procedures in SQL Server</span></span>
<span data-ttu-id="3c4c5-103">データベースを多層的に防御する 1 つの方法として、あらゆるデータ アクセスをストアド プロシージャまたはユーザー定義関数を使って実装することが考えられます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-103">One method of creating multiple lines of defense around your database is to implement all data access using stored procedures or user-defined functions.</span></span> <span data-ttu-id="3c4c5-104">テーブルなど、基になるオブジェクトに対する権限をすべて取り消すか拒否し、ストアド プロシージャに対して EXECUTE 権限を付与するようにします。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-104">You revoke or deny all permissions to underlying objects, such as tables, and grant EXECUTE permissions on stored procedures.</span></span> <span data-ttu-id="3c4c5-105">こうすることで、データやデータベース オブジェクトの周囲にセキュリティの境界を設けることができます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-105">This effectively creates a security perimeter around your data and database objects.</span></span>  
  
## <a name="stored-procedure-benefits"></a><span data-ttu-id="3c4c5-106">ストアド プロシージャの利点</span><span class="sxs-lookup"><span data-stu-id="3c4c5-106">Stored Procedure Benefits</span></span>  
 <span data-ttu-id="3c4c5-107">ストアド プロシージャには、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-107">Stored procedures have the following benefits:</span></span>  
  
-   <span data-ttu-id="3c4c5-108">データ ロジックとビジネス ルールがカプセル化されるため、ユーザーが、開発者およびデータベース管理者の想定外の方法でデータやオブジェクトにアクセスするのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-108">Data logic and business rules can be encapsulated so that users can access data and objects only in ways that developers and database administrators intend.</span></span>  
  
-   <span data-ttu-id="3c4c5-109">すべてのユーザー入力を検証するパラメーター化されたストアド プロシージャを使用することで、SQL インジェクション攻撃を阻止できます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-109">Parameterized stored procedures that validate all user input can be used to thwart SQL injection attacks.</span></span> <span data-ttu-id="3c4c5-110">動的 SQL を使用する場合は、必ずコマンドをパラメーター化するようにし、パラメーター値を直接クエリ文字列に追加することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-110">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into a query string.</span></span>  
  
-   <span data-ttu-id="3c4c5-111">アドホック クエリおよびデータ変更を禁止できます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-111">Ad hoc queries and data modifications can be disallowed.</span></span> <span data-ttu-id="3c4c5-112">悪意からまたは不注意によってデータが破壊されたり、サーバーやネットワークのパフォーマンスを損ねるようなクエリが実行されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-112">This prevents users from maliciously or inadvertently destroying data or executing queries that impair performance on the server or the network.</span></span>  
  
-   <span data-ttu-id="3c4c5-113">エラーをクライアント アプリケーションに直接渡すことなく、プロシージャ コード内で処理できます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-113">Errors can be handled in procedure code without being passed directly to client applications.</span></span> <span data-ttu-id="3c4c5-114">これにより、返されたエラー メッセージがプローブ攻撃に利用されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-114">This prevents error messages from being returned that could aid in a probing attack.</span></span> <span data-ttu-id="3c4c5-115">エラーはログに記録しサーバー上で処理するようにします。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-115">Log errors and handle them on the server.</span></span>  
  
-   <span data-ttu-id="3c4c5-116">ストアド プロシージャは 1 度作成すれば、さまざまなアプリケーションからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-116">Stored procedures can be written once, and accessed by many applications.</span></span>  
  
-   <span data-ttu-id="3c4c5-117">クライアント アプリケーションは基になるデータの構造を意識する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-117">Client applications do not need to know anything about the underlying data structures.</span></span> <span data-ttu-id="3c4c5-118">パラメーター リストや返されるデータ型に影響が及ばない限り、ストアド プロシージャのコードを変更しても、クライアント アプリケーション側に変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-118">Stored procedure code can be changed without requiring changes in client applications as long as the changes do not affect parameter lists or returned data types.</span></span>  
  
-   <span data-ttu-id="3c4c5-119">ストアド プロシージャによって、複数の操作を 1 回のプロシージャ呼び出しにまとめることができるため、ネットワーク トラフィックを削減できます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-119">Stored procedures can reduce network traffic by combining multiple operations into one procedure call.</span></span>  
  
## <a name="stored-procedure-execution"></a><span data-ttu-id="3c4c5-120">ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="3c4c5-120">Stored Procedure Execution</span></span>  
 <span data-ttu-id="3c4c5-121">ストアド プロシージャを使用すると、所有権の継承によるデータ アクセスを利用できるため、データベース オブジェクトにアクセスするための権限をユーザーに明示的に付与する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-121">Stored procedures take advantage of ownership chaining to provide access to data so that users do not need to have explicit permission to access database objects.</span></span> <span data-ttu-id="3c4c5-122">所有権の継承は、連鎖的にアクセスされる複数のオブジェクトが同じユーザーによって所有されている場合に適用されます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-122">An ownership chain exists when objects that access each other sequentially are owned by the same user.</span></span> <span data-ttu-id="3c4c5-123">たとえば、あるストアド プロシージャが別のストアド プロシージャを呼び出したり、特定のストアド プロシージャが複数のテーブルにアクセスしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-123">For example, a stored procedure can call other stored procedures, or a stored procedure can access multiple tables.</span></span> <span data-ttu-id="3c4c5-124">実行の連鎖に含まれるすべてのオブジェクトが同じ所有者を共有していた場合、SQL Server は呼び出し元の EXECUTE 権限だけをチェックします。つまり、他のオブジェクトの呼び出し元の権限はチェックされません。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-124">If all objects in the chain of execution have the same owner, then SQL Server only checks the EXECUTE permission for the caller, not the caller's permissions on other objects.</span></span> <span data-ttu-id="3c4c5-125">したがって、EXECUTE 権限はストアド プロシージャにのみ付与すればよく、基になるテーブルの権限はすべて取り消すか拒否できます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-125">Therefore you need to grant only EXECUTE permissions on stored procedures; you can revoke or deny all permissions on the underlying tables.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="3c4c5-126">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="3c4c5-126">Best Practices</span></span>  
 <span data-ttu-id="3c4c5-127">単にストアド プロシージャを作成するだけでは、アプリケーションを適切に保護することはできません。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-127">Simply writing stored procedures isn't enough to adequately secure your application.</span></span> <span data-ttu-id="3c4c5-128">同時に、次の点を考慮してセキュリティ ホールを防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-128">You should also consider the following potential security holes.</span></span>  
  
-   <span data-ttu-id="3c4c5-129">データ アクセスを許可するデータベース ロールに、ストアド プロシージャの EXECUTE 権限を付与する。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-129">Grant EXECUTE permissions on the stored procedures for database roles you want to be able to access the data.</span></span>  
  
-   <span data-ttu-id="3c4c5-130">基になるテーブルのすべての権限を取り消すか拒否する。`public` ロールを含め、データベース内のすべてのロールおよびユーザーが対象になります。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-130">Revoke or deny all permissions to the underlying tables for all roles and users in the database, including the `public` role.</span></span> <span data-ttu-id="3c4c5-131">すべてのユーザーは public から権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-131">All users inherit permissions from public.</span></span> <span data-ttu-id="3c4c5-132">したがって、`public` の権限を拒否することは、所有者と `sysadmin` メンバーだけがアクセス権を持つことを意味します。それ以外のすべてのユーザーは、他のロールのメンバーになっても権限を継承することはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-132">Therefore denying permissions to `public` means that only owners and `sysadmin` members have access; all other users will be unable to inherit permissions from membership in other roles.</span></span>  
  
-   <span data-ttu-id="3c4c5-133">`sysadmin` ロールまたは `db_owner` ロールに対してユーザーまたはロールを追加することは避ける。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-133">Do not add users or roles to the `sysadmin` or `db_owner` roles.</span></span> <span data-ttu-id="3c4c5-134">システム管理者およびデータベース所有者は、すべてのデータベース オブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-134">System administrators and database owners can access all database objects.</span></span>  
  
-   <span data-ttu-id="3c4c5-135">`guest` アカウントを無効にする。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-135">Disable the `guest` account.</span></span> <span data-ttu-id="3c4c5-136">こうすることで、匿名ユーザーがデータベースに接続することはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-136">This will prevent anonymous users from connecting to the database.</span></span> <span data-ttu-id="3c4c5-137">新しいデータベースの guest アカウントは既定で無効化されています。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-137">The guest account is disabled by default in new databases.</span></span>  
  
-   <span data-ttu-id="3c4c5-138">エラー処理を実装し、エラーのログを記録する。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-138">Implement error handling and log errors.</span></span>  
  
-   <span data-ttu-id="3c4c5-139">すべてのユーザー入力を検証するパラメーター化されたストアド プロシージャを作成する。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-139">Create parameterized stored procedures that validate all user input.</span></span> <span data-ttu-id="3c4c5-140">どのようなユーザー入力も "信頼できないもの" として扱うようにします。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-140">Treat all user input as untrusted.</span></span>  
  
-   <span data-ttu-id="3c4c5-141">どうしても必要な場合を除き、動的 SQL は使用しない。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-141">Avoid dynamic SQL unless absolutely necessary.</span></span> <span data-ttu-id="3c4c5-142">文字列値を Transact-SQL の QUOTENAME() 関数に渡すことで、入力文字列に含まれている可能性のある区切り記号をエスケープできます。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-142">Use the Transact-SQL QUOTENAME() function to delimit a string value and escape any occurrence of the delimiter in the input string.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="3c4c5-143">外部リソース</span><span class="sxs-lookup"><span data-stu-id="3c4c5-143">External Resources</span></span>  
 <span data-ttu-id="3c4c5-144">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-144">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="3c4c5-145">リソース</span><span class="sxs-lookup"><span data-stu-id="3c4c5-145">Resource</span></span>|<span data-ttu-id="3c4c5-146">説明</span><span class="sxs-lookup"><span data-stu-id="3c4c5-146">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3c4c5-147">[ストアド プロシージャ](http://msdn.microsoft.com/library/ms190782.aspx)と[SQL インジェクション](http://go.microsoft.com/fwlink/?LinkId=98234)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="3c4c5-147">[Stored Procedures](http://msdn.microsoft.com/library/ms190782.aspx) and [SQL Injection](http://go.microsoft.com/fwlink/?LinkId=98234) in SQL Server Books Online</span></span>|<span data-ttu-id="3c4c5-148">ストアド プロシージャの作成方法と SQL インジェクションのしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3c4c5-148">Topics describe how to create stored procedures and how SQL Injection works.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c4c5-149">参照</span><span class="sxs-lookup"><span data-stu-id="3c4c5-149">See Also</span></span>  
 [<span data-ttu-id="3c4c5-150">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3c4c5-150">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="3c4c5-151">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="3c4c5-151">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="3c4c5-152">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="3c4c5-152">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="3c4c5-153">SQL Server での安全な動的 SQL の作成</span><span class="sxs-lookup"><span data-stu-id="3c4c5-153">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="3c4c5-154">SQL Server でのストアド プロシージャの署名</span><span class="sxs-lookup"><span data-stu-id="3c4c5-154">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="3c4c5-155">SQL Server での借用を使用したアクセス許可のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="3c4c5-155">Customizing Permissions with Impersonation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [<span data-ttu-id="3c4c5-156">ストアド プロシージャでのデータの変更</span><span class="sxs-lookup"><span data-stu-id="3c4c5-156">Modifying Data with Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="3c4c5-157">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="3c4c5-157">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
