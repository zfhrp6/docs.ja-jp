---
title: "メッセージ フローの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# メッセージ フローの概要
相互接続されたサービスを持つ分散システムでは、サービス間の因果関係を調べる必要があります。  状態監視、トラブルシューティング、原因分析などの重要なシナリオをサポートするには、要求フローに含まれるさまざまなコンポーネントを理解することが重要です。  .NET Framework 4 では、多様なサービス間でトレースを関連付けることができるように、次の機能のサポートが追加されています。  
  
-   分析トレース: Event Tracing for Windows \(ETW\) を使用したトレース機能です。詳細度が低く、パフォーマンスに優れています。  
  
-   WCF\/WF サービス用のエンドツーエンドのアクティビティ モデル: <xref:System.ServiceModel> 名前空間および <xref:System.WorkflowModel> 名前空間が生成するトレースの相関関係をサポートする機能です。  
  
-   WF の ETW 追跡: この機能では、WF サービスによって生成された追跡レコードを使用して、ワークフローの現在の状態と進行状況を把握します。  
  
 追跡レコードまたはトレース レコードに記録されたエラーを使用して、コード障害や誤った形式のメッセージを検出できます。  エラー状態のアクティビティの特定には、イベントのメッセージ ヘッダーにある Correlation ノードの ActivityId プロパティを使用することができます。  アクティビティ ID ごとにメッセージ フローのトレースを有効にする方法については、「[メッセージ フローのトレースの構成](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)」を参照してください。  このトピックでは、チュートリアル入門で作成されたプロジェクトでメッセージ フローのトレースを有効にする方法を示します。  
  
### チュートリアル入門で作成されたプロジェクトでメッセージ フローのトレースを有効にするには  
  
1.  **\[スタート\]** ボタン、**\[ファイル名を指定して実行\]** の順にクリックし、「`eventvwr.exe`」と入力してイベント ビューアーを開きます。  
  
2.  分析トレースを有効にしていない場合は、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]**、**\[アプリケーション サーバー \- アプリケーション\]** の順に展開します。  **\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。  **\[分析\]** を右クリックし、**\[ログを有効にする\]** をクリックします。  トレースが表示されるように、イベント ビューアーを開いたままにします。  
  
3.  [チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)で作成されたサンプルを [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で開きます。  サービスを作成できるように、管理者として [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を実行する必要があることに注意してください。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルがインストールされている場合、このチュートリアルで作成する完成済みのプロジェクトが含まれている[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)を開くことができます。  
  
4.  **Service** プロジェクトを右クリックして、**\[追加\]**、**\[新しい項目\]** の順にクリックします。  **\[アプリケーション構成ファイル\]** をクリックし、**\[OK\]** をクリックします。  
  
5.  上の手順で作成した App.Config ファイルに次のコードを追加します。  
  
    ```  
    <system.serviceModel>  
      <diagnostics>  
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
      </diagnostics>  
    </system.serviceModel>  
  
    ```  
  
6.  Ctrl キーを押しながら F5 キーを押して、サーバー アプリケーションをデバッグなしで実行します。  **Client** プロジェクトを右クリックし、**\[デバッグ\]**、**\[新しいインスタンスを開始\]** の順にクリックして、Client プロジェクトを実行します。  
  
7.  クライアントからサーバーへのイベントをトレースするには、Client プロジェクトのアプリケーション構成ファイルに次の内容を追加します。  
  
    ```  
    <diagnostics>  
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
    </diagnostics>  
  
    ```  
  
8.  クライアントの Program.cs に、次の Using ステートメントを追加します。  
  
    ```  
    using System.Diagnostics;  
  
    ```  
  
9. Client プロジェクトの program.cs ファイルにある Main メソッドで、トレース GUID をイベント ログに伝達するように設定します。  
  
    ```  
    Guid guid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = guid;  
  
    ```  
  
10. 最新の情報に更新し、**\[分析\]** ログを調べます。  イベント ID が 220 のイベントを探します。  イベントを選択し、プレビュー ペインで **\[詳細\]** タブをクリックします。  このイベントには、呼び出し元アクティビティの相関 ID が含まれています。  
  
    ```  
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />  
    ```  
  
    > [!NOTE]
    >  ActivityID に同じ GUID を持つすべてのイベントは、1 つの要求に関連しています。  これは、特定のクライアントから特定のサービスへメッセージを関連付けるために使用できます。  このクライアントが別のサービスを呼び出した場合、同じクライアントが ActivityID によって識別されます。  
  
11. 場合によっては、ActivityID が元の GUID から新しい ActivityID に変更されます。  その場合、転送イベントが生成されます。  このイベント ID は 499 で、イベントのヘッダーに次のデータが格納されます。  
  
    ```  
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">  
        <System>  
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />   
            <EventID>499</EventID>   
            ...  
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />   
            ...  
       </System>  
    </Event>  
    ```  
  
    > [!NOTE]
    >  転送イベントは、アクティブな ActivityID が、ActivityID として指定された GUID から RelatedActivityID として指定された GUID に変更されたことを記録します。  転送イベントの生成後は、すべてのイベントに新しい GUID が ActivityID として格納されます。