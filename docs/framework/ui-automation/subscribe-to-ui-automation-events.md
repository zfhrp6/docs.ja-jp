---
title: "UI オートメーション イベントのサブスクライブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 39275c38e4a7d28248b46f1116990c5bbe21a15f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="a3e63-102">UI オートメーション イベントのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="a3e63-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
>  <span data-ttu-id="a3e63-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="a3e63-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a3e63-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3e63-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a3e63-105">このトピックでは、UI オートメーション プロバイダーによって生成されるイベントをサブスクライブする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3e63-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3e63-106">例</span><span class="sxs-lookup"><span data-stu-id="a3e63-106">Example</span></span>  
 <span data-ttu-id="a3e63-107">次のコード例では、ボタンなどのコントロールが呼び出された場合に生成されるイベントに対してイベント ハンドラーを登録し、アプリケーション フォームが閉じられた時にそのイベント ハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="a3e63-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="a3e63-108">イベントを識別、<xref:System.Windows.Automation.AutomationEvent>へのパラメーターとして渡される<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>です。</span><span class="sxs-lookup"><span data-stu-id="a3e63-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="a3e63-109">例</span><span class="sxs-lookup"><span data-stu-id="a3e63-109">Example</span></span>  
 <span data-ttu-id="a3e63-110">次の例は、使用する方法を示しています。[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]にフォーカスが変更されたときに発生するイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="a3e63-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="a3e63-111">イベント ハンドラーの登録は、アプリケーションのシャットダウン時に呼び出されるメソッドで解除されるか、UI イベントの通知が必要なくなった時に解除されます。</span><span class="sxs-lookup"><span data-stu-id="a3e63-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="a3e63-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3e63-112">See Also</span></span>  
 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>  
 [<span data-ttu-id="a3e63-113">UI オートメーション イベントの概要</span><span class="sxs-lookup"><span data-stu-id="a3e63-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
