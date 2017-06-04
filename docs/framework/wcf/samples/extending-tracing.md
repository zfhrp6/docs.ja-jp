---
title: "トレースの拡張 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# トレースの拡張
このサンプルでは、ユーザー定義のアクティビティ トレースをクライアントとサービス コードに記述することにより、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] トレース機能を拡張する方法を示します。これにより、ユーザーはトレース アクティビティを作成し、トレースを作業の論理単位ごとにグループ化することができます。さらに、転送 \(同じエンドポイント内\) や伝達 \(異なるエンドポイント間\) を経由してアクティビティを相互に関連付けることもできます。このサンプルでは、トレースはクライアントとサービスの両方で有効です。クライアントとサービスの構成ファイル内でトレースを有効にする方法の詳細については、「[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)」を参照してください。  
  
 このサンプルは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## トレースとアクティビティの伝達  
 ユーザー定義のアクティビティ トレースにより、ユーザー自身のトレース アクティビティを作成できます。これによって、複数のトレースを作業の論理単位ごとにグループ化したり、転送や伝達を経由してアクティビティを相互に関連付けたり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トレースのパフォーマンスの負荷 \(ログ ファイルによるディスク領域の負荷など\) を軽減できます。  
  
### カスタム ソースの追加  
 ユーザー定義のトレースは、クライアントとサービス コードの両方に追加できます。トレース ソースをクライアントまたはサービスの構成ファイルに追加すると、カスタム トレースを[サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)に記録および表示できます。次のコードは、`ServerCalculatorTraceSource` というユーザー定義のトレース ソースを構成ファイルに追加する方法を示します。  
  
```  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### アクティビティの相互関連付け  
 エンドポイント間でアクティビティを直接関連付けるには、`System.ServiceModel` トレース ソースの `propagateActivity` 属性を `true` に設定する必要があります。また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティビティを経由せずにトレースを伝達するには、ServiceModel アクティビティ トレースをオフにする必要があります。次のコード サンプルを参照してください。  
  
> [!NOTE]
>  ServiceModel アクティビティ トレースをオフにすることは、`switchValue` プロパティが表すトレース レベルをオフにすることとは異なります。  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### パフォーマンスの負荷の軽減  
 `System.ServiceModel` トレース ソースの `ActivityTracing` をオフに設定すると、ユーザー定義のアクティビティ トレースのみを含み、ServiceModel アクティビティ トレースは含まないトレース ファイルが生成されます。これによって、ログ ファイルのサイズがはるかに小さくなります。ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 処理トレースを関連付けることはできなくなります。  
  
##### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)