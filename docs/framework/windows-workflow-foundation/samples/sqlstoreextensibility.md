---
title: "SQLStoreExtensibility | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# SQLStoreExtensibility
このサンプルでは、SQL ワークフロー インスタンス ストアの昇格したプロパティの使用法と構成を示します。SQL Workflow Instance Store は、SQL ベースのインスタンス ストアの実装です。SQL Workflow Instance Store を使用すると、インスタンスの状態を SQL Server データベースや SQL Server Express データベースに保存したり読み込んだりすることができます。ストア拡張機能を使用すると、ユーザーは、インスタンス ストアに格納されるプロパティを定義できます。このようなプロパティは、ユーザーがクエリを実行できる昇格したプロパティ ビューに表示されます。  
  
 このサンプルは、カウント サービスを実装するワークフローで構成されています。サービスの start メソッドが呼び出されると、0 から 29 までのカウントが行われます。カウンターは 2 秒ごとにインクリメントされ、カウントのたびにワークフローが永続化されます。現在のカウンター値は、昇格したプロパティとしてインスタンス ストアに格納されます。  
  
 このカウント ワークフローは、ワークフロー サービス ホストによってホストされる自己ホスト型サービスです。プログラムの `Main` メソッドは、次のアクションを実行します。  
  
-   カウント ワークフローをホストするワークフロー サービス ホストのインスタンスを作成し、カウント ワークフローにアクセスできるエンドポイントを定義します。  
  
-   SQL Workflow Instance Store を構成するために使用される SQL Workflow Instance Store の動作を定義します。このストアは、`CountStatus` を昇格したプロパティとして扱うように指示されます。  
  
-   カウント ワークフローの start メソッドを呼び出すクライアントを作成します。  
  
 プログラムを開始すると、カウンターが自動的にカウントを開始します。インスタンスを読み込んで SQL Workflow Instance Store を構成するのに数秒かかる場合もあります。  
  
 カウンター値をカスタム プロパティとして昇格するには、次の手順を実行する必要があります。  
  
1.  クラス `CounterStatus` は、<xref:System.Activities.Persistence.PersistenceParticipant> 型のインスタンス拡張機能を定義し、この型はアクティビティが状態変数を提供するために使用されます。`Count` は書き込み専用値として定義されます。ワークフロー インスタンスが永続性ポイントに達すると、インスタンス拡張機能によって、`Count` プロパティが永続性データ コレクションに保存されます。  
  
2.  インスタンス ストアの作成時に、新しいプロパティ `CountStatus` が `store.Promote()` を使用して定義されます。  
  
3.  ワークフローの `SaveCounter` アクティビティによって、現在のカウンター値が `Count` 状態フィールドに代入されます。  
  
### このサンプルを使用するには  
  
1.  インスタンス ストア データベースを作成します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトを開きます。  
  
    2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトでサンプル ディレクトリ \(\\WF\\Basic\\Persistence\\SqlStoreExtensibility\\CS\) に移動して、CreateInstanceStore.cmd を実行します。  
  
        > [!WARNING]
        >  CreateInstanceStore.cmd スクリプトは、SQL Server 2008 Express の既定のインスタンスにデータベースを作成しようとします。別のインスタンスにデータベースをインストールする場合は、そのようにスクリプトを変更してください。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を開いて SqlStoreExtensibility.sln ソリューションを読み込み、CTRL キーと SHIFT キーを押しながら B キーを押してビルドします。  
  
    > [!WARNING]
    >  SQL Server の既定以外のインスタンスにデータベースをインストールした場合は、ソリューションをビルドする前に、コードの接続文字列を更新してください。  
  
3.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] でプロジェクトの bin ディレクトリ \(\\WF\\Basic\\Persistence\\SqlStoreExtensibility\\bin\\Debug\) に移動し、SqlStoreExtensibility.exe を右クリックして **\[管理者として実行\]** をクリックすることで、サンプルを管理者権限で実行します。  
  
### サンプルが正常に動作していることを確認するには  
  
1.  SQL Server Management Studio を使用して、オブジェクト エクスプローラーで **\[データベース\]**、**\[InstanceStore\]**、**\[System.ServiceModel.Activities.DurableInstancing.InstanceTable\]** の順に選択してインスタンス テーブルの内容を表示し、**\[System.ServiceModel.Activities.DurableInstancing.InstanceTable\]** を右クリックして **\[上位 1000 行を選択\]** をクリックします。SQL Server Management Studio [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[SQL Server Management Studio の概要](http://go.microsoft.com/fwlink/?LinkId=165645)」を参照してください。  
  
2.  一覧表示されるワークフロー インスタンスを確認します。  
  
3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトで、サンプル ディレクトリ \(\\WF\\Basic\\Persistence\\SqlStoreExtensibility\) にある QueryInstanceStore.cmd スクリプトを実行します。  
  
4.  **CountStatus** の下に表示されるカウンター値を確認します。  
  
5.  スクリプトを数回実行して **CountStats** の値の変化を確認します。  
  
6.  Enter キーを押してワークフロー アプリケーションを終了します。  
  
### サンプルをアンインストールするには  
  
1.  サンプル ディレクトリ \(\\WF\\Basic\\Persistence\\SqlStoreExtensibility\) にある RemoveInstanceStore.cmd スクリプトを実行して、インスタンス ストア データベースを削除します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## 参照  
 [ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation//workflow-persistence.md)   
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)