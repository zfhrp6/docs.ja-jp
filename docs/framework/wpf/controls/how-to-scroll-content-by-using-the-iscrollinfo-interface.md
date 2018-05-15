---
title: '方法 : IScrollInfo インターフェイスを使用してコンテンツをスクロールする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 8154a626c6bf48a59be0540f857c0c51d59a26c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="7fb6c-102">方法 : IScrollInfo インターフェイスを使用してコンテンツをスクロールする</span><span class="sxs-lookup"><span data-stu-id="7fb6c-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="7fb6c-103">この例を使用してコンテンツをスクロールする方法を示しています、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="7fb6c-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fb6c-104">例</span><span class="sxs-lookup"><span data-stu-id="7fb6c-104">Example</span></span>  
 <span data-ttu-id="7fb6c-105">次の例では、機能、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="7fb6c-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="7fb6c-106">例は、作成、<xref:System.Windows.Controls.StackPanel>内の要素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、親の入れ子になっている<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="7fb6c-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="7fb6c-107">子要素、<xref:System.Windows.Controls.StackPanel>によって定義されたメソッドを使用して、論理的にスクロールできる、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスとのインスタンスへのキャスト<xref:System.Windows.Controls.StackPanel>(`sp1`) のコードにします。</span><span class="sxs-lookup"><span data-stu-id="7fb6c-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="7fb6c-108">各<xref:System.Windows.Controls.Button>で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルでスクロール動作を制御する、関連付けられたカスタム メソッドをトリガーする<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="7fb6c-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="7fb6c-109">次の例を使用する方法を示しています、<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>と<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>メソッドです。 一般的にも配置のすべてのメソッドを使用する方法を示していますを、<xref:System.Windows.Controls.Primitives.IScrollInfo>クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="7fb6c-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7fb6c-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fb6c-110">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="7fb6c-111">ScrollViewer の概要</span><span class="sxs-lookup"><span data-stu-id="7fb6c-111">ScrollViewer Overview</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [<span data-ttu-id="7fb6c-112">方法トピック</span><span class="sxs-lookup"><span data-stu-id="7fb6c-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [<span data-ttu-id="7fb6c-113">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="7fb6c-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
