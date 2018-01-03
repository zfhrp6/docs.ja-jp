---
title: "トランザクション アプリケーションの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fab355da61ea7445e429cfc4e336a14b588e30c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-transactional-application"></a><span data-ttu-id="01d8f-102">トランザクション アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="01d8f-102">Writing a Transactional Application</span></span>
<span data-ttu-id="01d8f-103">トランザクション アプリケーションのプログラマは、<xref:System.Transactions> 名前空間に用意されている 2 つのプログラミング モデルを活用して、トランザクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="01d8f-103">As a transactional application programmer, you can take advantage of the two programming models provided by the <xref:System.Transactions> namespace to create a transaction.</span></span> <span data-ttu-id="01d8f-104">使用して、明示的なプログラミング モデルを使用することができます、<xref:System.Transactions.Transaction>クラス、または暗黙的なプログラミング モデルがトランザクションは自動的に管理のインフラストラクチャでを使用して、<xref:System.Transactions.TransactionScope>クラスです。</span><span class="sxs-lookup"><span data-stu-id="01d8f-104">You can utilize the explicit programming model by using the <xref:System.Transactions.Transaction> class, or the implicit programming model in which transactions are automatically managed by the infrastructure, by using the <xref:System.Transactions.TransactionScope> class.</span></span> <span data-ttu-id="01d8f-105">開発のため、暗黙のトランザクション モデルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="01d8f-105">We recommend that you use the implicit transaction model for development.</span></span> <span data-ttu-id="01d8f-106">トランザクション スコープを使用する方法の詳細についてを見つけることができます、[トランザクション スコープを使用して、暗黙的なトランザクションを実装する](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="01d8f-106">You can find more information on how to use a transaction scope in the [Implementing an Implicit Transaction using Transaction Scope](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) topic.</span></span>  
  
 <span data-ttu-id="01d8f-107">両モデルとも、プログラムが整合性の取れた状態に達した時点で、トランザクションのコミットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="01d8f-107">Both models support committing a transaction when the program reaches a consistent state.</span></span> <span data-ttu-id="01d8f-108">コミットが成功すると、トランザクションは永続的にコミットされます。</span><span class="sxs-lookup"><span data-stu-id="01d8f-108">If the commit succeeds, the transaction is durably committed.</span></span> <span data-ttu-id="01d8f-109">コミットが失敗すると、トランザクションは中止されます。</span><span class="sxs-lookup"><span data-stu-id="01d8f-109">If the commit fails, the transaction aborts.</span></span> <span data-ttu-id="01d8f-110">アプリケーション プログラムがトランザクションを完了できない場合は、トランザクションを中止してその処理内容を取り消すことを試みます。</span><span class="sxs-lookup"><span data-stu-id="01d8f-110">If the application program cannot successfully complete the transaction, it attempts to abort and undo the transaction's effects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01d8f-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="01d8f-111">In This Section</span></span>  
  
### <a name="creating-a-transaction"></a><span data-ttu-id="01d8f-112">トランザクションの作成</span><span class="sxs-lookup"><span data-stu-id="01d8f-112">Creating a Transaction</span></span>  
 <span data-ttu-id="01d8f-113"><xref:System.Transactions> 名前空間には、トランザクションを作成する 2 つのモデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="01d8f-113">The <xref:System.Transactions> namespace provides two models for creating a transaction.</span></span> <span data-ttu-id="01d8f-114">これらのモデルは、以下のトピックで取り上げられています。</span><span class="sxs-lookup"><span data-stu-id="01d8f-114">These models are covered in the following topics.</span></span>  
  
 [<span data-ttu-id="01d8f-115">トランザクション スコープを使用した暗黙的なトランザクションの実装</span><span class="sxs-lookup"><span data-stu-id="01d8f-115">Implementing an Implicit Transaction using Transaction Scope</span></span>](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <span data-ttu-id="01d8f-116"><xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なトランザクションの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="01d8f-116">Describes how the <xref:System.Transactions> namespace supports creating implicit transactions using the <xref:System.Transactions.TransactionScope> class.</span></span>  
  
 [<span data-ttu-id="01d8f-117">CommittableTransaction を使用した明示的なトランザクションの実装</span><span class="sxs-lookup"><span data-stu-id="01d8f-117">Implementing an Explicit Transaction using CommittableTransaction</span></span>](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <span data-ttu-id="01d8f-118"><xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.CommittableTransaction> クラスを使用した明示的なトランザクションの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="01d8f-118">Describes how the <xref:System.Transactions> namespace supports creating explicit transactions using the <xref:System.Transactions.CommittableTransaction> class.</span></span>  
  
### <a name="escalating-transaction-management"></a><span data-ttu-id="01d8f-119">トランザクション管理のエスカレート</span><span class="sxs-lookup"><span data-stu-id="01d8f-119">Escalating Transaction Management</span></span>  
 <span data-ttu-id="01d8f-120">トランザクションが別のアプリケーション ドメインにあるリソースにアクセスする必要がある場合、または別の永続的なリソース マネージャーに参加する場合は、トランザクションが MSDTC によって管理されるよう自動的にエスカレートされます。</span><span class="sxs-lookup"><span data-stu-id="01d8f-120">When a transaction needs to access a resource in another application domain, or if you want to enlist in another durable resource manager, the transaction is automatically escalated to be managed by the MSDTC.</span></span> <span data-ttu-id="01d8f-121">については、トランザクションのエスカレーション、[トランザクション管理のエスカレーション](../../../../docs/framework/data/transactions/transaction-management-escalation.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="01d8f-121">Transaction escalation is covered in the [Transaction Management Escalation](../../../../docs/framework/data/transactions/transaction-management-escalation.md) topic.</span></span>  
  
### <a name="concurrency"></a><span data-ttu-id="01d8f-122">同時実行</span><span class="sxs-lookup"><span data-stu-id="01d8f-122">Concurrency</span></span>  
 <span data-ttu-id="01d8f-123">トピック[DependentTransaction で同時実行を管理する](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md)を使用して非同期タスクの間で同時実行制御を実現する方法を示しています、<xref:System.Transactions.DependentTransaction>クラスです。</span><span class="sxs-lookup"><span data-stu-id="01d8f-123">The topic [Managing Concurrency with DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) demonstrates how concurrency can be achieved between asynchronous tasks by using the <xref:System.Transactions.DependentTransaction> class.</span></span>  
  
### <a name="com-interop"></a><span data-ttu-id="01d8f-124">COM+ 相互運用</span><span class="sxs-lookup"><span data-stu-id="01d8f-124">COM+ Interop</span></span>  
 <span data-ttu-id="01d8f-125">トピック[エンタープライズ サービス、および COM + トランザクションとの相互運用](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md)COM + トランザクションとの対話、分散トランザクションを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="01d8f-125">The topic [Interoperability with Enterprise Services and COM+ Transactions](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) illustrates how you can make your distributed transactions interact with COM+ transactions.</span></span>  
  
### <a name="diagnostics"></a><span data-ttu-id="01d8f-126">診断</span><span class="sxs-lookup"><span data-stu-id="01d8f-126">Diagnostics</span></span>  
 <span data-ttu-id="01d8f-127">[診断トレース](../../../../docs/framework/data/transactions/diagnostic-traces.md)によって生成されるトレース コードを使用する方法について説明します、<xref:System.Transactions>アプリケーションでエラーを解決するためのインフラストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="01d8f-127">[Diagnostic Traces](../../../../docs/framework/data/transactions/diagnostic-traces.md) describes how you can use the trace codes that are generated by the <xref:System.Transactions> infrastructure to troubleshoot errors in your applications.</span></span>  
  
### <a name="working-within-aspnet"></a><span data-ttu-id="01d8f-128">ASP.NET 内での使用</span><span class="sxs-lookup"><span data-stu-id="01d8f-128">Working within ASP.NET</span></span>  
 <span data-ttu-id="01d8f-129">[ASP.NET での System.Transactions の使用](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md)トピックでは、正常を使用する方法について説明<xref:System.Transactions>ASP.NET アプリケーション内です。</span><span class="sxs-lookup"><span data-stu-id="01d8f-129">The [Using System.Transactions in ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>
