---
title: トレースの拡張
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 685ba85dc240bc2fdefdf02d9ece2279e3507abc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="extending-tracing"></a>トレースの拡張
このサンプルでは、ユーザー定義のアクティビティ トレースをクライアントとサービス コードに記述して、Windows Communication Foundation (WCF) のトレース機能を拡張する方法を示します。 これにより、ユーザーはトレース アクティビティを作成し、トレースを作業の論理単位ごとにグループ化することができます。 さらに、転送 (同じエンドポイント内) や伝達 (異なるエンドポイント間) を経由してアクティビティを相互に関連付けることもできます。 このサンプルでは、トレースはクライアントとサービスの両方で有効です。 クライアントとサービス構成ファイルでトレースを有効にする方法の詳細については、次を参照してください。[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)です。  
  
 このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>トレースとアクティビティの伝達  
 ユーザー定義のアクティビティ トレースにより、ユーザー自身のトレース アクティビティを作成できます。これによって、複数のトレースを作業の論理単位ごとにグループ化したり、転送や伝達を経由してアクティビティを相互に関連付けたり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トレースのパフォーマンスの負荷 (ログ ファイルによるディスク領域の負荷など) を軽減できます。  
  
### <a name="adding-custom-sources"></a>カスタム ソースの追加  
 ユーザー定義のトレースは、クライアントとサービス コードの両方に追加できます。 これらのカスタム トレース記録しに表示するを許可するクライアントまたはサービス構成ファイルにトレース ソースの追加、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)です。 次のコードは、`ServerCalculatorTraceSource` というユーザー定義のトレース ソースを構成ファイルに追加する方法を示します。  
  
```xml  
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
  
### <a name="correlating-activities"></a>アクティビティの相互関連付け  
 エンドポイント間でアクティビティを直接関連付けるには、`propagateActivity` トレース ソースの `true` 属性を `System.ServiceModel` に設定する必要があります。 また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティビティを経由せずにトレースを伝達するには、ServiceModel アクティビティ トレースをオフにする必要があります。 次のコード サンプルを参照してください。  
  
> [!NOTE]
>  ServiceModel アクティビティ トレースをオフにすることは、`switchValue` プロパティが表すトレース レベルをオフにすることとは異なります。  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>パフォーマンスの負荷の軽減  
 `ActivityTracing` トレース ソースの `System.ServiceModel` をオフに設定すると、ユーザー定義のアクティビティ トレースのみを含み、ServiceModel アクティビティ トレースは含まないトレース ファイルが生成されます。 これによって、ログ ファイルのサイズがはるかに小さくなります。 ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 処理トレースを関連付けることはできなくなります。  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
## <a name="see-also"></a>関連項目  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
