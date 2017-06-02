---
title: "クライアントの UI オートメーション イベント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI オートメーション クライアントのイベント"
  - "イベント、UI オートメーション クライアント"
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
caps.latest.revision: 32
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 32
---
# クライアントの UI オートメーション イベント
> [!NOTE]
>  このドキュメントが目的とする、管理を使用する .NET Framework 開発者[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]で定義されたクラス、 <xref:System.Windows.Automation>名前空間。 最新情報について[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックについて説明する方法[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]イベントは、UI オートメーション クライアントによって使用されます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]クライアントは、関心のあるイベントを定期受信できます。 この機能は、すべてをポーリングし続ける必要がある、パフォーマンスを改善、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]すべてについては、構造体、または状態が変更されたかどうか、システム内の要素。  
  
 また、定義されたスコープ内のイベントだけをリッスンできるため、効率性も向上します。 たとえば、クライアントをリッスンできますフォーカス変更イベントをすべて[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーで、または&1; つだけの要素とその子孫の要素。  
  
> [!NOTE]
>  使用できるすべてのイベントを発生すると想定しないで、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]プロバイダー。 たとえば、すべてのプロパティの変更が発生するの標準のプロキシ プロバイダーによって発生させるイベントを[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]コントロールです。  
  
 広い視野の[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]イベントを参照してください[UI オートメーション イベントの概要](../../../docs/framework/ui-automation/ui-automation-events-overview.md)します。  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>イベントのサブスクライブ  
 クライアント アプリケーションは特定の種類のイベントをサブスクライブするために、次のいずれかのメソッドを使用してイベント ハンドラーを登録します。  
  
|メソッド|イベントの種類|イベント引数の種類|デリゲート型|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|フォーカスの変更|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|プロパティの変更|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|構造の変更|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|識別されるその他のすべてのイベント、 <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs>または<xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 メソッドを呼び出す前に、イベントを処理するデリゲート メソッドを作成する必要があります。 必要に応じて、単一のメソッドでさまざまな種類のイベントを処理し、そのメソッドを複数の呼び出しで表中のメソッドの&1; つに渡すことができます。 たとえば、1 つ<xref:System.Windows.Automation.AutomationEventHandler>異なるによると、さまざまなイベントを処理するを設定することができます、 <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>します。  
  
> [!NOTE]
>  ウィンドウを閉じるイベントを処理する、イベント ハンドラーに渡される引数の型をキャスト<xref:System.Windows.Automation.WindowClosedEventArgs>します。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]ウィンドウの要素が無効になって、使用することはできません、`sender`情報を取得するパラメーターを使用して<xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A>代わりにします。  
  
> [!CAUTION]
>  アプリケーションが独自のイベントを受け取った場合[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]、アプリケーションを使用しないでください[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]スレッドまたは登録を解除する、イベントを定期受信します。 使用すると、予期しない動作を招く可能性があります。 詳細については、次を参照してください。 [UI オートメーション スレッド処理の問題](../../../docs/framework/ui-automation/ui-automation-threading-issues.md)します。  
  
 シャット ダウン、または[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]イベントは、アプリケーションにとって重要な不要になった、UI オートメーション クライアントは、次の方法のいずれかを呼び出す必要があります。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|使用して登録されたイベント ハンドラーの登録を解除<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>します。|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|使用して登録されたイベント ハンドラーの登録を解除<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>します。|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|使用して登録されたイベント ハンドラーの登録を解除<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>します。|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|登録済みのすべてのイベント ハンドラーの登録を解除します。|  
  
 コード例は、「 [UI オートメーション イベントをサブスクライブ](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)します。  
  
## <a name="see-also"></a>関連項目  
 [UI オートメーション イベントを購読します。](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)   
 [UI オートメーション イベントの概要](../../../docs/framework/ui-automation/ui-automation-events-overview.md)   
 [UI オートメーション プロパティの概要](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)   
 [TrackFocus サンプル](http://msdn.microsoft.com/ja-jp/4a91c0af-6bb5-4d38-a743-cf136f268fc9)