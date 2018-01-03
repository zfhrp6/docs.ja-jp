---
title: "方法 : データベースに変更内容を送信する"
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
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 69ada8afe783ce8cc425a5804eab6a00475871c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="f70a3-102">方法 : データベースに変更内容を送信する</span><span class="sxs-lookup"><span data-stu-id="f70a3-102">How to: Submit Changes to the Database</span></span>
<span data-ttu-id="f70a3-103">オブジェクトに加えた変更は、その数にかかわらず、メモリ内のレプリカに対してのみ反映されています。</span><span class="sxs-lookup"><span data-stu-id="f70a3-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="f70a3-104">データベースの実際のデータは変更されていません。</span><span class="sxs-lookup"><span data-stu-id="f70a3-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="f70a3-105"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext> を明示的に呼び出すまでは、変更内容はサーバーに送信されません。</span><span class="sxs-lookup"><span data-stu-id="f70a3-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="f70a3-106">この呼び出しを行うと、<xref:System.Data.Linq.DataContext> は、変更内容を、同等の SQL コマンドに変換します。</span><span class="sxs-lookup"><span data-stu-id="f70a3-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="f70a3-107">独自のカスタム ロジックを使用して、これらのアクションをオーバーライドすることができますが、発行の順序は、サービスによって統制されます、<xref:System.Data.Linq.DataContext>と呼ばれる、*変更プロセッサ*です。</span><span class="sxs-lookup"><span data-stu-id="f70a3-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="f70a3-108">イベントの順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f70a3-108">The sequence of events is as follows:</span></span>  
  
1.  <span data-ttu-id="f70a3-109"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、一連の既知のオブジェクトをチェックして、新しいインスタンスがアタッチされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="f70a3-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="f70a3-110">その場合、それらの新しいインスタンスが、一連の追跡対象オブジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f70a3-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2.  <span data-ttu-id="f70a3-111">保留中の変更があるすべてのオブジェクトが、互いの依存関係に基づいて、オブジェクトのシーケンスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="f70a3-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="f70a3-112">他のオブジェクトに依存して変更内容が決まるオブジェクトは、その依存対象の後でシーケンスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="f70a3-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3.  <span data-ttu-id="f70a3-113">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、実際の変更を送信する直前に、一連の各コマンドをカプセル化するトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="f70a3-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4.  <span data-ttu-id="f70a3-114">オブジェクトに対する変更内容が 1 つずつ SQL コマンドに変換され、サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="f70a3-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="f70a3-115">この時点で、データベースによってエラーが検出された場合、送信処理は中断され、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="f70a3-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="f70a3-116">データベースに加えた変更はすべてロールバックされ、送信を行わなかった場合と同じ状態になります。</span><span class="sxs-lookup"><span data-stu-id="f70a3-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="f70a3-117">この時点でも、<xref:System.Data.Linq.DataContext> には、すべての変更内容の記録がそのまま残っています。</span><span class="sxs-lookup"><span data-stu-id="f70a3-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="f70a3-118">したがって、次のコード例のように、問題を修正したうえで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を再度呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f70a3-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f70a3-119">例</span><span class="sxs-lookup"><span data-stu-id="f70a3-119">Example</span></span>  
 <span data-ttu-id="f70a3-120">一連の送信処理のトランザクションが正常に完了した場合、<xref:System.Data.Linq.DataContext> は、変更追跡情報を無視して、オブジェクトに対する変更を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="f70a3-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f70a3-121">参照</span><span class="sxs-lookup"><span data-stu-id="f70a3-121">See Also</span></span>  
 [<span data-ttu-id="f70a3-122">方法 : 送信の競合を検出および解決する</span><span class="sxs-lookup"><span data-stu-id="f70a3-122">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [<span data-ttu-id="f70a3-123">方法 : 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="f70a3-123">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="f70a3-124">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="f70a3-124">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="f70a3-125">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="f70a3-125">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
