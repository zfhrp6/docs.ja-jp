---
title: "UI オートメーション要素のプロパティの取得"
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
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2b9e1f24a6384cd052dd7b15c7afb3facac05c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="d39c9-102">UI オートメーション要素のプロパティの取得</span><span class="sxs-lookup"><span data-stu-id="d39c9-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="d39c9-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="d39c9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d39c9-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d39c9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d39c9-105">このトピックのプロパティを取得する方法を示しています、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]要素。</span><span class="sxs-lookup"><span data-stu-id="d39c9-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="d39c9-106">現在のプロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d39c9-106">Get a Current Property Value</span></span>  
  
1.  <span data-ttu-id="d39c9-107">取得、<xref:System.Windows.Automation.AutomationElement>を取得するプロパティを持つ。</span><span class="sxs-lookup"><span data-stu-id="d39c9-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2.  <span data-ttu-id="d39c9-108">呼び出す<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>、または取得、<xref:System.Windows.Automation.AutomationElement.Current%2A>プロパティの構造とそのメンバーのいずれかの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d39c9-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="d39c9-109">キャッシュされたプロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d39c9-109">Get a Cached Property Value</span></span>  
  
1.  <span data-ttu-id="d39c9-110">取得、<xref:System.Windows.Automation.AutomationElement>を取得するプロパティを持つ。</span><span class="sxs-lookup"><span data-stu-id="d39c9-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="d39c9-111">プロパティが指定されている必要があります、<xref:System.Windows.Automation.CacheRequest>です。</span><span class="sxs-lookup"><span data-stu-id="d39c9-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="d39c9-112">呼び出す<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>、または取得、<xref:System.Windows.Automation.AutomationElement.Cached%2A>プロパティの構造とそのメンバーのいずれかの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d39c9-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d39c9-113">例</span><span class="sxs-lookup"><span data-stu-id="d39c9-113">Example</span></span>  
 <span data-ttu-id="d39c9-114">次の例の現在のプロパティを取得するさまざまな方法を示しています、<xref:System.Windows.Automation.AutomationElement>です。</span><span class="sxs-lookup"><span data-stu-id="d39c9-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="d39c9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d39c9-115">See Also</span></span>  
 [<span data-ttu-id="d39c9-116">UI Automation Properties for Clients</span><span class="sxs-lookup"><span data-stu-id="d39c9-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [<span data-ttu-id="d39c9-117">UI オートメーションにおけるキャッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="d39c9-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [<span data-ttu-id="d39c9-118">UI オートメーション クライアントにおけるキャッシュ</span><span class="sxs-lookup"><span data-stu-id="d39c9-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
