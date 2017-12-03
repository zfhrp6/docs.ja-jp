---
title: "単一フェースおよび複数フェーズでのトランザクションのコミット"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96304cdde766f264fcfbd0f4aa3cf168adf8422d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="84fcf-102">単一フェースおよび複数フェーズでのトランザクションのコミット</span><span class="sxs-lookup"><span data-stu-id="84fcf-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="84fcf-103">トランザクションで使用される各リソースは、リソース マネージャー (RM) によって管理され、その動作はトランザクション マネージャー (TM) によって調整されます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="84fcf-104">[リソースをトランザクションの参加者として参加](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)リソース (または複数のリソース) をトランザクションに参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-104">The [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="84fcf-105">ここでは、参加リソース間でトランザクションのコミットメントを調整する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="84fcf-106">トランザクションの最後に、アプリケーションはトランザクションのコミットまたはロールバックを要求します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="84fcf-107">トランザクション マネージャーは、一部のリソース マネージャーがトランザクションのコミットを選択し、他のリソース マネージャーがトランザクションのロールバックを選択するというようなリスクを回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="84fcf-108">トランザクションに複数のリソースが含まれる場合は、2 フェーズ コミット (2PC) を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="84fcf-109">2 フェーズ コミット プロトコル (準備フェーズとコミット フェーズ) により、すべてのリソースに対する変更がトランザクションの終了時に完全にコミットされるか、または完全にロールバックされることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="84fcf-110">その後、すべての参加要素に最終結果が通知されます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="84fcf-111">2 フェーズ コミット プロトコルの詳細については、ブックを参照してください"*トランザクション処理: 概念および手法 (データ管理システムで更に系列を Morgan) ISBN:1558601902*"Jim Gray でします。</span><span class="sxs-lookup"><span data-stu-id="84fcf-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="84fcf-112">単一フェーズ コミット プロトコルに参加することで、トランザクションのパフォーマンスを最適化することもできます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="84fcf-113">詳細については、次を参照してください。[単一フェーズのコミットし、昇格可能な単一フェーズの通知を使用して、最適化](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)です。</span><span class="sxs-lookup"><span data-stu-id="84fcf-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="84fcf-114">トランザクション結果の通知を受信するだけで、コミットまたはロールバックの選択には参加しない場合は、<xref:System.Transactions.Transaction.TransactionCompleted> イベントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="84fcf-115">2 フェーズ コミット (2PC)</span><span class="sxs-lookup"><span data-stu-id="84fcf-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="84fcf-116">最初のトランザクション フェーズで、トランザクション マネージャーは、トランザクションをコミットするかロールバックするかを決定するため、各リソースに照会します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="84fcf-117">2 番目のトランザクション フェーズでは、トランザクション マネージャーは照会結果を各リソースに通知し、必要なクリーンアップを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="84fcf-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="84fcf-118">この種のトランザクションに参加するために、リソース マネージャーは <xref:System.Transactions.IEnlistmentNotification> インターフェイスを実装する必要があります。このインターフェイスは、2PC 中に通知として TM が呼び出すメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="84fcf-119">このような実装の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="84fcf-120">準備フェーズ (フェーズ 1)</span><span class="sxs-lookup"><span data-stu-id="84fcf-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="84fcf-121">アプリケーションから <xref:System.Transactions.CommittableTransaction.Commit%2A> 要求を受信すると、トランザクション マネージャーは、各リソースのトランザクションに対する選択を取得するため、各参加リソースに対して <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> メソッドを呼び出し、参加しているすべての参加要素の準備フェーズを開始します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="84fcf-122"><xref:System.Transactions.IEnlistmentNotification> インターフェイスを実装するリソース マネージャーは、次の簡単な例に示すように、最初に <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```  
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 <span data-ttu-id="84fcf-123">永続的リソース マネージャーがこの呼び出しを受信すると、トランザクションの回復情報 (<xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> プロパティの取得により利用可) と、コミット時にトランザクションを完了させるのに必要な情報をすべてログに記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="84fcf-124">RM はワーカー スレッドでこれを実行できるため、<xref:System.Transactions.IEnlistmentNotification.Prepare%2A> メソッド内で実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="84fcf-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="84fcf-125">この準備操作が完了したら、RM は <xref:System.Transactions.PreparingEnlistment.Prepared%2A> メソッドまたは <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> メソッドを呼び出して、コミットまたはロールバックを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="84fcf-126"><xref:System.Transactions.PreparingEnlistment> クラスは、<xref:System.Transactions.Enlistment.Done%2A> クラスから <xref:System.Transactions.Enlistment> メソッドを継承することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="84fcf-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="84fcf-127">準備フェーズ中に <xref:System.Transactions.PreparingEnlistment> コールバックでこのメソッドを呼び出すと、読み取り専用の参加 (トランザクション保護されたデータを読み取れるが更新できないリソース マネージャー) であることが TM に通知され、RM はフェーズ 2 でのトランザクションの結果として、トランザクション マネージャーからの通知を受信しなくなります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="84fcf-128">すべてのリソース マネージャーが <xref:System.Transactions.PreparingEnlistment.Prepared%2A> を選択すると、トランザクションのコミットメントが成功したことがアプリケーションに通知されます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="84fcf-129">コミット フェーズ (フェーズ 2)</span><span class="sxs-lookup"><span data-stu-id="84fcf-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="84fcf-130">トランザクションの 2 番目のフェーズで、トランザクション マネージャーがすべてのリソース マネージャーから準備の成功を受信すると (すべてのリソース マネージャーがフェーズ 1 の終わりで <xref:System.Transactions.PreparingEnlistment.Prepared%2A> を呼び出した場合)、各リソース マネージャーに対して <xref:System.Transactions.IEnlistmentNotification.Commit%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="84fcf-131">これにより、リソース マネージャーは、変更を永続的なものとして、コミットを完了できます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="84fcf-132">いずれかのリソース マネージャーがフェーズ 1 での準備の失敗を報告すると、トランザクション マネージャーは、各リソース マネージャーに対して <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> メソッドを呼び出し、アプリケーションにコミットの失敗を通知します。</span><span class="sxs-lookup"><span data-stu-id="84fcf-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="84fcf-133">したがって、リソース マネージャーは次のメソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-133">Thus, your resource manager should implement the following methods.</span></span>  
  
```  
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 <span data-ttu-id="84fcf-134">RM は、通知の種類に基づいてトランザクションを終了するために必要な作業を実行し、<xref:System.Transactions.Enlistment.Done%2A> パラメーターで <xref:System.Transactions.Enlistment> メソッドを呼び出すことにより、TM に作業の完了を通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="84fcf-135">これはワーカー スレッドで実行できます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="84fcf-136">フェーズ 2 の通知は、フェーズ 1 で <xref:System.Transactions.PreparingEnlistment.Prepared%2A> メソッドを呼び出した同じスレッドで、インラインで発生する可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="84fcf-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="84fcf-137">このため、フェーズ 2 の通知を受け取る前に既に完了したと考えられる作業 (ロックの解除など) は、<xref:System.Transactions.PreparingEnlistment.Prepared%2A> 呼び出しの後には実行できません。</span><span class="sxs-lookup"><span data-stu-id="84fcf-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="84fcf-138">InDoubt の実装</span><span class="sxs-lookup"><span data-stu-id="84fcf-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="84fcf-139">最後に、揮発性リソース マネージャーに <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="84fcf-140">このメソッドは、トランザクション マネージャーが 1 つ以上の参加要素と接続できなくなり、そのステータスが不明になった場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="84fcf-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="84fcf-141">この場合は、トランザクションのいずれかの参加要素が矛盾した状態のままになっていないかどうかを後で調べることができるよう、この事実を記録しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="84fcf-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```  
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="84fcf-142">単一フェーズ コミットの最適化</span><span class="sxs-lookup"><span data-stu-id="84fcf-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="84fcf-143">単一フェーズ コミット プロトコルは、すべての更新が明示的な調整なしに行われるため、実行時に、より効率的です。</span><span class="sxs-lookup"><span data-stu-id="84fcf-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="84fcf-144">このプロトコルの詳細については、次を参照してください。[単一フェーズのコミットし、昇格可能な単一フェーズの通知を使用して、最適化](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)です。</span><span class="sxs-lookup"><span data-stu-id="84fcf-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fcf-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="84fcf-145">See Also</span></span>  
 [<span data-ttu-id="84fcf-146">単一フェーズのコミットし、昇格可能な単一フェーズの通知を使用して、最適化</span><span class="sxs-lookup"><span data-stu-id="84fcf-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [<span data-ttu-id="84fcf-147">トランザクションの参加者としてリソースを参加させる</span><span class="sxs-lookup"><span data-stu-id="84fcf-147">Enlisting Resources as Participants in a Transaction</span></span>](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
