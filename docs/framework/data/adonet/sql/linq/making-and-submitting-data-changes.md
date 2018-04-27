---
title: データの変更と変更の送信
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 79ed671c667c43f501647900ca6326891cba3c28
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="ccc46-102">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="ccc46-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="ccc46-103">このセクションのトピックでは、データベースを変更し、その変更を送信する方法と、オプティミスティック同時実行の競合を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccc46-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の `Insert`、`Update`、および `Delete` の既定のデータベース操作メソッドはオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ccc46-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="ccc46-105">詳細については、次を参照してください。[のカスタマイズを挿入、更新、および削除を行う](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="ccc46-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="ccc46-106">Visual Studio を使用している開発者が使用できる、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]同じ用途のストアド プロシージャを開発します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-106">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ccc46-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ccc46-107">In This Section</span></span>  
 [<span data-ttu-id="ccc46-108">方法 : 行をデータベースに挿入する</span><span class="sxs-lookup"><span data-stu-id="ccc46-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="ccc46-109">オブジェクト モデルにオブジェクトを追加することにより、データベースに行を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="ccc46-110">方法 : データベースの行を更新する</span><span class="sxs-lookup"><span data-stu-id="ccc46-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="ccc46-111">オブジェクト モデルのオブジェクトを更新することにより、データベースの行を更新する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="ccc46-112">方法 : 行をデータベースから削除する</span><span class="sxs-lookup"><span data-stu-id="ccc46-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="ccc46-113">オブジェクト モデルのオブジェクトを削除することにより、データベースの行を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="ccc46-114">方法 : データベースに変更内容を送信する</span><span class="sxs-lookup"><span data-stu-id="ccc46-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="ccc46-115">オブジェクト モデルに対する変更をデータベースに送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="ccc46-116">方法 : データ送信をトランザクションで囲む</span><span class="sxs-lookup"><span data-stu-id="ccc46-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="ccc46-117">トランザクションに操作を含める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="ccc46-118">方法 : データベースを動的に作成する</span><span class="sxs-lookup"><span data-stu-id="ccc46-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="ccc46-119">動的にデータベースを生成する方法と、この方法を使用する一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="ccc46-120">方法 : 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="ccc46-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="ccc46-121">オプティミスティック同時実行制御の問題に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccc46-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
