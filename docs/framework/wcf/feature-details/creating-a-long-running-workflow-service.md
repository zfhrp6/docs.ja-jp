---
title: "長時間のワークフロー サービスの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 長時間のワークフロー サービスの作成
ここでは、実行時間の長いワークフロー サービスを作成する方法について説明します。  実行時間の長いワークフロー サービスは、長期間にわたって実行できます。  ワークフローでは、いくつかの追加情報を待つ間アイドル状態になることがあります。  アイドル状態になると、ワークフローは SQL データベースに永続化され、メモリから削除されます。  追加情報が使用可能になると、ワークフロー インスタンスがメモリに読み込み直されて、実行を継続します。  このシナリオでは、非常に簡略化された注文システムを実装します。  クライアントは、最初のメッセージをワークフロー サービスに送信して注文を開始します。  ワークフロー サービスは、注文 ID をクライアントに返します。  この時点で、ワークフロー サービスは、クライアントからの別のメッセージを待機しており、アイドル状態に入って、SQL Server データベースに永続化されます。  クライアントが次のメッセージを送信して項目を注文すると、ワークフロー サービスはメモリに読み込み直されて、注文の処理を終了します。  次のコード例では、項目が注文に追加されたことを示す文字列を返します。  このコード例は、テクノロジの実際の適用を意図するものではなく、実行時間の長いワークフロー サービスを示す簡単な例です。このトピックでは、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] のプロジェクトおよびソリューションの作成方法を理解していることを前提としています。  
  
## 必須コンポーネント  
 このチュートリアルを使用するには、次のソフトウェアがインストールされている必要があります。  
  
1.  Microsoft SQL Server 2008  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
4.  ユーザーは WCF および [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] に精通しており、プロジェクトおよびソリューションの作成方法を理解している必要があります。  
  
### SQL データベースを設定するには  
  
1.  ワークフロー サービス インスタンスが永続化されるようにするには、Microsoft SQL Server をインストールして、永続化ワークフロー インスタンスを保存するようにデータベースを設定する必要があります。  **\[スタート\]** ボタンをクリックし、**\[すべてのプログラム\]**、**\[Microsoft SQL Server 2008\]**、**\[Microsoft SQL Management Studio\]** の順にクリックして、Microsoft SQL Management Studio を実行します。  
  
2.  **\[接続\]** ボタンをクリックして、SQL Server インスタンスにログオンします。  
  
3.  ツリー ビューで **\[データベース\]** を右クリックして **\[新しいデータベース\]** をクリックし、`SQLPersistenceStore` という名前の新しいデータベースを作成します。  
  
4.  SQLPersistenceStore データベースの C:\\Windows\\Microsoft.NET\\Framework\\v4.0\\SQL\\en ディレクトリにある SqlWorkflowInstanceStoreSchema.sql スクリプト ファイルを実行して、必要なデータベース スキーマを設定します。  
  
5.  SQLPersistenceStore データベースの C:\\Windows\\Microsoft.NET\\Framework\\v4.0\\SQL\\en ディレクトリにある SqlWorkflowInstanceStoreLogic.sql スクリプト ファイルを実行して、必要なデータベース ロジックを設定します。  
  
### Web ホスト ワークフロー サービスを作成するには  
  
1.  空の [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ソリューションを作成し、`OrderProcessing` という名前を付けます。  
  
2.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] という新しい `OrderService` ワークフロー サービス アプリケーション プロジェクトをソリューションに追加します。  
  
3.  プロジェクトのプロパティのダイアログで、**\[Web\]** タブをクリックします。  
  
    1.  **\[開始動作\]** の **\[ページを指定する\]** をクリックし、`Service1.xamlx` を指定します。  
  
         ![ワークフロー サービス プロジェクトの Web プロパティ](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")  
  
    2.  **\[サーバー\]** の **\[ローカル IIS Web サーバーを使用する\]** を選択します。  
  
         ![ローカル Web サーバーの設定](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")  
  
        > [!WARNING]
        >  この設定を行うには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を管理者モードで実行する必要があります。  
  
         次の 2 つの手順で、ワークフロー サービス プロジェクトが IIS でホストされるように設定します。  
  
4.  `Service1.xamlx` が開いていない場合は開き、既存の **ReceiveRequest** アクティビティと **SendResponse** アクティビティを削除します。  
  
5.  **\[シーケンシャル サービス\]** アクティビティを選択して **\[変数\]** リンクをクリックし、次の図に示されている変数を追加します。  こうするといくつかの変数が追加され、後でワークフロー サービスで使用されます。  
  
    > [!NOTE]
    >  CorrelationHandle が \[変数の型\] ボックスにない場合、ボックスから **\[型の参照\]** を選択します。  **\[型名\]** ボックスに「CorrelationHandle」と入力し、リスト ボックスから CorrelationHandle を選択して **\[OK\]** をクリックします。  
  
     ![変数の追加](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")  
  
6.  **ReceiveAndSendReply** アクティビティ テンプレートをドラッグして、**\[シーケンシャル サービス\]** アクティビティにドロップします。  このアクティビティのセットは、クライアントからメッセージを受信して、返信を送信します。  
  
    1.  **Receive** アクティビティを選択し、次の図で強調表示されているプロパティを設定します。  
  
         ![Receive アクティビティのプロパティの設定](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")  
  
         DisplayName プロパティは、デザイナーに表示される Receive アクティビティの名前を設定します。  ServiceContractName プロパティと OperationName プロパティは、Receive アクティビティで実装されるサービス コントラクトおよび操作の名前を指定します。  ワークフロー サービスでのコントラクトの使用方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー内でのコントラクトの使用](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)」を参照してください。  
  
    2.  **ReceiveStartOrder** アクティビティの **\[定義\]** リンクをクリックし、次の図に示されているプロパティを設定します。  **\[パラメーター\]** オプション ボタンが選択され、`p_customerName` という名前のパラメーターが `customerName` 変数にバインドされていることに注目してください。  これにより、**Receive** アクティビティがいくつかのデータを受け取り、そのデータをローカル変数にバインドするように設定されます。  
  
         ![Receive アクティビティが受信するデータの設定](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")  
  
    3.  **SendReplyToReceive** アクティビティを選択し、次の図で強調表示されているプロパティを設定します。  
  
         ![SendReply アクティビティのプロパティの設定](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")  
  
    4.  **SendReplyToStartOrder** アクティビティの **\[定義\]** リンクをクリックし、次の図に示されているプロパティを設定します。  **\[パラメーター\]** オプション ボタンが選択され、`p_orderId` という名前のパラメーターが `orderId` 変数にバインドされていることに注目してください。  この設定により、SendReplyToStartOrder アクティビティが型文字列の値を呼び出し元に返すように指定されます。  
  
         ![SendReply アクティビティのコンテンツ データの構成](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")  
  
        > [!NOTE]
    5.  Assign アクティビティをドラッグして **Receive** アクティビティと **SendReply** アクティビティの間にドロップし、次の図に示されているようにプロパティを設定します。  
  
         ![Assign アクティビティの追加](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")  
  
         これにより、新しい注文 ID が作成され、orderId 変数に値が配置されます。  
  
    6.  **ReplyToStartOrder** アクティビティを選択します。  プロパティ ウィンドウで、**CorrelationInitializers** の省略記号ボタンをクリックします。  **\[初期化子の追加\]** リンクを選択し、\[初期化子\] ボックスに「`orderIdHandle`」と入力して、\[関連付けの種類\] に \[クエリ関連付け初期化子\] を選択し、\[XPATH クエリ\] ボックスの p\_orderId を選択します。  これらの設定を次の図に示します。  **\[OK\]** をクリックします。  これにより、クライアントとワークフロー サービスのこのインスタンス間の相関関係が初期化されます。  この注文 ID を含むメッセージが受信されると、ワークフロー サービスのこのインスタンスにルーティングされます。  
  
         ![関連付け初期化子の追加](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")  
  
7.  別の **ReceiveAndSendReply** アクティビティをドラッグしてワークフローの最後 \(最初の **Receive** アクティビティと **SendReply** アクティビティを含む **\[シーケンス\]** の外側\) にドロップします。  これで、クライアントで送信された 2 つ目のメッセージを受信し、それに応答します。  
  
    1.  新しく追加した **Receive** アクティビティと **SendReply** アクティビティを含む **\[シーケンス\]** を選択し、**\[変数\]** ボタンをクリックします。  次の図で強調表示されている変数を追加します。  
  
         ![新しい変数の追加](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")  
  
    2.  **Receive** アクティビティを選択し、次の図に示されているプロパティを設定します。  
  
         ![Receive アクティビティのプロパティの設定](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")  
  
    3.  **ReceiveAddItem** アクティビティの **\[定義\]** リンクをクリックし、次の図に示されているパラメーターを追加します。これにより、Receive アクティビティが 2 つのパラメーター、注文 ID、および注文されている項目の ID を受け取るように設定されます。  
  
         ![2 つ目の Receive のパラメーター指定](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")  
  
    4.  **CorrelateOn** の省略記号ボタンをクリックし、「`orderIdHandle`」を入力します。  **\[XPath クエリ\]** のドロップダウン矢印をクリックし、`p_orderId` を選択します。  これにより、2 つ目の Receive アクティビティに相関関係が設定されます。  相関関係[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[関連付け](../../../../docs/framework/wcf/feature-details/correlation.md)」を参照してください。  
  
         ![CorrelatesOn プロパティの設定](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")  
  
    5.  **If** アクティビティをドラッグして **ReceiveAddItem** アクティビティの直後にドロップします。  このアクティビティは、if ステートメントと同様に動作します。  
  
        1.  **Condition** プロパティを `itemId==”Zune HD” (itemId=”Zune HD” for Visual Basic)` に設定します。  
  
        2.  **Assign** アクティビティを **Then** セクションと **Else** セクションにそれぞれドラッグ アンド ドロップして、次の図に示されているように **Assign** アクティビティのプロパティを設定します。  
  
             ![サービス呼び出しの結果の割り当て](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")  
  
             条件が `true` である場合、**Then** セクションが実行されます。  条件が `false` である場合、**Else** セクションが実行されます。  
  
        3.  **SendReplyToReceive** アクティビティを選択し、次の図で強調表示されている **DisplayName** プロパティを設定します。  
  
             ![SendReply アクティビティのプロパティの設定](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")  
  
        4.  **SetReplyToAddItem** アクティビティの **\[定義\]** リンクをクリックし、次の図に示されているように設定します。  これにより、**SendReplyToAddItem** アクティビティが `orderResult` 変数に値を返すように設定されます。  
  
             ![SendReply アクティビティのデータ バインディングの設定](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")  
  
8.  web.config ファイルを開いて、次の要素を \<behavior\> セクションに追加し、ワークフロー永続化を有効にします。  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
  
    ```  
  
    > [!WARNING]
    >  前のコード スニペットでホストと SQL Server インスタンス名を置換するようにします。  
  
9. ソリューションをビルドします。  
  
### クライアント アプリケーションを作成してワークフロー サービスを呼び出すには  
  
1.  `OrderClient` という新しいコンソール アプリケーション プロジェクトをソリューションに追加します。  
  
2.  次のアセンブリへの参照を `OrderClient` プロジェクトに追加します。  
  
    1.  System.ServiceModel.dll  
  
    2.  System.ServiceModel.Activities.dll  
  
3.  サービス参照をワークフロー サービスに追加し、`OrderService` を名前空間として指定します。  
  
4.  クライアント プロジェクトの `Main()` メソッド内に次のコードを追加します。  
  
    ```  
    static void Main(string[] args)  
    {  
       // Send initial message to start the workflow service  
       Console.WriteLine("Sending start message");  
       StartOrderClient startProxy = new StartOrderClient();  
       string orderId = startProxy.StartOrder("Kim Abercrombie");  
  
       // The workflow service is now waiting for the second message to be sent  
       Console.WriteLine("Workflow service is idle...");  
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");  
       Console.ReadLine();  
  
       // Send the second message  
       Console.WriteLine("Sending add item message");  
       AddItemClient addProxy = new AddItemClient();  
       AddItem item = new AddItem();  
       item.p_itemId = "Zune HD";  
       item.p_orderId = orderId;  
  
       string orderResult = addProxy.AddItem(item);  
       Console.WriteLine("Service returned: " + orderResult);  
    }  
  
    ```  
  
5.  ソリューションをビルドし、`OrderClient` アプリケーションを実行します。  クライアントに次のテキストが表示されます。  
  
    ```Output  
  
                  開始メッセージを送信します  
    ワークフロー サービスがアイドル状態です...  Enter キーを押して項目の追加メッセージを送信し、ワークフロー サービスを再びアクティブにします。    
    ```  
  
6.  ワークフロー サービスが永続化されていることを確認するには、**\[スタート\]** メニューで **\[すべてのプログラム\]**、**\[Microsoft SQL Server 2008\]**、**\[SQL Server Management Studio\]** の順にクリックして、SQL Server Management Studio を起動します。  
  
    1.  左ペインで、**\[データベース\]**、**\[SQLPersistenceStore\]**、**\[ビュー\]** の順に展開し、**System.Activities.DurableInstancing.Instances** を右クリックして **\[上位 1000 行を選択\]** をクリックします。  **\[結果\]** ペインで、少なくとも 1 つのインスタンスがリストされていることを確認します。  実行中に例外が発生した場合は、前の実行のその他のインスタンスがある可能性があります。  既存の行を削除するには、**System.Activities.DurableInstancing.Instances** を右クリックして **\[上位 200 行を編集\]** をクリックし、**\[実行\]** ボタンを押し、\[結果\] ペインのすべての行を選択して **\[削除\]** をクリックします。  データベースに表示されているインスタンスが、アプリケーションで作成されたインスタンスであることを確認するには、クライアントを実行する前に、Instances ビューが空であることを確認します。  クライアントが実行されると、クエリ \(\[上位 1000 行を選択\]\) を再実行し、新しいインスタンスが追加されていることを確認します。  
  
7.  Enter キーを押して、項目の追加メッセージをワークフロー サービスに送信します。  クライアントに次のテキストが表示されます。  
  
    ```Output  
  
                  項目の追加メッセージを送信します。  
    サービスは注文に追加された項目を返しました。  
    続行するには、いずれかのキーを押します.  .  .    
    ```  
  
## 参照  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)