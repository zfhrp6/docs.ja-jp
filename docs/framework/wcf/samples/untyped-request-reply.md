---
title: "型指定されていない要求/応答"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45e68bd28a4ab5a0e7425bf06b02b8c3d3d25311
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="untyped-requestreply"></a>型指定のない要求/応答
このサンプルは、Message クラスを使用する操作コントラクトを定義する方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。 サービス コントラクトは、メッセージの種類を引数として取得してメッセージを返すという 1 つの操作を定義します。 この操作は、合計の計算に必要なすべてのデータをメッセージ本文から収集し、その合計を返信メッセージの本文に格納して返送します。  
  
```  
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 サービスでは、操作によって入力メッセージ内で渡された整数の配列が取得され、その合計が計算されます。 応答メッセージの送信では、サンプルは適切なメッセージ バージョンと Action を含む新しいメッセージを作成し、計算された合計をメッセージ本文に追加します。 これを実行するサンプル コードを次に示します。  
  
```  
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be   
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,   
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 クライアントによって生成されるコードを使用して[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)リモート サービスにプロキシを作成します。 要求メッセージを送信するには、クライアントにメッセージ バージョンが存在する必要があります。これは基になるチャネルによって異なります。 したがって、クライアントは、作成済みのプロキシ チャネルに適用される新しい <xref:System.ServiceModel.OperationContextScope> を作成し、これが、<xref:System.ServiceModel.OperationContext> プロパティで設定されている正しいメッセージ バージョンにより、`OutgoingMessageHeaders.MessageVersion` を作成します。 クライアントは入力配列を本文として要求メッセージに渡し、プロキシの `ComputeSum` を呼び出します。 次にクライアントは、応答メッセージの `GetBody<T>` メソッドにアクセスし、渡した入力の合計を取得します。 これを実行するサンプル コードを次に示します。  
  
```  
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,   
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",   
                                                       response);  
}  
```  
  
 このサンプルは Web ホストのサンプルです。したがって、クライアント実行可能ファイルのみを実行する必要があります。 クライアントでの出力のサンプルを次に示します。  
  
```  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 このサンプルは Web ホストのサンプルです。したがって、手順 3. で示したリンクを確認し、サンプルのビルド方法と実行方法を確認してください。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>関連項目
