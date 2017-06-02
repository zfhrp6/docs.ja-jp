---
title: "System.Transactions で提供される機能  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# System.Transactions で提供される機能 
ここでは、<xref:System.Transactions> 名前空間により提供される機能を使用して、独自のトランザクション アプリケーションとリソース マネージャーを作成する方法について説明します。特に、1 つまたは複数の参加要素を含むローカル トランザクションまたは分散トランザクションを作成し、参加する方法について説明します。  
  
## System.Transactions の概要  
 <xref:System.Transactions> 名前空間内のクラスにより提供されるインフラストラクチャは、SQL Server、ADO.NET、メッセージ キュー \(MSMQ\)、および Microsoft 分散トランザクション コーディネーター \(MSDTC\) で開始されたトランザクションをサポートすることにより、トランザクション プログラミングを単純で効率的なものにします。<xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。この 2 つのモデルを使用したトランザクション アプリケーション作成方法の詳細については、「[トランザクション アプリケーションの作成 ](../../../../docs/framework/data/transactions/writing-a-transactional-application.md)」を参照してください。  
  
 <xref:System.Transactions> 名前空間には、リソース マネージャーを実装するための型も用意されています。リソース マネージャーは、トランザクションで使用する永続性データまたは揮発性データを管理し、トランザクション マネージャーと連携してアプリケーションの原子性と分離を保証します。<xref:System.Transactions> インフラストラクチャにより提供されるトランザクション マネージャーは、複数の揮発性リソースまたは単一の永続性リソースに関連するトランザクションをサポートします。リソース マネージャーの実装の詳細については、「[リソース マネージャーの実装 ](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md)」を参照してください。  
  
 また、トランザクション マネージャーは、他の永続的リソース マネージャーがそれ自体をトランザクションに参加させた場合に、DTC などのディスク ベースのトランザクション マネージャーと連携して、ローカル トランザクションを分散トランザクションへと透過的にエスカレートします。<xref:System.Transactions> インフラストラクチャでは、主に 2 つの方法でパフォーマンスを向上させています。  
  
-   ダイナミック エスカレーション。これにより、トランザクションが複数の分散リソースにわたる場合、<xref:System.Transactions> インフラストラクチャが MSDTC のみを使用すること保証します。ダイナミック エスカレーションの詳細については、「[トランザクション管理エスカレーション ](../../../../docs/framework/data/transactions/transaction-management-escalation.md)」トピックを参照してください。  
  
-   昇格可能参加リスト。これにより、データベースなどのリソースが、トランザクションに参加している唯一のエンティティである場合に、トランザクションの所有権を取得できます。その後、必要に応じて、<xref:System.Transactions> インフラストラクチャがトランザクションの管理を MSDTC にエスカレートすることもできます。これにより、MSDTC の使用頻度をさらに減らすことができます。昇格可能参加リストの詳細については、「[単一フェーズ コミットと昇格可能単一フェーズ通知を使用した最適化 ](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)」のトピックで詳しく解説されています。  
  
 <xref:System.Transactions> 名前空間は、AllowPartiallyTrustedCallers \(APTCA\)、DistributedTransactionPermission \(DTP\)、および完全な信頼の 3 つの信頼レベルを定義し、公開するリソースの種類へのアクセスを制限しています。各種の信頼レベルの詳細については、「[リソースへのアクセスでのセキュリティ信頼レベル ](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md)」を参照してください。  
  
## このセクションの内容  
  
### トランザクション アプリケーションの作成  
 <xref:System.Transactions> 名前空間には、トランザクション アプリケーションを作成するための 2 つのモデルが用意されています。「[トランザクション スコープを使用した暗黙的なトランザクションの実装 ](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)」では、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なトランザクションの作成が、<xref:System.Transactions> 名前空間でどのようにサポートされるかについて説明します。  
  
 「[CommittableTransaction を使用した明示的なトランザクションの実装 ](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)」では、<xref:System.Transactions.CommittableTransaction> クラスを使用した明示的なトランザクションの作成が、<xref:System.Transactions> 名前空間でどのようにサポートされるかについて説明します。  
  
 トランザクション アプリケーションの作成の詳細については、「[トランザクション アプリケーションの作成 ](../../../../docs/framework/data/transactions/writing-a-transactional-application.md)」を参照してください。  
  
### リソース マネージャーの実装  
 トランザクションに参加できるリソース マネージャーの実装については、「[リソース マネージャーの実装 ](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md)」を参照してください。ここでは、リソースの参加、トランザクションのコミット、障害後の回復、および最適化のベスト プラクティスについて説明しています。