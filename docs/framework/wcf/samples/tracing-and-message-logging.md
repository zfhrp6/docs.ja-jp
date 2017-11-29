---
title: "トレースとメッセージ ログ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: "53"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a73c6e544b7aae003a525c29743d68db18a54515
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tracing-and-message-logging"></a>トレースとメッセージ ログ
このサンプルでは、トレースとメッセージ ログを有効にする方法を示します。 結果のトレースとメッセージ ログを使用して表示、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)です。 このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## <a name="tracing"></a>トレース  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、<xref:System.Diagnostics> 名前空間で定義されたトレース機構が使用されます。 このトレース モデルのトレース データは、アプリケーションが実装するトレース ソースによって作成されます。 各ソースは、名前によって識別されます。 トレース コンシューマでは、情報を取得するトレース ソースのトレース リスナが作成されます。 トレース データを受け取るには、トレース ソースのリスナを作成する必要があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でこれを行うには、サービス モデルのトレース ソース `switchValue` を設定することにより、次のコードをサービスまたはクライアントのどちらかの構成ファイルに追加します。  
  
```xml  
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
  
 トレース ソースの詳細については、トレース ソースのセクションを参照してください、[トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)トピックです。  
  
## <a name="activity-tracing-and-propagation"></a>アクティビティのトレースと伝達  
 持つ`ActivityTracing`有効になっていると`propagateActivity`'éý'`true`で、`system.ServiceModel`トレース ソースに、クライアントとサービスの両方のエンドポイント (内のアクティビティ間 (アクティビティ) の処理の論理単位内のトレースの相関関係を提供します。アクティビティ転送を使用)、および複数のエンドポイント (アクティビティ ID の伝達) にわたるアクティビティ間です。  
  
 3 つの機構 (アクティビティ、転送、および伝達) により、サービス トレース ビューア ツールを使用してエラーの根本原因をより迅速に見つけることができます。 詳細については、次を参照してください。[相関トレースの表示とトラブルシューティング サービス トレース ビューアーを使用して](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)です。  
  
 ユーザー定義のアクティビティ トレースを作成することにより、サービス モデルによって提供されるトレースを拡張することができます。 ユーザー定義のアクティビティ トレースによって、次の操作を可能にするトレース アクティビティを作成できます。  
  
-   複数のトレースを作業の論理単位ごとにグループ化します。  
  
-   転送や伝達を利用してアクティビティを相互に関連付けます。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トレースのパフォーマンスの負荷 (ログ ファイルによるディスク領域の負荷など) を軽減します。  
  
 ユーザー定義のアクティビティ トレースの詳細についてを参照してください、[トレースを拡張する](../../../../docs/framework/wcf/samples/extending-tracing.md)サンプルです。  
  
## <a name="message-logging"></a>メッセージ ログ  
 メッセージ ログは、任意の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションのクライアントとサービスの両方で有効にできます。 メッセージ ログを有効にするには、クライアントとサービスのどちらかに次のコードを追加する必要があります。  
  
```xml  
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
  
 メッセージが記録されるときのトレースの種類は、そのメッセージがクライアントでトレースされるか、またはサーバーでトレースされるかによって異なります。 たとえば、クライアントに送信される "Add" メッセージは、クライアントでは "TransportWrite" カテゴリの下でトレースされるのに対し、サービスでは同じメッセージが "TransportRead" カテゴリの下でトレースされます。  
  
 クライアントの App.config ファイルまたはサービスの Web.config ファイルの <xref:System.Diagnostics> セクションに次のコードを追加して、トレース リスナを構成します。  
  
```xml  
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
>  最初にログ ディレクトリが作成されていないと、トレース ファイルは作成されません。 ディレクトリ C:\logs\ が存在することを確認するか、またはリスナの構成でログ記録用の代替ディレクトリを指定します。 詳細については、このドキュメントの最後にある初期セットアップ手順を参照してください。  
  
 メッセージのログ記録の詳細については、次を参照してください。、[メッセージ ログの構成](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)トピックです。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  トレースとメッセージ ログのサンプルを実行する前に、サービスによって .svclog ファイルが書き込まれるディレクトリ C:\logs\ を作成します。 このディレクトリ名は、トレースとメッセージがログ記録されるパスとして、構成ファイル内で定義されます。この名前は変更可能です。 ユーザー Network Service に、そのログ ディレクトリへの書き込みアクセスを与えます。  
  
3.  C#、C++、または Visual Basic .NET のバージョンのソリューションをビルドするの指示に従って、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
4.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>関連項目  
 [トレース](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
