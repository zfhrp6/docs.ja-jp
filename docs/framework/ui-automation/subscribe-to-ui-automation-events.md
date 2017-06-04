---
title: "UI オートメーション イベントのサブスクライブ | Microsoft Docs"
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
  - "UI オートメーション、イベントにサブスクライブします。"
  - "サブスクライブ (UI オートメーション イベントを)"
  - "イベントをサブスクライブするには"
  - "リッスン (イベントを)"
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
caps.latest.revision: 16
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 16
---
# UI オートメーション イベントのサブスクライブ
> [!NOTE]
>  このドキュメントが目的とする、管理を使用する .NET Framework 開発者[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]で定義されたクラス、 <xref:System.Windows.Automation>名前空間。 最新情報について[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、UI オートメーション プロバイダーによって生成されるイベントをサブスクライブする方法について説明します。  
  
## <a name="example"></a>例  
 次のコード例では、ボタンなどのコントロールが呼び出された場合に生成されるイベントに対してイベント ハンドラーを登録し、アプリケーション フォームが閉じられた時にそのイベント ハンドラーを削除します。 イベントがで識別される、 <xref:System.Windows.Automation.AutomationEvent>をパラメーターとして渡された<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>します。  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示しています。[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]フォーカスが変更されたときに発生するイベントを定期受信します。 イベント ハンドラーの登録は、アプリケーションのシャットダウン時に呼び出されるメソッドで解除されるか、UI イベントの通知が必要なくなった時に解除されます。  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>   
 <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>   
 <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>   
 [UI オートメーション イベントの概要](../../../docs/framework/ui-automation/ui-automation-events-overview.md)