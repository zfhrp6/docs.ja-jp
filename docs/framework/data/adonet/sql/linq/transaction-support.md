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
# <a name="transaction-support"></a>トランザクションのサポート
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]次の 3 つの種類のトランザクション モデルをサポートしています。 チェックが行われる順に、これらのモデルを以下に示します。  
  
## <a name="explicit-local-transaction"></a>明示的なローカル トランザクション  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が呼び出されたときに <xref:System.Data.Linq.DataContext.Transaction%2A> プロパティが (`IDbTransaction`) トランザクションに設定されている場合、同じトランザクションのコンテキストで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼び出しが実行されます。  
  
 トランザクションの実行が終了したら、ユーザーがトランザクションをコミットまたはロールバックする必要があります。 トランザクションに対応する接続は、<xref:System.Data.Linq.DataContext> を構築するのに使用した接続に一致する必要があります。 異なる接続が使用されると、例外がスローされます。  
  
## <a name="explicit-distributable-transaction"></a>明示的な分散トランザクション  
 呼び出すことができます[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Api (などですが、これらに限定されません<xref:System.Data.Linq.DataContext.SubmitChanges%2A>) のアクティブなスコープで<xref:System.Transactions.Transaction>です。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]検出された、呼び出しがトランザクションのスコープ内に新しいトランザクションを作成しません。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ここでは、接続を閉じる必要もなくなります。 このようなトランザクションのコンテキストで、クエリと <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の実行が可能です。  
  
## <a name="implicit-transaction"></a>暗黙のトランザクション  
 呼び出すと<xref:System.Data.Linq.DataContext.SubmitChanges%2A>、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]呼び出しがのスコープであるかどうかをチェック、<xref:System.Transactions.Transaction>場合、または、`Transaction`プロパティ (`IDbTransaction`) がユーザーによって開始されたローカル トランザクションに設定します。 どちらのトランザクションが検出されると[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ローカル トランザクションを開始 (`IDbTransaction`) され、生成された SQL コマンドを実行するために使用します。 すべての SQL コマンドは正常に完了したら、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ローカル トランザクションをコミットして戻ります。  
  
## <a name="see-also"></a>関連項目  
 [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [方法: トランザクションを使用してデータの送信を囲む](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
