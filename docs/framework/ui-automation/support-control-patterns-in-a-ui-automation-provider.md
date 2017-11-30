---
title: "UI オートメーション プロバイダーでのコントロール パターンのサポート"
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
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d427c4e3957dd620659f6f5097f4c16caf290d72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a><span data-ttu-id="09a46-102">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="09a46-102">Support Control Patterns in a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="09a46-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="09a46-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="09a46-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09a46-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="09a46-105">このトピックでは、クライアント アプリケーションがコントロールを操作して、それらからデータを取得できるように、UI オートメーション プロバイダーに 1 つ以上のコントロール パターンを実装する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="09a46-105">This topic shows how to implement one or more control patterns on a UI Automation provider so that client applications can manipulate controls and get data from them.</span></span>  
  
### <a name="support-control-patterns"></a><span data-ttu-id="09a46-106">コントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="09a46-106">Support Control Patterns</span></span>  
  
1.  <span data-ttu-id="09a46-107"><xref:System.Windows.Automation.Provider.IInvokeProvider> の <xref:System.Windows.Automation.InvokePattern>など、要素がサポートする必要のあるコントロール パターンの適切なインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="09a46-107">Implement the appropriate interfaces for the control patterns that the element should support, such as <xref:System.Windows.Automation.Provider.IInvokeProvider> for <xref:System.Windows.Automation.InvokePattern>.</span></span>  
  
2.  <span data-ttu-id="09a46-108">実装では、各コントロール インターフェイスの実装を含むオブジェクトを返す<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="09a46-108">Return the object containing your implementation of each control interface in your implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType></span></span>  
  
## <a name="example"></a><span data-ttu-id="09a46-109">例</span><span class="sxs-lookup"><span data-stu-id="09a46-109">Example</span></span>  
 <span data-ttu-id="09a46-110">単一選択のカスタム リスト ボックスの <xref:System.Windows.Automation.Provider.ISelectionProvider> の実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="09a46-110">The following example shows an implementation of <xref:System.Windows.Automation.Provider.ISelectionProvider> for a single-selection custom list box.</span></span> <span data-ttu-id="09a46-111">3 つのプロパティを返し、現在選択されている項目を取得します。</span><span class="sxs-lookup"><span data-stu-id="09a46-111">It returns three properties and gets the currently selected item.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a><span data-ttu-id="09a46-112">例</span><span class="sxs-lookup"><span data-stu-id="09a46-112">Example</span></span>  
 <span data-ttu-id="09a46-113"><xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> を実装するクラスを返す <xref:System.Windows.Automation.Provider.ISelectionProvider>の実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="09a46-113">The following example shows an implementation of <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> that returns the class implementing <xref:System.Windows.Automation.Provider.ISelectionProvider>.</span></span> <span data-ttu-id="09a46-114">ほとんどのリスト ボックス コントロールは、同様にその他のパターンをサポートしますが、次の例では、他のすべてのパターン識別子に対して null 参照 (`Nothing` の [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]) が返されます。</span><span class="sxs-lookup"><span data-stu-id="09a46-114">Most list box controls would support other patterns as well, but in this example a null reference (`Nothing` in [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]) is returned for all other pattern identifiers.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a><span data-ttu-id="09a46-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="09a46-115">See Also</span></span>  
 [<span data-ttu-id="09a46-116">UI オートメーション プロバイダーの概要</span><span class="sxs-lookup"><span data-stu-id="09a46-116">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="09a46-117">サーバー側 UI オートメーション プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="09a46-117">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
