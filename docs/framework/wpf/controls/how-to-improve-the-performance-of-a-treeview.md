---
title: '方法 : TreeView のパフォーマンスを改善する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: 75f17c770af89f08fedfd3c8193a916901fe6f79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552754"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="cff4b-102">方法 : TreeView のパフォーマンスを改善する</span><span class="sxs-lookup"><span data-stu-id="cff4b-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="cff4b-103">場合、<xref:System.Windows.Controls.TreeView>多くの項目を含むの読み込みにかかる時間は、ユーザー インターフェイスに大きな遅延を引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cff4b-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="cff4b-104">設定して、読み込み時間を向上させることができます、`VirtualizingStackPanel.IsVirtualizing`添付プロパティ`true`です。</span><span class="sxs-lookup"><span data-stu-id="cff4b-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="cff4b-105">UI ユーザーがスクロール時に応答しに時間がかかる場合があります、<xref:System.Windows.Controls.TreeView>をマウスのホイールを使用するか、スクロール バーのつまみをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="cff4b-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="cff4b-106">パフォーマンスを向上させることができます、<xref:System.Windows.Controls.TreeView>を設定してユーザーをスクロールするときに、`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="cff4b-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cff4b-107">例</span><span class="sxs-lookup"><span data-stu-id="cff4b-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="cff4b-108">説明</span><span class="sxs-lookup"><span data-stu-id="cff4b-108">Description</span></span>  
<span data-ttu-id="cff4b-109">次の例を作成、<xref:System.Windows.Controls.TreeView>が設定された、`VirtualizingStackPanel.IsVirtualizing`添付プロパティを true と`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>パフォーマンスを最適化します。</span><span class="sxs-lookup"><span data-stu-id="cff4b-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="cff4b-110">コード</span><span class="sxs-lookup"><span data-stu-id="cff4b-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="cff4b-111">次の例では、前の例で使用するデータを示します。</span><span class="sxs-lookup"><span data-stu-id="cff4b-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="cff4b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cff4b-112">See Also</span></span>  
 [<span data-ttu-id="cff4b-113">コントロール</span><span class="sxs-lookup"><span data-stu-id="cff4b-113">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
