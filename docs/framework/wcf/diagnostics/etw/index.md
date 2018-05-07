---
title: ETW を使用した分析トレース
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: a0e3e3d27283e588b161e2209c5a682558d18f79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="analytic-tracing-with-etw"></a>ETW を使用した分析トレース
Windows Communication Foundation (WCF) の分析トレースの実行中に診断情報をキャプチャする方法を提供する、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サービス。 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] スタック内のキー ポイントで [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレース イベントが生成され、運用環境での [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスのトラブルシューティングが可能になります。 分析トレースは[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サービスには影響を最小限製品のサーバーのパフォーマンスにホストする[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services のようにこれらのイベントはイベント トレース for Windows (ETW) セッションに非常に効率よく生成されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [分析トレースの概要](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレースが [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] でどのように機能するかについて説明します。  
  
 [分析トレースの動的な有効化](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 ETW を使用してトレースを動的に有効化または無効化する方法について説明します。  
  
 [メッセージ フローのトレースの構成](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 メッセージ フローのトレースを構成する方法について説明します。  
  
 [分析トレース イベント リファレンス](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 イベント ID とそれらのイベント レベル、イベント メッセージ、およびキーワードを表で示します。  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Windows のイベント トレースへの追跡イベント](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
