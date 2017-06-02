---
title: "トランザクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# トランザクション
このセクションには、[!INCLUDE[wf](../../../../includes/wf-md.md)] のワークフロー トランザクションを使用するシナリオを示すサンプルが含まれています。  
  
## このセクションの内容  
 [命令型 TransactionScope でのワークフローの実行](../../../../docs/framework/windows-workflow-foundation/samples/execute-a-workflow-in-an-imperative-transactionscope.md)  
 命令型 C\# コードから <xref:System.Transactions.Transaction> の下にある <xref:System.Activities.WorkflowInvoker> を使用してワークフローを実行する方法を示します。  
  
 [トランザクション コンボイ スコープ](../../../../docs/framework/windows-workflow-foundation/samples/transaction-convoy-scope.md)  
 パラレルなコンボイ メッセージング アクティビティ パターンを <xref:System.ServiceModel.Activities.TransactedReceiveScope> と組み合わせて作成し、多数の操作をすべて同じトランザクションで任意の順序で行うことができるプロトコルをモデル化する方法を示します。  
  
 [トランザクションのロールバック](../../../../docs/framework/windows-workflow-foundation/samples/transaction-rollback.md)  
 アンビエント <xref:System.Activities.RuntimeTransactionHandle> にアクセスしてアンビエント トランザクションを取得し、そのトランザクションを明示的にロールバックするカスタム <xref:System.Activities.NativeActivity> を作成する方法を示します。  
  
 [トランザクション スコープの抑制](../../../../docs/framework/windows-workflow-foundation/samples/suppress-transaction-scope.md)  
 アンビエント ランタイム トランザクションが存在する場合はそのトランザクションを抑制するカスタム `SuppressTransactionScope` アクティビティを作成する方法を示します。  
  
 [トランザクション キュー](../../../../docs/framework/windows-workflow-foundation/samples/transacted-queues.md)  
 キューとトランザクションを [!INCLUDE[wf1](../../../../includes/wf1-md.md)] に統合し、信頼性があり、拡張性の高いサービスを作成する方法を示します。