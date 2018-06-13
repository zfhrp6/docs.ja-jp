---
title: '方法 : MenuStrip にオプション ボタンを表示する (Windows フォーム)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: da2bb7edceaf83aa5178618fd4098631d65a7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538029"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="cac8f-102">方法 : MenuStrip にオプション ボタンを表示する (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="cac8f-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="cac8f-103">オプション ボタン、オプション ボタンとも呼ばれるは、ユーザーが一度に 1 つだけを選択する点を除いて、チェック ボックスに似ています。</span><span class="sxs-lookup"><span data-stu-id="cac8f-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="cac8f-104">既定では、<xref:System.Windows.Forms.ToolStripMenuItem>クラスは、オプション ボタンの動作を提供していない、このクラスのメニュー項目にオプション ボタンの動作を実装するカスタマイズ可能なチェック ボックスの動作を提供する<xref:System.Windows.Forms.MenuStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="cac8f-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="cac8f-105">ときに、<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>メニュー項目のプロパティは`true`ユーザーがアイテムをクリックしてチェック マークの表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="cac8f-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="cac8f-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>プロパティは、項目の現在の状態を示します。</span><span class="sxs-lookup"><span data-stu-id="cac8f-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="cac8f-107">動作を実装する基本のオプション ボタン、項目が選択されているときに設定することを確認する必要があります、<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>に以前に選択した項目のプロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="cac8f-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="cac8f-108">次の手順がこれを実装する方法を説明し、継承するクラスの追加機能、<xref:System.Windows.Forms.ToolStripMenuItem>クラスです。</span><span class="sxs-lookup"><span data-stu-id="cac8f-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="cac8f-109">`ToolStripRadioButtonMenuItem`などの上書きをメンバー クラス<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>と<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>選択の動作およびオプション ボタンの外観を提供します。</span><span class="sxs-lookup"><span data-stu-id="cac8f-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="cac8f-110">さらに、このクラスは、オーバーライド、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>親項目が選択されていないプロパティを [オプション] サブメニューでは無効になります。</span><span class="sxs-lookup"><span data-stu-id="cac8f-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="cac8f-111">オプション ボタンの選択の動作を実装するには</span><span class="sxs-lookup"><span data-stu-id="cac8f-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="cac8f-112">初期化、<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>プロパティを`true`項目の選択を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cac8f-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="cac8f-113">上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>新しい項目が選択されているときに、以前に選択した項目の選択をクリアします。</span><span class="sxs-lookup"><span data-stu-id="cac8f-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="cac8f-114">上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>は既に選択されている項目をクリックすることを確認するメソッドは、選択範囲をクリアされません。</span><span class="sxs-lookup"><span data-stu-id="cac8f-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="cac8f-115">オプション ボタンの項目の外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="cac8f-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="cac8f-116">上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>を使用して、オプション ボタンの既定のチェック マークするメソッド、<xref:System.Windows.Forms.RadioButtonRenderer>クラスです。</span><span class="sxs-lookup"><span data-stu-id="cac8f-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="cac8f-117">上書き、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>、 <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>、および<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>マウスの状態を追跡していることを確認する方法、<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>メソッドは、正しいオプション ボタンの状態を描画します。</span><span class="sxs-lookup"><span data-stu-id="cac8f-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="cac8f-118">親項目が選択されていないときに、サブメニューのオプションを無効にするには</span><span class="sxs-lookup"><span data-stu-id="cac8f-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="cac8f-119">上書き、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティ両方を含む親項目にある場合に、項目が無効にできるように、<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>の値`true`と<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>の値`false`です。</span><span class="sxs-lookup"><span data-stu-id="cac8f-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="cac8f-120">上書き、<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>をサブスクライブするメソッド、<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>親アイテムのイベントです。</span><span class="sxs-lookup"><span data-stu-id="cac8f-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="cac8f-121">親項目のハンドラーで<xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged>イベント、新しい有効な状態で画面を更新する項目が無効にします。</span><span class="sxs-lookup"><span data-stu-id="cac8f-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="cac8f-122">例</span><span class="sxs-lookup"><span data-stu-id="cac8f-122">Example</span></span>  
 <span data-ttu-id="cac8f-123">次のコード例は、完全な`ToolStripRadioButtonMenuItem`クラス、および<xref:System.Windows.Forms.Form>クラスと`Program`オプション ボタンの動作を確認するクラス。</span><span class="sxs-lookup"><span data-stu-id="cac8f-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cac8f-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="cac8f-124">Compiling the Code</span></span>  
 <span data-ttu-id="cac8f-125">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cac8f-125">This example requires:</span></span>  
  
-   <span data-ttu-id="cac8f-126">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="cac8f-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac8f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="cac8f-127">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [<span data-ttu-id="cac8f-128">MenuStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="cac8f-128">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [<span data-ttu-id="cac8f-129">方法: カスタムの ToolStripRenderer を実装する</span><span class="sxs-lookup"><span data-stu-id="cac8f-129">How to: Implement a Custom ToolStripRenderer</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
