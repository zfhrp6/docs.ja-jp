---
title: "サポートされている UI オートメーション コントロール パターンの取得"
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
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 26cdf2dea8ec924d4345c1591be8fee1ed489c0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="f011c-102">サポートされている UI オートメーション コントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="f011c-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
>  <span data-ttu-id="f011c-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="f011c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f011c-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f011c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f011c-105">このトピックからコントロール パターン オブジェクトを取得する方法を示しています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]要素。</span><span class="sxs-lookup"><span data-stu-id="f011c-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="f011c-106">すべてのコントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="f011c-106">Obtain All Control Patterns</span></span>  
  
1.  <span data-ttu-id="f011c-107">取得、<xref:System.Windows.Automation.AutomationElement>をコントロールが対象とするパターンします。</span><span class="sxs-lookup"><span data-stu-id="f011c-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="f011c-108">呼び出す<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>要素からすべてのコントロール パターンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f011c-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f011c-109">クライアントが使用しないことを強くお勧め<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>です。</span><span class="sxs-lookup"><span data-stu-id="f011c-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="f011c-110">パフォーマンスに深刻な影響ようにこのメソッドを呼び出します<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>の各既存のコントロール パターンを内部的にします。</span><span class="sxs-lookup"><span data-stu-id="f011c-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="f011c-111">可能であれば、クライアントが呼び出す必要があります<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>の主なパターンです。</span><span class="sxs-lookup"><span data-stu-id="f011c-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="f011c-112">特定のコントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="f011c-112">Obtain a Specific Control Pattern</span></span>  
  
1.  <span data-ttu-id="f011c-113">取得、<xref:System.Windows.Automation.AutomationElement>をコントロールが対象とするパターンします。</span><span class="sxs-lookup"><span data-stu-id="f011c-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2.  <span data-ttu-id="f011c-114">呼び出す<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>または<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>特定のパターンを照会します。</span><span class="sxs-lookup"><span data-stu-id="f011c-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="f011c-115">これらのメソッドと同様に、パターンが見つからない場合は<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A>、例外が発生し、<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>を返します`false`です。</span><span class="sxs-lookup"><span data-stu-id="f011c-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f011c-116">例</span><span class="sxs-lookup"><span data-stu-id="f011c-116">Example</span></span>  
 <span data-ttu-id="f011c-117">次の例を取得、<xref:System.Windows.Automation.AutomationElement>リスト項目を取得し、<xref:System.Windows.Automation.SelectionItemPattern>その要素から。</span><span class="sxs-lookup"><span data-stu-id="f011c-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="f011c-118">参照</span><span class="sxs-lookup"><span data-stu-id="f011c-118">See Also</span></span>  
 [<span data-ttu-id="f011c-119">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="f011c-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
