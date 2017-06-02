---
title: "Analytic Tracing with ETW | Microsoft Docs"
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
  - "diagnostics [WCF], analytic tracing"
  - "administration [WCF], analytic tracing"
  - "analytic tracing [WCF]"
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Analytic Tracing with ETW
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] の分析トレースでは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの実行中に診断情報をキャプチャする手段が提供されます。[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] スタック内のキー ポイントで [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレース イベントが生成され、運用環境での [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスのトラブルシューティングが可能になります。[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの分析トレースは、[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスをホストする運用サーバーのパフォーマンスに最小限の影響しか与えません。これは、これらのイベントが効率的に ETW \(Event Tracing for Windows\) セッションに送出されるためです。  
  
## このセクションの内容  
 [分析トレースの概要](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレースが [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] でどのように機能するかについて説明します。  
  
 [分析トレースの動的な有効化](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 ETW を使用してトレースを動的に有効化または無効化する方法について説明します。  
  
 [メッセージ フローのトレースの構成](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 メッセージ フローのトレースを構成する方法について説明します。  
  
 [分析トレース イベント リファレンス](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 イベント ID とそれらのイベント レベル、イベント メッセージ、およびキーワードを表で示します。  
  
## 参照  
 [WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)   
 [Windows のイベント トレースへの追跡イベント](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)