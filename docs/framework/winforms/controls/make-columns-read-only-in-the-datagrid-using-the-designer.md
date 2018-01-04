---
title: "方法 : デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする"
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
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 426c47010a7b1d3f20700d8041ed882e149aaa7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="6a106-102">方法 : デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする</span><span class="sxs-lookup"><span data-stu-id="6a106-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="6a106-103">ユーザーが既定では、テキストと Windows フォームに表示される数値のデータ変更できる<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6a106-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6a106-104">変更できないデータを表示する場合は、読み取り専用のデータを含む列を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a106-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="6a106-105">完全に読み取り専用のコントロールを作成する方法については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールを使用して、デザイナーで防ぐ行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="6a106-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="6a106-106">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6a106-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6a106-107">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="6a106-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a106-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6a106-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6a106-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6a106-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6a106-110">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a106-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="6a106-111">デザイナーを使用して、列を読み取り専用にする</span><span class="sxs-lookup"><span data-stu-id="6a106-111">To make a column read-only by using the designer</span></span>  
  
1.  <span data-ttu-id="6a106-112">スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の編集**です。</span><span class="sxs-lookup"><span data-stu-id="6a106-112">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="6a106-113">列を選択して、**選択されている列** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="6a106-113">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="6a106-114">**列プロパティ**グリッドで、設定、<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="6a106-114">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a106-115">作成することも、列読み取り専用 を選択して追加すると、**読み取り専用** チェック ボックス、**列の追加** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="6a106-115">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a106-116">参照</span><span class="sxs-lookup"><span data-stu-id="6a106-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="6a106-117">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="6a106-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="6a106-118">方法: デザイナーを使用して Windows フォーム DataGridView コントロールで行が追加および削除されないようにする</span><span class="sxs-lookup"><span data-stu-id="6a106-118">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="6a106-119">方法: Windows アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="6a106-119">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="6a106-120">方法: Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="6a106-120">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
