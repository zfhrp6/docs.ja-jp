---
title: UI オートメーションを使用した、チェック ボックスのトグル状態の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4f0af8eac1238c377682bd4880efb89c4d9442db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a><span data-ttu-id="5203c-102">UI オートメーションを使用した、チェック ボックスのトグル状態の取得</span><span class="sxs-lookup"><span data-stu-id="5203c-102">Get the Toggle State of a Check Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="5203c-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="5203c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5203c-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5203c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5203c-105">このトピックは、使用する方法を示します[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]コントロールの表示/非表示状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="5203c-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to get the toggle state of a control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5203c-106">例</span><span class="sxs-lookup"><span data-stu-id="5203c-106">Example</span></span>  
 <span data-ttu-id="5203c-107">この例では、<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>のメソッド、<xref:System.Windows.Automation.AutomationElement>を取得するクラス、<xref:System.Windows.Automation.TogglePattern>コントロールからオブジェクトを返す、<xref:System.Windows.Automation.ToggleState>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5203c-107">This example uses the <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to obtain a <xref:System.Windows.Automation.TogglePattern> object from a control and return its <xref:System.Windows.Automation.ToggleState> property.</span></span>  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
