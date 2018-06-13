---
title: '方法 : ポップアップのカスタム位置を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 8714cfa4f7e5bb0ca157ee9d551392571303f60e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551740"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="ea98a-102">方法 : ポップアップのカスタム位置を指定する</span><span class="sxs-lookup"><span data-stu-id="ea98a-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="ea98a-103">この例のカスタム位置を指定する方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>タイミングを制御、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されている<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>です。</span><span class="sxs-lookup"><span data-stu-id="ea98a-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea98a-104">例</span><span class="sxs-lookup"><span data-stu-id="ea98a-104">Example</span></span>  
 <span data-ttu-id="ea98a-105">ときに、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティに設定されている<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>、<xref:System.Windows.Controls.Primitives.Popup>の定義済みのインスタンスを呼び出す、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>を委任します。</span><span class="sxs-lookup"><span data-stu-id="ea98a-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="ea98a-106">このデリゲートが対象となる領域の左上隅およびの左上隅に対して相対的な可能なポイントのセットを返す、<xref:System.Windows.Controls.Primitives.Popup>です。</span><span class="sxs-lookup"><span data-stu-id="ea98a-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="ea98a-107"><xref:System.Windows.Controls.Primitives.Popup>配置が、最適な可視性を提供するポイントで発生します。</span><span class="sxs-lookup"><span data-stu-id="ea98a-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="ea98a-108">次の例の位置を定義する方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>を設定して、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>プロパティを<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>です。</span><span class="sxs-lookup"><span data-stu-id="ea98a-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="ea98a-109">作成して割り当てる方法も示しています、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>を配置するためにデリゲート、<xref:System.Windows.Controls.Primitives.Popup>です。</span><span class="sxs-lookup"><span data-stu-id="ea98a-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="ea98a-110">コールバック デリゲートでは、2 つを返します<xref:System.Windows.Controls.Primitives.CustomPopupPlacement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ea98a-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="ea98a-111">場合、<xref:System.Windows.Controls.Primitives.Popup>最初の位置にある画面の端で非表示には、<xref:System.Windows.Controls.Primitives.Popup>は 2 番目の位置に置かれます。</span><span class="sxs-lookup"><span data-stu-id="ea98a-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="ea98a-112">サンプル全体については、次を参照してください。[ポップアップ配置サンプル](http://go.microsoft.com/fwlink/?LinkID=160032)です。</span><span class="sxs-lookup"><span data-stu-id="ea98a-112">For the complete sample, see [Popup Placement Sample](http://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea98a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea98a-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="ea98a-114">ポップアップの概要</span><span class="sxs-lookup"><span data-stu-id="ea98a-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="ea98a-115">方法トピック</span><span class="sxs-lookup"><span data-stu-id="ea98a-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
