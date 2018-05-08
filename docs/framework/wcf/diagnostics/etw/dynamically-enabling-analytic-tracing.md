---
title: 分析トレースの動的な有効化
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 46dfba2cb148009ddfd0bbd40e3b7202d774e0b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dynamically-enabling-analytic-tracing"></a>分析トレースの動的な有効化
Windows オペレーティング システムに付属のツールでは、ETW (Event Tracing for Windows) を使用して、トレースを動的に有効化または無効化できます。 すべての[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]Windows Communication Foundation (WCF) サービスでは、有効および無効なしで動的には、アプリケーションの Web.config ファイルを変更またはサービスを再起動して、分析トレースを指定できます。 このため、トレース イベントを生成するアプリケーションに影響が生じません。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のトレース オプションも同様に構成できます。 たとえば、アプリケーションに影響を与えずに、重大度レベルを **Error** から **Information** に変更できます。 これは、次のツールで実行できます。  
  
-   **Logman** : トレース データを構成、制御、および照会するためのコマンド ライン ツールです。 詳細については、次を参照してください。 [Logman 作成トレース](http://go.microsoft.com/fwlink/?LinkId=165426)と[Logman Update Trace](http://go.microsoft.com/fwlink/?LinkId=165427)です。  
  
-   **EventViewer** : トレース結果を表示するための、Windows のグラフィカル管理ツールです。 詳細については、次を参照してください。 [WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)と[イベント ビューアー](http://go.microsoft.com/fwlink/?LinkId=165428)です。  
  
-   **Perfmon** : カウンターを使用して、トレース カウンターおよびパフォーマンス トレースの効果を監視する、Windows のグラフィカル管理ツールです。 詳細については、次を参照してください。 [、データ コレクター設定を手動で作成](http://go.microsoft.com/fwlink/?LinkId=165429)です。  
  
### <a name="keywords"></a>キーワード  
 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> クラスを使用するときには、通常、.NET Framework トレース メッセージが重大度レベル (エラー、警告、情報など) でフィルターされます。 ETW は、重大度レベルの概念をサポートしますが、キーワードを使用して、新しい柔軟なフィルター機構も追加されています。 キーワードは任意のテキスト値で、これによって、トレース イベントでそのイベントの意味に関する追加のコンテキストが提供されます。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレースでは、各トレース イベントに 2 種類のキーワードがあります。 まず、各イベントには 1 つ以上のシナリオ キーワードがあります。 これらのキーワードは、そのイベントがサポートするシナリオを示します。 次の表に示すように、特定の目的に対応する 3 つのシナリオ キーワードがあります。 キーワードを使用したフィルター処理は、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスに影響を与えずに動的に変更できます。 このため、現在のトレース シナリオおよび収集するトレース情報の量を動的に変更できます。 たとえば、 `HealthMonitoring` を `Troubleshooting` に変更し、トレース イベントの詳細度を上げることができます。  
  
|キーワード|説明|  
|-------------|-----------------|  
|`HealthMonitoring`|サービスのアクティビティを監視できる、軽量の、最小限のトレース。|  
|`EndToEndMonitoring`|メッセージ フロー トレースのサポートに使用するイベント。|  
|`Troubleshooting`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]の拡張ポイントに関連するより詳細なイベント。|  
  
 キーワードの 2 番目のグループは、 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] のどのコンポーネントがイベントを生成するかを定義します。  
  
|キーワード|説明|  
|-------------|-----------------|  
|`UserEvents`|[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]ではなく、ユーザー コードが生成するイベント。|  
|`ServiceModel`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ランタイムが生成するイベント。|  
|`ServiceHost`|サービス ホストが生成するイベント。|  
|`WCFMessageLogging`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージ ログ イベント。|  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
