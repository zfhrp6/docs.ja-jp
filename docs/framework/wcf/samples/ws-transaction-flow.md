---
title: "WS トランザクション フロー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "トランザクション"
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
caps.latest.revision: 43
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 43
---
# WS トランザクション フロー
このサンプルでは、クライアントによって調整されるトランザクションの使用方法と、WS\-AtomicTransaction プロトコルまたは OleTransactions プロトコルを使用するトランザクション フローに関するクライアントとサーバーのオプションの使用方法を示します。  このサンプルは、電卓サービスを実装する[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいていますが、これらの操作は、どの程度のトランザクション フローが可能かを `TransactionFlowAttribute` および **TransactionFlowOption** 列挙体を使用して設定する方法を示すためのものです。  フローされたトランザクションのスコープ内では、要求された操作のログがデータベースに書き込まれ、クライアント調整トランザクションが完了するまで保持されます。クライアント トランザクションが完了しない場合は、データベースに対する該当する更新はコミットされません。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービスとトランザクションへの接続を開始した後で、クライアントは複数のサービス操作にアクセスします。  サービスのコントラクトは次のように定義されています。操作はそれぞれ、`TransactionFlowOption` の設定が異なります。  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
  
```  
  
 操作は、処理される順に次のように定義されています。  
  
-   `Add` \(加算\) 操作要求には、フローされたトランザクションが含まれている必要があります。  
  
-   `Subtract` \(減算\) 操作要求には、フローされたトランザクションが含まれていてもかまいません。  
  
-   `Multiply` \(乗算\) 操作要求には、フローされたトランザクションが含まれてはならないことが、明示的な NotAllowed 設定で指定されています。  
  
-   `Divide` \(除算\) 操作要求には、フローされたトランザクションが含まれてはならないことが、`TransactionFlow` 属性の省略によって指定されています。  
  
 トランザクション フローを有効にするには、適切な操作の属性に加えて、使用するバインディングで [\<transactionFlow\>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) プロパティが有効化されている必要があります。  このサンプルでは、サービスの構成は Metadata Exchange エンドポイントのほかに TCP エンドポイントと HTTP エンドポイントを公開します。  TCP エンドポイントと HTTP エンドポイントは、次のバインディングを使用します。どちらのバインディングでも [\<transactionFlow\>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) プロパティは有効です。  
  
```  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  システムで提供される netTcpBinding では transactionProtocol を指定できるのに対し、システムで提供される wsHttpBinding では、相互運用性に優れた WSAtomicTransactionOctober2004 プロトコルのみが使用されます。  OleTransactions プロトコルは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントで使用する場合にのみ利用できます。  
  
 `ICalculator` インターフェイスを実装するクラスでは、すべてのメソッドの属性で <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティが `true` に設定されています。  この設定は、メソッド内で実行されるすべてのアクションがトランザクションのスコープ内で実行されることを宣言するものです。  この場合、実行されるアクションには、ログ データベースへの記録が含まれます。  操作要求の中に、フローされたトランザクションが含まれている場合は、受信トランザクションのスコープ内でアクションが実行されるか、新しいトランザクションが自動生成されます。  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティは、サービス メソッド実装固有の動作を定義しますが、トランザクションをフローさせるためのクライアントの機能や要件は定義しません。  
  
```  
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```  
  
 クライアントでは、操作に対するサービスの `TransactionFlowOption` 設定が、クライアントで生成される `ICalculator` インターフェイスの定義に反映されます。  さらに、サービスの `transactionFlow` プロパティの設定はクライアントのアプリケーション構成に反映されます。  クライアントでは、適切な `endpointConfigurationName` を選択することによってトランスポートとプロトコルを選択できます。  
  
```  
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
  
```  
  
> [!NOTE]
>  このサンプルを実行したときの動作は、選択したプロトコルとトランスポートの種類にかかわらず同一です。  
  
 サービスへの接続を開始した後で、クライアントは次のように、サービス操作の呼び出しを囲む新しい `TransactionScope` を作成します。  
  
```  
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
```  
  
 操作の呼び出しは次のとおりです。  
  
-   `Add` 要求によって、必須のトランザクションがサービスにフローされ、サービスのアクションはクライアントのトランザクション スコープ内で実行されます。  
  
-   最初の `Subtract` 要求も、許可されたトランザクションをサービスにフローするので、このときもサービスのアクションはクライアントのトランザクション スコープ内で実行されます。  
  
-   2 番目の `Subtract` 要求は、`TransactionScopeOption.Suppress` オプションと共に宣言された新しいトランザクション スコープ内で実行されます。  これによって、クライアントの最初の外側トランザクションが抑制されます。また、新しいトランザクションがサービスにフローされることはありません。  この方法を使用すると、クライアントは、トランザクションをサービスにフローすることが必要ない場合に、このことを行わないように明示的に指定できます。  サービスのアクションは、新しい独立したトランザクションのスコープ内で発生します。  
  
-   `Multiply` 要求はトランザクションをサービスにフローしません。クライアントで生成された `ICalculator` インターフェイスの定義には <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed` に設定された <xref:System.ServiceModel.TransactionFlowAttribute> が含まれているためです。  
  
-   `Divide` 要求は、トランザクションをサービスにフローしません。同様に、クライアントで生成された `ICalculator` インターフェイスの定義には `TransactionFlowAttribute` が含まれていないためです。  このときも、サービスのアクションは別の新しい独立したトランザクションのスコープ内で実行されます。  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。  クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 サービス操作要求のログ記録は、サービスのコンソール ウィンドウに表示されます。  クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 実行が正常に終了すると、クライアントのトランザクション スコープが完了し、そのスコープ内で実行されたすべてのアクションがコミットされます。  具体的には、ここに示した 5 レコードがサービスのデータベースに保存されます。  最初の 2 レコードは、クライアントのトランザクションのスコープ内で発生しています。  
  
 クライアントの `TransactionScope` 内の場所で例外が発生した場合、トランザクションは完了しません。  その結果、そのスコープ内でログに記録されたレコードはデータベースにコミットされなくなります。  この影響を確認するには、外側の `TransactionScope` を完了させる呼び出しをコメント化した後にサンプルをもう一度実行します。  この実行では、最後の 3 つのアクション \(2 番目の `Subtract` 要求、`Multiply` 要求、`Divide` 要求\) だけがログに記録されます。クライアント トランザクションはこれらのアクションにフローしないためです。  
  
### サンプルをセットアップ、ビルド、および実行するには  
  
1.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
2.  SQL Server Express Edition または SQL Server がインストールされ、接続文字列が、サービスのアプリケーション構成ファイルで正しく設定されていることを確認します。  データベースを使用せずにサンプルを実行するには、サービスのアプリケーション構成ファイルで `usingSql` の値を `false` に設定します。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
    > [!NOTE]
    >  複数コンピューター構成の場合は、次の説明に従って分散トランザクション コーディネーターを有効にし、Windows SDK の WsatConfig.exe ツールを使用して WCF トランザクション ネットワークのサポートを有効にします。  WsatConfig.exe のセットアップの詳細については、「[WS\-AtomicTransaction サポートの構成](http://go.microsoft.com/fwlink/?LinkId=190370)」を参照してください。  
  
 サンプルを同じコンピューターまたは複数のコンピューターのどちらで実行する場合も、Microsoft 分散トランザクション コーディネーター \(MSDTC\) を構成してネットワーク トランザクション フローを有効にし、WsatConfig.exe ツールを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トランザクション ネットワーク サポートを有効にする必要があります。  
  
### Microsoft 分散トランザクション コーディネーター \(MSDTC\) を構成してサンプルを実行できるようにするには  
  
1.  Windows Server 2003 または Windows XP が動作するサービス コンピューターで、次の説明に従い、受信ネットワーク トランザクションを許可するよう MSDTC を構成します。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[コントロール パネル\]**、**\[管理ツール\]** の順にポイントして **\[コンポーネント サービス\]** をクリックします。  
  
    2.  **\[コンポーネント サービス\]** を展開します。  **\[コンピューター\]** フォルダーを開きます。  
  
    3.  **\[マイ コンピューター\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
    4.  **\[MSDTC\]** タブの **\[セキュリティの構成\]** をクリックします。  
  
    5.  **\[ネットワーク DTC アクセス\]** および **\[受信を許可する\]** のチェック ボックスをオンにします。  
  
    6.  **\[OK\]** をクリックし、**\[はい\]** をクリックして、MSDTC サービスを再起動します。  
  
    7.  **\[OK\]** をクリックし、ダイアログ ボックスを閉じます。  
  
2.  Windows Server 2008 または Windows Vista が動作するサービス コンピューターで、次の説明に従い、受信ネットワーク トランザクションを許可するよう MSDTC を構成します。  
  
    1.  **\[スタート\]** ボタンをクリックし、**\[コントロール パネル\]**、**\[管理ツール\]** の順にポイントして **\[コンポーネント サービス\]** をクリックします。  
  
    2.  **\[コンポーネント サービス\]** を展開します。  **\[コンピューター\]** フォルダーを開きます。  **\[分散トランザクション コーディネーター\]** をクリックします。  
  
    3.  **\[DTC コーディネーター\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
    4.  **\[セキュリティ\]** タブで、**\[ネットワーク DTC アクセス\]** チェックボックスと **\[受信を許可する\]** チェック ボックスをオンにします。  
  
    5.  **\[OK\]** をクリックし、**\[はい\]** をクリックして、MSDTC サービスを再起動します。  
  
    6.  **\[OK\]** をクリックし、ダイアログ ボックスを閉じます。  
  
3.  クライアント コンピューターで、送信ネットワーク トランザクションを許可するよう MSDTC を構成します。  
  
    1.  **\[スタート\]** メニューから`Control Panel`に移動し、**\[管理ツール\]**、**\[コンポーネント サービス\]** の順に選択します。  
  
    2.  **\[マイ コンピューター\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
    3.  **\[MSDTC\]** タブの **\[セキュリティの構成\]** をクリックします。  
  
    4.  **\[ネットワーク DTC アクセス\]** および **\[送信を許可する\]** のチェック ボックスをオンにします。  
  
    5.  **\[OK\]** をクリックし、**\[はい\]** をクリックして、MSDTC サービスを再起動します。  
  
    6.  **\[OK\]** をクリックし、ダイアログ ボックスを閉じます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`