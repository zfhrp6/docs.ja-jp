---
title: "方法 : イベントを使用してロールオーバー効果を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c82d993c31174419793319da74ffa38d122ef203
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="3943e-102">方法 : イベントを使用してロールオーバー効果を作成する</span><span class="sxs-lookup"><span data-stu-id="3943e-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="3943e-103">この例では、マウス ポインターが要素で占有される領域に出入りとして要素の色を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3943e-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="3943e-104">この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="3943e-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3943e-105">この例は、イベントを使用する方法を示しますが、これと同じ効果を実現するために推奨される方法を使用する、<xref:System.Windows.Trigger>スタイルでします。</span><span class="sxs-lookup"><span data-stu-id="3943e-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="3943e-106">詳しくは、「 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3943e-106">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3943e-107">例</span><span class="sxs-lookup"><span data-stu-id="3943e-107">Example</span></span>  
 <span data-ttu-id="3943e-108">次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]から構成されるユーザー インターフェイスを作成<xref:System.Windows.Controls.Border>の周囲、 <xref:System.Windows.Controls.TextBlock>、アタッチ、<xref:System.Windows.Input.Mouse.MouseEnter>と<xref:System.Windows.UIElement.MouseLeave>イベント ハンドラーを<xref:System.Windows.Controls.Border>です。</span><span class="sxs-lookup"><span data-stu-id="3943e-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="3943e-109">次のコードを作成、<xref:System.Windows.UIElement.MouseEnter>と<xref:System.Windows.UIElement.MouseLeave>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="3943e-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="3943e-110">マウス ポインターが入ったとき、<xref:System.Windows.Controls.Border>の背景、<xref:System.Windows.Controls.Border>が赤に変更します。</span><span class="sxs-lookup"><span data-stu-id="3943e-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="3943e-111">マウス ポインターを離れるときに、<xref:System.Windows.Controls.Border>の背景、<xref:System.Windows.Controls.Border>白に変更します。</span><span class="sxs-lookup"><span data-stu-id="3943e-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
