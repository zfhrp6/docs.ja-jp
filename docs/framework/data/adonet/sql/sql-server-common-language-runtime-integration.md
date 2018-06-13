---
title: SQL Server の共通言語ランタイム統合
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 7451ed06e8a7c9797c66fd81734eb8b6b3b81f12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355738"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="9e3fa-102">SQL Server の共通言語ランタイム統合</span><span class="sxs-lookup"><span data-stu-id="9e3fa-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="9e3fa-103">SQL Server 2005 で、Microsoft Windows 用の .NET Framework の共通言語ランタイム (CLR) コンポーネントの統合が導入されました。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="9e3fa-104">つまり、Microsoft Visual Basic .NET や Microsoft Visual C# を含む任意の .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="9e3fa-105">マネージ コードが Microsoft SQL Server 環境とデータをやり取りできるように、<xref:Microsoft.SqlServer.Server> 名前空間には新しいアプリケーション プログラミング インターフェイス (API) のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="9e3fa-106">このセクションでは、SQL Server の共通言語ランタイム (CLR) 統合および SQL Server のインプロセス固有の ADO.NET の拡張に固有の機能や動作ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="9e3fa-107">このセクションは、SQL Server の CLR 統合を利用したプログラミングを始めるのに十分な情報を提供することを目的としており、包括的な情報の提供は目的としていません。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="9e3fa-108">詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9e3fa-109">**SQL Server オンライン ブック**</span><span class="sxs-lookup"><span data-stu-id="9e3fa-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="9e3fa-110">共通言語ランタイム (CLR) 統合のプログラミングの概念</span><span class="sxs-lookup"><span data-stu-id="9e3fa-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](http://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="9e3fa-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9e3fa-111">In This Section</span></span>  
 [<span data-ttu-id="9e3fa-112">SQL Server の CLR 統合の概要</span><span class="sxs-lookup"><span data-stu-id="9e3fa-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="9e3fa-113">SQL Server の CLR 統合の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="9e3fa-114">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="9e3fa-115">CLR ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="9e3fa-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="9e3fa-116">テーブル値関数、スカラー関数、ユーザー定義集計関数など、さまざまな種類の CLR 関数の実装方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="9e3fa-117">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="9e3fa-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="9e3fa-118">CLR のユーザー定義型を実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="9e3fa-119">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="9e3fa-120">CLR ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="9e3fa-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="9e3fa-121">CLR のストアド プロシージャを実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="9e3fa-122">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="9e3fa-123">CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="9e3fa-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="9e3fa-124">CLR のトリガーを実装して使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="9e3fa-125">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="9e3fa-126">コンテキスト接続</span><span class="sxs-lookup"><span data-stu-id="9e3fa-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="9e3fa-127">コンテキスト接続について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="9e3fa-128">SQL Server のインプロセス固有の ADO.NET の動作</span><span class="sxs-lookup"><span data-stu-id="9e3fa-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="9e3fa-129">SQL Server のインプロセス固有の ADO.NET の拡張およびコンテキスト接続について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="9e3fa-130">追加情報へのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="9e3fa-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e3fa-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e3fa-131">See Also</span></span>  
 [<span data-ttu-id="9e3fa-132">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9e3fa-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="9e3fa-133">マネージ コードでの SQL Server 2005 のオブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="9e3fa-133">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="9e3fa-134">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="9e3fa-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
