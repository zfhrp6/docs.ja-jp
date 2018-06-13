---
title: '方法 : Windows フォーム内の ToolStrip 項目の間隔と配置を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 7951a545fd8cbd0ae30907922551216161171a8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531265"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="011ab-102">方法 : Windows フォーム内の ToolStrip 項目の間隔と配置を変更する</span><span class="sxs-lookup"><span data-stu-id="011ab-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="011ab-103"><xref:System.Windows.Forms.ToolStrip>コントロールがサイズ変更の間隔などのレイアウト機能を完全にサポート<xref:System.Windows.Forms.ToolStripItem>互いを基準として、コントロールの配置のコントロールに対して、<xref:System.Windows.Forms.ToolStrip>とを基準とするコントロールの間の間隔、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="011ab-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="011ab-104">の既定値、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティは`true`、コントロールはサイズが自動的に設定しない限り、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="011ab-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="011ab-105">ToolStripItem を手動で調整するには</span><span class="sxs-lookup"><span data-stu-id="011ab-105">To manually size a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="011ab-106">設定、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティを`false`関連付けられたコントロール。</span><span class="sxs-lookup"><span data-stu-id="011ab-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  <span data-ttu-id="011ab-107">設定、<xref:System.Windows.Forms.ToolStripItem.Size%2A>プロパティに関連付けられた希望どおり<xref:System.Windows.Forms.ToolStripItem>です。</span><span class="sxs-lookup"><span data-stu-id="011ab-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="011ab-108">ToolStripItem の間隔を設定するには</span><span class="sxs-lookup"><span data-stu-id="011ab-108">To set the spacing of a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="011ab-109">ピクセル単位で、目的の値を挿入、<xref:System.Windows.Forms.ToolStripItem.Margin%2A>関連付けられたコントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="011ab-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="011ab-110">値、<xref:System.Windows.Forms.ToolStripItem.Margin%2A>プロパティは、この順序で、項目と隣接するアイテムの間隔を指定します。 左、上、右、および下です。</span><span class="sxs-lookup"><span data-stu-id="011ab-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="011ab-111">コマンド バーの右側に ToolStripItem を配置するには</span><span class="sxs-lookup"><span data-stu-id="011ab-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1.  <span data-ttu-id="011ab-112">設定、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemAlignment.Right>関連付けられたコントロール。</span><span class="sxs-lookup"><span data-stu-id="011ab-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="011ab-113">既定では、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>に設定されている<xref:System.Windows.Forms.ToolStripItemAlignment.Left>の左側にコントロールを配置する、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="011ab-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="011ab-114">ToolStrip の ToolStrip 項目を整理するには</span><span class="sxs-lookup"><span data-stu-id="011ab-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="011ab-115">設定、<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>プロパティの値を<xref:System.Windows.Forms.ToolStripLayoutStyle>します。</span><span class="sxs-lookup"><span data-stu-id="011ab-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="011ab-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="011ab-116">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="011ab-117">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="011ab-117">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="011ab-118">ToolStrip コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="011ab-118">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="011ab-119">ToolStrip テクノロジの概要</span><span class="sxs-lookup"><span data-stu-id="011ab-119">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
