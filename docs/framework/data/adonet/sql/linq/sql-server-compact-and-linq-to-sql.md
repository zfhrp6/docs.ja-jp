---
title: SQL Server Compact および LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 74b8a7a6dfc9a4050dbba9a8c2f6969dba42656c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355787"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="061d4-102">SQL Server Compact および LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="061d4-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="061d4-103">SQL Server Compact は、Visual Studio と共にインストールされる既定のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="061d4-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="061d4-104">詳細については、次を参照してください。 [PAVE 経由でを使用して SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc)です。</span><span class="sxs-lookup"><span data-stu-id="061d4-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="061d4-105">このトピックでは説明の使用法、構成、機能セット、およびスコープの主要な違い[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]をサポートします。</span><span class="sxs-lookup"><span data-stu-id="061d4-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="061d4-106">LINQ to SQL との関係における SQL Server Compact の特徴</span><span class="sxs-lookup"><span data-stu-id="061d4-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="061d4-107">既定では、SQL Server Compact はすべて Visual Studio のエディション用にインストールし、開発用コンピューターで使用するために使用できるよう[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="061d4-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="061d4-108">SQL Server Compact を使用するアプリケーションの展開と[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL Server アプリケーションと異なります。</span><span class="sxs-lookup"><span data-stu-id="061d4-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="061d4-109">SQL Server Compact は .NET Framework の一部ではないため、アプリケーションにパッケージ化するか、Microsoft サイトから個別にダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="061d4-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="061d4-110">これには、次のような特徴があります。</span><span class="sxs-lookup"><span data-stu-id="061d4-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="061d4-111">SQL Server Compact は DLL としてパッケージ化されており、データベース ファイル (.sdf 拡張子) に対して直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="061d4-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="061d4-112">SQL Server Compact は、クライアント アプリケーションと同じプロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="061d4-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="061d4-113">SQL Server Compact との通信の効率性は、SQL Server と通信するよりも大幅に高いためできます。</span><span class="sxs-lookup"><span data-stu-id="061d4-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="061d4-114">その一方で、SQL Server Compact はコストを伴うマネージ コードとアンマネージ コード間の相互運用性が必要です。</span><span class="sxs-lookup"><span data-stu-id="061d4-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="061d4-115">SQL Server Compact DLL のサイズは小さいです。</span><span class="sxs-lookup"><span data-stu-id="061d4-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="061d4-116">このため、アプリケーション全体のサイズが抑制されます。</span><span class="sxs-lookup"><span data-stu-id="061d4-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="061d4-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムおよび SQLMetal コマンド ライン ツールが SQL Server Compact をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="061d4-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="061d4-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] では、SQL Server Compact はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="061d4-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="061d4-119">機能セット</span><span class="sxs-lookup"><span data-stu-id="061d4-119">Feature Set</span></span>  
 <span data-ttu-id="061d4-120">影響を与える次のように、SQL Server Compact の機能セットが SQL Server の機能セットよりもはるかに簡単[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="061d4-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="061d4-121">SQL Server Compact は、ストアド プロシージャまたはビューをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="061d4-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="061d4-122">SQL Server Compact は、一部のデータ型と SQL 関数のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="061d4-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="061d4-123">SQL Server Compact は、一部の SQL コンストラクトのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="061d4-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="061d4-124">SQL Server Compact は、最小限のオプティマイザーを備えています。</span><span class="sxs-lookup"><span data-stu-id="061d4-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="061d4-125">一部のクエリがタイムアウトを可能性があることができます。</span><span class="sxs-lookup"><span data-stu-id="061d4-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="061d4-126">SQL Server Compact は、部分信頼をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="061d4-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061d4-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="061d4-127">See Also</span></span>  
 [<span data-ttu-id="061d4-128">参照</span><span class="sxs-lookup"><span data-stu-id="061d4-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
