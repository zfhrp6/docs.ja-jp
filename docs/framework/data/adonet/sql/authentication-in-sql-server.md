---
title: "SQL Server での認証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa9a23f00e7ce3b52c2ff64c8b22e1b4b8727b97
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="b9ed3-102">SQL Server での認証</span><span class="sxs-lookup"><span data-stu-id="b9ed3-102">Authentication in SQL Server</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-103"> は、Windows 認証モードと混合モードという 2 つの認証モードをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-103"> supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
-   <span data-ttu-id="b9ed3-104">Windows 認証は既定の認証モードです。この [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] セキュリティ モデルは Windows と緊密に統合されているため、多くの場合、統合セキュリティと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-104">Windows authentication is the default, and is often referred to as integrated security because this [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] security model is tightly integrated with Windows.</span></span> <span data-ttu-id="b9ed3-105">特定の Windows ユーザーおよび Windows グループが、信頼されたアカウントとして SQL Server へのログインが許可されます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="b9ed3-106">既に認証済みの Windows ユーザーは別途資格情報を提示する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
-   <span data-ttu-id="b9ed3-107">混合モードは、Windows による認証と [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] による認証の両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-107">Mixed mode supports authentication both by Windows and by [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b9ed3-108">ユーザー名とパスワードの組み合わせは、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 内で管理されます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-108">User name and password pairs are maintained within [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9ed3-109">できるだけ Windows 認証を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="b9ed3-110">Windows 認証では、暗号化された一連のメッセージを使用して [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のユーザーを認証します。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-110">Windows authentication uses a series of encrypted messages to authenticate users in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b9ed3-111">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ログインを使用した場合、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のログイン名とパスワードはネットワーク経由で渡されるためセキュリティが低下します。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-111">When [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins are used, [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] login names and passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="b9ed3-112">Windows 認証では、既に Windows にログオンしているユーザーが別途 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] にログオンする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b9ed3-113">次の `SqlConnection.ConnectionString` では、Windows 認証が指定されているため、ユーザー名もパスワードも不要です。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring the a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  <span data-ttu-id="b9ed3-114">ログインは、データベース ユーザーとは異なります。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-114">Logins are distinct from database users.</span></span> <span data-ttu-id="b9ed3-115">ログインまたは Windows グループは、別個の操作でデータベース ユーザーまたはロールにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="b9ed3-116">その後、ユーザーまたはロールに対してデータベース オブジェクトにアクセスするための権限を付与することになります。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="b9ed3-117">認証のシナリオ</span><span class="sxs-lookup"><span data-stu-id="b9ed3-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="b9ed3-118">通常、以下の状況では Windows 認証が最良の選択肢です。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
-   <span data-ttu-id="b9ed3-119">ドメイン コントローラーが存在する。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-119">There is a domain controller.</span></span>  
  
-   <span data-ttu-id="b9ed3-120">アプリケーションとデータベースが同じコンピューター上に存在する。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-120">The application and the database are on the same computer.</span></span>  
  
-   <span data-ttu-id="b9ed3-121">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express または LocalDB のインスタンスを使用している。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-121">You are using an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express or LocalDB.</span></span>  
  
 <span data-ttu-id="b9ed3-122">次の状況では、SQL Server ログインを使用することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-122">SQL Server logins are often used in the following situations:</span></span>  
  
-   <span data-ttu-id="b9ed3-123">ワークグループが存在する。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-123">If you have a workgroup.</span></span>  
  
-   <span data-ttu-id="b9ed3-124">ユーザーが別の信頼されていないドメインから接続する。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-124">Users connect from different, non-trusted domains.</span></span>  
  
-   <span data-ttu-id="b9ed3-125">[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] などのインターネット アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-125">Internet applications, such as [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9ed3-126">Windows 認証を指定しても、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ログインは無効になりません。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-126">Specifying Windows authentication does not disable [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="b9ed3-127">高い権限を持つ [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] ログインを無効にするには、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ステートメント ALTER LOGIN DISABLE を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-127">Use the ALTER LOGIN DISABLE [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statement to disable highly-privileged [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="b9ed3-128">ログインの種類</span><span class="sxs-lookup"><span data-stu-id="b9ed3-128">Login Types</span></span>  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-129"> では、次の 3 種類のログインがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-129"> supports three types of logins:</span></span>  
  
-   <span data-ttu-id="b9ed3-130">ローカル Windows ユーザー アカウントまたは信頼されたドメイン アカウント。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-130">A local Windows user account or trusted domain account.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-131"> が Windows に依存する形で Windows ユーザー アカウントを認証します。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-131"> relies on Windows to authenticate the Windows user accounts.</span></span>  
  
-   <span data-ttu-id="b9ed3-132">Windows グループ。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-132">Windows group.</span></span> <span data-ttu-id="b9ed3-133">Windows グループへのアクセス権を付与すると、そのグループに属しているすべての Windows ユーザー ログインにアクセス権が付与されます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-134"> ログイン。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-134"> login.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-135"> はユーザー名およびパスワードのハッシュを master データベースに格納し、内部の認証方法を使ってログイン試行を検証します。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-135"> stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-136"> では、証明書または非対称キーから作成されたログインが提供されています。このログインはコード署名にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-136"> provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="b9ed3-137">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] への接続には使用できません。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-137">They cannot be used to connect to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="b9ed3-138">混合モード認証</span><span class="sxs-lookup"><span data-stu-id="b9ed3-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="b9ed3-139">混合モード認証を使用する場合は、SQL Server に格納される [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ログインを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-139">If you must use mixed mode authentication, you must create [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins, which are stored in SQL Server.</span></span> <span data-ttu-id="b9ed3-140">さらに、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のユーザー名とパスワードを実行時に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-140">You then have to supply the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] user name and password at run time.</span></span>  
  
> [!IMPORTANT]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-141"> は、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ("system administrator" の略) という名前の `sa` ログインが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-141"> installs with a [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="b9ed3-142">`sa` ログインには強力なパスワードを割り当て、アプリケーションで `sa` ログインを使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="b9ed3-143">`sa` ログインは、サーバー全体に対する取り消し不可能な管理者の資格情報を持つ `sysadmin` 固定サーバー ロールにマップされます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="b9ed3-144">システム管理者のアクセス権が攻撃者によって取得された場合の潜在的な損害は計り知れません。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="b9ed3-145">既定では、Windows `BUILTIN\Administrators` グループ (ローカル管理者のグループ) のすべてのメンバーが `sysadmin` ロールに所属しますが、sysadmin ロールから Windows の Administrators グループのメンバーを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-146"> 以降のバージョンで [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] を実行している場合、[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] ログインに Windows のパスワード ポリシー メカニズムが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-146"> provides Windows password policy mechanisms for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="b9ed3-147">パスワードの複雑性のポリシーは、考えられるパスワードの数を増やすことにより、総当たり攻撃を防ぐようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="b9ed3-148"> では、[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] 内部で使用されるパスワードに、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] で使用されているものと同じ複雑性ポリシーおよび有効期限ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-148"> can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9ed3-149">ユーザー入力から文字列を連結することによって接続文字列を構築している場合、接続文字列のインジェクション攻撃に対して脆弱になります。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="b9ed3-150"><xref:System.Data.SqlClient.SqlConnectionStringBuilder> を使用すると、構文的に正しい接続文字列を実行時に作成できます。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="b9ed3-151">詳細については、次を参照してください。[接続文字列ビルダー](../../../../../docs/framework/data/adonet/connection-string-builders.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-151">For more information, see [Connection String Builders](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="b9ed3-152">外部リソース</span><span class="sxs-lookup"><span data-stu-id="b9ed3-152">External Resources</span></span>  
 <span data-ttu-id="b9ed3-153">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="b9ed3-154">リソース</span><span class="sxs-lookup"><span data-stu-id="b9ed3-154">Resource</span></span>|<span data-ttu-id="b9ed3-155">説明</span><span class="sxs-lookup"><span data-stu-id="b9ed3-155">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b9ed3-156">[プリンシパル](http://msdn.microsoft.com/library/bb543165.aspx)で[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="b9ed3-156">[Principals](http://msdn.microsoft.com/library/bb543165.aspx) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="b9ed3-157">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のログインおよびその他のセキュリティ プリンシパルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9ed3-157">Describes logins and other security principals in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9ed3-158">参照</span><span class="sxs-lookup"><span data-stu-id="b9ed3-158">See Also</span></span>  
 [<span data-ttu-id="b9ed3-159">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="b9ed3-159">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="b9ed3-160">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="b9ed3-160">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="b9ed3-161">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="b9ed3-161">Connecting to a Data Source</span></span>](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="b9ed3-162">接続文字列</span><span class="sxs-lookup"><span data-stu-id="b9ed3-162">Connection Strings</span></span>](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="b9ed3-163">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="b9ed3-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
