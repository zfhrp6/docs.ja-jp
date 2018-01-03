---
title: "UI オートメーション スレッド処理の問題点"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
caps.latest.revision: "9"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9e5c38f5c4681210a4f3be552a3f08be3962bc2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-threading-issues"></a><span data-ttu-id="4dd06-102">UI オートメーション スレッド処理の問題点</span><span class="sxs-lookup"><span data-stu-id="4dd06-102">UI Automation Threading Issues</span></span>
> [!NOTE]
>  <span data-ttu-id="4dd06-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="4dd06-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4dd06-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dd06-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4dd06-105">[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] の Windows メッセージを使用する方法が原因で、クライアント アプリケーションが [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] スレッド上のそれ自体の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] と対話しようとするときに、競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4dd06-105">Because of the way [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uses Windows messages, conflicts can occur when a client application attempts to interact with its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] on the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="4dd06-106">これらの競合が発生すると、パフォーマンスが著しく低下する恐れがあります。また、アプリケーションが応答を停止する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="4dd06-106">These conflicts can lead to very slow performance or even cause the application to stop responding.</span></span>  
  
 <span data-ttu-id="4dd06-107">クライアント アプリケーションがデスクトップ上のすべての要素 (それ自体の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]を含む) と対話する場合、すべての [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の呼び出しを個別のスレッドで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd06-107">If your client application is intended to interact with all elements on the desktop, including its own [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you should make all [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls on a separate thread.</span></span> <span data-ttu-id="4dd06-108">これには、要素の検索 (たとえば、 <xref:System.Windows.Automation.TreeWalker> または <xref:System.Windows.Automation.AutomationElement.FindAll%2A> メソッドを使用) とコントロール パターンの使用が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4dd06-108">This includes locating elements (for example, by using <xref:System.Windows.Automation.TreeWalker> or the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method) and using control patterns.</span></span>  
  
 <span data-ttu-id="4dd06-109">イベント ハンドラーは常に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 以外のスレッドで呼び出されるため、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の呼び出しを[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] イベント ハンドラー内で実行しても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="4dd06-109">It is safe to make [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] calls within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event handler, because the event handler is always called on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="4dd06-110">ただし、クライアント アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]から発生するイベントをサブスクライブする場合、 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>以外のスレッド上の[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (または関連するメソッド) への呼び出しを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dd06-110">However, when subscribing to events that may originate from your client application's [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], you must make the call to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, or a related method, on a non-[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] thread.</span></span> <span data-ttu-id="4dd06-111">同じスレッドにあるイベント ハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4dd06-111">Remove event handlers on the same thread.</span></span>
