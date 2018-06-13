---
title: ETW を使用した分析トレース
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 210418b8a8765a1fc59658e9df57c92ce087c95f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809265"
---
# <a name="analytic-tracing-with-etw"></a>ETW を使用した分析トレース
Windows Communication Foundation (WCF) の分析トレースは、WCF サービスの実行中に診断情報をキャプチャする手段を提供します。 WCF 分析トレース イベントは、運用環境で WCF サービスのトラブルシューティングが可能に WCF スタック内のキー_ポイントで出力されます。 WCF サービスの分析トレースは最小限に影響を及ぼします製品のサーバーのパフォーマンスをホストする[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]WCF サービスのようにこれらのイベントはイベント トレース for Windows (ETW) セッションに非常に効率よく生成されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [分析トレースの概要](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 WCF 分析トレースがでどのように動作するかについて説明[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]です。  
  
 [分析トレースの動的な有効化](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 ETW を使用してトレースを動的に有効化または無効化する方法について説明します。  
  
 [メッセージ フローのトレースの構成](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 メッセージ フローのトレースを構成する方法について説明します。  
  
 [分析トレース イベント リファレンス](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 イベント ID とそれらのイベント レベル、イベント メッセージ、およびキーワードを表で示します。  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Windows のイベント トレースへの追跡イベント](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
