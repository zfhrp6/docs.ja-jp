---
title: "例外、トランザクション、および補正"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7fab7247540ba4e098a793adebab54ca4219e503
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="65079-102">例外、トランザクション、および補正</span><span class="sxs-lookup"><span data-stu-id="65079-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="65079-103"> には、ワークフロー内のランタイム エラー条件を処理するさまざまな機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="65079-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="65079-104">ワークフローでは、例外ハンドラー、トランザクション、キャンセル、および補正の組み合わせを使用して、エラー条件の処理と適切な回復を行えます。</span><span class="sxs-lookup"><span data-stu-id="65079-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65079-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="65079-105">In This Section</span></span>  
 [<span data-ttu-id="65079-106">例外</span><span class="sxs-lookup"><span data-stu-id="65079-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="65079-107"><xref:System.Activities.Statements.TryCatch> アクティビティを使用して、ワークフローで例外を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65079-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="65079-108">トランザクション</span><span class="sxs-lookup"><span data-stu-id="65079-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="65079-109"><xref:System.Activities.Statements.TransactionScope> アクティビティを利用してワークフローでトランザクションを使用する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="65079-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="65079-110">補正</span><span class="sxs-lookup"><span data-stu-id="65079-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="65079-111">ワークフローの補正について説明します。また、<xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate>、および <xref:System.Activities.Statements.Confirm> などの補正アクティビティを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65079-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="65079-112">キャンセル</span><span class="sxs-lookup"><span data-stu-id="65079-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="65079-113">組み込みのアクティビティとカスタム アクティビティを使用してワークフローでキャンセル処理を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65079-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="65079-114">ワークフローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="65079-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="65079-115">ワークフローをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65079-115">Describes how to debug workflows.</span></span>
