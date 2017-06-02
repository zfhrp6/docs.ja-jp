---
title: "単一フェーズ コミットと昇格可能単一フェーズ通知を使用した最適化  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 単一フェーズ コミットと昇格可能単一フェーズ通知を使用した最適化 
ここでは、パフォーマンスを最適化するために <xref:System.Transactions> インフラストラクチャに用意されているメカニズムについて説明します。  
  
## PSPE \(Promotable Single Phase Enlistment\)  
 <xref:System.Transactions> インフラストラクチャは、単一の永続性リソースまたは複数の揮発性リソースを含む単一のアプリケーション ドメイン内のトランザクションを管理します。<xref:System.Transactions> インフラストラクチャは、アプリケーション内ドメインの呼び出しのみを使用するため、最良のスループットおよびパフォーマンスを得られます。  
  
 ただし、トランザクションが同じコンピューター上の別のアプリケーション ドメインにある別のオブジェクト \(プロセスやコンピューターの境界にまたがるものを含む\) に供給される場合や、別の永続的リソース マネージャーを参加させる場合、<xref:System.Transactions> インフラストラクチャは、MSDTC によって管理されるトランザクションを自動的にエスカレートします。MSDTC によって管理されるトランザクションは、<xref:System.Transactions> インフラストラクチャによって管理されるトランザクションに比べて、パフォーマンスが落ちます。  
  
 パフォーマンスを最適化するため、<xref:System.Transactions> インフラストラクチャには PSPE \(Promotable Single Phase Enlistment\) が用意されており、異なるアプリケーション ドメイン、プロセス、またはコンピューターにある単一のリモート永続性リソースが、MSDTC トランザクションにエスカレートされることなく <xref:System.Transactions> トランザクションに参加できるようになります。このリソース マネージャー \(RM\) は、必要に応じて後で分散トランザクション \(または MSDTC トランザクション\) にエスカレートできるトランザクションをホストおよび "所有" できます。これにより、MSDTC の使用頻度が少なくなります。  
  
 この特別なリソース マネージャーは通常、内部に独自の非分散トランザクションを所有しており、実行時にこれらのトランザクションを分散トランザクションに変換する必要があります。たとえば、SQL Server 2005 はこのようなリソース マネージャーです。この場合、<xref:System.Transactions> インフラストラクチャは、トランザクションのエスカレーションが必要かどうかを監視するだけという受動的な管理役割を担います。<xref:System.Transactions> インフラストラクチャとリソース マネージャー間の相互動作をサポートするため、リソース マネージャーは、<xref:System.Transactions.IPromotableSinglePhaseNotification> インターフェイスを実装する必要があります。  
  
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> メソッドは、後でエスカレートできる単一の永続性リソースを参加させるのに使用されます。このメソッドにより、必要に応じて参加リストをエスカレートできます。参加が成功すると、RM は内部トランザクションを作成し、<xref:System.Transactions> トランザクションに関連付けます。PSPE の参加が失敗すると、RM は代わりに <xref:System.Transactions.Transaction.EnlistDurable%2A> メソッドを使用して参加を行います。トランザクションが既に分散トランザクションである場合や、別の RM が既に PSPE の参加を実行している場合、PSPE の参加は失敗します。  
  
 参加すると、<xref:System.Transactions> トランザクションをコミットまたは中止するクライアントからの呼び出しがリソース マネージャーでの呼び出しに変換されます。これは、それぞれ <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> メソッドまたは <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> を呼び出すことで行われます。  
  
 <xref:System.Transactions> トランザクションのエスカレーションが必要ない場合、トランザクションがコミットされると、RM が <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> 通知を受信します。次に、最初に作成された内部トランザクションがコミットされます。  
  
 <xref:System.Transactions> トランザクションのエスカレートが必要な場合 \(複数の RM をサポートする場合など\) は、<xref:System.Transactions> がリソース マネージャーに通知します。この通知は、<xref:System.Transactions.IPromotableSinglePhaseNotification> インターフェイスの派生元である <xref:System.Transactions.ITransactionPromoter> インターフェイス上の <xref:System.Transactions.ITransactionPromoter.Promote%2A> メソッドを呼び出すことで行われます。次に、リソース マネージャーは、ローカル トランザクション \(ログが不要\) から DTC トランザクションに参加できるトランザクション オブジェクトへ、トランザクションを内部的に変換し、既に実行済みの作業に関連付けます。トランザクションのコミットが要求されると、トランザクション マネージャーが <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> 通知をリソース マネージャーに送信し、リソース マネージャーがエスカレーション中に作成される分散トランザクションをコミットします。  
  
> [!NOTE]
>  エスカレートされたトランザクションでコミットが呼び出されたときに生成される **TransactionCommitted** トレースは、DTC トランザクションのアクティビティ ID を含んでいます。  
  
 管理エスカレーションの詳細については、「[トランザクション管理エスカレーション ](../../../../docs/framework/data/transactions/transaction-management-escalation.md)」を参照してください。  
  
## トランザクション管理エスカレーションのシナリオ  
 次のシナリオは、<xref:System.Data> 名前空間をリソース マネージャーの "プロキシ" として使用して、分散トランザクションにエスカレートする操作を示しています。このシナリオでは、トランザクションで呼び出されたデータベースへの <xref:System.Data> 接続 \(CN1\) が既に存在し、アプリケーションが別の <xref:System.Data> 接続 \(CN2\) を呼び出そうとしている場合を想定しています。トランザクションは、完全な分散 2 フェーズ コミット トランザクションとして、DTC にエスカレートする必要があります。  
  
 このシナリオの内容  
  
1.  CN1 は、トランザクションに参加するため、<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> メソッドを呼び出します。ここで、トランザクションはまだローカルであり、トランザクションには他に昇格可能参加リストがないため、<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 呼び出しは成功します。  
  
2.  2 番目の接続 \(CN2\) が <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> を呼び出すと、関連する別の昇格可能参加リストがあるため、呼び出しが失敗します。このため、CN2 は、DTC トランザクションを取得して、SQL に渡す必要があります。これには、<xref:System.Transactions.TransactionInterop> クラスで提供されるメソッドの 1 つを使用して、SQL に渡すことができるトランザクションの形式を生成します。  
  
3.  <xref:System.Transactions> は、CN1 によって実装された <xref:System.Transactions.ITransactionPromoter> インターフェイス上で、<xref:System.Transactions.ITransactionPromoter.Promote%2A> メソッドを呼び出します。  
  
4.  この時点で CN1 は、SQL 2005 固有のメカニズムと <xref:System.Data> を使用して、トランザクションをエスカレートします。  
  
5.  <xref:System.Transactions.ITransactionPromoter.Promote%2A> メソッドからの戻り値は、トランザクションの反映トークンを含むバイト配列です。<xref:System.Transactions> は、この反映トークンを使用して、ローカル トランザクションに組み込むことができる DTC トランザクションを作成します。  
  
6.  この時点で CN2 は、<xref:System.Transactions.TransactionInterop> によるメソッドの 1 つを呼び出すことで受信したデータを使用して、SQL にトランザクションを渡すことができます。  
  
7.  ここで、両方が DTC 分散トランザクションに参加します。  
  
## 単一フェーズ コミットの最適化  
 単一フェーズ コミット プロトコルは、すべての更新が明示的な調整なしに行われるため、実行時に、より効率的です。この最適化を活用するには、リソースの <xref:System.Transactions.ISinglePhaseNotification> インターフェイスを使用してリソース マネージャーを実装し、<xref:System.Transactions.Transaction.EnlistDurable%2A> メソッドまたは <xref:System.Transactions.Transaction.EnlistVolatile%2A> メソッドを使用してトランザクションに参加する必要があります。特に、単一フェーズ コミットを確実に実行するには、*EnlistmentOptions* パラメーターを <xref:System.Transactions.EnlistmentOptions> と同じにする必要があります。  
  
 <xref:System.Transactions.ISinglePhaseNotification> インターフェイスは <xref:System.Transactions.IEnlistmentNotification> インターフェイスから派生するため、RM が単一フェーズ コミットを実行できない場合でも、2 フェーズ コミット通知を受信できます。RM が TM から <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> 通知を受信した場合は、コミットするために必要な作業を実行する必要があります。そして、それに応じて <xref:System.Transactions.SinglePhaseEnlistment> パラメーター上の <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>、<xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>、または <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> メソッドを呼び出すことにより、トランザクションのコミットまたはロールバックのどちらが実行されるかを、トランザクション マネージャーに通知する必要があります。この段階で、参加リストの <xref:System.Transactions.Enlistment.Done%2A> の応答は、ReadOnly セマンティクスを意味します。したがって、他のメソッドに加えて、<xref:System.Transactions.Enlistment.Done%2A> を応答しないでください。  
  
 揮発性参加リストが 1 つだけ存在し、永続参加リストが存在しない場合は、揮発性参加リストが SPC 通知を受信します。揮発性リストが複数、永続参加リストが 1 つだけ存在する場合は、揮発性参加リストが 2PC を受信します。完了すると、永続参加リストが SPC を受信します。  
  
## 参照  
 [参加要素としてのリソースのトランザクションへの参加 ](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)   
 [単一フェーズおよび複数フェーズでのトランザクションのコミット ](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)