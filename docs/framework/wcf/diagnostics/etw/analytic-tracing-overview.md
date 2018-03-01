---
title: "分析トレースの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3492821d56f7089c2aa53bba566690ded02f8a5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-overview"></a>分析トレースの概要
[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] の分析トレースは、Event Tracing for Windows (ETW) を基盤とするトレース機能のセットです。詳細度は低いのですが、パフォーマンスに優れています。 ETW は、カーネル レベルで実行され、トレース操作のオーバーヘッドを大幅に削減します。 ユーザー モードおよびカーネル モードのイベントを効率よくバッファーし、サービスの再起動を必要とすることなく、動的にログを有効化できます。 トレース データは、生成および受信されると、イベント ログから確認できます。  
  
 ETW の[!INCLUDE[crabout](../../../../../includes/crabout-md.md)] については、「 [ETW によりデバッグおよびパフォーマンス調整を改善する](http://go.microsoft.com/fwlink/?LinkId=164781)」を参照してください。  
  
 Windows のシステム、セキュリティ、およびアプリケーション イベント ログによるアプリケーションの分析のほかに、 [!INCLUDE[wv](../../../../../includes/wv-md.md)] および [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] では、最上位ノードの [アプリケーションとサービス ログ] の下にログが追加されています。 これらの新しいログは、システム全体に影響するグローバルなイベント (セキュリティ イベント ログで記録されるようなイベントなど) ではなく、特定のアプリケーションやコンポーネントのイベントを格納することを目的としています。 [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] では、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース イベント、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージ ログ、および [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] 追跡レコードのログを [アプリケーションとサービス ログ] にまとめ、相互に関連付けています。  
  
## <a name="concepts-and-capabilities"></a>概念と機能  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析トレースには、次の概念と機能があります。  
  
### <a name="enabling-wcf-diagnostics-settings"></a>WCF 診断設定の有効化  
 内で WCF の診断が有効になっている、 \<system.serviceModel >\<診断 > 構成セクション。  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Web でホストされる IIS 仮想アプリケーションの WCF 診断の設定は、アプリケーションの Web.config ファイルで有効にします。 または、アプリケーション内のサブディレクトリに Web.config を作成することもできます。  この方法では、設定がサブディレクトリ内のすべてのサービスに適用されます。  診断設定が、アプリケーション内のすべてのサービスに対して一貫して初期化されるようにするには、これらの設定を、アプリケーション内の個別のサブディレクトリの 1 つではなく、アプリケーション ディレクトリ内の Web.config に含める必要があります。  
  
### <a name="channels"></a>チャネル  
 ETW の場合、ソフトウェア コンポーネントは、チャネルを使用することで、トレース イベントをユーザーの種類に応じて振り分けることができます。 たとえば、システム管理者向けのイベントを 1 つのチャネルに送信し、アプリケーション開発者にとって重要なイベントを別のチャネルに送信できます。 チャネルには名前が付けられ、Windows に登録されるので、ユーザーは、特定のチャネルのイベントをイベント ビューアーを使用して確認できます。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] の分析トレース機能は、Microsoft-Windows-Application-Server-Applications チャネルに書き込みます。 このチャネルは、特に、運用中の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの状態を監視する必要があるユーザー向けに設計されています。 このチャネルでは、さまざまな状態監視およびトラブルシューティング シナリオで使用できるイベントがいくつか定義されています。  
  
 メッセージがイベント ログで正常にデコードされるように Event Tracing for Windows マニファストを有効にするために、次のようにコマンド ラインで ServiceModelReg ツールを使用します。  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>動的構成  
 ETW のインフラストラクチャでは、標準の Windows ツールを使用して動的にトレースを有効化および構成できます。 [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][分析トレースを動的に有効にする](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)です。  
  
### <a name="message-flow-tracing"></a>メッセージ フローのトレース  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] については、「 [Configuring Message Flow Tracing](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)」を参照してください。  
  
### <a name="keywords"></a>キーワード  
 キーワードは、トレース メッセージをフィルター処理するため、およびイベントを生成した [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] コンポーネントを定義するために使用されます。 [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][分析トレースを動的に有効にする](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)です。
