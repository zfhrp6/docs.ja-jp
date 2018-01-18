---
title: "SQL Server でのアプリケーション ロールの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a6c8027e3cbf7bcef3bbe36ba381a08b650516bc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="creating-application-roles-in-sql-server"></a><span data-ttu-id="92eb5-102">SQL Server でのアプリケーション ロールの作成</span><span class="sxs-lookup"><span data-stu-id="92eb5-102">Creating Application Roles in SQL Server</span></span>
<span data-ttu-id="92eb5-103">アプリケーション ロールは、データベース ロールやユーザーに対してではなく、アプリケーションに権限を割り当てる手段です。</span><span class="sxs-lookup"><span data-stu-id="92eb5-103">Application roles provide a way to assign permissions to an application instead of a database role or user.</span></span> <span data-ttu-id="92eb5-104">ユーザーはデータベースに接続し、アプリケーション ロールをアクティブ化して、そのアプリケーションに付与された権限を使用することになります。</span><span class="sxs-lookup"><span data-stu-id="92eb5-104">Users can connect to the database, activate the application role, and assume the permissions granted to the application.</span></span> <span data-ttu-id="92eb5-105">アプリケーション ロールに付与された権限は、接続している間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="92eb5-105">The permissions granted to the application role are in force for the duration of the connection.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92eb5-106">アプリケーション ロールは、クライアント アプリケーションが接続文字列でアプリケーション ロール名とパスワードを渡すことによってアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-106">Application roles are activated when a client application supplies an application role name and a password in the connection string.</span></span> <span data-ttu-id="92eb5-107">2 層アプリケーションでは、パスワードをクライアント コンピューターに保存する必要があるため、セキュリティ上の脆弱性を伴います。</span><span class="sxs-lookup"><span data-stu-id="92eb5-107">They present a security vulnerability in a two-tier application because the password must be stored on the client computer.</span></span> <span data-ttu-id="92eb5-108">3 層アプリケーションでは、アプリケーションのユーザーがアクセスできないような形でパスワードを保存できます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-108">In a three-tier application, you can store the password so that it cannot be accessed by users of the application.</span></span>  
  
## <a name="application-role-features"></a><span data-ttu-id="92eb5-109">アプリケーション ロールの特徴</span><span class="sxs-lookup"><span data-stu-id="92eb5-109">Application Role Features</span></span>  
 <span data-ttu-id="92eb5-110">アプリケーション ロールには次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="92eb5-110">Application roles have the following features:</span></span>  
  
-   <span data-ttu-id="92eb5-111">データベース ロールとは異なり、アプリケーション ロールはメンバーを持ちません。</span><span class="sxs-lookup"><span data-stu-id="92eb5-111">Unlike database roles, application roles contain no members.</span></span>  
  
-   <span data-ttu-id="92eb5-112">アプリケーション ロールは、アプリケーションが `sp_setapprole` システム ストアド プロシージャにアプリケーション ロール名とパスワードを渡すことによってアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-112">Application roles are activated when an application supplies the application role name and a password to the `sp_setapprole` system stored procedure.</span></span>  
  
-   <span data-ttu-id="92eb5-113">パスワードはクライアント コンピューターに保存しておき、実行時に渡す必要があります。アプリケーション ロールを SQL Server 内からアクティブ化することはできません。</span><span class="sxs-lookup"><span data-stu-id="92eb5-113">The password must be stored on the client computer and supplied at run time; an application role cannot be activated from inside of SQL Server.</span></span>  
  
-   <span data-ttu-id="92eb5-114">パスワードは暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="92eb5-114">The password is not encrypted.</span></span> <span data-ttu-id="92eb5-115">パラメーターのパスワードが一方向のハッシュとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-115">The parameter password is stored as a one-way hash.</span></span>  
  
-   <span data-ttu-id="92eb5-116">アクティブ化後、アプリケーション ロールを使用して取得した権限は、接続している間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="92eb5-116">Once activated, permissions acquired through the application role remain in effect for the duration of the connection.</span></span>  
  
-   <span data-ttu-id="92eb5-117">アプリケーション ロールは、`public` ロールに付与された権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="92eb5-117">The application role inherits permissions granted to the `public` role.</span></span>  
  
-   <span data-ttu-id="92eb5-118">アプリケーション ロールが `sysadmin` 固定サーバー ロールのメンバーによってアクティブ化された場合、セキュリティ コンテキストは、接続している間、アプリケーション ロールのセキュリティ コンテキストに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="92eb5-118">If a member of the `sysadmin` fixed server role activates an application role, the security context switches to that of the application role for the duration of the connection.</span></span>  
  
-   <span data-ttu-id="92eb5-119">アプリケーション ロールを持ったデータベースに `guest` アカウントを作成した場合、そのアプリケーション ロールまたはそれを呼び出すログインに対するデータベース ユーザー アカウントを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="92eb5-119">If you create a `guest` account in a database that has an application role, you do not need to create a database user account for the application role or for any of the logins that invoke it.</span></span> <span data-ttu-id="92eb5-120">別のデータベースに `guest` アカウントが存在する場合は、アプリケーション ロールでそのデータベースに直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-120">Application roles can directly access another database only if a `guest` account exists in the second database</span></span>  
  
-   <span data-ttu-id="92eb5-121">SYSTEM_USER など、ログイン名を返す組み込み関数を実行した場合、アプリケーション ロールを呼び出したログイン名が返されます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-121">Built-in functions that return login names, such as SYSTEM_USER, return the name of the login that invoked the application role.</span></span> <span data-ttu-id="92eb5-122">データベース ユーザー名を返す組み込み関数を実行した場合、アプリケーション ロールの名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-122">Built-in functions that return database user names return the name of the application role.</span></span>  
  
### <a name="the-principle-of-least-privilege"></a><span data-ttu-id="92eb5-123">最小特権の原則</span><span class="sxs-lookup"><span data-stu-id="92eb5-123">The Principle of Least Privilege</span></span>  
 <span data-ttu-id="92eb5-124">パスワードが漏洩した場合に備えて、アプリケーション ロールには必要な権限だけを付与してください。</span><span class="sxs-lookup"><span data-stu-id="92eb5-124">Application roles should be granted only required permissions in case the password is compromised.</span></span> <span data-ttu-id="92eb5-125">アプリケーション ロールを使ったデータベースでは、`public` ロールに対する権限は取り消す必要があります。</span><span class="sxs-lookup"><span data-stu-id="92eb5-125">Permissions to the `public` role should be revoked in any database using an application role.</span></span> <span data-ttu-id="92eb5-126">アプリケーション ロールの呼び出し元が特定のデータベースにアクセスできないようにするには、そのデータベースの `guest` アカウントを無効にします。</span><span class="sxs-lookup"><span data-stu-id="92eb5-126">Disable the `guest` account in any database you do not want callers of the application role to have access to.</span></span>  
  
### <a name="application-role-enhancements"></a><span data-ttu-id="92eb5-127">アプリケーション ロールの機能強化</span><span class="sxs-lookup"><span data-stu-id="92eb5-127">Application Role Enhancements</span></span>  
 <span data-ttu-id="92eb5-128">アプリケーション ロールをアクティブ化した後で実行コンテキストを元の呼び出し元に戻すことができるため、接続プールを無効にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="92eb5-128">The execution context can be switched back to the original caller after activating an application role, removing the need to disable connection pooling.</span></span> <span data-ttu-id="92eb5-129">呼び出し元のコンテキスト情報を格納するクッキーを作成するための新しいオプションが `sp_setapprole` プロシージャに追加されています。</span><span class="sxs-lookup"><span data-stu-id="92eb5-129">The `sp_setapprole` procedure has a new option that creates a cookie, which contains context information about the caller.</span></span> <span data-ttu-id="92eb5-130">`sp_unsetapprole` プロシージャにそのクッキーを渡して呼び出すことによって、元のセッションに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-130">You can revert the session by calling the `sp_unsetapprole` procedure, passing it the cookie.</span></span>  
  
## <a name="application-role-alternatives"></a><span data-ttu-id="92eb5-131">アプリケーション ロールに代わる方法</span><span class="sxs-lookup"><span data-stu-id="92eb5-131">Application Role Alternatives</span></span>  
 <span data-ttu-id="92eb5-132">アプリケーション ロールはパスワードのセキュリティに依存する関係上、セキュリティ上の脆弱性を伴います。</span><span class="sxs-lookup"><span data-stu-id="92eb5-132">Application roles depend on the security of a password, which presents a potential security vulnerability.</span></span> <span data-ttu-id="92eb5-133">パスワードをアプリケーション コードに組み込んだり、ディスクに保存したりすると、パスワードが漏洩する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92eb5-133">Passwords may be exposed by being embedded in application code or saved on disk.</span></span>  
  
 <span data-ttu-id="92eb5-134">以下の代替策を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92eb5-134">You may want to consider the following alternatives.</span></span>  
  
-   <span data-ttu-id="92eb5-135">EXECUTE AS ステートメントに NO REVERT 句と WITH COOKIE 句を指定してコンテキスト切り替えを行う。</span><span class="sxs-lookup"><span data-stu-id="92eb5-135">Use context switching with the EXECUTE AS statement with its NO REVERT and WITH COOKIE clauses.</span></span> <span data-ttu-id="92eb5-136">ログインにマップされていないユーザー アカウントをデータベースに作成し、</span><span class="sxs-lookup"><span data-stu-id="92eb5-136">You can create a user account in a database that is not mapped to a login.</span></span> <span data-ttu-id="92eb5-137">このアカウントに権限を割り当てるようにします。</span><span class="sxs-lookup"><span data-stu-id="92eb5-137">You then assign permissions to this account.</span></span> <span data-ttu-id="92eb5-138">EXECUTE AS はパスワード ベースではなく、権限ベースであるため、非ログイン ユーザーで使用した方が高いセキュリティを確保できます。</span><span class="sxs-lookup"><span data-stu-id="92eb5-138">Using EXECUTE AS with a login-less user is more secure because it is permission-based, not password-based.</span></span> <span data-ttu-id="92eb5-139">詳細については、次を参照してください。 [SQL Server での偽装でのアクセス許可をカスタマイズする](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)です。</span><span class="sxs-lookup"><span data-stu-id="92eb5-139">For more information, see [Customizing Permissions with Impersonation in SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
-   <span data-ttu-id="92eb5-140">証明書を使ってストアド プロシージャに署名し、そのプロシージャを実行するのに必要な権限だけを付与する。</span><span class="sxs-lookup"><span data-stu-id="92eb5-140">Sign stored procedures with certificates, granting only permission to execute the procedures.</span></span> <span data-ttu-id="92eb5-141">詳細については、次を参照してください。 [SQL Server でストアド プロシージャの署名](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)です。</span><span class="sxs-lookup"><span data-stu-id="92eb5-141">For more information, see [Signing Stored Procedures in SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="92eb5-142">外部リソース</span><span class="sxs-lookup"><span data-stu-id="92eb5-142">External Resources</span></span>  
 <span data-ttu-id="92eb5-143">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="92eb5-143">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="92eb5-144">リソース</span><span class="sxs-lookup"><span data-stu-id="92eb5-144">Resource</span></span>|<span data-ttu-id="92eb5-145">説明</span><span class="sxs-lookup"><span data-stu-id="92eb5-145">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="92eb5-146">[アプリケーション ロール](http://msdn.microsoft.com/library/ms190998.aspx)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="92eb5-146">[Application Roles](http://msdn.microsoft.com/library/ms190998.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="92eb5-147">SQL Server 2008 でアプリケーション ロールを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="92eb5-147">Describes how to create and use application roles in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92eb5-148">参照</span><span class="sxs-lookup"><span data-stu-id="92eb5-148">See Also</span></span>  
 [<span data-ttu-id="92eb5-149">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="92eb5-149">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="92eb5-150">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="92eb5-150">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="92eb5-151">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="92eb5-151">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="92eb5-152">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="92eb5-152">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
