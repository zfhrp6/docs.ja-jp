---
title: "方法 : 同時実行例外をいつスローするかを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8af833574544410977b9f881f9b2db4e6d88aa73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="cec0b-102">方法 : 同時実行例外をいつスローするかを指定する</span><span class="sxs-lookup"><span data-stu-id="cec0b-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="cec0b-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、オプティミスティック同時実行の競合によってオブジェクトが更新されないときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="cec0b-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="cec0b-104">詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="cec0b-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="cec0b-105">変更内容をデータベースに送信する前に、同時実行例外をどの時点でスローするかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cec0b-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="cec0b-106">例外を最初のエラーの時点でスローします (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>)。</span><span class="sxs-lookup"><span data-stu-id="cec0b-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="cec0b-107">更新の再試行を決められた回数繰り返し、すべてのエラー情報を集積してから、この情報を例外で報告します (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>)。</span><span class="sxs-lookup"><span data-stu-id="cec0b-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="cec0b-108"><xref:System.Data.Linq.ChangeConflictException> 例外がスローされると、例外を通じて <xref:System.Data.Linq.ChangeConflictCollection> コレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cec0b-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="cec0b-109">このコレクションを使用して、個々の競合 (それぞれが 1 回の更新失敗に対応する) の詳細情報を取得したり、<xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> コレクションにアクセスしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="cec0b-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="cec0b-110">各メンバー競合は、同時実行チェックでエラーになった更新の 1 つのメンバーに対応します。</span><span class="sxs-lookup"><span data-stu-id="cec0b-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec0b-111">例</span><span class="sxs-lookup"><span data-stu-id="cec0b-111">Example</span></span>  
 <span data-ttu-id="cec0b-112">両方の値の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="cec0b-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cec0b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="cec0b-113">See Also</span></span>  
 [<span data-ttu-id="cec0b-114">方法: 変更の競合の管理</span><span class="sxs-lookup"><span data-stu-id="cec0b-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="cec0b-115">作成方法とデータの変更の送信</span><span class="sxs-lookup"><span data-stu-id="cec0b-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
