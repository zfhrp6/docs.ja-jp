---
title: "分析トレースの動的な有効化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 分析トレースの動的な有効化
Windows オペレーティング システムに付属のツールでは、ETW \(Event Tracing for Windows\) を使用して、トレースを動的に有効化または無効化できます。 すべての [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスについては、アプリケーションの Web.config ファイルを変更したり、サービスを再起動したりせずに、分析トレースを動的に有効化および無効化できます。 このため、トレース イベントを生成するアプリケーションに影響が生じません。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のトレース オプションも同様に構成できます。 たとえば、アプリケーションに影響を与えずに、重大度レベルを **Error** から **Information** に変更できます。 これは、次のツールで実行できます。  
  
-   **Logman**: トレース データを構成、制御、および照会するためのコマンド ライン ツールです。[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][logman create trace](http://go.microsoft.com/fwlink/?LinkId=165426)」と「[logman update trace](http://go.microsoft.com/fwlink/?LinkId=165427)」を参照してください。  
  
-   **EventViewer**: トレース結果を表示するための、Windows のグラフィカル管理ツールです。[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)」および「[イベント ビューアー](http://go.microsoft.com/fwlink/?LinkId=165428)」を参照してください。  
  
-   **Perfmon**: カウンターを使用して、トレース カウンターおよびパフォーマンス トレースの効果を監視する、Windows のグラフィカル管理ツールです。[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][データ コレクター セットを手動で作成する](http://go.microsoft.com/fwlink/?LinkId=165429)」を参照してください。  
  
### キーワード  
 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> クラスを使用するときには、通常、.NET Framework トレース メッセージが重大度レベル \(エラー、警告、情報など\) でフィルターされます。 ETW は、重大度レベルの概念をサポートしますが、キーワードを使用して、新しい柔軟なフィルター機構も追加されています。 キーワードは任意のテキスト値で、これによって、トレース イベントでそのイベントの意味に関する追加のコンテキストが提供されます。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレースでは、各トレース イベントに 2 種類のキーワードがあります。 まず、各イベントには 1 つ以上のシナリオ キーワードがあります。 これらのキーワードは、そのイベントがサポートするシナリオを示します。 次の表に示すように、特定の目的に対応する 3 つのシナリオ キーワードがあります。 キーワードを使用したフィルター処理は、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスに影響を与えずに動的に変更できます。 このため、現在のトレース シナリオおよび収集するトレース情報の量を動的に変更できます。 たとえば、`HealthMonitoring` を `Troubleshooting` に変更し、トレース イベントの詳細度を上げることができます。  
  
|キーワード|説明|  
|-----------|--------|  
|`HealthMonitoring`|サービスのアクティビティを監視できる、軽量の、最小限のトレース。|  
|`EndToEndMonitoring`|メッセージ フロー トレースのサポートに使用するイベント。|  
|`Troubleshooting`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の拡張ポイントに関連するより詳細なイベント。|  
  
 キーワードの 2 番目のグループは、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] のどのコンポーネントがイベントを生成するかを定義します。  
  
|キーワード|説明|  
|-----------|--------|  
|`UserEvents`|[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] ではなく、ユーザー コードが生成するイベント。|  
|`ServiceModel`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ランタイムが生成するイベント。|  
|`ServiceHost`|サービス ホストが生成するイベント。|  
|`WCFMessageLogging`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージ ログ イベント。|  
  
## 参照  
 [WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)