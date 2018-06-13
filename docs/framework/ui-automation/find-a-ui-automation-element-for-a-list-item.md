---
title: リスト項目の UI オートメーション要素の検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4813f5c9485c819a22a1598e869304d2534c85bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399991"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="f3ee5-102">リスト項目の UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="f3ee5-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
>  <span data-ttu-id="f3ee5-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="f3ee5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f3ee5-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3ee5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f3ee5-105">このトピックの内容を取得する方法を示しています、<xref:System.Windows.Automation.AutomationElement>内の項目の一覧の項目のインデックスがわかっている場合。</span><span class="sxs-lookup"><span data-stu-id="f3ee5-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ee5-106">例</span><span class="sxs-lookup"><span data-stu-id="f3ee5-106">Example</span></span>  
 <span data-ttu-id="f3ee5-107">次の例を使用して、一覧から、指定した項目を取得する 2 つの方法を示しています。<xref:System.Windows.Automation.TreeWalker>とその他の using<xref:System.Windows.Automation.AutomationElement.FindAll%2A>です。</span><span class="sxs-lookup"><span data-stu-id="f3ee5-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="f3ee5-108">最初の手法の処理が速くなる傾向があります[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]コントロールが、2 つ目は、Windows Presentation Foundation (WPF) コントロールの高速です。</span><span class="sxs-lookup"><span data-stu-id="f3ee5-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="f3ee5-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3ee5-109">See Also</span></span>  
 [<span data-ttu-id="f3ee5-110">UI オートメーション要素の取得</span><span class="sxs-lookup"><span data-stu-id="f3ee5-110">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
