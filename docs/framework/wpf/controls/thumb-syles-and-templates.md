---
title: "つまみのスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9f0b8559497939737b97568a679953d392d5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="547db-102">つまみのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="547db-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="547db-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.Thumb>コントロール。</span><span class="sxs-lookup"><span data-stu-id="547db-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="547db-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="547db-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="547db-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="547db-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="547db-106">つまみのパーツ</span><span class="sxs-lookup"><span data-stu-id="547db-106">Thumb Parts</span></span>  
 <span data-ttu-id="547db-107"><xref:System.Windows.Controls.Primitives.Thumb>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="547db-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="547db-108">つまみの状態</span><span class="sxs-lookup"><span data-stu-id="547db-108">Thumb States</span></span>  
 <span data-ttu-id="547db-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.Thumb>コントロール。</span><span class="sxs-lookup"><span data-stu-id="547db-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="547db-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="547db-110">VisualState Name</span></span>|<span data-ttu-id="547db-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="547db-111">VisualStateGroup Name</span></span>|<span data-ttu-id="547db-112">説明</span><span class="sxs-lookup"><span data-stu-id="547db-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="547db-113">標準</span><span class="sxs-lookup"><span data-stu-id="547db-113">Normal</span></span>|<span data-ttu-id="547db-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="547db-114">CommonStates</span></span>|<span data-ttu-id="547db-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="547db-115">The default state.</span></span>|  
|<span data-ttu-id="547db-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="547db-116">MouseOver</span></span>|<span data-ttu-id="547db-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="547db-117">CommonStates</span></span>|<span data-ttu-id="547db-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="547db-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="547db-119">押されている</span><span class="sxs-lookup"><span data-stu-id="547db-119">Pressed</span></span>|<span data-ttu-id="547db-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="547db-120">CommonStates</span></span>|<span data-ttu-id="547db-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="547db-121">The control is pressed.</span></span>|  
|<span data-ttu-id="547db-122">無効</span><span class="sxs-lookup"><span data-stu-id="547db-122">Disabled</span></span>|<span data-ttu-id="547db-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="547db-123">CommonStates</span></span>|<span data-ttu-id="547db-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="547db-124">The control is disabled.</span></span>|  
|<span data-ttu-id="547db-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="547db-125">Focused</span></span>|<span data-ttu-id="547db-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="547db-126">FocusStates</span></span>|<span data-ttu-id="547db-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="547db-127">The control has focus.</span></span>|  
|<span data-ttu-id="547db-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="547db-128">Unfocused</span></span>|<span data-ttu-id="547db-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="547db-129">FocusStates</span></span>|<span data-ttu-id="547db-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="547db-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="547db-131">有効</span><span class="sxs-lookup"><span data-stu-id="547db-131">Valid</span></span>|<span data-ttu-id="547db-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="547db-132">ValidationStates</span></span>|<span data-ttu-id="547db-133">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="547db-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="547db-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="547db-134">InvalidFocused</span></span>|<span data-ttu-id="547db-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="547db-135">ValidationStates</span></span>|<span data-ttu-id="547db-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="547db-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="547db-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="547db-137">InvalidUnfocused</span></span>|<span data-ttu-id="547db-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="547db-138">ValidationStates</span></span>|<span data-ttu-id="547db-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="547db-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="547db-140">Thumb ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="547db-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="547db-141">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.Thumb>コントロール。</span><span class="sxs-lookup"><span data-stu-id="547db-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="547db-142">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="547db-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="547db-143">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="547db-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="547db-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="547db-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="547db-145">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="547db-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="547db-146">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="547db-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="547db-147">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="547db-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="547db-148">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="547db-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
