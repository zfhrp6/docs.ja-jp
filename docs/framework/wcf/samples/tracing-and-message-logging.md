---
title: "トレースとメッセージ ログ | Microsoft Docs"
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
  - "トレースとログ"
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: 53
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 53
---
# トレースとメッセージ ログ
このサンプルでは、トレースとメッセージ ログを有効にする方法を示します。結果のトレースとメッセージ ログは、[サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) を使用することによって表示されます。このサンプルは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## トレース  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、<xref:System.Diagnostics> 名前空間で定義されたトレース機構が使用されます。このトレース モデルのトレース データは、アプリケーションが実装するトレース ソースによって作成されます。各ソースは、名前によって識別されます。トレース コンシューマでは、情報を取得するトレース ソースのトレース リスナが作成されます。トレース データを受け取るには、トレース ソースのリスナを作成する必要があります。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でこれを行うには、サービス モデルのトレース ソース `switchValue` を設定することにより、次のコードをサービスまたはクライアントのどちらかの構成ファイルに追加します。  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 トレース ソースの詳細については、「[トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)」トピックの「トレース ソース」セクションを参照してください。  
  
## アクティビティのトレースと伝達  
 クライアントとサービスの両方の `system.ServiceModel` トレース ソースで `ActivityTracing` を有効にして `propagateActivity` を `true` に設定することにより、処理の論理単位 \(アクティビティ\) 内や、エンドポイント内のアクティビティ間 \(アクティビティ転送を使用\)、および複数のエンドポイントにわたるアクティビティ間 \(アクティビティ ID の伝達を使用\) で、トレースを相互に関連付けることができます。  
  
 3 つの機構 \(アクティビティ、転送、および伝達\) により、サービス トレース ビューア ツールを使用してエラーの根本原因をより迅速に見つけることができます。詳細については、「[サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)」を参照してください。  
  
 ユーザー定義のアクティビティ トレースを作成することにより、サービス モデルによって提供されるトレースを拡張することができます。ユーザー定義のアクティビティ トレースによって、次の操作を可能にするトレース アクティビティを作成できます。  
  
-   複数のトレースを作業の論理単位ごとにグループ化します。  
  
-   転送や伝達を利用してアクティビティを相互に関連付けます。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トレースのパフォーマンスの負荷 \(ログ ファイルによるディスク領域の負荷など\) を軽減します。  
  
 ユーザー定義のアクティビティ トレースの詳細については、「[トレースの拡張](../../../../docs/framework/wcf/samples/extending-tracing.md)」のサンプルを参照してください。  
  
## メッセージ ログ  
 メッセージ ログは、任意の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションのクライアントとサービスの両方で有効にできます。メッセージ ログを有効にするには、クライアントとサービスのどちらかに次のコードを追加する必要があります。  
  
```  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels >  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 メッセージが記録されるときのトレースの種類は、そのメッセージがクライアントでトレースされるか、またはサーバーでトレースされるかによって異なります。たとえば、クライアントに送信される "Add" メッセージは、クライアントでは "TransportWrite" カテゴリの下でトレースされるのに対し、サービスでは同じメッセージが "TransportRead" カテゴリの下でトレースされます。  
  
 クライアントの App.config ファイルまたはサービスの Web.config ファイルの <xref:System.Diagnostics> セクションに次のコードを追加して、トレース リスナを構成します。  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 メッセージは、構成ファイルで指定された対象ディレクトリ内に XML 形式で記録されます。  
  
> [!NOTE]
>  最初にログ ディレクトリが作成されていないと、トレース ファイルは作成されません。ディレクトリ C:\\logs\\ が存在することを確認するか、またはリスナの構成でログ記録用の代替ディレクトリを指定します。詳細については、このドキュメントの最後にある初期セットアップ手順を参照してください。  
  
 メッセージ ログの詳細については、トピック「[メッセージ ログの構成](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)」を参照してください。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  トレースとメッセージ ログのサンプルを実行する前に、サービスによって .svclog ファイルが書き込まれるディレクトリ C:\\logs\\ を作成します。このディレクトリ名は、トレースとメッセージがログ記録されるパスとして、構成ファイル内で定義されます。この名前は変更可能です。ユーザー Network Service に、そのログ ディレクトリへの書き込みアクセスを与えます。  
  
3.  ソリューションの C\# 版、C\+\+ 版、または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## 参照  
 [トレース](../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)