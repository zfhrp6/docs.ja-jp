---
title: "例外、トランザクション、および補正 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プログラミング [WF], エラー処理"
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 例外、トランザクション、および補正
[!INCLUDE[wf1](../../../includes/wf1-md.md)] には、ワークフロー内のランタイム エラー条件を処理するさまざまな機構が用意されています。ワークフローでは、例外ハンドラー、トランザクション、キャンセル、および補正の組み合わせを使用して、エラー条件の処理と適切な回復を行えます。  
  
## このセクションの内容  
 [例外](../../../docs/framework/windows-workflow-foundation//exceptions.md)  
 <xref:System.Activities.Statements.TryCatch> アクティビティを使用して、ワークフローで例外を処理する方法について説明します。  
  
 [トランザクション](../../../docs/framework/windows-workflow-foundation//workflow-transactions.md)  
 <xref:System.Activities.Statements.TransactionScope> アクティビティを利用してワークフローでトランザクションを使用する方法を説明します。  
  
 [補正](../../../docs/framework/windows-workflow-foundation//compensation.md)  
 ワークフローの補正について説明します。また、<xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate>、および <xref:System.Activities.Statements.Confirm> などの補正アクティビティを使用する方法について説明します。  
  
 [取り消し](../../../docs/framework/windows-workflow-foundation//modeling-cancellation-behavior-in-workflows.md)  
 組み込みのアクティビティとカスタム アクティビティを使用してワークフローでキャンセル処理を実行する方法について説明します。  
  
 [デバッグのワークフロー](../../../docs/framework/windows-workflow-foundation//debugging-workflows.md)  
 ワークフローをデバッグする方法について説明します。