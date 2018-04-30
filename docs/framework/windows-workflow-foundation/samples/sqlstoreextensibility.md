---
title: SQLStoreExtensibility
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 722c7cda49b2efc4c146970c69cc5e3c7bbad9b0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
このサンプルでは、SQL ワークフロー インスタンス ストアの昇格したプロパティの使用法と構成を示します。 SQL Workflow Instance Store は、SQL ベースのインスタンス ストアの実装です。 SQL Workflow Instance Store を使用すると、インスタンスの状態を SQL Server データベースや SQL Server Express データベースに保存したり読み込んだりすることができます。 ストア拡張機能を使用すると、ユーザーは、インスタンス ストアに格納されるプロパティを定義できます。 このようなプロパティは、ユーザーがクエリを実行できる昇格したプロパティ ビューに表示されます。  
  
 このサンプルは、カウント サービスを実装するワークフローで構成されています。 サービスの start メソッドが呼び出されると、0 から 29 までのカウントが行われます。 カウンターは 2 秒ごとにインクリメントされ、 カウントのたびにワークフローが永続化されます。 現在のカウンター値は、昇格したプロパティとしてインスタンス ストアに格納されます。  
  
 このカウント ワークフローは、ワークフロー サービス ホストによってホストされる自己ホスト型サービスです。 プログラムの `Main` メソッドは、次のアクションを実行します。  
  
-   カウント ワークフローをホストするワークフロー サービス ホストのインスタンスを作成し、カウント ワークフローにアクセスできるエンドポイントを定義します。  
  
-   SQL Workflow Instance Store を構成するために使用される SQL Workflow Instance Store の動作を定義します。 このストアは、`CountStatus` を昇格したプロパティとして扱うように指示されます。  
  
-   カウント ワークフローの start メソッドを呼び出すクライアントを作成します。  
  
 プログラムを開始すると、カウンターが自動的にカウントを開始します。 インスタンスを読み込んで SQL Workflow Instance Store を構成するのに数秒かかる場合もあります。  
  
 カウンター値をカスタム プロパティとして昇格するには、次の手順を実行する必要があります。  
  
1.  クラス `CounterStatus` は、<xref:System.Activities.Persistence.PersistenceParticipant> 型のインスタンス拡張機能を定義し、これはアクティビティが状態変数を提供するために使用されます。 `Count` は書き込み専用値として定義されます。 ワークフロー インスタンスが永続性ポイントに達すると、インスタンス拡張機能によって、`Count` プロパティが永続性データ コレクションに保存されます。  
  
2.  インスタンス ストアの作成時に、新しいプロパティ `CountStatus` が `store.Promote()` を使用して定義されます。  
  
3.  ワークフローの `SaveCounter` アクティビティによって、現在のカウンター値が `Count` 状態フィールドに代入されます。  
  
### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  インスタンス ストア データベースを作成します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
    2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトでサンプル ディレクトリ (\WF\Basic\Persistence\SqlStoreExtensibility\CS) に移動して、CreateInstanceStore.cmd を実行します。  
  
        > [!WARNING]
        >  CreateInstanceStore.cmd スクリプトは、SQL Server 2008 Express の既定のインスタンスにデータベースを作成しようとします。 別のインスタンスにデータベースをインストールする場合は、そのようにスクリプトを変更してください。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を開いて SqlStoreExtensibility.sln ソリューションを読み込み、Ctrl キーと Shift キーを押しながら B キーを押してビルドします。  
  
    > [!WARNING]
    >  SQL Server の既定以外のインスタンスにデータベースをインストールした場合は、ソリューションをビルドする前に、コードの接続文字列を更新してください。  
  
3.  管理者特権でのプロジェクトの bin ディレクトリ (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) に移動してサンプルを実行[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]SqlStoreExtensibility.exe を右クリックしを選択すると、**として実行管理者**です。  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>サンプルが正常に動作していることを確認するには  
  
1.  SQL Server Management Studio を使用して、選択してインスタンス テーブルの内容を表示する**データベース**、 **InstanceStore**、し**System.ServiceModel.Activities.DurableInstancing.InstanceTable**オブジェクト エクスプ ローラーで右クリック**System.ServiceModel.Activities.DurableInstancing.InstanceTable** の選択**上位 1000 行を選択して**です。 SQL Server Management Studio の詳細については、次を参照してください[SQL Server Management Studio の概要。](http://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  一覧表示されるワークフロー インスタンスを確認します。  
  
3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトで、サンプル ディレクトリ (\WF\Basic\Persistence\SqlStoreExtensibility) にある QueryInstanceStore.cmd スクリプトを実行します。  
  
4.  カウンターの値が表示される確認して**CountStatus**です。  
  
5.  スクリプトを数回実行して、 **CountStats**値の変更。  
  
6.  Enter キーを押してワークフロー アプリケーションを終了します。  
  
### <a name="to-uninstall-the-sample"></a>サンプルをアンインストールするには  
  
1.  サンプル ディレクトリ (\WF\Basic\Persistence\SqlStoreExtensibility) にある RemoveInstanceStore.cmd スクリプトを実行して、インスタンス ストア データベースを削除します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>関連項目  
 [ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
