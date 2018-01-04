---
title: "方法 : ListBox のスクロール速度を向上させる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58435948a3ddd8042b95b30b8d6cbdba984f34d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a><span data-ttu-id="83c0a-102">方法 : ListBox のスクロール速度を向上させる</span><span class="sxs-lookup"><span data-stu-id="83c0a-102">How to: Improve the Scrolling Performance of a ListBox</span></span>
<span data-ttu-id="83c0a-103">場合、 <xref:System.Windows.Controls.ListBox> 、多くのアイテムが含まれています、ユーザーがスクロールすると、ユーザー インターフェイスの応答が遅くなる、<xref:System.Windows.Controls.ListBox>をマウスのホイールを使用するか、スクロール バーのつまみをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="83c0a-103">If a <xref:System.Windows.Controls.ListBox> contains many items, the user interface response can be slow when a user scrolls the <xref:System.Windows.Controls.ListBox> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="83c0a-104">パフォーマンスを向上させることができます、<xref:System.Windows.Controls.ListBox>を設定してユーザーをスクロールするときに、`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="83c0a-104">You can improve the performance of the <xref:System.Windows.Controls.ListBox> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83c0a-105">例</span><span class="sxs-lookup"><span data-stu-id="83c0a-105">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="83c0a-106">説明</span><span class="sxs-lookup"><span data-stu-id="83c0a-106">Description</span></span>  
<span data-ttu-id="83c0a-107">次の例を作成、<xref:System.Windows.Controls.ListBox>設定と、`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>スクロール中にパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="83c0a-107">The following example creates a <xref:System.Windows.Controls.ListBox> and sets the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to improve performance during scrolling.</span></span>  
  
## <a name="code"></a><span data-ttu-id="83c0a-108">コード</span><span class="sxs-lookup"><span data-stu-id="83c0a-108">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 <span data-ttu-id="83c0a-109">次の例では、前の例で使用するデータを示します。</span><span class="sxs-lookup"><span data-stu-id="83c0a-109">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
