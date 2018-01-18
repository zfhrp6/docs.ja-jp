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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 543ea3d1a0f767a10b36e040155e7e9304aca5a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
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
  
## <a name="see-also"></a>参照  
 [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [方法 : データ送信をトランザクションで囲む](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
