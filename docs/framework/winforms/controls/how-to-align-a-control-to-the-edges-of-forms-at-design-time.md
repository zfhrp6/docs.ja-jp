---
title: '方法 : デザイン時にフォームの端に合わせてコントロールを配置する'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: 5b36879413442ff99da034fcbee6bf6388affa6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528720"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="e1c1b-102">方法 : デザイン時にフォームの端に合わせてコントロールを配置する</span><span class="sxs-lookup"><span data-stu-id="e1c1b-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="e1c1b-103">コントロールを設定して、フォームの端に合わせて調整を行うことができます、<xref:System.Windows.Forms.Control.Dock%2A>です。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="e1c1b-104">このプロパティは、フォーム内のコントロールの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="e1c1b-105"><xref:System.Windows.Forms.Control.Dock%2A> プロパティには次の値のいずれかを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="e1c1b-106">設定</span><span class="sxs-lookup"><span data-stu-id="e1c1b-106">Setting</span></span>|<span data-ttu-id="e1c1b-107">コントロールへの影響</span><span class="sxs-lookup"><span data-stu-id="e1c1b-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="e1c1b-108">フォームの下部にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="e1c1b-109">フォームの残りの全スペースを埋めます。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="e1c1b-110">フォームの左側にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="e1c1b-111">指定された場所に表示されますどこにもドッキングせず、<xref:System.Windows.Forms.Control.Location%2A>です。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="e1c1b-112">フォームの右側にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="e1c1b-113">フォームの上部にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="e1c1b-114">これらの値は、コードでも設定できます。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-114">These values can also be set in code.</span></span> <span data-ttu-id="e1c1b-115">詳細については、次を参照してください。[する方法: コントロールをフォームの端を揃える](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-115">For more information, see [How to: Align a Control to the Edges of Forms](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1c1b-116">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e1c1b-117">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e1c1b-118">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="e1c1b-119">デザイン時に、コントロールの Dock プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="e1c1b-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="e1c1b-120">Windows フォーム デザイナーでコントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="e1c1b-121">**プロパティ**ウィンドウで、ドロップダウン リスト ボックスには、[次へ] をクリック、<xref:System.Windows.Forms.Control.Dock%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="e1c1b-122">6 つを表すグラフィカル インターフェイス<xref:System.Windows.Forms.Control.Dock%2A>設定が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="e1c1b-123">適切な設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="e1c1b-124">コントロールの設定で指定された方法でドッキングされます。</span><span class="sxs-lookup"><span data-stu-id="e1c1b-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c1b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1c1b-125">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e1c1b-126">方法: フォームの端に合わせてコントロールを配置する</span><span class="sxs-lookup"><span data-stu-id="e1c1b-126">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [<span data-ttu-id="e1c1b-127">チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="e1c1b-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="e1c1b-128">方法: Windows フォームにコントロールを固定する</span><span class="sxs-lookup"><span data-stu-id="e1c1b-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [<span data-ttu-id="e1c1b-129">方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="e1c1b-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="e1c1b-130">方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="e1c1b-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="e1c1b-131">チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="e1c1b-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="e1c1b-132">チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="e1c1b-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="e1c1b-133">デザイン時の Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="e1c1b-133">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
