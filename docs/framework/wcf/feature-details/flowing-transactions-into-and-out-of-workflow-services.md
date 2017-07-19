---
title: "ワークフロー サービスへのトランザクションのフロー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# ワークフロー サービスへのトランザクションのフロー
ワークフロー サービスとワークフロー クライアントはトランザクションに参加できます。サービス操作をアンビエント トランザクションの一部にするには、<xref:System.ServiceModel.Activities.Receive> アクティビティを <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティの中に配置します。<xref:System.ServiceModel.Activities.TransactedReceiveScope> 内の <xref:System.ServiceModel.Activities.Send> または <xref:System.ServiceModel.Activities.SendReply> アクティビティによる呼び出しが行われると、アンビエント トランザクション内でも呼び出しが行われます。ワークフロー クライアント アプリケーションでは、<xref:System.Activities.Statements.TransactionScope> アクティビティを使用してアンビエント トランザクションを作成し、そのアンビエント トランザクションを使用してサービス操作を呼び出すことができます。ここでは、トランザクションに参加するワークフロー サービスとワークフロー クライアントを作成する手順について説明します。  
  
> [!WARNING]
>  ワークフロー サービス インスタンスがトランザクション内に読み込まれて、ワークフローに <xref:System.Activities.Statements.Persist> アクティビティが含まれている場合、ワークフロー インスタンスはトランザクションがタイムアウトするまでハングします。  
  
> [!IMPORTANT]
>  <xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用する場合は、<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティ内のワークフローにすべての受信を配置することをお勧めします。  
  
> [!IMPORTANT]
>  <xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用して、メッセージが不適切な順序で到着する場合、最初の順序を無視したメッセージを配信しようとするとワークフローは中止されます。ワークフローがアイドル状態である場合、ワークフローは常に一致する停止ポイントにあるようにする必要があります。これによって、ワークフローが中止された場合、前の永続性ポイントからワークフローを再開することができます。  
  
### 共有ライブラリの作成  
  
1.  新しい空の Visual Studio ソリューションを作成します。  
  
2.  `Common` という新しいクラス ライブラリ プロジェクトを追加します。次のアセンブリへの参照を追加します。  
  
    -   System.Activities.dll  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceModel.Activities.dll  
  
    -   System.Transactions.dll  
  
3.  `PrintTransactionInfo` という新しいクラスを `Common` プロジェクトに追加します。このクラスは <xref:System.Activities.NativeActivity> の派生クラスで、<xref:System.Activities.NativeActivity.Execute%2A> メソッドをオーバーロードします。  
  
    ```  
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
  
    ```  
  
     これは、アンビエント トランザクションに関する情報を表示するネイティブ アクティビティで、ここで使用するサービス ワークフローとクライアント ワークフローの両方で使用されます。ソリューションをビルドして、このアクティビティを **\[ツールボックス\]** の **\[Common\]** セクションで使用できるようにします。  
  
### ワークフロー サービスの実装  
  
1.  `WorkflowService` という新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ワークフロー サービスを `Common` プロジェクトに追加します。そのためには、`Common` プロジェクトを右クリックし、**\[追加\]**、**\[新しい項目\]** の順にクリックします。次に、**\[インストールされているテンプレート\]** で **\[ワークフロー\]** をクリックし、**\[WCF ワークフロー サービス\]** をクリックします。  
  
     ![ワークフロー サービスの追加](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")  
  
2.  既定の `ReceiveRequest` アクティビティと `SendResponse` アクティビティを削除します。  
  
3.  <xref:System.Activities.Statements.WriteLine> アクティビティを `Sequential Service` アクティビティにドラッグ アンド ドロップします。次の例に示すように、Text プロパティを `"Workflow Service starting ..."` に設定します。  
  
     ![WriteLine アクティビティの追加](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")  
  
4.  <xref:System.ServiceModel.Activities.TransactedReceiveScope> を <xref:System.Activities.Statements.WriteLine> アクティビティの後にドラッグ アンド ドロップします。<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティは、**\[ツールボックス\]** の **\[メッセージング\]** セクションにあり、**Request** と **Body** の 2 つのセクションで構成されています。**Request** セクションには、<xref:System.ServiceModel.Activities.Receive> アクティビティが含まれます。**Body** セクションには、メッセージの受信後にトランザクション内で実行されるアクティビティが含まれます。  
  
     ![TransactedReceiveScope アクティビティの追加](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TRS")  
  
5.  <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを選択し、**\[変数\]** をクリックします。次の変数を追加します。  
  
     ![TransactedReceiveScope への変数の追加](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")  
  
    > [!NOTE]
    >  既定で含まれているデータ変数は削除してかまいません。既存のハンドル変数を使用することもできます。  
  
6.  <xref:System.ServiceModel.Activities.Receive> アクティビティを <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティの **Request** セクションにドラッグ アンド ドロップします。次のプロパティを設定します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |CanCreateInstance|True \(チェック ボックスをオンにする\)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     ワークフローは次のようになります。  
  
     ![Receive アクティビティの追加](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")  
  
7.  <xref:System.ServiceModel.Activities.Receive> アクティビティの **\[定義...\]** リンクをクリックし、次の設定を行います。  
  
     ![Recieve アクティビティのメッセージ設定](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")  
  
8.  <xref:System.Activities.Statements.Sequence> アクティビティを <xref:System.ServiceModel.Activities.TransactedReceiveScope> の Body セクションにドラッグ アンド ドロップします。<xref:System.Activities.Statements.Sequence> アクティビティに 2 つの <xref:System.Activities.Statements.WriteLine> アクティビティをドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを次の表のとおりに設定します。  
  
    |アクティビティ|値|  
    |-------------|-------|  
    |1 つ目の WriteLine|“Service: Receive Completed”|  
    |2 つ目の WriteLine|"Service: Received \= " \+ requestMessage|  
  
     ワークフローは次のようになります。  
  
     ![WriteLine アクティビティの追加](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")  
  
9. `PrintTransactionInfo` アクティビティを、<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティの **Body** の 2 つ目の <xref:System.Activities.Statements.WriteLine> アクティビティの後にドラッグ アンド ドロップします。  
  
     ![PrintTransactionInfo の追加後](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")  
  
10. <xref:System.Activities.Statements.Assign> アクティビティを `PrintTransactionInfo` アクティビティの後にドラッグ アンド ドロップし、次の表のとおりにプロパティを設定します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |To|replyMessage|  
    |Value|"Service: Sending reply."|  
  
11. <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Assign> アクティビティの後にドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを "Service: Begin reply" に設定します。  
  
     ワークフローは次のようになります。  
  
     ![Assign および WriteLine の追加後](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")  
  
12. <xref:System.ServiceModel.Activities.Receive> アクティビティを右クリックして **\[SendReply の作成\]** をクリックし、最後の <xref:System.Activities.Statements.WriteLine> アクティビティの後に貼り付けます。`SendReplyToReceive` アクティビティの **\[定義...\]** リンクをクリックし、次の設定を行います。  
  
     ![応答メッセージの設定](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")  
  
13. <xref:System.Activities.Statements.WriteLine> アクティビティを `SendReplyToReceive` アクティビティの後にドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを "Service: Reply sent" に設定します。  
  
14. <xref:System.Activities.Statements.WriteLine> アクティビティをワークフローの末尾にドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを "Service: Workflow ends, press ENTER to exit" に設定します。  
  
     完成したサービス ワークフローは次のようになります。  
  
     ![完全なサービス ワークフロー](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")  
  
### ワークフロー クライアントの実装  
  
1.  `WorkflowClient` という新しい WCF ワークフロー アプリケーションを `Common` プロジェクトに追加します。そのためには、`Common` プロジェクトを右クリックし、**\[追加\]**、**\[新しい項目\]** の順にクリックします。次に、**\[インストールされているテンプレート\]** で **\[ワークフロー\]** をクリックし、**\[アクティビティ\]** をクリックします。  
  
     ![アクティビティ プロジェクトの追加](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")  
  
2.  <xref:System.Activities.Statements.Sequence> アクティビティをデザイン画面にドラッグ アンド ドロップします。  
  
3.  <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを `"Client: Workflow starting"` に設定します。ワークフローは次のようになります。  
  
     ![WriteLine アクティビティを追加する](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")  
  
4.  <xref:System.Activities.Statements.TransactionScope> アクティビティを <xref:System.Activities.Statements.WriteLine> アクティビティの後にドラッグ アンド ドロップします。<xref:System.Activities.Statements.TransactionScope> アクティビティを選択し、\[変数\] をクリックして次の変数を追加します。  
  
     ![TransactionScope への変数の追加](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")  
  
5.  <xref:System.Activities.Statements.Sequence> アクティビティを <xref:System.Activities.Statements.TransactionScope> アクティビティの Body セクションにドラッグ アンド ドロップします。  
  
6.  `PrintTransactionInfo` アクティビティを <xref:System.Activities.Statements.Sequence> アクティビティにドラッグ アンド ドロップします。  
  
7.  <xref:System.Activities.Statements.WriteLine> アクティビティを `PrintTransactionInfo` アクティビティの後にドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを "Client: Beginning Send" に設定します。ワークフローは次のようになります。  
  
     ![アクティビティの追加](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")  
  
8.  <xref:System.ServiceModel.Activities.Send> アクティビティを <xref:System.Activities.Statements.Assign> アクティビティの後にドラッグ アンド ドロップし、次のプロパティを設定します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     ワークフローは次のようになります。  
  
     ![Send アクティビティのプロパティの設定](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")  
  
9. **\[定義...\]** リンクをクリックし、次の設定を行います。  
  
     ![Send アクティビティのメッセージの設定](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")  
  
10. <xref:System.ServiceModel.Activities.Send> アクティビティを右クリックし、**\[ReceiveReply の作成\]** をクリックします。<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティが <xref:System.ServiceModel.Activities.Send> アクティビティの後に自動的に配置されます。  
  
11. ReceiveReplyForSend アクティビティの \[定義\] リンクをクリックし、次の設定を行います。  
  
     ![ReceiveForSend メッセージの設定](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")  
  
12. <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの間にドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを "Client: Send complete" に設定します。  
  
13. <xref:System.Activities.Statements.WriteLine> アクティビティを <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの後にドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを "Client side: Reply received \= " \+ replyMessage に設定します。  
  
14. `PrintTransactionInfo` アクティビティを <xref:System.Activities.Statements.WriteLine> アクティビティの後にドラッグ アンド ドロップします。  
  
15. <xref:System.Activities.Statements.WriteLine> アクティビティをワークフローの末尾にドラッグ アンド ドロップし、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティを "Client workflow ends" に設定します。完成したクライアント ワークフローは次の図のようになります。  
  
     ![完成したクライアント ワークフロー](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")  
  
16. ソリューションをビルドします。  
  
### サービス アプリケーションの作成  
  
1.  `Service` という新しいコンソール アプリケーション プロジェクトをソリューションに追加します。次のアセンブリへの参照を追加します。  
  
    1.  System.Activities.dll  
  
    2.  System.ServiceModel.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
2.  生成された Program.cs ファイルを開き、次のコードを追加します。  
  
    ```  
    static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
  
    ```  
  
3.  次の app.config ファイルをプロジェクトに追加します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
  
    ```  
  
### クライアント アプリケーションの作成  
  
1.  `Client` という新しいコンソール アプリケーション プロジェクトをソリューションに追加します。System.Activities.dll への参照を追加します。  
  
2.  program.cs ファイルを開き、次のコードを追加します。  
  
    ```  
    class Program  
        {  
  
            private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
            static void Main(string[] args)  
            {  
                //Build client  
                Console.WriteLine("Building the client.");  
                WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
                client.Completed = Program.Completed;  
                client.Aborted = Program.Aborted;  
                client.OnUnhandledException = Program.OnUnhandledException;  
  
                //Wait for service to start  
                Console.WriteLine("Press ENTER once service is started.");  
                Console.ReadLine();  
  
                //Start the client              
                Console.WriteLine("Starting the client.");  
                client.Run();  
                syncEvent.WaitOne();  
  
                //Sample complete  
                Console.WriteLine();  
                Console.WriteLine("Client complete. Press ENTER to exit.");  
                Console.ReadLine();  
            }  
  
            private static void Completed(WorkflowApplicationCompletedEventArgs e)  
            {  
                Program.syncEvent.Set();  
            }  
  
            private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
            {  
                Console.WriteLine("Client Aborted: {0}", e.Reason);  
                Program.syncEvent.Set();  
            }  
  
            private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
            {  
                Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
                return UnhandledExceptionAction.Cancel;  
            }  
        }  
  
    ```  
  
## 参照  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [Windows Communication Foundation のトランザクションの概要](../../../../docs/framework/wcf/feature-details/transactions-overview.md)   
 [TransactedReceiveScope の使用](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)