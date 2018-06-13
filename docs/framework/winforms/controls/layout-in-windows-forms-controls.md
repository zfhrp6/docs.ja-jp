---
title: Windows フォーム コントロールのレイアウト
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- sizing [Windows Forms], automatic [Windows Forms]
- Margin property [Windows Forms]
- Padding property [Windws Forms]
ms.assetid: 99400e3a-720e-4f56-b68f-89df911a251c
ms.openlocfilehash: 11db7b49f37b4367f31b2c27c61225f8f71bde80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535842"
---
# <a name="layout-in-windows-forms-controls"></a><span data-ttu-id="15f30-102">Windows フォーム コントロールのレイアウト</span><span class="sxs-lookup"><span data-stu-id="15f30-102">Layout in Windows Forms Controls</span></span>
<span data-ttu-id="15f30-103">フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。</span><span class="sxs-lookup"><span data-stu-id="15f30-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="15f30-104"><xref:System.Windows.Forms?displayProperty=nameWithType>名前空間は、これを実現するさまざまなレイアウト ツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="15f30-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout tools to accomplish this.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15f30-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="15f30-105">In This Section</span></span>  
 [<span data-ttu-id="15f30-106">AutoSize プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="15f30-106">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 <span data-ttu-id="15f30-107">について説明します、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティとレイアウトでは、そのロール。</span><span class="sxs-lookup"><span data-stu-id="15f30-107">Describes the <xref:System.Windows.Forms.Control.AutoSize%2A> property and its role in layout.</span></span>  
  
 [<span data-ttu-id="15f30-108">Windows フォーム コントロールでのマージンと埋め込み</span><span class="sxs-lookup"><span data-stu-id="15f30-108">Margin and Padding in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)  
 <span data-ttu-id="15f30-109">について説明します、<xref:System.Windows.Forms.Control.Margin%2A>と<xref:System.Windows.Forms.Control.Padding%2A>プロパティと、そのロールのレイアウトでします。</span><span class="sxs-lookup"><span data-stu-id="15f30-109">Describes the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties and their roles in layout.</span></span>  
  
 [<span data-ttu-id="15f30-110">方法: フォームの端に合わせてコントロールを配置する</span><span class="sxs-lookup"><span data-stu-id="15f30-110">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 <span data-ttu-id="15f30-111">使用する方法を示します、<xref:System.Windows.Forms.Control.Dock%2A>プロパティを合わせて、コントロールが占有するフォームの端を配置します。</span><span class="sxs-lookup"><span data-stu-id="15f30-111">Demonstrates how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="15f30-112">方法: 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する</span><span class="sxs-lookup"><span data-stu-id="15f30-112">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-border-around-a-windows-forms-control-using-padding.md)  
 <span data-ttu-id="15f30-113">使用する方法を示します、<xref:System.Windows.Forms.Control.Padding%2A>プロパティ、コントロールの要点を説明します。</span><span class="sxs-lookup"><span data-stu-id="15f30-113">Demonstrates how to use the <xref:System.Windows.Forms.Control.Padding%2A> property to outline a control.</span></span>  
  
 [<span data-ttu-id="15f30-114">方法: カスタム レイアウト エンジンを実装する</span><span class="sxs-lookup"><span data-stu-id="15f30-114">How to: Implement a Custom Layout Engine</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-layout-engine.md)  
 <span data-ttu-id="15f30-115">実装する方法を示します、 <xref:System.Windows.Forms.Layout.LayoutEngine> Windows フォーム コントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="15f30-115">Demonstrates how to implement a <xref:System.Windows.Forms.Layout.LayoutEngine> for arranging Windows Forms controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="15f30-116">参照</span><span class="sxs-lookup"><span data-stu-id="15f30-116">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="15f30-117"><xref:System.Windows.Forms.TableLayoutPanel> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="15f30-117">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="15f30-118"><xref:System.Windows.Forms.FlowLayoutPanel> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="15f30-118">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f30-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="15f30-119">See Also</span></span>  
 [<span data-ttu-id="15f30-120">方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="15f30-120">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="15f30-121">方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="15f30-121">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="15f30-122">方法: ローカリゼーションに対応した Windows フォーム レイアウトをデザインする</span><span class="sxs-lookup"><span data-stu-id="15f30-122">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="15f30-123">TableLayoutPanel コントロールにおける AutoSize 動作</span><span class="sxs-lookup"><span data-stu-id="15f30-123">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)
