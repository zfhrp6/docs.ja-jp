---
title: "方法 : フォームの端に合わせてコントロールを配置する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7979b58d52c6df7341259af50a39e104781dd148
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="74290-102">方法 : フォームの端に合わせてコントロールを配置する</span><span class="sxs-lookup"><span data-stu-id="74290-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="74290-103"><xref:System.Windows.Forms.Control.Dock%2A> プロパティを設定することにより、フォームの端に合わせてコントロールを配置することができます。</span><span class="sxs-lookup"><span data-stu-id="74290-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="74290-104">このプロパティは、フォーム内のコントロールの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="74290-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="74290-105"><xref:System.Windows.Forms.Control.Dock%2A> プロパティには次の値のいずれかを設定できます。</span><span class="sxs-lookup"><span data-stu-id="74290-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="74290-106">設定</span><span class="sxs-lookup"><span data-stu-id="74290-106">Setting</span></span>|<span data-ttu-id="74290-107">コントロールへの影響</span><span class="sxs-lookup"><span data-stu-id="74290-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="74290-108">フォームの下部にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="74290-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="74290-109">フォームの残りの全スペースを埋めます。</span><span class="sxs-lookup"><span data-stu-id="74290-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="74290-110">フォームの左側にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="74290-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="74290-111">どこにもドッキングせず、その <xref:System.Windows.Forms.Control.Location%2A> プロパティで指定された位置に表示されます。</span><span class="sxs-lookup"><span data-stu-id="74290-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="74290-112">フォームの右側にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="74290-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="74290-113">フォームの上部にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="74290-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="74290-114">Visual Studio では、この機能のデザイン時サポートがあります。</span><span class="sxs-lookup"><span data-stu-id="74290-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="74290-115">実行時にコントロールの Dock プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="74290-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="74290-116">コードで <xref:System.Windows.Forms.Control.Dock%2A> プロパティを適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="74290-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="74290-117">参照</span><span class="sxs-lookup"><span data-stu-id="74290-117">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="74290-118">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="74290-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="74290-119">方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="74290-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="74290-120">方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="74290-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="74290-121">AutoSize プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="74290-121">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
