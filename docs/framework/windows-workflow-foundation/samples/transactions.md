---
title: Transactions2
ms.date: 03/30/2017
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
ms.openlocfilehash: 361022851d971c0b9350899e1fee6a27c557d666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514596"
---
# <a name="transactions"></a><span data-ttu-id="63c9b-102">トランザクション</span><span class="sxs-lookup"><span data-stu-id="63c9b-102">Transactions</span></span>
<span data-ttu-id="63c9b-103">このセクションには、ワークフロー トランザクションには、Windows Workflow Foundation (WF) を示すサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="63c9b-103">This section contains samples that demonstrate workflow transactions in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63c9b-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="63c9b-104">In This Section</span></span>  
 [<span data-ttu-id="63c9b-105">基本 TransactionScope</span><span class="sxs-lookup"><span data-stu-id="63c9b-105">Basic TransactionScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 <span data-ttu-id="63c9b-106"><xref:System.Activities.Statements.TransactionScope> インスタンスを入れ子にする方法を示す 4 つのシナリオで構成されます。</span><span class="sxs-lookup"><span data-stu-id="63c9b-106">Consists of four scenarios that show how to nest <xref:System.Activities.Statements.TransactionScope> instances.</span></span>  
  
 [<span data-ttu-id="63c9b-107">TransactedReceiveScope の使用</span><span class="sxs-lookup"><span data-stu-id="63c9b-107">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 <span data-ttu-id="63c9b-108">クライアントからサーバーにトランザクションをフローする方法を示します。このために、<xref:System.Activities.Statements.TransactionScope> を使用してクライアント上に新しいトランザクションを作成し、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用してフローされたトランザクションを含むメッセージを受信し、サーバー上でトランザクションの有効期間のスコープを設定します。</span><span class="sxs-lookup"><span data-stu-id="63c9b-108">Demonstrates how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span>  
  
 [<span data-ttu-id="63c9b-109">サービス内での TransactionScope の入れ子化</span><span class="sxs-lookup"><span data-stu-id="63c9b-109">Nesting of TransactionScope within a service</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 <span data-ttu-id="63c9b-110">サービス内で <xref:System.Activities.Statements.TransactionScope> アクティビティ インスタンスを処理する方法を示す 2 つのシナリオで構成されます。</span><span class="sxs-lookup"><span data-stu-id="63c9b-110">Consists of two scenarios that show how to handle <xref:System.Activities.Statements.TransactionScope> activity instances within a service.</span></span>
