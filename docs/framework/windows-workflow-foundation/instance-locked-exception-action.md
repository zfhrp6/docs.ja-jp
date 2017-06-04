---
title: "インスタンス ロック例外アクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# インスタンス ロック例外アクション
SQL Workflow Instance Store の <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> プロパティでは、SQL 永続化プロバイダーが <xref:System.Runtime.DurableInstancing.InstanceLockedException> を受け取ったときに実行するアクションを指定します。永続化プロバイダーがこの例外を受け取るのは、別のサービス ホストが現在ロックしているワークフロー サービス インスタンスをこの永続化プロバイダーがロックしようとしたときです。このプロパティの値は <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>、<xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>、および <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> です。既定値は <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> です。この 3 つのオプションを次の一覧で説明します。  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.サービス ホストはワーク フロー サービスのインスタンスをロックしようとせず、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。ワーク フローが 60 秒を超える期間をメモリにとどまったら再試行として <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> を使用します。既定値は <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> です。  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.サービス ホストは一定の再試行間隔でワークフロー サービス インスタンスのロックを再試行し、シーケンスの最後に <xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。ワークフローがおよそ 5\-60 秒間メモリに留まり、ワークフローをアンロードする前にすべてのメッセージを処理するため、同じホスト上の同じインスタンスに送信されるメッセージのようにメッセージがバッチで届く場合、リソースを無駄にしない最適な待ち時間を実現するため <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> を使用します。  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.サービス ホストは指数バックオフ間隔でワークフロー サービス インスタンスのロックを再試行し、シーケンスの最後に例外を呼び出し元に渡します。ワーク フローがとても短い間 \(5 秒以内\) 目盛りに留まる場合、または Web ファームが大きく別のメッセージが同じホストに渡される可能性が高くない場合、最適な待ち時間を実現するため <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> を使用します。  
  
 インスタンス ロック例外アクション機能は、次のシナリオをサポートしています。いずれのシナリオでも、SqlWorkflowInstanceStore の instanceLockedExceptionAction プロパティが <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> または <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> に設定されていれば、ホストはインスタンスのロックを取得するために、再試行を自動的に繰り返します。  
  
1.  **正常なシャットダウンの有効化およびアプリケーション ドメインの重複したリサイクル。**ワークフロー サービス インスタンスを実行するサービス ホストを持つ **AppDomain** がリサイクルされていて、新しい要求を処理するために新しい **AppDomain** が起動され、古い **AppDomain** が正常にシャットダウンされることが想定されています。このシャットダウンは、ワークフロー サービス インスタンスがアイドル状態になるまで待機した後、このインスタンスを永続化してアンロードします。新しい **AppDomain** でインスタンスをロックする処理をホストが再試行すると、<xref:System.Runtime.DurableInstancing.InstanceLockedException> が発生します。  
  
2.  **同種サーバー ファームでの永続的ワークフローの水平的スケーリング。**ワークフロー インスタンスが実行されているサーバー ファームのノードがクラッシュし、ワークフロー ホストが実行しているインスタンスのロックを解除できないことを想定しています。ファームの別のノードで実行されているサービス ホストは、そのワークフロー インスタンスのメッセージを受け取ると、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を受け取ることになる、これらのインスタンスのロックを取得する処理を試行します。ロックを更新することになっていたホストは存在しないため、ロックはしばらくすると期限切れになります。  
  
     **同種サーバー ファームでの永続的ワークフローの水平的スケーリング:** NLB \(ネットワーク負荷分散\) の内側で複数のホストを使用して永続的なワークフローを水平的にスケーリングし、ファームのいずれかのノードで実行されているワークフロー ホストがワークフロー インスタンスを読み込み、メッセージを処理することを想定しています。また、このインスタンスへの次のメッセージは別のノードで実行されているホストにルーティングされます。これは、すでにインスタンスを実行しているホストにメッセージを届けるルーティング アルゴリズムが NLB にないためです。メッセージを受け取ると、最初のホストがワークフロー インスタンスのロックを保持しているため、2 つ目のホストがこのインスタンスをロードする処理を試行し、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を受け取ります。最初のホストは、最初のメッセージ処理の終了時にこのインスタンスのロックを解除し、2 つ目のホストは次に再試行し、インスタンスをロードして、2 つ目のメッセージを処理する時にロックを取得します。