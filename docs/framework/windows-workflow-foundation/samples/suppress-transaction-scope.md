---
title: "トランザクション スコープの抑制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# トランザクション スコープの抑制
このサンプルでは、アンビエント ランタイム トランザクションが存在する場合はそのトランザクションを抑制するカスタム `SuppressTransactionScope` アクティビティを作成する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## サンプルの詳細  
 このカスタム アクティビティを使用すると、トランザクション フローが特定のシナリオに適さない場合に、別のサービスにトランザクションがフローされないようにすることができます。ワークフロー ランタイムには <xref:System.Activities.NativeActivity> クラスのアンビエント トランザクションを抑制するためのサポートが組み込まれていますが、そのサポートを使用するには、このサンプルで示すようなカスタム <xref:System.Activities.NativeActivity> アクティビティを作成する必要があります。  
  
 このシナリオは、3 つの部分で構成されています。まず、<xref:System.Activities.Statements.TransactionScope> によって、アンビエントになるランタイム トランザクションが作成されます。これは、トランザクションのローカル識別子と分散識別子を出力するカスタム アクティビティによって検証されます。その後、トランザクションがリモート サービスにフローされてから、2 番目の部分が始まります。2 番目の部分では、ワークフローが `SuppressTransactionScope` に移り、トランザクション識別子を出力してトランザクションをフローさせるプロセスがもう一度繰り返されます。ただし、カスタム アクティビティでアンビエント トランザクションを探さないため、サービスにフローされるメッセージにはトランザクションが含まれません。その結果、サービスによってトランザクションが作成され、クライアントとサービスで出力される分散 ID が一致しなくなります。最後の部分は、`SuppressTransactionScope` が終了した後の部分です。分散識別子が最初のメッセージの識別子と一致する別のメッセージがサービスにフローされ、そのメッセージによる検証でランタイム トランザクションがもう一度アンビエントになります。  
  
 アクティビティ自体は、子アクティビティをスケジュールして実行プロパティを追加する必要があるため、<xref:System.Activities.NativeActivity> から派生します。`SuppressTransactionScope` には、<xref:System.Activities.RuntimeTransactionHandle> 型の <xref:System.Activities.Variable> が含まれます。ハンドルを初期化する必要があるため、<xref:System.Activities.RuntimeTransactionHandle> 型のインスタンス フィールドではなく、この変数を使用する必要があります。`Variable<RuntimeTransactionHandle>` は内部でのみ使用されるため、実装変数としてアクティビティのメタデータに追加されます。  
  
 アクティビティを実行すると、まず本体が指定されているかどうかがチェックされ、指定されていれば <xref:System.Activities.RuntimeTransactionHandle> に `SuppressTransaction` プロパティが設定されます。このプロパティは、設定されると実行プロパティに追加され、アンビエントになります。つまり、`SuppressTransactionScope` のすべての子アクティビティがこのプロパティを参照できるようになります。これにより、ランタイム トランザクションの抑制が適用され、入れ子になった <xref:System.Activities.Statements.TransactionScope> で例外がスローされます。実行プロパティにハンドルが追加されると、本体の実行がスケジュールされます。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で SuppressTransactionScope.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、CTRL キーと SHIFT キーを押したまま B キーを押すか、**\[ビルド\]** メニューの **\[ソリューションのビルド\]** を選択します。  
  
3.  ビルドが完了したら、ソリューションを右クリックし、**\[スタートアップ プロジェクトの設定\]** をクリックします。ダイアログで、**\[マルチ スタートアップ プロジェクト\]** を選択し、両方のプロジェクトのアクションが **\[開始\]** になっていることを確認します。  
  
4.  F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。または、Ctrl キーを押しながら F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックして、デバッグ機能なしで実行します。  
  
    > [!NOTE]
    >  クライアントを起動する前に、サーバーを起動しておく必要があります。サービスをホストするコンソール ウィンドウの出力で、起動された時間が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## 参照