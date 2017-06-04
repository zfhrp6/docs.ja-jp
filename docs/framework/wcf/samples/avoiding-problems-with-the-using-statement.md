---
title: "Using ステートメントに関する問題の回避 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Using ステートメントに関する問題の回避
このサンプルでは、型指定のあるクライアントを使用する際に C\# の "using" ステートメントを使用せずに、リソースを自動的にクリーンアップする方法を示します。このサンプルは、電卓サービスを実装する「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。この例では、クライアントはコンソール アプリケーション \(.exe\) で、サービスはインターネット インフォメーション サービス \(IIS\) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、C\# の "using" ステートメントを型指定のあるクライアントと共に使用する際に発生する 2 つの一般的な問題と、例外が発生した後に正しくクリーンアップするコードを示します。  
  
 C\# の "using" ステートメントにより `Dispose`\(\) が呼び出されます。これは `Close`\(\) と同じで、ネットワーク エラーが発生したときに例外をスローする場合があります。`Dispose`\(\) への呼び出しは、"using" ブロックの閉じかっこで暗黙的に発生するので、コードを記述するユーザーとコードを読み取るユーザーの両者が、これを例外の発生元と気付かない可能性があります。これは、アプリケーション エラーの潜在的な原因となります。  
  
 最初の問題は、次の `DemonstrateProblemUsingCanThrow` メソッドに示すように、閉じかっこで例外がスローされるとその後のコードが実行されないことです。  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 using ブロック内部からスローされる例外がない場合、または using ブロック内のすべての例外がキャッチされた場合でも、`Console.Writeline` は発生しません。閉じかっこでの `Dispose`\(\) の暗黙の呼び出しによって例外がスローされるためです。  
  
 2 番目の問題は、次の `DemonstrateProblemUsingCanThrowAndMask` メソッドで示すように、閉じかっこで別の例外が暗黙的にスローされる点です。  
  
```  
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 `Dispose`\(\) は "最後の" ブロック内で発生するので、`Dispose`\(\) が失敗した場合、`ApplicationException` は using ブロックの外側には表示されません。外側のコードで、`ApplicationException` の発生時期を認識できるよう考慮されている場合は、この例外をマスクすると、"using" コンストラクトが問題の原因となる場合があります。  
  
 最後に、このサンプルでは、`DemonstrateCleanupWithExceptions` で例外が発生した場合に正しくクリーンアップする方法を示します。ここでは、try\/catch ブロックを使用してエラーを報告し、`Abort` を呼び出します。クライアントの呼び出しから例外をキャッチする方法の詳細については、「[予期される例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)」のサンプルを参照してください。  
  
```  
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  using ステートメントと ServiceHost: 多くの自己ホスト アプリケーションでは、サービスをホストする以外の処理はほとんど行われず、ServiceHost.Close から例外がスローされることはほとんどありません。したがって、このようなアプリケーションでは、using ステートメントを ServiceHost と共に使用しても安全です。ただし、ServiceHost.Close では `CommunicationException` がスローされる場合があることに注意してください。したがって、ServiceHost を閉じた後でアプリケーションを続行する場合は、using ステートメントを使用せずに前のパターンに従う必要があります。  
  
 このサンプルを実行すると、操作応答と例外がクライアントのコンソール ウィンドウに表示されます。  
  
 クライアント プロセスでは 3 つのシナリオが実行されます。各シナリオでは `Divide` の呼び出しが試行されます。最初のシナリオでは、`Dispose`\(\) からの例外のためにスキップされるコードを示します。2 番目のシナリオでは、`Dispose`\(\) からの例外のためにマスクされる重要な例外を示します。3 番目のシナリオでは、正しいクリーンアップを示します。  
  
 クライアント プロセスから予期される出力は次のとおりです。  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
  
```  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## 参照