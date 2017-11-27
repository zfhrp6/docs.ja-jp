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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 071c0c8bc7e0bb8dca01e9fc51c66fb930ed102b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="f2293-102">方法 : データ送信をトランザクションで囲む</span><span class="sxs-lookup"><span data-stu-id="f2293-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="f2293-103">データベースへの送信を <xref:System.Transactions.TransactionScope> で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="f2293-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="f2293-104">詳細については、次を参照してください。[トランザクション サポート](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2293-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2293-105">例</span><span class="sxs-lookup"><span data-stu-id="f2293-105">Example</span></span>  
 <span data-ttu-id="f2293-106">次のコードでは、データベース送信を <xref:System.Transactions.TransactionScope> で囲みます。</span><span class="sxs-lookup"><span data-stu-id="f2293-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f2293-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2293-107">See Also</span></span>  
 [<span data-ttu-id="f2293-108">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="f2293-108">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="f2293-109">作成方法とデータの変更の送信</span><span class="sxs-lookup"><span data-stu-id="f2293-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="f2293-110">トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="f2293-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
