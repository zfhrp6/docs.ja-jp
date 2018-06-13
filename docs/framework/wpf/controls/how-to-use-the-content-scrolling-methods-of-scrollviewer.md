---
title: '方法 : ScrollViewer のコンテンツ スクロール メソッドを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: b4da666934be7dd182838d870e54e496b2646901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552767"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="9fadb-102">方法 : ScrollViewer のコンテンツ スクロール メソッドを使用する</span><span class="sxs-lookup"><span data-stu-id="9fadb-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="9fadb-103">この例のスクロール メソッドを使用する方法を示しています、<xref:System.Windows.Controls.ScrollViewer>要素。</span><span class="sxs-lookup"><span data-stu-id="9fadb-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="9fadb-104">これらのメソッドは、増分、コンテンツの行またはページのいずれかのスクロールを提供する<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="9fadb-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fadb-105">例</span><span class="sxs-lookup"><span data-stu-id="9fadb-105">Example</span></span>  
 <span data-ttu-id="9fadb-106">次の例を作成、<xref:System.Windows.Controls.ScrollViewer>という`sv1`、子ホスト<xref:System.Windows.Controls.TextBlock>要素。</span><span class="sxs-lookup"><span data-stu-id="9fadb-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="9fadb-107"><xref:System.Windows.Controls.TextBlock>が親よりも大きい<xref:System.Windows.Controls.ScrollViewer>、スクロールを有効にするためにスクロール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9fadb-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="9fadb-108"><xref:System.Windows.Controls.Button> スクロールのさまざまな方法を表す要素は別個の左側にドッキングされて<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="9fadb-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="9fadb-109">各<xref:System.Windows.Controls.Button>で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルがでスクロール動作を制御する関連のカスタム メソッドを呼び出して<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="9fadb-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="9fadb-110">次の例では、<xref:System.Windows.Controls.ScrollViewer.LineUp%2A>と<xref:System.Windows.Controls.ScrollViewer.LineDown%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9fadb-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9fadb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fadb-111">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
