---
title: "ワークフローとワークフロー サービスの永続化を有効にする方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ワークフローとワークフロー サービスの永続化を有効にする方法
ここでは、ワークフローとワークフロー サービスの永続化を有効にする方法について説明します。  
  
## ワークフローの永続化を有効にする  
 <xref:System.Activities.WorkflowApplication> クラスの <xref:System.Activities.WorkflowApplication.InstanceStore%2A> プロパティを使用して、インスタンス ストアと **WorkflowApplication** を関連付けることができます。<xref:System.Activities.WorkflowApplication.Persist%2A> メソッドは、アプリケーションに関連付けられたインスタンス ストアにワークフローを保存または永続化します。<xref:System.Activities.WorkflowApplication.Unload%2A> メソッドは、ワークフローをインスタンス ストアに永続化し、メモリからインスタンスをアンロードします。**Load** メソッドは、インスタンスの永続化ストアに格納されているワークフロー データを使用し、ワークフローをメモリに読み込みます。  
  
 **Persist** メソッドは、次の手順を実行します。  
  
1.  ワークフローのスケジューラを一時停止し、アイドル状態に移行するまで待機します。  
  
2.  ワークフローを永続化 \(永続化ストアに保存\) します。  
  
3.  ワークフローのスケジューラを再開します。  
  
 **Unload** メソッドは、次の手順を実行します。  
  
1.  ワークフローのスケジューラを一時停止し、アイドル状態に移行するまで待機します。  
  
2.  ワークフローを永続化 \(永続化ストアに保存\) します。  
  
3.  メモリ内のワークフロー インスタンスを破棄します。  
  
 ワークフローが非永続化ゾーンにある間は、ワークフローが非永続化ゾーンを終了するまで、**Persist** メソッドと **Unload** メソッドのどちらもブロックします。メソッドは、非永続化ゾーンの完了後に、永続化またはアンロードの操作を続行します。期限切れになる前に非永続化ゾーンが完了しない場合、または永続化プロセスに時間がかかりすぎる場合は、TimeoutException がスローされます。  
  
## コードでのワークフロー サービスの永続化を有効にする  
 <xref:System.ServiceModel.WorkflowServiceHost> クラスの **DurableInstancingOptions** メンバーには **InstanceStore** というプロパティがあり、インスタンス ストアを **WorkflowServiceHost** に関連付けるために使用できます。  
  
```  
  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
  
```  
  
 **WorkflowServiceHost** を開くと、**DurableInstancingOptions.InstanceStore** が null ではない場合、永続化が自動的に有効になります。  
  
 通常、サービスの動作には、**InstanceStore** プロパティを使用してワークフロー サービス ホストと共に使用できる具象インスタンス ストアが用意されています。たとえば、SqlWorkflowInstanceStoreBehavior は、**SqlWorkflowInstanceStore** のインスタンスを作成し、構成して、**DurableInstancingOptions.InstanceStore** に割り当てます。  
  
## アプリケーション構成ファイルを使用してワークフロー サービスの永続化を有効にする  
 次のコードを app.config または web.config file に追加すると、アプリケーション構成ファイルを使用して永続化を有効にできます。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name=”myBehavior”>  
          <SqlWorkflowInstanceStore connectionString=”Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase”>  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
  
```