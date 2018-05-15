---
title: '方法 : DataRepeater コントロールのレイアウトを変更する (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: fa780ee40171143c17b5bdbda4a97179ed5f2151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="0b443-102">方法 : DataRepeater コントロールのレイアウトを変更する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="0b443-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="0b443-103"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを垂直方向 (垂直方向にスクロールを項目) または水平方向 (水平方向にスクロールを項目) のいずれかで表示されることができますの向きです。</span><span class="sxs-lookup"><span data-stu-id="0b443-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="0b443-104">デザイン時または実行時に印刷の向きを変更するには変更することによって、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0b443-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="0b443-105">変更した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>実行時にプロパティをすることもサイズを変更する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>および子コントロールを再配置します。</span><span class="sxs-lookup"><span data-stu-id="0b443-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b443-106">上のコントロールの位置を変更する場合、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 、実行時に呼び出す必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>と<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>メソッドの先頭と末尾のコントロールが再配置されるコード ブロックにします。</span><span class="sxs-lookup"><span data-stu-id="0b443-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="0b443-107">デザイン時レイアウトを変更するには</span><span class="sxs-lookup"><span data-stu-id="0b443-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="0b443-108">Windows フォーム デザイナーで、選択、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="0b443-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b443-109">外側の境界線を選択する必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>上ではなく、コントロールの下の領域内をクリックするコントロール<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>領域。</span><span class="sxs-lookup"><span data-stu-id="0b443-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="0b443-110">[プロパティ] ウィンドウで、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティを<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>または<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>です。</span><span class="sxs-lookup"><span data-stu-id="0b443-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="0b443-111">実行時にレイアウトを変更するには</span><span class="sxs-lookup"><span data-stu-id="0b443-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="0b443-112">次のコードを追加するボタンまたはメニュー`Click`イベントのハンドラー。</span><span class="sxs-lookup"><span data-stu-id="0b443-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="0b443-113">サイズを変更する例」のセクションで示すようなコードを追加する必要はほとんどの場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>および新しい向きに合わせてコントロールを再配置します。</span><span class="sxs-lookup"><span data-stu-id="0b443-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b443-114">例</span><span class="sxs-lookup"><span data-stu-id="0b443-114">Example</span></span>  
 <span data-ttu-id="0b443-115">次の例に応答する方法を示しています、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged>イベント ハンドラーでイベント。</span><span class="sxs-lookup"><span data-stu-id="0b443-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="0b443-116">この例では、ある必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>という名前のコントロール`DataRepeater1`フォームでその<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>2 つが含まれて<xref:System.Windows.Forms.TextBox>という名前のコントロール`TextBox1`と`TextBox2`です。</span><span class="sxs-lookup"><span data-stu-id="0b443-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0b443-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b443-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [<span data-ttu-id="0b443-118">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="0b443-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="0b443-119">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0b443-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="0b443-120">方法: DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="0b443-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
