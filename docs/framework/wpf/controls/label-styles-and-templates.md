---
title: ラベルのスタイルとテンプレート
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6189470b5a0a01911bfe71ddfa003f72f64356c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="2c41d-102">ラベルのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="2c41d-102">Label Styles and Templates</span></span>
<span data-ttu-id="2c41d-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Label>コントロール。</span><span class="sxs-lookup"><span data-stu-id="2c41d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="2c41d-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="2c41d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2c41d-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c41d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="2c41d-106">ラベル部分</span><span class="sxs-lookup"><span data-stu-id="2c41d-106">Label Parts</span></span>  
 <span data-ttu-id="2c41d-107"><xref:System.Windows.Controls.Label>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="2c41d-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="2c41d-108">ラベルの状態</span><span class="sxs-lookup"><span data-stu-id="2c41d-108">Label States</span></span>  
 <span data-ttu-id="2c41d-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Label>コントロール。</span><span class="sxs-lookup"><span data-stu-id="2c41d-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="2c41d-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="2c41d-110">VisualState Name</span></span>|<span data-ttu-id="2c41d-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="2c41d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="2c41d-112">説明</span><span class="sxs-lookup"><span data-stu-id="2c41d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2c41d-113">有効</span><span class="sxs-lookup"><span data-stu-id="2c41d-113">Valid</span></span>|<span data-ttu-id="2c41d-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2c41d-114">ValidationStates</span></span>|<span data-ttu-id="2c41d-115">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="2c41d-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2c41d-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2c41d-116">InvalidFocused</span></span>|<span data-ttu-id="2c41d-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2c41d-117">ValidationStates</span></span>|<span data-ttu-id="2c41d-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="2c41d-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2c41d-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2c41d-119">InvalidUnfocused</span></span>|<span data-ttu-id="2c41d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2c41d-120">ValidationStates</span></span>|<span data-ttu-id="2c41d-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="2c41d-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="2c41d-122">ControlTemplate の例にラベルを付ける</span><span class="sxs-lookup"><span data-stu-id="2c41d-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="2c41d-123">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Label>コントロール。</span><span class="sxs-lookup"><span data-stu-id="2c41d-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="2c41d-124"><xref:System.Windows.Controls.ControlTemplate>次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="2c41d-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2c41d-125">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c41d-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c41d-126">参照</span><span class="sxs-lookup"><span data-stu-id="2c41d-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="2c41d-127">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="2c41d-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="2c41d-128">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="2c41d-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="2c41d-129">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="2c41d-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="2c41d-130">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="2c41d-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
