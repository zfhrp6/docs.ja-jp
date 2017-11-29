---
title: "トランザクションのサポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c1d438a83f090795a158ade1dfdbb7d2b2df863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="transaction-support"></a><span data-ttu-id="04b5a-102">トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="04b5a-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="04b5a-103">次の 3 つの種類のトランザクション モデルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="04b5a-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="04b5a-104">チェックが行われる順に、これらのモデルを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04b5a-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="04b5a-105">明示的なローカル トランザクション</span><span class="sxs-lookup"><span data-stu-id="04b5a-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="04b5a-106"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> が呼び出されたときに <xref:System.Data.Linq.DataContext.Transaction%2A> プロパティが (`IDbTransaction`) トランザクションに設定されている場合、同じトランザクションのコンテキストで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼び出しが実行されます。</span><span class="sxs-lookup"><span data-stu-id="04b5a-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="04b5a-107">トランザクションの実行が終了したら、ユーザーがトランザクションをコミットまたはロールバックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04b5a-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="04b5a-108">トランザクションに対応する接続は、<xref:System.Data.Linq.DataContext> を構築するのに使用した接続に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04b5a-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="04b5a-109">異なる接続が使用されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="04b5a-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="04b5a-110">明示的な分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="04b5a-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="04b5a-111">呼び出すことができます[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Api (などですが、これらに限定されません<xref:System.Data.Linq.DataContext.SubmitChanges%2A>) のアクティブなスコープで<xref:System.Transactions.Transaction>です。</span><span class="sxs-lookup"><span data-stu-id="04b5a-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="04b5a-112">検出された、呼び出しがトランザクションのスコープ内に新しいトランザクションを作成しません。</span><span class="sxs-lookup"><span data-stu-id="04b5a-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="04b5a-113">ここでは、接続を閉じる必要もなくなります。</span><span class="sxs-lookup"><span data-stu-id="04b5a-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="04b5a-114">このようなトランザクションのコンテキストで、クエリと <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の実行が可能です。</span><span class="sxs-lookup"><span data-stu-id="04b5a-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="04b5a-115">暗黙のトランザクション</span><span class="sxs-lookup"><span data-stu-id="04b5a-115">Implicit Transaction</span></span>  
 <span data-ttu-id="04b5a-116">呼び出すと<xref:System.Data.Linq.DataContext.SubmitChanges%2A>、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]呼び出しがのスコープであるかどうかをチェック、<xref:System.Transactions.Transaction>場合、または、`Transaction`プロパティ (`IDbTransaction`) がユーザーによって開始されたローカル トランザクションに設定します。</span><span class="sxs-lookup"><span data-stu-id="04b5a-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="04b5a-117">どちらのトランザクションが検出されると[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ローカル トランザクションを開始 (`IDbTransaction`) され、生成された SQL コマンドを実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="04b5a-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="04b5a-118">すべての SQL コマンドは正常に完了したら、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ローカル トランザクションをコミットして戻ります。</span><span class="sxs-lookup"><span data-stu-id="04b5a-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b5a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="04b5a-119">See Also</span></span>  
 [<span data-ttu-id="04b5a-120">背景情報</span><span class="sxs-lookup"><span data-stu-id="04b5a-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="04b5a-121">方法: トランザクションを使用してデータの送信を囲む</span><span class="sxs-lookup"><span data-stu-id="04b5a-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
