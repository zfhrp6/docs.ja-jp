---
title: '方法 : ScrollViewer を持つエキスパンダーを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 6c014d4f6a12bfb58c2ae68f580f632c9478c82f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553063"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="ad3ee-102">方法 : ScrollViewer を持つエキスパンダーを作成する</span><span class="sxs-lookup"><span data-stu-id="ad3ee-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="ad3ee-103">この例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>イメージやテキストなどの複雑なコンテンツを格納するコントロール。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="ad3ee-104">この例ものコンテンツを囲む、<xref:System.Windows.Controls.Expander>で、<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad3ee-105">例</span><span class="sxs-lookup"><span data-stu-id="ad3ee-105">Example</span></span>  
 <span data-ttu-id="ad3ee-106">次の例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>です。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="ad3ee-107">この例では、<xref:System.Windows.Controls.Primitives.BulletDecorator>を定義するのには画像とテキストを含むコントロール、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>です。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="ad3ee-108">A<xref:System.Windows.Controls.ScrollViewer>コントロールに展開されたコンテンツをスクロールするためのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="ad3ee-109">例では、セット、<xref:System.Windows.FrameworkElement.Height%2A>プロパティを<xref:System.Windows.Controls.ScrollViewer>の代わりに、コンテンツにします。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="ad3ee-110">場合、 <xref:System.Windows.FrameworkElement.Height%2A> 、コンテンツに設定されている、<xref:System.Windows.Controls.ScrollViewer>ユーザー コンテンツをスクロールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="ad3ee-111"><xref:System.Windows.FrameworkElement.Width%2A>プロパティが設定されて、<xref:System.Windows.Controls.Expander>に制御し、この設定が適用されます、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>と展開されたコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="ad3ee-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="ad3ee-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad3ee-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="ad3ee-113">エキスパンダーの概要</span><span class="sxs-lookup"><span data-stu-id="ad3ee-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="ad3ee-114">方法トピック</span><span class="sxs-lookup"><span data-stu-id="ad3ee-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
