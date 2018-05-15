---
title: '方法 : TableLayoutPanel コントロールの列と行を編集する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 763d5df6c49d45f7ee305f4a3be0a1f0a2539872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="04f87-102">方法 : TableLayoutPanel コントロールの列と行を編集する</span><span class="sxs-lookup"><span data-stu-id="04f87-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="04f87-103">コレクション エディターを使用することができます、<xref:System.Windows.Forms.TableLayoutPanel>と呼ばれるコントロール、**列と行のスタイル**ダイアログ ボックスで、行と、コントロールの列を編集します。</span><span class="sxs-lookup"><span data-stu-id="04f87-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04f87-104">を複数の行または列の span を制御する場合は、設定、`RowSpan`と`ColumnSpan`コントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="04f87-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="04f87-105">詳細については、「 [チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04f87-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="04f87-106">セル内のコントロールを配置する場合、またはセル内で stretch を制御する場合は、使用、コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="04f87-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="04f87-107">詳細については、「 [チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04f87-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="04f87-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="04f87-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="04f87-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04f87-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="04f87-110">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04f87-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="04f87-111">行と列を編集するには</span><span class="sxs-lookup"><span data-stu-id="04f87-111">To edit rows and columns</span></span>  
  
1.  <span data-ttu-id="04f87-112">ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="04f87-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="04f87-113">クリックして、<xref:System.Windows.Forms.TableLayoutPanel>コントロールのスマート タグ グリフ (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) を選択して**編集行と列**を開くには、 **列と行のスタイル** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="04f87-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="04f87-114">右クリックで、<xref:System.Windows.Forms.TableLayoutPanel>してコントロールを選択**編集行と列**ショートカット メニューからです。</span><span class="sxs-lookup"><span data-stu-id="04f87-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="04f87-115">列を追加または削除、選択**列**から、**メンバー型**ドロップダウン リスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="04f87-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4.  <span data-ttu-id="04f87-116">追加したり、行を削除する選択**行**から、**メンバー型**ドロップダウン リスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="04f87-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5.  <span data-ttu-id="04f87-117">クリックして、**追加**の末尾に行または列を追加するボタン、**メンバー**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="04f87-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6.  <span data-ttu-id="04f87-118">をクリックして、**挿入**一覧で行または現在選択されている項目の前に列を追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="04f87-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7.  <span data-ttu-id="04f87-119">行または列を追加する場合は、選択、**サイズの種類**新しい行または列に対応します。</span><span class="sxs-lookup"><span data-stu-id="04f87-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="04f87-120">詳細については、「<xref:System.Windows.Forms.SizeType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04f87-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8.  <span data-ttu-id="04f87-121">行または列を削除する をクリックして、**削除**で現在選択されている項目を削除するボタン、**メンバー**  ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="04f87-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f87-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="04f87-122">See Also</span></span>  
 <xref:System.Windows.Forms.SizeType>  
 [<span data-ttu-id="04f87-123">TableLayoutPanel コントロール</span><span class="sxs-lookup"><span data-stu-id="04f87-123">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
