---
title: "方法 : FocusVisualStyle をコントロールに適用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f614e244293d08cd836edaf82496ca9e7b51423e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="002ae-102">方法 : FocusVisualStyle をコントロールに適用する</span><span class="sxs-lookup"><span data-stu-id="002ae-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="002ae-103">この例は、リソースにフォーカス visual スタイルを作成して、コントロールにスタイルを適用する方法を示しますを使用して、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="002ae-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="002ae-104">例</span><span class="sxs-lookup"><span data-stu-id="002ae-104">Example</span></span>  
 <span data-ttu-id="002ae-105">次の例は、そのコントロールがキーボードでのフォーカスされたときにのみ適用する追加コントロールの複合を作成するスタイルを定義、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="002ae-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="002ae-106">設定されたスタイルを定義することによってこれは、 <xref:System.Windows.Controls.ControlTemplate>、参照をリソースとしてのスタイルを設定するときに、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティ。</span><span class="sxs-lookup"><span data-stu-id="002ae-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="002ae-107">境界線に似た外部四角形は四角形の領域の外側に配置します。</span><span class="sxs-lookup"><span data-stu-id="002ae-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="002ae-108">スタイルのサイジングを使用して、それ以外の場合は変更しない限り、<xref:System.Windows.FrameworkElement.ActualHeight%2A>と<xref:System.Windows.FrameworkElement.ActualWidth%2A>四角形のコントロールがフォーカス visual スタイルが適用されるのです。</span><span class="sxs-lookup"><span data-stu-id="002ae-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="002ae-109">この例に負の値の設定、<xref:System.Windows.FrameworkElement.Margin%2A>フォーカスされたコントロールの外に若干表示枠を作成します。</span><span class="sxs-lookup"><span data-stu-id="002ae-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="002ae-110">A<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>に付属している任意のコントロール テンプレート スタイル加法から、明示的なスタイルまたはテーマ スタイル; コントロールの主なスタイルも作成できますを使用して、<xref:System.Windows.Controls.ControlTemplate>にそのスタイルを設定して、<xref:System.Windows.FrameworkElement.Style%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="002ae-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="002ae-111">Visual スタイルは、テーマ、または、UI の間で一貫して使用する必要がありますフォーカス フォーカス可能な要素ごとに別の名前を使用するのではなくです。</span><span class="sxs-lookup"><span data-stu-id="002ae-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="002ae-112">詳細については、「[コントロール、および FocusVisualStyle でフォーカスのスタイルは](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)します。</span><span class="sxs-lookup"><span data-stu-id="002ae-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002ae-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="002ae-113">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [<span data-ttu-id="002ae-114">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="002ae-114">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="002ae-115">コントロールのフォーカスのスタイルと FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="002ae-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
