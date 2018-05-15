---
title: '方法 : 読み込まれたイベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: 6f3520fc3bc2a64d76083af415588ff819890eb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="ff0d0-102">方法 : 読み込まれたイベントを処理する</span><span class="sxs-lookup"><span data-stu-id="ff0d0-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="ff0d0-103">この例では、処理、<xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType>イベント、およびそのイベントを処理するための適切なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="ff0d0-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="ff0d0-104">ハンドラーを作成、<xref:System.Windows.Controls.Button>ページが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ff0d0-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff0d0-105">例</span><span class="sxs-lookup"><span data-stu-id="ff0d0-105">Example</span></span>  
 <span data-ttu-id="ff0d0-106">次の例では[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]と共に分離コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="ff0d0-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="ff0d0-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff0d0-107">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 [<span data-ttu-id="ff0d0-108">オブジェクトの有効期間イベント</span><span class="sxs-lookup"><span data-stu-id="ff0d0-108">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [<span data-ttu-id="ff0d0-109">ルーティング イベントの概要</span><span class="sxs-lookup"><span data-stu-id="ff0d0-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="ff0d0-110">方法トピック</span><span class="sxs-lookup"><span data-stu-id="ff0d0-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
