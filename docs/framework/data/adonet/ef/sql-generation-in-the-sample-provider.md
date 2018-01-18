---
title: "サンプル プロバイダーでの SQL 生成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a7f95f7432fdac00a34e7d878ef979656a7af4e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="f15ec-102">サンプル プロバイダーでの SQL 生成</span><span class="sxs-lookup"><span data-stu-id="f15ec-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="f15ec-103">[Entity Framework サンプル プロバイダー](http://go.microsoft.com/fwlink/?LinkId=180616)をサポートする ADO.NET データ プロバイダーの新しいコンポーネントを示しています、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f15ec-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="f15ec-104">これは、SQL Server 2005 データベースで動作し、System.Data.SqlClient ADO.NET 2.0 データ プロバイダーのラッパーとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="f15ec-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="f15ec-105">サンプル プロバイダーの SQL 生成モジュール (DmlSqlGenerator.cs ファイルを除き、SQL Generation フォルダーにあります) では、入力として DbQueryCommandTree を使用し、単一の SQL SELECT ステートメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="f15ec-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f15ec-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f15ec-106">In This Section</span></span>  
 <span data-ttu-id="f15ec-107">ここでは、次のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f15ec-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="f15ec-108">アーキテクチャとデザイン</span><span class="sxs-lookup"><span data-stu-id="f15ec-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="f15ec-109">チュートリアル: SQL 生成</span><span class="sxs-lookup"><span data-stu-id="f15ec-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="f15ec-110">参照</span><span class="sxs-lookup"><span data-stu-id="f15ec-110">See Also</span></span>  
 [<span data-ttu-id="f15ec-111">SQL 生成</span><span class="sxs-lookup"><span data-stu-id="f15ec-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
