---
title: "循環トレース | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 循環トレース
このサンプルでは、循環バッファ トレース リスナの実装を示します。製品版サービスの一般的なシナリオは、長期間使用できるサービスを持つことと、トレース ログを低レベルで有効にすることです。こうしたサービスは、大量のディスク領域を消費します。サービスのトラブルシューティングを行う場合、問題の解決に関連するのはトレース ログの最新データです。このサンプルで示す循環バッファ トレース リスナの実装では、設定可能なデータ量を上限とする最新のトレースのみがディスク上に保持されます。このサンプルは「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいており、カスタム トレース リスナを含んでいます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、「[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)」サンプルを理解し、「[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)」サンプルで取り上げられているドキュメントを読んでいることを前提にしています。  
  
## 循環バッファ トレース リスナ  
 循環バッファ トレース リスナの実装の概念とは、2 つのファイルを使って、必要なトレース ログ データの全体量の半分を上限としたデータをそれぞれに保存することです。リスナは 1 つのファイルを作成して、データ サイズの半分という限界に到達するまでデータを書き込みます。この限界に到達した時点で、2 番目のファイルに切り替わります。2 番目のファイルの限界に到達したら、リスナは最初のファイルを新しいトレースで上書きします。  
  
 このリスナは `XmlWriteTraceListener` から派生し、ログを[サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) で表示できるようにします。ログの表示を試みる際に、サービス トレース ビューア ツールで 2 つのログ ファイルを両方同時に開くと、これらのファイルを簡単に再結合することができます。サービス トレース ビューア ツールは、トレースが正しい順序で表示されるように自動的にトレースの並べ替えを管理します。  
  
## 構成  
 サービスは、リスナとソースの要素に対して次のコードを追加することによって、循環バッファ トレース リスナを使用するように構成できます。ファイルの最大サイズは、循環トレース リスナの構成の `maxFileSizeKB` 属性を設定することによって指定します。このコードを次に示します。  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
  
```  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)