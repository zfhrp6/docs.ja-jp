---
title: "SQL Server セキュリティの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ff0a78a852bdbf2fa1eb075273cad317c21fb182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="31b7c-102">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="31b7c-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="31b7c-103">セキュリティを幾重にも重ねて講じる多層防御は、セキュリティ上の脅威に対抗する最も有効な手段です。</span><span class="sxs-lookup"><span data-stu-id="31b7c-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="31b7c-104">SQL Server のセキュリティ アーキテクチャは、データベースの管理者および開発者が安全なデータベース アプリケーションを作成して脅威に対応できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="31b7c-105">SQL Server は、前のバージョンに新しい機能を導入することによって絶えず進化してきました。</span><span class="sxs-lookup"><span data-stu-id="31b7c-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="31b7c-106">しかし、セキュリティを箱詰めして出荷することはできません。</span><span class="sxs-lookup"><span data-stu-id="31b7c-106">However, security does not ship in the box.</span></span> <span data-ttu-id="31b7c-107">アプリケーションには、それぞれ固有のセキュリティ要件があります。</span><span class="sxs-lookup"><span data-stu-id="31b7c-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="31b7c-108">開発者は、既知の脅威に対してどのような機能を組み合わせるのが最も効果的かを理解し、将来発生する可能性のある脅威を予測する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31b7c-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="31b7c-109">SQL Server のインスタンスは、サーバーを頂点とする階層形式のエンティティのコレクションを持ちます。</span><span class="sxs-lookup"><span data-stu-id="31b7c-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="31b7c-110">各サーバーには複数のデータベースが存在し、各データベースには、セキュリティ保護可能なオブジェクトのコレクションが存在します。</span><span class="sxs-lookup"><span data-stu-id="31b7c-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="31b7c-111">セキュリティ保護可能なすべての SQL Server が関連付けられている*権限*に付与する、*プリンシパル*これは、個人、グループ、または SQL Server へのアクセス許可を処理します。</span><span class="sxs-lookup"><span data-stu-id="31b7c-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="31b7c-112">SQL Server のセキュリティ フレームワークを通じてセキュリティ保護可能なエンティティへのアクセスを管理する*認証*と*承認*です。</span><span class="sxs-lookup"><span data-stu-id="31b7c-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
-   <span data-ttu-id="31b7c-113">認証は SQL Server にログオンするプロセスです。プリンシパルは、サーバーによって評価される資格情報を送信することによってアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="31b7c-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="31b7c-114">認証対象となるユーザーまたはプロセスの ID は、認証によって確立されます。</span><span class="sxs-lookup"><span data-stu-id="31b7c-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
-   <span data-ttu-id="31b7c-115">承認は、プリンシパルがアクセスできる、セキュリティ保護可能なリソースと、これらのリソースに対して許可された操作を特定するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="31b7c-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="31b7c-116">このセクションの各トピックでは、SQL Server のセキュリティの基礎を取り上げています。より詳細な情報を確認できるように、該当するバージョンの SQL Server オンライン ブックへのリンクも用意されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31b7c-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="31b7c-117">In This Section</span></span>  
 [<span data-ttu-id="31b7c-118">SQL Server での認証</span><span class="sxs-lookup"><span data-stu-id="31b7c-118">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 <span data-ttu-id="31b7c-119">SQL Server のログインと認証の説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="31b7c-120">SQL Server のサーバー ロールとデータベース ロール</span><span class="sxs-lookup"><span data-stu-id="31b7c-120">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="31b7c-121">固定サーバー ロールと固定データベース ロール、カスタム データベース ロール、組み込みアカウントの説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="31b7c-122">SQL Server における所有権とユーザーとスキーマの分離</span><span class="sxs-lookup"><span data-stu-id="31b7c-122">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="31b7c-123">オブジェクトの所有権とユーザーとスキーマの分離の説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="31b7c-124">SQL Server の承認とアクセス許可</span><span class="sxs-lookup"><span data-stu-id="31b7c-124">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="31b7c-125">最小特権の原則に基づく権限の付与について説明しているほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="31b7c-126">SQL Server でのデータの暗号化</span><span class="sxs-lookup"><span data-stu-id="31b7c-126">Data Encryption in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 <span data-ttu-id="31b7c-127">SQL Server におけるデータの暗号化オプションの説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="31b7c-128">SQL Server の CLR 統合セキュリティ</span><span class="sxs-lookup"><span data-stu-id="31b7c-128">CLR Integration Security in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="31b7c-129">CLR 統合セキュリティ関連リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="31b7c-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b7c-130">参照</span><span class="sxs-lookup"><span data-stu-id="31b7c-130">See Also</span></span>  
 [<span data-ttu-id="31b7c-131">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="31b7c-131">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="31b7c-132">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="31b7c-132">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [<span data-ttu-id="31b7c-133">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="31b7c-133">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="31b7c-134">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="31b7c-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
