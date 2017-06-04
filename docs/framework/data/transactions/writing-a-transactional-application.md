---
title: "トランザクション アプリケーションの作成  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# トランザクション アプリケーションの作成 
トランザクション アプリケーションのプログラマは、<xref:System.Transactions> 名前空間に用意されている 2 つのプログラミング モデルを活用して、トランザクションを作成できます。<xref:System.Transactions.Transaction> クラスを使用した明示的なプログラミング モデルを使用できるほか、<xref:System.Transactions.TransactionScope> クラスを使用して、トランザクションが自動的にインフラストラクチャによって管理される暗黙的なプログラミング モデルも利用できます。開発では、暗黙的なトランザクション モデルを使用することをお勧めします。トランザクション スコープの使用方法については、「[トランザクション スコープを使用した暗黙的なトランザクションの実装 ](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)」を参照してください。  
  
 両モデルとも、プログラムが整合性の取れた状態に達した時点で、トランザクションのコミットをサポートします。コミットが成功すると、トランザクションは永続的にコミットされます。コミットが失敗すると、トランザクションは中止されます。アプリケーション プログラムがトランザクションを完了できない場合は、トランザクションを中止してその処理内容を取り消すことを試みます。  
  
## このセクションの内容  
  
### トランザクションの作成  
 <xref:System.Transactions> 名前空間には、トランザクションを作成する 2 つのモデルが用意されています。これらのモデルは、以下のトピックで取り上げられています。  
  
 [トランザクション スコープを使用した暗黙的なトランザクションの実装 ](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なトランザクションの作成について説明します。  
  
 [CommittableTransaction を使用した明示的なトランザクションの実装 ](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.CommittableTransaction> クラスを使用した明示的なトランザクションの作成について説明します。  
  
### トランザクション管理のエスカレート  
 トランザクションが別のアプリケーション ドメインにあるリソースにアクセスする必要がある場合、または別の永続的なリソース マネージャーに参加する場合は、トランザクションが MSDTC によって管理されるよう自動的にエスカレートされます。トランザクションのエスカレーションの詳細については、「[トランザクション管理エスカレーション ](../../../../docs/framework/data/transactions/transaction-management-escalation.md)」を参照してください。  
  
### 同時実行  
 「[DependentTransaction の同時実行の管理 ](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md)」では、<xref:System.Transactions.DependentTransaction> クラスを使用して、非同期タスク間で同時実行を実現する方法について説明します。  
  
### COM\+ 相互運用  
 「[Enterprise Services と COM\+ トランザクションの相互運用性 ](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md)」では、分散トランザクションを COM\+ トランザクションと連係させる方法について説明します。  
  
### 診断  
 「[診断トレース ](../../../../docs/framework/data/transactions/diagnostic-traces.md)」では、<xref:System.Transactions> インフラストラクチャによって生成されるトレース コードを使用して、アプリケーションのエラーをトラブルシューティングする方法について説明します。  
  
### ASP.NET 内での使用  
 「[ASP.NET での System.Transactions の使用](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md)」では、ASP.NET アプリケーション内で <xref:System.Transactions> を正しく使用する方法について説明します。