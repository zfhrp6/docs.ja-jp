---
title: "SQL Server のセキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c186b25aeaa42b7285316d7bc9de913dd7b89af7
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="sql-server-security"></a><span data-ttu-id="a68df-102">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="a68df-102">SQL Server Security</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] <span data-ttu-id="a68df-103">セキュリティで保護されたデータベース アプリケーションの作成をサポートする多くの機能があります。</span><span class="sxs-lookup"><span data-stu-id="a68df-103">has many features that support creating secure database applications.</span></span>  
  
 <span data-ttu-id="a68df-104">データの盗難や破壊など、セキュリティに関する基本的な考慮事項は、使用している [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のバージョンに関係なく当てはまります。</span><span class="sxs-lookup"><span data-stu-id="a68df-104">Common security considerations, such as data theft or vandalism, apply regardless of the version of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] you are using.</span></span> <span data-ttu-id="a68df-105">また、データの整合性もセキュリティの問題として考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a68df-105">Data integrity should also be considered as a security issue.</span></span> <span data-ttu-id="a68df-106">データの保護を怠り、その場しのぎでデータの操作を許可すると、不注意でまたは意図的に不正確な値に置き換えられたり、完全に削除されてしまうことによってデータの価値が失われてしまうこともあります。</span><span class="sxs-lookup"><span data-stu-id="a68df-106">If data is not protected, it is possible that it could become worthless if ad hoc data manipulation is permitted and the data is inadvertently or maliciously modified with incorrect values or deleted entirely.</span></span> <span data-ttu-id="a68df-107">加えて、機密情報の適切な保管方法など、遵守すべき法的要件が存在します。</span><span class="sxs-lookup"><span data-stu-id="a68df-107">In addition, there are often legal requirements that must be adhered to, such as the correct storage of confidential information.</span></span> <span data-ttu-id="a68df-108">特定の司法管轄域の法令によっては、一部の種類の個人データについて、保管すること自体が完全に禁止されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a68df-108">Storing some kinds of personal data is proscribed entirely, depending on the laws that apply in a particular jurisdiction.</span></span>  
  
 <span data-ttu-id="a68df-109">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] の各バージョンにはそれぞれ異なるセキュリティ機能があり、Windows と同様、新しいバージョンほど機能が強化されています。</span><span class="sxs-lookup"><span data-stu-id="a68df-109">Each version of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] has different security features, as does each version of Windows, with later versions having enhanced functionality over earlier ones.</span></span> <span data-ttu-id="a68df-110">ただし、セキュリティ機能だけでは、データベース アプリケーションの安全性は保証されません。この点を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a68df-110">It is important to understand that security features alone cannot guarantee a secure database application.</span></span> <span data-ttu-id="a68df-111">データベース アプリケーションの要件、実行環境、配置モデル、物理的な場所、およびユーザー数は、アプリケーションごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="a68df-111">Each database application is unique in its requirements, execution environment, deployment model, physical location, and user population.</span></span> <span data-ttu-id="a68df-112">使用範囲がローカルに限定されている一部のアプリケーションでは最小限のセキュリティで済む場合もありますが、インターネット経由で配置されたアプリケーションには、きわめて強固なセキュリティ対策と継続的な監視および評価が要求されます。</span><span class="sxs-lookup"><span data-stu-id="a68df-112">Some applications that are local in scope may need only minimal security whereas other local applications or applications deployed over the Internet may require stringent security measures and ongoing monitoring and evaluation.</span></span>  
  
 <span data-ttu-id="a68df-113">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] データベース アプリケーションのセキュリティ要件は、事後的対策としてではなく設計時に考慮することが大切です。</span><span class="sxs-lookup"><span data-stu-id="a68df-113">The security requirements of a [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] database application should be considered at design time, not as an afterthought.</span></span> <span data-ttu-id="a68df-114">開発サイクルの初期段階で脅威を評価すれば、どこで脆弱性が見つかろうと潜在的な損害を緩和する機会は得ることができます。</span><span class="sxs-lookup"><span data-stu-id="a68df-114">Evaluating threats early in the development cycle gives you the opportunity to mitigate potential damage wherever a vulnerability is detected.</span></span>  
  
 <span data-ttu-id="a68df-115">アプリケーションの初期設計に問題がなくても、システムの進化に伴って新しい脅威が出現する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a68df-115">Even if the initial design of an application is sound, new threats may emerge as the system evolves.</span></span> <span data-ttu-id="a68df-116">データベースを多層的に防御することにより、セキュリティ侵害によって受ける損害を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="a68df-116">By creating multiple lines of defense around your database, you can minimize the damage inflicted by a security breach.</span></span> <span data-ttu-id="a68df-117">防御の第 1 段階は、本当に必要な権限以外は決して付与しないという方針の下、攻撃者に与える隙を減らすことです。</span><span class="sxs-lookup"><span data-stu-id="a68df-117">Your first line of defense is to reduce the attack surface area by never to granting more permissions than are absolutely necessary.</span></span>  
  
 <span data-ttu-id="a68df-118">このセクションの各トピックでは、開発者に関係のある [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のセキュリティ機能を簡単に説明します。[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの関連項目へのリンクのほか、より掘り下げて解説したリソースへのリンクも示しています。</span><span class="sxs-lookup"><span data-stu-id="a68df-118">The topics in this section briefly describe the security features in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] that are relevant for developers, with links to relevant topics in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online and other resources that provide more detailed coverage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a68df-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a68df-119">In This Section</span></span>  
 [<span data-ttu-id="a68df-120">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="a68df-120">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 <span data-ttu-id="a68df-121">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のアーキテクチャおよびセキュリティ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="a68df-121">Describes the architecture and security features of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="a68df-122">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="a68df-122">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 <span data-ttu-id="a68df-123">ADO.NET および [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] アプリケーションに該当するさまざまなセキュリティ シナリオを取り上げます。</span><span class="sxs-lookup"><span data-stu-id="a68df-123">Contains topics discussing various application security scenarios for ADO.NET and [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="a68df-124">SQL Server Express のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="a68df-124">SQL Server Express Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 <span data-ttu-id="a68df-125">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express のセキュリティ上の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="a68df-125">Describes security considerations for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a68df-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a68df-126">Related Sections</span></span>  
[<span data-ttu-id="a68df-127">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="a68df-127">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
<span data-ttu-id="a68df-128">SQL Server と Azure SQL Database のセキュリティに関する考慮事項をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a68df-128">Describes security considerations for SQL Server and Azure SQL Database.</span></span>

[<span data-ttu-id="a68df-129">SQL Server のインストールのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="a68df-129">Security Considerations for a SQL Server Installation</span></span>](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
<span data-ttu-id="a68df-130">SQL Server をインストールする前に考慮すべきセキュリティに関する注意事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="a68df-130">Describes security concerns to consider before installing SQL Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="a68df-131">参照</span><span class="sxs-lookup"><span data-stu-id="a68df-131">See Also</span></span>  
 [<span data-ttu-id="a68df-132">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="a68df-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="a68df-133">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a68df-133">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
