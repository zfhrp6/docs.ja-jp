---
title: "LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f44b6da8ecc8d036a9550856f71b2981770e9478
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="cf43b-102">LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション</span><span class="sxs-lookup"><span data-stu-id="cf43b-102">N-Tier and Remote Applications with LINQ to SQL</span></span>
<span data-ttu-id="cf43b-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用する n 層つまり多層アプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="cf43b-103">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="cf43b-104">通常、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]データ コンテキスト、エンティティ クラス、およびクエリ構築ロジック上にある、中間層のデータ アクセス層 (DAL) とします。</span><span class="sxs-lookup"><span data-stu-id="cf43b-104">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="cf43b-105">ビジネス ロジックと非永続的データは、エンティティとデータ コンテキストの部分クラスと部分メソッドの中に完全に実装できます。または、別個のクラスに実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf43b-105">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>  
  
 <span data-ttu-id="cf43b-106">クライアントまたはプレゼンテーション層は、中間層のリモート インターフェイス上のメソッドを呼び出し、その層の DAL は、<xref:System.Data.Linq.DataContext> メソッドにマップされるクエリまたはストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf43b-106">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="cf43b-107">中間層は、通常、エンティティまたはプロキシ オブジェクトの XML 表現としてデータをクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="cf43b-107">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>  
  
 <span data-ttu-id="cf43b-108">中間層では、データ コンテキストによってエンティティが作成され、データ コンテキストはエンティティの状態を追跡し、データベースからの遅延読み込み、および変更内容のデータベースへの送信を管理します。</span><span class="sxs-lookup"><span data-stu-id="cf43b-108">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="cf43b-109">これらのエンティティは、`DataContext` にいわばアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="cf43b-109">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="cf43b-110">ただし、シリアル化によってエンティティが別の層に送られた後は、エンティティがデタッチされます。つまり、その状態が `DataContext` によって追跡されなくなります。</span><span class="sxs-lookup"><span data-stu-id="cf43b-110">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="cf43b-111">更新のためにクライアントによって戻されるエンティティは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が変更内容をデータベースに送信する前に、データ コンテキストに再びアタッチされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf43b-111">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="cf43b-112">オプティミスティック同時実行チェックのために元の値またはタイムスタンプが必要とされる場合、クライアントはこれらを中間層に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf43b-112">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>  
  
 <span data-ttu-id="cf43b-113">ASP.NET アプリケーションでは、このような複雑な操作の大部分が <xref:System.Web.UI.WebControls.LinqDataSource> によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="cf43b-113">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="cf43b-114">詳細については、次を参照してください。 [NIB: LinqDataSource Web サーバー コントロールの概要](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)です。</span><span class="sxs-lookup"><span data-stu-id="cf43b-114">For more information, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="cf43b-115">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="cf43b-115">Additional Resources</span></span>  
 <span data-ttu-id="cf43b-116">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用する n 層アプリケーションの実装方法について、詳しくは以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf43b-116">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>  
  
-   [<span data-ttu-id="cf43b-117">LINQ to SQL N 層と ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cf43b-117">LINQ to SQL N-Tier with ASP.NET</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [<span data-ttu-id="cf43b-118">LINQ to SQL N 層 Web サービスと</span><span class="sxs-lookup"><span data-stu-id="cf43b-118">LINQ to SQL N-Tier with Web Services</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [<span data-ttu-id="cf43b-119">密結合クライアント サーバー アプリケーションと LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cf43b-119">LINQ to SQL with Tightly-Coupled Client-Server Applications</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [<span data-ttu-id="cf43b-120">N 層ビジネス ロジックの実装</span><span class="sxs-lookup"><span data-stu-id="cf43b-120">Implementing N-Tier Business Logic</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [<span data-ttu-id="cf43b-121">データで取得および CUD 操作 N 層アプリケーション (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="cf43b-121">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 <span data-ttu-id="cf43b-122">ADO.NET データセットを使用する n 層アプリケーションの詳細については、次を参照してください。 [n 層アプリケーションでデータセットを操作](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)です。</span><span class="sxs-lookup"><span data-stu-id="cf43b-122">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf43b-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf43b-123">See Also</span></span>  
 [<span data-ttu-id="cf43b-124">背景情報</span><span class="sxs-lookup"><span data-stu-id="cf43b-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
