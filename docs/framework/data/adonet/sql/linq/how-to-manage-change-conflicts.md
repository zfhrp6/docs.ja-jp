---
title: "方法 : 変更の競合を管理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: caacb4c3b877ce6bf7ba11001f602a76ad7f9734
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="1eda7-102">方法 : 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="1eda7-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1eda7-103">発見、評価、および同時実行の競合を解決するための Api のコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-103"> provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1eda7-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1eda7-104">In This Section</span></span>  
 [<span data-ttu-id="1eda7-105">方法 : 送信の競合を検出および解決する</span><span class="sxs-lookup"><span data-stu-id="1eda7-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="1eda7-106">同時実行の競合を検出および解決する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="1eda7-107">方法 : 同時実行例外をいつスローするかを指定する</span><span class="sxs-lookup"><span data-stu-id="1eda7-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="1eda7-108">同時実行の競合をいつ通知するかを指定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="1eda7-109">方法 : 同時実行の競合を検査するメンバーを指定する</span><span class="sxs-lookup"><span data-stu-id="1eda7-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="1eda7-110">メンバーに属性を設定して、そのメンバーで同時実行の競合をチェックするかどうかを指定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="1eda7-111">方法 : エンティティの競合情報を取得する</span><span class="sxs-lookup"><span data-stu-id="1eda7-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="1eda7-112">エンティティの競合に関する情報を収集する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="1eda7-113">方法 : メンバーの競合情報を取得する</span><span class="sxs-lookup"><span data-stu-id="1eda7-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="1eda7-114">メンバーの競合に関する情報を収集する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="1eda7-115">方法 : データベース値を維持することで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="1eda7-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="1eda7-116">現在の値をデータベースの値で上書きする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="1eda7-117">方法 : データベース値を上書きすることで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="1eda7-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="1eda7-118">データベースの値を上書きして現在の値を維持する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="1eda7-119">方法 : データベース値とマージすることで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="1eda7-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="1eda7-120">データベースの値と現在の値をマージして競合を解決する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1eda7-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="1eda7-121">Related Sections</span></span>  
 [<span data-ttu-id="1eda7-122">オプティミスティック同時実行の概要</span><span class="sxs-lookup"><span data-stu-id="1eda7-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="1eda7-123">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のオプティミスティック同時実行制御で使用される用語を説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda7-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
