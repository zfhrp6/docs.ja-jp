---
title: "ワークフロー トランザクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# ワークフロー トランザクション
[!INCLUDE[wf1](../../../includes/wf1-md.md)] は、<xref:System.Activities.Statements.TransactionScope> アクティビティを使用してトランザクション済み作業単位のスコープを設定することで、<xref:System.Transactions> トランザクションへの参加をサポートします。<xref:System.Transactions.TransactionScope?displayProperty=fullName> は明示的に完了する必要がありますが、<xref:System.Activities.Statements.TransactionScope?displayProperty=fullName> アクティビティは正常完了時にトランザクション上で暗黙的に完了を呼び出します。<xref:System.Activities.Statements.TransactionScope.Body%2A> アクティビティの <xref:System.Activities.Statements.TransactionScope> に含まれるすべてのアクティビティは、トランザクションに参加します。WF は、<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを使用してワークフローにトランザクションをフローできます。<xref:System.Activities.Statements.TransactionScope> アクティビティと同様に、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> に含まれるすべてのアクティビティはトランザクションに参加します。WF は、<xref:System.Transactions.Transaction.Current%2A?displayProperty=fullName> に依存するアクティビティが、<xref:System.Activities.Statements.TransactionScope> と <xref:System.ServiceModel.Activities.TransactedReceiveScope> の両方で確実に動作するようにします。システム標準アクティビティがすべての要件を満たさない場合、高度なフロー シナリオやトランザクション制御シナリオを可能にするには、<xref:System.Activities.RuntimeTransactionHandle> を使用してカスタム アクティビティを構築します。  
  
 次の例は、[基本 TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) サンプルから取られ、ワーク フローは <xref:System.Activities.Statements.Sequence> アクティビティの構成で作成され、<xref:System.Activities.Statements.TransactionScope> のアクティビティを含む子アクティビティが含まれます。<xref:System.Activities.Statements.TransactionScope> の <xref:System.Activities.Statements.TransactionScope.Body%2A> アクティビティは、<xref:System.Activities.Statements.TransactionScope> アクティビティにより初期化されるトランザクションの下で実行されます。  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] は基本 [トランザクション](../../../docs/framework/windows-workflow-foundation/samples/basic-transactions.md) サンプル、およびシナリオ ベースの [トランザクション](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) サンプルです。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Activities.TransactedReceiveScope> の使用は、「[ワークフロー サービスへのトランザクションのフロー](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md)」を参照してください。  
  
## 参照  
 <xref:System.Activities.Statements.TransactionScope>   
 <xref:System.Transactions.TransactionScope>   
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=fullName>