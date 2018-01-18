---
title: "方法 : データ送信をトランザクションで囲む"
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
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a5d7f1e0b0419874f694a0b3953f6b037a777016
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="d6d3f-102">方法 : データ送信をトランザクションで囲む</span><span class="sxs-lookup"><span data-stu-id="d6d3f-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="d6d3f-103">データベースへの送信を <xref:System.Transactions.TransactionScope> で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="d6d3f-104">詳細については、次を参照してください。[トランザクション サポート](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6d3f-105">例</span><span class="sxs-lookup"><span data-stu-id="d6d3f-105">Example</span></span>  
 <span data-ttu-id="d6d3f-106">次のコードでは、データベース送信を <xref:System.Transactions.TransactionScope> で囲みます。</span><span class="sxs-lookup"><span data-stu-id="d6d3f-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d6d3f-107">参照</span><span class="sxs-lookup"><span data-stu-id="d6d3f-107">See Also</span></span>  
 [<span data-ttu-id="d6d3f-108">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="d6d3f-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="d6d3f-109">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="d6d3f-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="d6d3f-110">トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="d6d3f-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
