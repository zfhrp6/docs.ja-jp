---
title: "ContextMenu のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a51860b21c21f8ce21510b04e817ec75d0e3b4fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="ba20a-102">ContextMenu のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="ba20a-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="ba20a-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ContextMenu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ba20a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="ba20a-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="ba20a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ba20a-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba20a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="ba20a-106">ContextMenu 部分</span><span class="sxs-lookup"><span data-stu-id="ba20a-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="ba20a-107"><xref:System.Windows.Controls.ContextMenu>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="ba20a-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="ba20a-108">作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ContextMenu>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="ba20a-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="ba20a-109">(、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.ContextMenu>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。</span><span class="sxs-lookup"><span data-stu-id="ba20a-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="ba20a-110">場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="ba20a-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="ba20a-111">コンテキスト メニューの状態</span><span class="sxs-lookup"><span data-stu-id="ba20a-111">ContextMenu States</span></span>  
 <span data-ttu-id="ba20a-112">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ContextMenu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ba20a-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="ba20a-113">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="ba20a-113">VisualState Name</span></span>|<span data-ttu-id="ba20a-114">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="ba20a-114">VisualStateGroup Name</span></span>|<span data-ttu-id="ba20a-115">説明</span><span class="sxs-lookup"><span data-stu-id="ba20a-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ba20a-116">有効</span><span class="sxs-lookup"><span data-stu-id="ba20a-116">Valid</span></span>|<span data-ttu-id="ba20a-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ba20a-117">ValidationStates</span></span>|<span data-ttu-id="ba20a-118">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="ba20a-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ba20a-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ba20a-119">InvalidFocused</span></span>|<span data-ttu-id="ba20a-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ba20a-120">ValidationStates</span></span>|<span data-ttu-id="ba20a-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="ba20a-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ba20a-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ba20a-122">InvalidUnfocused</span></span>|<span data-ttu-id="ba20a-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ba20a-123">ValidationStates</span></span>|<span data-ttu-id="ba20a-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="ba20a-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="ba20a-125">ContextMenu ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="ba20a-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="ba20a-126">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ContextMenu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ba20a-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="ba20a-127"><xref:System.Windows.Controls.ControlTemplate>は次のリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba20a-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ba20a-128">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba20a-128">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba20a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba20a-129">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ba20a-130">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="ba20a-130">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ba20a-131">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="ba20a-131">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ba20a-132">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="ba20a-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ba20a-133">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="ba20a-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
