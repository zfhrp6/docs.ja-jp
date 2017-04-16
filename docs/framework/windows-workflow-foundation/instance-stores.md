---
title: "インスタンス ストア | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# インスタンス ストア
インスタンス ストアは、インスタンスの論理コンテナーです。この場所には、インスタンス データとメタデータが格納されます。インスタンス ストアは、専用の物理的なストレージを意味しているわけではありません。インスタンス ストアには SQL Server データベースの永続的な情報と、メモリ内の非永続的な状態の情報が含まれます。[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には SQL Workflow Instance Store が付属しています。これはインスタンス ストアの具象実装で、ワークフローが SQL Server 2005 または SQL Server 2008 データベースにインスタンス データとメタデータを永続化できるようにします。また、Windows Server App Fabric は、インスタンス ストアの具象実装を提供します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric のインスタンス ストア、クエリ、および管理プロバイダー](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409)。  
  
 永続化 API は、ホストがコマンド要求 \(<xref:System.Activities.DurableInstancing.LoadWorkflowCommand> や <xref:System.Activities.DurableInstancing.SaveWorkflowCommand> など\) をインスタンス ストアに送信できるようにするための、ホストとインスタンス ストア間のインターフェイスです。この API の具象実装は、永続化プロバイダーと呼ばれます。永続化プロバイダーはホストからの要求を受け取り、インスタンス ストアを変更します。  
  
 ホストで多くのインスタンス ストアを使用し、インスタンス ストアを多くのホストで使用できるように、ホストとインスタンス ストアはプラグ可能です。通常、インスタンス ストアは特定のホストの使用パターンに合わせて最適化されますが、インスタンス ストアとホストはそれぞれのライフ サイクルで進化する場合があります。たとえば、**WorkflowServiceHost** と **SqlWorkflowInstanceStore** は、併せて効果的に使用できるように設計されています。独自のインスタンス ストアを作成して、ワークフロー サービス インスタンスのデータとメタデータを永続化したり、そのインスタンス ストアを **WorkflowServiceHost** と一緒に使用したりすることができます。たとえば、SQL Server データベースに保存するのではなく、OracleWorkflowInstanceStore を作成して、ワークフローに Oracle データベースに情報を永続化させることができます。  
  
 通常、ホストは保存されたオブジェクトを変更する機能を追加して拡張されます。たとえば、インスタンス永続化システムに、ワークフロー ホスト、「中断」操作をサポートする拡張機能、および SQL インスタンス ストアがあるとします。ワークフロー ホストは保存または読み込みなどの標準的なコマンドを送信して、インスタンス ストアに対してワークフローの保存または読み込みを行ったり、インスタンス ストアにワークフローを保存したりします。中断されたワークフロー インスタンスが読み込まれないように、中断の拡張機能によって、ワークフロー インスタンスの保存および読み込みを行うコマンドに追加のセマンティクスが追加されます。SQL インスタンス ストアの永続化プロバイダーは、ワークフロー インスタンスの保存と読み込み用のコマンドを理解し、SQL Server データベースの永続オブジェクトのテーブルを変更する適切なストアド プロシージャを呼び出して、コマンドを実装します。  
  
 インスタンス ストア内では、ホストはインスタンスの所有者として動作します。ホストは、同時に複数のインスタンス ストアを持つ複数のインスタンスの所有者として動作します。ホストはインスタンスに関連付けられているインスタンス キーの GUID を提供します。インスタンス キーは、インスタンスを識別する一意の別名です。永続化システムは、ホストが要求したコマンドを実行するときに、インスタンスの所有者情報を作成、更新、および削除します。  
  
 ホストとインスタンス ストアとの対話に関連する重要な手順を次に示します。  
  
1.  永続化プロバイダーから **InstanceStore** を取得します。  
  
2.  **InstanceStore** の<xref:System.Runtime.Persistence.InstanceStore.CreateInstanceHandle%2A> メソッドを呼び出して、インスタンスへのハンドルを取得します。  
  
3.  **InstanceStore** の<xref:System.Runtime.Persistence.InstanceStore.Execute%2A> メソッドを呼び出して、インスタンスのハンドルに対してコマンドを呼び出します。  
  
4.  **InstanceStore.Execute** から返された <xref:System.Runtime.Persistence.InstanceView> を確認して、コマンドの結果を判断します。