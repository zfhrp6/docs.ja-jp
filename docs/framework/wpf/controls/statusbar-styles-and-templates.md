---
title: StatusBar のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: 11fa3ab6edd62f0b5484d9ccf76c101d04be353c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457866"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="4ccac-102">StatusBar のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="4ccac-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="4ccac-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4ccac-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="4ccac-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="4ccac-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4ccac-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ccac-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="4ccac-106">ステータス バーのパーツ</span><span class="sxs-lookup"><span data-stu-id="4ccac-106">StatusBar Parts</span></span>  
 <span data-ttu-id="4ccac-107"><xref:System.Windows.Controls.Primitives.StatusBar>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="4ccac-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="4ccac-108">ステータス バーの状態</span><span class="sxs-lookup"><span data-stu-id="4ccac-108">StatusBar States</span></span>  
 <span data-ttu-id="4ccac-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4ccac-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="4ccac-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="4ccac-110">VisualState Name</span></span>|<span data-ttu-id="4ccac-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="4ccac-111">VisualStateGroup Name</span></span>|<span data-ttu-id="4ccac-112">説明</span><span class="sxs-lookup"><span data-stu-id="4ccac-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4ccac-113">有効</span><span class="sxs-lookup"><span data-stu-id="4ccac-113">Valid</span></span>|<span data-ttu-id="4ccac-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4ccac-114">ValidationStates</span></span>|<span data-ttu-id="4ccac-115">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="4ccac-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4ccac-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4ccac-116">InvalidFocused</span></span>|<span data-ttu-id="4ccac-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4ccac-117">ValidationStates</span></span>|<span data-ttu-id="4ccac-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="4ccac-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4ccac-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4ccac-119">InvalidUnfocused</span></span>|<span data-ttu-id="4ccac-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4ccac-120">ValidationStates</span></span>|<span data-ttu-id="4ccac-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="4ccac-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="4ccac-122">StatusBarItem 部分</span><span class="sxs-lookup"><span data-stu-id="4ccac-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="4ccac-123"><xref:System.Windows.Controls.Primitives.StatusBarItem>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="4ccac-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="4ccac-124">ステータス バーの状態</span><span class="sxs-lookup"><span data-stu-id="4ccac-124">StatusBar States</span></span>  
 <span data-ttu-id="4ccac-125">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.StatusBarItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4ccac-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="4ccac-126">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="4ccac-126">VisualState Name</span></span>|<span data-ttu-id="4ccac-127">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="4ccac-127">VisualStateGroup Name</span></span>|<span data-ttu-id="4ccac-128">説明</span><span class="sxs-lookup"><span data-stu-id="4ccac-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4ccac-129">有効</span><span class="sxs-lookup"><span data-stu-id="4ccac-129">Valid</span></span>|<span data-ttu-id="4ccac-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4ccac-130">ValidationStates</span></span>|<span data-ttu-id="4ccac-131">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="4ccac-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4ccac-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="4ccac-132">InvalidFocused</span></span>|<span data-ttu-id="4ccac-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4ccac-133">ValidationStates</span></span>|<span data-ttu-id="4ccac-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="4ccac-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4ccac-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="4ccac-135">InvalidUnfocused</span></span>|<span data-ttu-id="4ccac-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="4ccac-136">ValidationStates</span></span>|<span data-ttu-id="4ccac-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="4ccac-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="4ccac-138">StatusBar ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="4ccac-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="4ccac-139">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4ccac-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="4ccac-140"><xref:System.Windows.Controls.ControlTemplate>次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ccac-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4ccac-141">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ccac-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ccac-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ccac-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="4ccac-143">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="4ccac-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="4ccac-144">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="4ccac-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="4ccac-145">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="4ccac-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="4ccac-146">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="4ccac-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
