---
title: "SQL Server Compact および LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2717a94228dc1be8da0d84179201747d60c896a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="4a386-102">SQL Server Compact および LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4a386-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="4a386-103">SQL Server Compact は、Visual Studio と共にインストールされる既定のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="4a386-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="4a386-104">詳細については、次を参照してください。 [PAVE 経由でを使用して SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc)です。</span><span class="sxs-lookup"><span data-stu-id="4a386-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="4a386-105">このトピックでは説明の使用法、構成、機能セット、およびスコープの主要な違い[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4a386-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="4a386-106">LINQ to SQL との関係における SQL Server Compact の特徴</span><span class="sxs-lookup"><span data-stu-id="4a386-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="4a386-107">既定では、SQL Server Compact がインストールされているすべての[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]のエディションであるため、開発用コンピューターで使用するために使用可能な[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="4a386-107">By default, SQL Server Compact is installed for all [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="4a386-108">SQL Server Compact を使用するアプリケーションの展開と[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]のとは異なる、[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="4a386-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application.</span></span> <span data-ttu-id="4a386-109">SQL Server Compact は .NET Framework の一部ではないため、アプリケーションにパッケージ化するか、Microsoft サイトから個別にダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a386-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="4a386-110">これには、次のような特徴があります。</span><span class="sxs-lookup"><span data-stu-id="4a386-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="4a386-111">SQL Server Compact は DLL としてパッケージ化されており、データベース ファイル (.sdf 拡張子) に対して直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a386-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="4a386-112">SQL Server Compact は、クライアント アプリケーションと同じプロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a386-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="4a386-113">SQL Server Compact との通信の効率と通信するよりもかなり大きくしたがって、[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="4a386-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4a386-114">その一方で、SQL Server Compact はコストを伴うマネージ コードとアンマネージ コード間の相互運用性が必要です。</span><span class="sxs-lookup"><span data-stu-id="4a386-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="4a386-115">SQL Server Compact DLL のサイズは小さいです。</span><span class="sxs-lookup"><span data-stu-id="4a386-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="4a386-116">このため、アプリケーション全体のサイズが抑制されます。</span><span class="sxs-lookup"><span data-stu-id="4a386-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="4a386-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムおよび SQLMetal コマンド ライン ツールが SQL Server Compact をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4a386-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="4a386-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] では、SQL Server Compact はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4a386-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="4a386-119">機能セット</span><span class="sxs-lookup"><span data-stu-id="4a386-119">Feature Set</span></span>  
 <span data-ttu-id="4a386-120">SQL Server Compact の機能セットが、機能セットよりもはるかに簡単[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]に影響を与える次の方法で[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="4a386-120">The SQL Server Compact feature set is much simpler than the feature set of [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="4a386-121">SQL Server Compact は、ストアド プロシージャまたはビューをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="4a386-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="4a386-122">SQL Server Compact は、一部のデータ型と SQL 関数のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="4a386-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="4a386-123">SQL Server Compact は、一部の SQL コンストラクトのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="4a386-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="4a386-124">SQL Server Compact は、最小限のオプティマイザーを備えています。</span><span class="sxs-lookup"><span data-stu-id="4a386-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="4a386-125">一部のクエリがタイムアウトを可能性があることができます。</span><span class="sxs-lookup"><span data-stu-id="4a386-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="4a386-126">SQL Server Compact は、部分信頼をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="4a386-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a386-127">参照</span><span class="sxs-lookup"><span data-stu-id="4a386-127">See Also</span></span>  
 [<span data-ttu-id="4a386-128">参照</span><span class="sxs-lookup"><span data-stu-id="4a386-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
