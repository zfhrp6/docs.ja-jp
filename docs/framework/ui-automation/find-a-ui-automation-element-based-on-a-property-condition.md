---
title: プロパティ条件に基づく UI オートメーション要素の検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: da455b10425c9e0b20a644679358dde469ed92e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400758"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="1bde3-102">プロパティ条件に基づく UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="1bde3-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="1bde3-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="1bde3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1bde3-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bde3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1bde3-105">このトピックには内の要素を検索する方法を示すコード例が含まれています、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーは、特定のプロパティまたはプロパティに基づいています。</span><span class="sxs-lookup"><span data-stu-id="1bde3-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bde3-106">例</span><span class="sxs-lookup"><span data-stu-id="1bde3-106">Example</span></span>  
 <span data-ttu-id="1bde3-107">次の例では、一連のプロパティの条件がで指定された関心のある特定の要素 (または要素) を識別する、<xref:System.Windows.Automation.AutomationElement>ツリー。</span><span class="sxs-lookup"><span data-stu-id="1bde3-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="1bde3-108">一致するすべての要素の検索が実行し、<xref:System.Windows.Automation.AutomationElement.FindAll%2A>の系列が組み込まれているメソッド<xref:System.Windows.Automation.AndCondition>一致する要素の数を制限するブール演算です。</span><span class="sxs-lookup"><span data-stu-id="1bde3-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bde3-109">検索するときに、 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>、直接の子のみを取得しようとする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bde3-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="1bde3-110">子孫を検索は、数百または数千もの要素のスタック オーバーフローの可能性のある処理を反復処理可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1bde3-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="1bde3-111">下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bde3-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="1bde3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bde3-112">See Also</span></span>  
 [<span data-ttu-id="1bde3-113">InvokePattern および ExpandCollapsePattern メニュー項目のサンプル</span><span class="sxs-lookup"><span data-stu-id="1bde3-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="1bde3-114">UI オートメーション要素の取得</span><span class="sxs-lookup"><span data-stu-id="1bde3-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="1bde3-115">AutomationID プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="1bde3-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
