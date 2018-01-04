---
title: "命令型 TransactionScope でのワークフローの実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 530a590931a1cb3994406e5605f8da2853ceddaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a><span data-ttu-id="a3aaa-102">命令型 TransactionScope でのワークフローの実行</span><span class="sxs-lookup"><span data-stu-id="a3aaa-102">Execute a Workflow in an Imperative TransactionScope</span></span>
<span data-ttu-id="a3aaa-103">このサンプルでは、命令型 C# コードから <xref:System.Activities.WorkflowInvoker> で <xref:System.Transactions.Transaction> を使用してワークフローを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-103">This sample shows how to execute a workflow using <xref:System.Activities.WorkflowInvoker> under a <xref:System.Transactions.Transaction> from imperative C# code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a3aaa-104">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="a3aaa-104">Sample Details</span></span>  
 <span data-ttu-id="a3aaa-105">命令型 C# コードで、<xref:System.Transactions.TransactionScope> を使用して、同じトランザクションで実行される一連の作業をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-105">In imperative C# code, the <xref:System.Transactions.TransactionScope> is used to encapsulate a set of work that executes under the same transaction.</span></span> <span data-ttu-id="a3aaa-106"><xref:System.Transactions.TransactionScope> は、アンビエント トランザクションを作成し、<xref:System.Transactions.Transaction.Current%2A> プロパティを初期化することによって機能します。初期化後、このプロパティには、そのスレッドで実行されるどの作業からでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-106">The <xref:System.Transactions.TransactionScope> works by creating an ambient transaction and initializing the <xref:System.Transactions.Transaction.Current%2A> property, which can then be accessed by any work being executed on that thread.</span></span>  
  
 <span data-ttu-id="a3aaa-107">ワークフローではアクティビティ間でスレッド アフィニティが維持されないため、ワークフローで同等の動作を実現するには、ランタイムで、追加の作業として各アクティビティの実行前に <xref:System.Transactions.Transaction.Current%2A> を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-107">To get equivalent behavior in workflow, the runtime has to do the extra work of initializing <xref:System.Transactions.Transaction.Current%2A> before executing each activity because a workflow does not maintain thread affinity between activities.</span></span> <span data-ttu-id="a3aaa-108">このランタイムによるサポートの結果として、<xref:System.Activities.WorkflowInvoker> 内で <xref:System.Transactions.TransactionScope> を使用してワークフローを実行するとき、すべてのアクティビティが、<xref:System.Transactions.TransactionScope> によって作成されたアンビエント トランザクションのコンテキストで実行されるようになります。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-108">With this runtime support, the resulting behavior is that when executing a workflow with <xref:System.Activities.WorkflowInvoker> inside a <xref:System.Transactions.TransactionScope>, all activities are guaranteed to run under the context of the ambient transaction created by the <xref:System.Transactions.TransactionScope>.</span></span>  
  
 <span data-ttu-id="a3aaa-109">ワークフローではワークフロー インスタンスごとに 1 つのアンビエント トランザクションしか使用できず、入れ子になったトランザクションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-109">A workflow can have only a single ambient transaction for each workflow instance; nested transactions are not available.</span></span> <span data-ttu-id="a3aaa-110">ワークフローに <xref:System.Activities.Statements.TransactionScope> アクティビティがある場合でも、新しい内側のトランザクションは作成されません。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-110">Even if the workflow contains a <xref:System.Activities.Statements.TransactionScope> activity, this does not create a new inner transaction.</span></span> <span data-ttu-id="a3aaa-111">代わりに、ワークフロー外で作成されたアンビエント トランザクションが再利用されます。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-111">Instead, this reuses the ambient transaction that was created outside the workflow.</span></span>  
  
 <span data-ttu-id="a3aaa-112">このサンプルでは、新しい <xref:System.Transactions.TransactionScope> を開始し、トランザクション ID を出力して、<xref:System.Activities.WorkflowInvoker> によってワークフローを開始します。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-112">The sample begins a new <xref:System.Transactions.TransactionScope>, prints the transaction ID and begins a workflow using <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="a3aaa-113">ワークフローではトランザクション ID を再度出力し (これにより、同じトランザクションであることが示されます)、<xref:System.Activities.Statements.TransactionScope> を実行して、完了します。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-113">The workflow prints the transaction ID again, showing that it is the same transaction, then runs a <xref:System.Activities.Statements.TransactionScope>, then completes.</span></span> <span data-ttu-id="a3aaa-114"><xref:System.Activities.WorkflowInvoker.Invoke%2A> での <xref:System.Activities.WorkflowInvoker> の呼び出しは同期的であるので、元のスレッドはワークフローが完了するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-114">The <xref:System.Activities.WorkflowInvoker.Invoke%2A> call on <xref:System.Activities.WorkflowInvoker> is synchronous so the original thread blocks until the workflow completes.</span></span> <span data-ttu-id="a3aaa-115">ワークフローが完了すると、トランザクションが完了し、リソースが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-115">Once the workflow is complete, the transaction is completed and resources disposed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a3aaa-116">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="a3aaa-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="a3aaa-117">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ImperativeTransactionSample.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ImperativeTransactionSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a3aaa-118">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a3aaa-119">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-119">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a3aaa-120">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a3aaa-121">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a3aaa-122">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3aaa-123">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a3aaa-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`