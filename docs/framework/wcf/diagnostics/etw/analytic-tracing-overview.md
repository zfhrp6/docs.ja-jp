---
title: "分析トレースの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析トレース [WCF], 概要"
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# 分析トレースの概要
[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] の分析トレースは、Event Tracing for Windows \(ETW\) を基盤とするトレース機能のセットです。詳細度は低いのですが、パフォーマンスに優れています。 ETW は、カーネル レベルで実行され、トレース操作のオーバーヘッドを大幅に削減します。 ユーザー モードおよびカーネル モードのイベントを効率よくバッファーし、サービスの再起動を必要とすることなく、動的にログを有効化できます。 トレース データは、生成および受信されると、イベント ログから確認できます。  
  
 ETW の[!INCLUDE[crabout](../../../../../includes/crabout-md.md)]については、「[ETW によりデバッグおよびパフォーマンス調整を改善する](http://go.microsoft.com/fwlink/?LinkId=164781)」を参照してください。  
  
 Windows のシステム、セキュリティ、およびアプリケーション イベント ログによるアプリケーションの分析のほかに、[!INCLUDE[wv](../../../../../includes/wv-md.md)] および [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] では、最上位ノードの \[アプリケーションとサービス ログ\] の下にログが追加されています。 これらの新しいログは、システム全体に影響するグローバルなイベント \(セキュリティ イベント ログで記録されるようなイベントなど\) ではなく、特定のアプリケーションやコンポーネントのイベントを格納することを目的としています。[!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] では、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース イベント、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージ ログ、および [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] 追跡レコードのログを \[アプリケーションとサービス ログ\] にまとめ、相互に関連付けています。  
  
## 概念と機能  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析トレースには、次の概念と機能があります。  
  
### WCF 診断設定の有効化  
 WCF の診断は、\<system.serviceModel\>\<\>diagnostics 構成セクション内で有効にします。  
  
```  
  
<system.serviceModel>  
  <diagnostics>  
  
```  
  
 Web でホストされる IIS 仮想アプリケーションの WCF 診断の設定は、アプリケーションの Web.config ファイルで有効にします。 または、アプリケーション内のサブディレクトリに Web.config を作成することもできます。  この方法では、設定がサブディレクトリ内のすべてのサービスに適用されます。  診断設定が、アプリケーション内のすべてのサービスに対して一貫して初期化されるようにするには、これらの設定を、アプリケーション内の個別のサブディレクトリの 1 つではなく、アプリケーション ディレクトリ内の Web.config に含める必要があります。  
  
### チャネル  
 ETW の場合、ソフトウェア コンポーネントは、チャネルを使用することで、トレース イベントをユーザーの種類に応じて振り分けることができます。 たとえば、システム管理者向けのイベントを 1 つのチャネルに送信し、アプリケーション開発者にとって重要なイベントを別のチャネルに送信できます。 チャネルには名前が付けられ、Windows に登録されるので、ユーザーは、特定のチャネルのイベントをイベント ビューアーを使用して確認できます。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] の分析トレース機能は、Microsoft\-Windows\-Application\-Server\-Applications チャネルに書き込みます。 このチャネルは、特に、運用中の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの状態を監視する必要があるユーザー向けに設計されています。 このチャネルでは、さまざまな状態監視およびトラブルシューティング シナリオで使用できるイベントがいくつか定義されています。  
  
 メッセージがイベント ログで正常にデコードされるように Event Tracing for Windows マニファストを有効にするために、次のようにコマンド ラインで ServiceModelReg ツールを使用します。  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### 動的構成  
 ETW のインフラストラクチャでは、標準の Windows ツールを使用して動的にトレースを有効化および構成できます。[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][分析トレースの動的な有効化](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### メッセージ フローのトレース  
 メッセージ フローのトレースを有効にする方法の[!INCLUDE[crabout](../../../../../includes/crabout-md.md)]については、「[メッセージ フローのトレースの構成](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)」を参照してください。  
  
### キーワード  
 キーワードは、トレース メッセージをフィルター処理するため、およびイベントを生成した [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] コンポーネントを定義するために使用されます。[!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [分析トレースの動的な有効化](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)。