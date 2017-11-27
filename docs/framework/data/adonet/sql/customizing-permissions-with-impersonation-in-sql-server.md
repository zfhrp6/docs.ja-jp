---
title: "SQL Server での借用を使用した権限のカスタマイズ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cde4fafaa10d7c9b495d4f98ddcd42c7f8a7524a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a><span data-ttu-id="59818-102">SQL Server での借用を使用した権限のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="59818-102">Customizing Permissions with Impersonation in SQL Server</span></span>
<span data-ttu-id="59818-103">多くのアプリケーションでは、ベース テーブルへのアクセスを制限する組み合わせ所有権を利用して、ストアド プロシージャを使ってデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="59818-103">Many applications use stored procedures to access data, relying on ownership chaining to restrict access to base tables.</span></span> <span data-ttu-id="59818-104">ストアド プロシージャに対して EXECUTE 権限を付与するとき、ベース テーブルに対する権限を取り消したり拒否したりできます。</span><span class="sxs-lookup"><span data-stu-id="59818-104">You can grant EXECUTE permissions on stored procedures, revoking or denying permissions on the base tables.</span></span> <span data-ttu-id="59818-105">ストアド プロシージャとテーブルの所有者が同じ場合、SQL Server では呼び出し元の権限をチェックしません。</span><span class="sxs-lookup"><span data-stu-id="59818-105">SQL Server does not check the permissions of the caller if the stored procedure and tables have the same owner.</span></span> <span data-ttu-id="59818-106">ただし、オブジェクトの所有者が異なる場合や、動的 SQL の場合には、組み合わせ所有権が無効になります。</span><span class="sxs-lookup"><span data-stu-id="59818-106">However, ownership chaining doesn't work if objects have different owners or in the case of dynamic SQL.</span></span>  
  
 <span data-ttu-id="59818-107">参照先オブジェクトに対する権限が呼び出し元になくても、ストアド プロシージャで EXECUTE AS 句を使用できます。</span><span class="sxs-lookup"><span data-stu-id="59818-107">You can use the EXECUTE AS clause in a stored procedure when the caller doesn't have permissions on the referenced database objects.</span></span> <span data-ttu-id="59818-108">EXECUTE AS 句の効果は、実行コンテキストがプロキシ ユーザーに切り替えられることです。</span><span class="sxs-lookup"><span data-stu-id="59818-108">The effect of the EXECUTE AS clause is that the execution context is switched to the proxy user.</span></span> <span data-ttu-id="59818-109">入れ子になったストアド プロシージャやトリガーへの呼び出しを含め、すべてのコードがプロキシ ユーザーのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="59818-109">All code, as well as any calls to nested stored procedures or triggers, executes under the security context of the proxy user.</span></span> <span data-ttu-id="59818-110">プロシージャの実行後、または REVERT ステートメントが発行されたときにのみ、実行コンテキストが最初の呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="59818-110">Execution context is reverted to the original caller only after execution of the procedure or when a REVERT statement is issued.</span></span>  
  
## <a name="context-switching-with-the-execute-as-statement"></a><span data-ttu-id="59818-111">EXECUTE AS ステートメントを使用したコンテキスト切り替え</span><span class="sxs-lookup"><span data-stu-id="59818-111">Context Switching with the EXECUTE AS Statement</span></span>  
 <span data-ttu-id="59818-112">Transact-SQL の EXECUTE AS ステートメントを使用して、別のログインまたはデータベース ユーザーの権限を借用することで、ステートメントの実行コンテキストを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="59818-112">The Transact-SQL EXECUTE AS statement allows you to switch the execution context of a statement by impersonating another login or database user.</span></span> <span data-ttu-id="59818-113">これは、クエリとプロシージャを別のユーザーとしてテストできる便利な手法です。</span><span class="sxs-lookup"><span data-stu-id="59818-113">This is a useful technique for testing queries and procedures as another user.</span></span>  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 <span data-ttu-id="59818-114">権限を借用するログインまたはユーザーに対する IMPERSONATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="59818-114">You must have IMPERSONATE permissions on the login or user you are impersonating.</span></span> <span data-ttu-id="59818-115">この権限は、`sysadmin` にはすべてのデータベースに対して与えられ、`db_owner` ロールのメンバーには所有するデータベースに対して与えられます。</span><span class="sxs-lookup"><span data-stu-id="59818-115">This permission is implied for `sysadmin` for all databases, and `db_owner` role members in databases that they own.</span></span>  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a><span data-ttu-id="59818-116">EXECUTE AS 句を使用した権限の許可</span><span class="sxs-lookup"><span data-stu-id="59818-116">Granting Permissions with the EXECUTE AS Clause</span></span>  
 <span data-ttu-id="59818-117">EXECUTE AS 句は、ストアド プロシージャ、トリガー、ユーザー定義関数 (インライン テーブル値関数を除く) の定義ヘッダーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="59818-117">You can use the EXECUTE AS clause in the definition header of a stored procedure, trigger, or user-defined function (except for inline table-valued functions).</span></span> <span data-ttu-id="59818-118">そのため、EXECUTE AS 句で指定されたユーザー名またはキーワードのコンテキストでプロシージャが実行されます。</span><span class="sxs-lookup"><span data-stu-id="59818-118">This causes the procedure to execute in the context of the user name or keyword specified in the EXECUTE AS clause.</span></span> <span data-ttu-id="59818-119">データベースに、ログインに割り当てられないプロキシ ユーザーを作成し、プロシージャがアクセスするオブジェクトに対して必要な権限のみを許可することができます。</span><span class="sxs-lookup"><span data-stu-id="59818-119">You can create a proxy user in the database that is not mapped to a login, granting it only the necessary permissions on the objects accessed by the procedure.</span></span> <span data-ttu-id="59818-120">EXECUTE AS 句で指定されたプロキシ ユーザーのみが、モジュールからアクセスされるすべてのオブジェクトに対する権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="59818-120">Only the proxy user specified in the EXECUTE AS clause must have permissions on all objects accessed by the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59818-121">TRUNCATE TABLE など、許可する権限のない操作もあります。</span><span class="sxs-lookup"><span data-stu-id="59818-121">Some actions, such as TRUNCATE TABLE, do not have grantable permissions.</span></span> <span data-ttu-id="59818-122">プロシージャ内にステートメントを組み込み、ALTER TABLE 権限を持つプロキシ ユーザーを指定することで、プロシージャに対する EXECUTE 権限のみを持つ呼び出し元に、テーブルを切り捨てる権限を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="59818-122">By incorporating the statement within a procedure and specifying a proxy user who has ALTER TABLE permissions, you can extend the permissions to truncate the table to callers who have only EXECUTE permissions on the procedure.</span></span>  
  
 <span data-ttu-id="59818-123">EXECUTE AS 句で指定されたコンテキストは、入れ子になったプロシージャやトリガーを含むプロシージャの実行中に有効となります。</span><span class="sxs-lookup"><span data-stu-id="59818-123">The context specified in the EXECUTE AS clause is valid for the duration of the procedure, including nested procedures and triggers.</span></span> <span data-ttu-id="59818-124">実行が完了したとき、または REVERT ステートメントが発行されたときに、コンテキストが呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="59818-124">Context reverts to the caller when execution is complete or the REVERT statement is issued.</span></span>  
  
 <span data-ttu-id="59818-125">プロシージャで EXECUTE AS 句を使用する際には、次の 3 つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="59818-125">There are three steps involved in using the EXECUTE AS clause in a procedure.</span></span>  
  
1.  <span data-ttu-id="59818-126">ログインに割り当てられていないプロキシ ユーザーをデータベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="59818-126">Create a proxy user in the database that is not mapped to a login.</span></span> <span data-ttu-id="59818-127">この操作は必須ではありませんが、権限を管理するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="59818-127">This is not required, but it helps when managing permissions.</span></span>  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1.  <span data-ttu-id="59818-128">プロキシ ユーザーに必要な権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="59818-128">Grant the proxy user the necessary permissions.</span></span>  
  
2.  <span data-ttu-id="59818-129">ストアド プロシージャまたはユーザー定義関数に EXECUTE AS 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="59818-129">Add the EXECUTE AS clause to the stored procedure or user-defined function.</span></span>  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  <span data-ttu-id="59818-130">呼び出し元の元のセキュリティ コンテキストが保持されないため、監査の必要なアプリケーションはブレークされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="59818-130">Applications that require auditing can break because the original security context of the caller is not retained.</span></span> <span data-ttu-id="59818-131">SESSION_USER、USER、USER_NAME など、現在のユーザーの識別情報を返す組み込み関数では、最初の呼び出し元ではなく EXECUTE AS 句に関連付けられているユーザーが返されます。</span><span class="sxs-lookup"><span data-stu-id="59818-131">Built-in functions that return the identity of the current user, such as SESSION_USER, USER, or USER_NAME, return the user associated with the EXECUTE AS clause, not the original caller.</span></span>  
  
### <a name="using-execute-as-with-revert"></a><span data-ttu-id="59818-132">REVERT での EXECUTE AS の使用</span><span class="sxs-lookup"><span data-stu-id="59818-132">Using EXECUTE AS with REVERT</span></span>  
 <span data-ttu-id="59818-133">Transact-SQL REVERT ステートメントを使用して、元の実行コンテキストに戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="59818-133">You can use the Transact-SQL REVERT statement to revert to the original execution context.</span></span>  
  
 <span data-ttu-id="59818-134">オプションの句で WITH NO REVERT COOKIE = @variableName、により、場合、呼び出し元に、実行コンテキストを切り替える、@variableName変数には、適切な値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="59818-134">The optional clause, WITH NO REVERT COOKIE = @variableName, allows you switch the execution context back to the caller if the @variableName variable contains the correct value.</span></span> <span data-ttu-id="59818-135">これにより、接続プールが使用されている環境では実行コンテキストを呼び出し元に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="59818-135">This allows you to switch the execution context back to the caller in environments where connection pooling is used.</span></span> <span data-ttu-id="59818-136">の値@variableNameEXECUTE AS の呼び出し元のみが知っているステートメントでは、呼び出し元保証できる、アプリケーションを呼び出すエンドユーザーが実行コンテキストを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="59818-136">Because the value of @variableName is known only to the caller of the EXECUTE AS statement, the caller can guarantee that the execution context cannot be changed by the end user that invokes the application.</span></span> <span data-ttu-id="59818-137">接続は、閉じられるとプールに返されます。</span><span class="sxs-lookup"><span data-stu-id="59818-137">When the connection is closed, it is returned to the pool.</span></span> <span data-ttu-id="59818-138">接続の詳細については、ADO.NET のプールを参照してください[SQL サーバー接続プール (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)です。</span><span class="sxs-lookup"><span data-stu-id="59818-138">For more information on connection pooling in ADO.NET, see [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
### <a name="specifying-the-execution-context"></a><span data-ttu-id="59818-139">実行コンテキストの指定</span><span class="sxs-lookup"><span data-stu-id="59818-139">Specifying the Execution Context</span></span>  
 <span data-ttu-id="59818-140">EXECUTE AS は、ユーザーを指定するだけでなく、次のキーワードを指定して使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="59818-140">In addition to specifying a user, you can also use EXECUTE AS with any of the following keywords.</span></span>  
  
-   <span data-ttu-id="59818-141">CALLER : </span><span class="sxs-lookup"><span data-stu-id="59818-141">CALLER.</span></span> <span data-ttu-id="59818-142">既定で、CALLER として実行されます。他にオプションが指定されていない場合、プロシージャは呼び出し元のセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="59818-142">Executing as CALLER is the default; if no other option is specified, then the procedure executes in the security context of the caller.</span></span>  
  
-   <span data-ttu-id="59818-143">OWNER : </span><span class="sxs-lookup"><span data-stu-id="59818-143">OWNER.</span></span> <span data-ttu-id="59818-144">OWNER として実行すると、プロシージャがプロシージャ所有者のコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="59818-144">Executing as OWNER executes the procedure in the context of the procedure owner.</span></span> <span data-ttu-id="59818-145">`dbo` すなわちデータベース所有者が所有するスキーマでプロシージャが作成されている場合、プロシージャは権限無制限で実行されます。</span><span class="sxs-lookup"><span data-stu-id="59818-145">If the procedure is created in a schema owned by `dbo` or the database owner, the procedure will execute with unrestricted permissions.</span></span>  
  
-   <span data-ttu-id="59818-146">SELF : </span><span class="sxs-lookup"><span data-stu-id="59818-146">SELF.</span></span> <span data-ttu-id="59818-147">SELF として実行すると、ストアド プロシージャの作成者のセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="59818-147">Executing as SELF executes in the security context of the creator of the stored procedure.</span></span> <span data-ttu-id="59818-148">これは、指定されたユーザーとして実行することと同じです。指定されたユーザーとは、プロシージャを作成または変更した人物です。</span><span class="sxs-lookup"><span data-stu-id="59818-148">This is equivalent to executing as a specified user, where the specified user is the person creating or altering the procedure.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="59818-149">外部リソース</span><span class="sxs-lookup"><span data-stu-id="59818-149">External Resources</span></span>  
 <span data-ttu-id="59818-150">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="59818-150">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="59818-151">リソース</span><span class="sxs-lookup"><span data-stu-id="59818-151">Resource</span></span>|<span data-ttu-id="59818-152">説明</span><span class="sxs-lookup"><span data-stu-id="59818-152">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="59818-153">[コンテキストの切り替え](http://msdn.microsoft.com/library/ms188268.aspx)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="59818-153">[Context Switching](http://msdn.microsoft.com/library/ms188268.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="59818-154">EXECUTE AS 句の使用方法を説明しているトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="59818-154">Contains links to topics describing how to use the EXECUTE AS clause.</span></span>|  
|<span data-ttu-id="59818-155">[EXECUTE AS を使用してカスタム アクセス許可セットを作成する](http://msdn.microsoft.com/library/ms190384.aspx)と[モジュールで EXECUTE AS を使用して](http://msdn.microsoft.com/library/ms178106.aspx)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="59818-155">[Using EXECUTE AS to Create Custom Permission Sets](http://msdn.microsoft.com/library/ms190384.aspx) and [Using EXECUTE AS in Modules](http://msdn.microsoft.com/library/ms178106.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="59818-156">EXECUTE AS 句の使用方法を説明するトピックです。</span><span class="sxs-lookup"><span data-stu-id="59818-156">Topics describe how to use the EXECUTE AS clause.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59818-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="59818-157">See Also</span></span>  
 [<span data-ttu-id="59818-158">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="59818-158">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="59818-159">SQL Server のセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="59818-159">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="59818-160">SQL Server におけるアプリケーション セキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="59818-160">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="59818-161">SQL Server でストアド プロシージャを使用した権限の管理</span><span class="sxs-lookup"><span data-stu-id="59818-161">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="59818-162">SQL Server での動的 SQL の安全な作成</span><span class="sxs-lookup"><span data-stu-id="59818-162">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="59818-163">SQL Server でストアド プロシージャの署名</span><span class="sxs-lookup"><span data-stu-id="59818-163">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="59818-164">ストアド プロシージャによるデータの変更</span><span class="sxs-lookup"><span data-stu-id="59818-164">Modifying Data with Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="59818-165">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="59818-165">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
