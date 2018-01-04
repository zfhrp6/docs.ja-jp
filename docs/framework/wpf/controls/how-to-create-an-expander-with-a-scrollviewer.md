---
title: "方法 : ScrollViewer を持つエキスパンダーを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2066ccce28138cfecf4e0b4574d45783a9ba4ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="552c3-102">方法 : ScrollViewer を持つエキスパンダーを作成する</span><span class="sxs-lookup"><span data-stu-id="552c3-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="552c3-103">この例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>イメージやテキストなどの複雑なコンテンツを格納するコントロール。</span><span class="sxs-lookup"><span data-stu-id="552c3-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="552c3-104">この例ものコンテンツを囲む、<xref:System.Windows.Controls.Expander>で、<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="552c3-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="552c3-105">例</span><span class="sxs-lookup"><span data-stu-id="552c3-105">Example</span></span>  
 <span data-ttu-id="552c3-106">次の例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>です。</span><span class="sxs-lookup"><span data-stu-id="552c3-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="552c3-107">この例では、<xref:System.Windows.Controls.Primitives.BulletDecorator>を定義するのには画像とテキストを含むコントロール、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>です。</span><span class="sxs-lookup"><span data-stu-id="552c3-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="552c3-108">A<xref:System.Windows.Controls.ScrollViewer>コントロールに展開されたコンテンツをスクロールするためのメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="552c3-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="552c3-109">例では、セット、<xref:System.Windows.FrameworkElement.Height%2A>プロパティを<xref:System.Windows.Controls.ScrollViewer>の代わりに、コンテンツにします。</span><span class="sxs-lookup"><span data-stu-id="552c3-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="552c3-110">場合、 <xref:System.Windows.FrameworkElement.Height%2A> 、コンテンツに設定されている、<xref:System.Windows.Controls.ScrollViewer>ユーザー コンテンツをスクロールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="552c3-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="552c3-111"><xref:System.Windows.FrameworkElement.Width%2A>プロパティが設定されて、<xref:System.Windows.Controls.Expander>に制御し、この設定が適用されます、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>と展開されたコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="552c3-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="552c3-112">参照</span><span class="sxs-lookup"><span data-stu-id="552c3-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="552c3-113">エキスパンダーの概要</span><span class="sxs-lookup"><span data-stu-id="552c3-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="552c3-114">方法トピック</span><span class="sxs-lookup"><span data-stu-id="552c3-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
