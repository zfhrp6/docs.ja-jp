---
title: "SQL 生成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 727aa0ca3e1673a5bbd29884077ed5aa65d792f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation"></a><span data-ttu-id="f8e2f-102">SQL 生成</span><span class="sxs-lookup"><span data-stu-id="f8e2f-102">SQL Generation</span></span>
<span data-ttu-id="f8e2f-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] のプロバイダーを作成する場合は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] コマンド ツリーを特定のデータベースが認識できる SQL (たとえば、SQL Server の場合は Transact-SQL、Oracle の場合は PL/SQL) に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-103">When you write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you must translate [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] command trees into SQL that a specific database can understand, such as Transact-SQL for SQL Server or PL/SQL for Oracle.</span></span> <span data-ttu-id="f8e2f-104">ここでは、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] プロバイダーの SQL 生成コンポーネント (SELECT クエリ用) の開発方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-104">In this section, you will learn how to develop a SQL generation component (for SELECT queries) for an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="f8e2f-105">挿入方法については、更新、および削除クエリを参照してください[変更 SQL 生成](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-105">For information about insert, update, and delete queries, see [Modification SQL Generation](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).</span></span>  
  
 <span data-ttu-id="f8e2f-106">このセクションの内容を理解するには、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] と ADO.NET プロバイダー モデルについての知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-106">To understand this section, you should be familiar with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the ADO.NET Provider Model.</span></span> <span data-ttu-id="f8e2f-107">また、コマンド ツリーと <xref:System.Data.Common.CommandTrees.DbExpression> について理解している必要もあります。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-107">You should also understand command trees and <xref:System.Data.Common.CommandTrees.DbExpression>.</span></span>  
  
## <a name="the-role-of-the-sql-generation-module"></a><span data-ttu-id="f8e2f-108">SQL 生成モジュールの役割</span><span class="sxs-lookup"><span data-stu-id="f8e2f-108">The Role of the SQL Generation Module</span></span>  
 <span data-ttu-id="f8e2f-109">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] プロバイダーの SQL 生成モジュールは、指定されたクエリ コマンド ツリーを、SQL:1999 準拠のデータベースを対象とする 1 つの SQL SELECT ステートメントに変換します。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-109">The SQL generation module of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider translates a given query command tree into a single SQL SELECT statement that targets a SQL:1999-compliant database.</span></span> <span data-ttu-id="f8e2f-110">生成される SQL 内の入れ子になったクエリは、できるだけ少なくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-110">The generated SQL should have as few nested queries as possible.</span></span> <span data-ttu-id="f8e2f-111">SQL 生成モジュールによって出力クエリ コマンド ツリーを簡素化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-111">The SQL generation module should not simplify the output query command tree.</span></span> <span data-ttu-id="f8e2f-112">これは、結合の排除や連続するフィルター ノードの折りたたみなどにより、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] が実行する処理です。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-112">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] will do this, for example by eliminating joins and collapsing consecutive filter nodes.</span></span>  
  
 <span data-ttu-id="f8e2f-113"><!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices`クラスは、コマンド ツリーに変換する、SQL 生成レイヤーにアクセスするための出発点<!--zz<xref:System.Data.Common.DbCommands>-->`System.Data.Common.DbCommands`です。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-113">The <!--zz<xref:System.Data.Common.DBProviderServices> --> `System.Data.Common.DBProviderServices`  class is the starting point for accessing the SQL generation layer to convert command trees into <!--zz<xref:System.Data.Common.DbCommands>--> `System.Data.Common.DbCommands`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8e2f-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f8e2f-114">In This Section</span></span>  
 [<span data-ttu-id="f8e2f-115">コマンド ツリーの構造</span><span class="sxs-lookup"><span data-stu-id="f8e2f-115">The Shape of the Command Trees</span></span>](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [<span data-ttu-id="f8e2f-116">コマンド ツリーのベスト プラクティスから SQL を生成します。</span><span class="sxs-lookup"><span data-stu-id="f8e2f-116">Generating SQL from Command Trees - Best Practices</span></span>](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [<span data-ttu-id="f8e2f-117">サンプル プロバイダーでの SQL 生成</span><span class="sxs-lookup"><span data-stu-id="f8e2f-117">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a><span data-ttu-id="f8e2f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8e2f-118">See Also</span></span>  
 [<span data-ttu-id="f8e2f-119">Entity Framework データ プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="f8e2f-119">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
