---
title: "GroupBox のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99150de10fcbd45d3617621a916793ad5cfe72db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="413bd-102">GroupBox のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="413bd-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="413bd-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="413bd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="413bd-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="413bd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="413bd-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="413bd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="413bd-106">GroupBox 部分</span><span class="sxs-lookup"><span data-stu-id="413bd-106">GroupBox Parts</span></span>  
 <span data-ttu-id="413bd-107"><xref:System.Windows.Controls.GroupBox>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="413bd-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="413bd-108">GroupBox 状態</span><span class="sxs-lookup"><span data-stu-id="413bd-108">GroupBox States</span></span>  
 <span data-ttu-id="413bd-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="413bd-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="413bd-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="413bd-110">VisualState Name</span></span>|<span data-ttu-id="413bd-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="413bd-111">VisualStateGroup Name</span></span>|<span data-ttu-id="413bd-112">説明</span><span class="sxs-lookup"><span data-stu-id="413bd-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="413bd-113">有効</span><span class="sxs-lookup"><span data-stu-id="413bd-113">Valid</span></span>|<span data-ttu-id="413bd-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="413bd-114">ValidationStates</span></span>|<span data-ttu-id="413bd-115">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="413bd-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="413bd-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="413bd-116">InvalidFocused</span></span>|<span data-ttu-id="413bd-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="413bd-117">ValidationStates</span></span>|<span data-ttu-id="413bd-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="413bd-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="413bd-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="413bd-119">InvalidUnfocused</span></span>|<span data-ttu-id="413bd-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="413bd-120">ValidationStates</span></span>|<span data-ttu-id="413bd-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="413bd-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="413bd-122">GroupBox ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="413bd-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="413bd-123">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="413bd-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="413bd-124"><xref:System.Windows.Controls.ControlTemplate>次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="413bd-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="413bd-125">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="413bd-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413bd-126">参照</span><span class="sxs-lookup"><span data-stu-id="413bd-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="413bd-127">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="413bd-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="413bd-128">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="413bd-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="413bd-129">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="413bd-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="413bd-130">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="413bd-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
