---
title: プログラミング ガイド
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 081b5b9fb0765a69e1f45dd0dc25234b8d217ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361385"
---
# <a name="programming-guide"></a><span data-ttu-id="ed2fa-102">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ed2fa-102">Programming Guide</span></span>
<span data-ttu-id="ed2fa-103">ここでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のオブジェクト モデルを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="ed2fa-104">Visual Studio を使用している場合は、使用することも、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]同じタスクの多くを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-104">If you are using Visual Studio, you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="ed2fa-105">特定の問題に関する Microsoft のドキュメントを検索することもでき、参加することができます、 [LINQ フォーラム](http://go.microsoft.com/fwlink/?LinkId=76488)、専門家の複雑なトピックについての詳細を説明することができます。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="ed2fa-106">最後に、 [LINQ to SQL: リレーショナル データ用 .net 統合言語クエリ](http://go.microsoft.com/fwlink/?LinkId=93205)ホワイト ペーパー詳細[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]テクノロジ、Visual Basic および c# のコード例に完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed2fa-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ed2fa-107">In This Section</span></span>  
 [<span data-ttu-id="ed2fa-108">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="ed2fa-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="ed2fa-109">オブジェクト モデルを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="ed2fa-110">データベースとの通信</span><span class="sxs-lookup"><span data-stu-id="ed2fa-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="ed2fa-111">データベースへのコンジットとして <xref:System.Data.Linq.DataContext> オブジェクトを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="ed2fa-112">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="ed2fa-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="ed2fa-113">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でクエリを実行する方法を説明し、多数の例を示します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="ed2fa-114">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="ed2fa-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="ed2fa-115">データベース内のデータを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="ed2fa-116">デバッグのサポート</span><span class="sxs-lookup"><span data-stu-id="ed2fa-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="ed2fa-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトのデバッグ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="ed2fa-118">背景情報</span><span class="sxs-lookup"><span data-stu-id="ed2fa-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="ed2fa-119">同時実行の競合の解決、新しいデータベースの作成など、上級ユーザー向けの追加項目が記載されています。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ed2fa-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed2fa-120">Related Sections</span></span>  
 [<span data-ttu-id="ed2fa-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ed2fa-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="ed2fa-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] テクノロジの説明および機能の解説が記載されているトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="ed2fa-123">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ed2fa-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="ed2fa-124">ストアド プロシージャの使用手順のトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="ed2fa-125">LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="ed2fa-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="ed2fa-126">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使い始めるときに役立つリソースを示します。</span><span class="sxs-lookup"><span data-stu-id="ed2fa-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
