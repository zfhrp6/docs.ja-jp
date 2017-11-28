---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a97899d544dcc0d9f9ad59cbb34a01da76ef5fe5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="3feeb-102">方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する</span><span class="sxs-lookup"><span data-stu-id="3feeb-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="3feeb-103">ユーザーが Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールに表示されるデータを確認するときに、1 つの列または列のセットを頻繁に参照しなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="3feeb-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="3feeb-104">たとえば、多数の列を含む顧客情報のテーブルを表示するとき、表示領域外にスクロールするには、他の列の有効化中に常に、顧客名を表示するため便利です。</span><span class="sxs-lookup"><span data-stu-id="3feeb-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="3feeb-105">この動作を実現するために、コントロールの列を固定することができます。</span><span class="sxs-lookup"><span data-stu-id="3feeb-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="3feeb-106">列を固定すると、左側 (右から左へ記述する言語のスクリプトでは右側) のすべての列も同様に固定されます。</span><span class="sxs-lookup"><span data-stu-id="3feeb-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="3feeb-107">固定された列は表示されたままになり、その他のすべての列はスクロールできます。</span><span class="sxs-lookup"><span data-stu-id="3feeb-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="3feeb-108">列の並べ替えが有効な場合、固定された列は、固定されていない列とは異なるグループとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="3feeb-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="3feeb-109">ユーザーは、どちらかのグループに列を再配置できますが、1 つのグループから別のグループに列を移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="3feeb-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="3feeb-110">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3feeb-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3feeb-111">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="3feeb-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3feeb-112">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3feeb-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3feeb-113">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3feeb-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3feeb-114">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3feeb-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="3feeb-115">デザイナーを使用して列を固定するには</span><span class="sxs-lookup"><span data-stu-id="3feeb-115">To freeze a column using the designer</span></span>  
  
1.  <span data-ttu-id="3feeb-116">スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の編集**です。</span><span class="sxs-lookup"><span data-stu-id="3feeb-116">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="3feeb-117">列を選択して、**選択されている列** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="3feeb-117">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="3feeb-118">**列プロパティ**グリッドで、設定、<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="3feeb-118">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3feeb-119">選択して追加する際、列を固定することも、 **Frozen**ボックスに、**列の追加** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="3feeb-119">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3feeb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3feeb-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3feeb-121">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="3feeb-121">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="3feeb-122">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の並べ替えを有効にする</span><span class="sxs-lookup"><span data-stu-id="3feeb-122">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="3feeb-123">方法: グローバリゼーション用の Windows フォームで右から左へテキストを表示</span><span class="sxs-lookup"><span data-stu-id="3feeb-123">How to: Display Right-to-Left Text in Windows Forms for Globalization</span></span>](http://msdn.microsoft.com/en-us/f0663385-2354-4c65-8676-706422283b14)  
 [<span data-ttu-id="3feeb-124">方法: Windows アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3feeb-124">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="3feeb-125">方法: Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="3feeb-125">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
