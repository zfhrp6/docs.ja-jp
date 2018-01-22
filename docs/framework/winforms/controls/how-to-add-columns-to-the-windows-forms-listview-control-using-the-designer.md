---
title: "方法 :デザイナーを使って Windows フォーム ListView コントロールに列を追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 971d3918fd6085bea85e43183ea67745d40e51b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="496c0-102">方法 :デザイナーを使って Windows フォーム ListView コントロールに列を追加する</span><span class="sxs-lookup"><span data-stu-id="496c0-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="496c0-103">Windows フォーム<xref:System.Windows.Forms.ListView>コントロールが各リストの複数の列を表示できる項目の場合に、**詳細**ビュー。</span><span class="sxs-lookup"><span data-stu-id="496c0-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="496c0-104">列を使用すると、いくつかの種類の各リスト項目に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="496c0-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="496c0-105">たとえば、ファイルのリストには、ファイル名、ファイルの種類、サイズ、およびファイルの最終更新日を表示できます。</span><span class="sxs-lookup"><span data-stu-id="496c0-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="496c0-106">作成されると、列の設定方法の詳細については、次を参照してください。[する方法: Windows フォーム ListView コントロールでの列にサブ項目を表示](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="496c0-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
 <span data-ttu-id="496c0-107">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="496c0-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="496c0-108">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="496c0-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="496c0-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="496c0-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="496c0-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="496c0-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="496c0-111">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="496c0-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="496c0-112">デザイナーで列を追加するには</span><span class="sxs-lookup"><span data-stu-id="496c0-112">To add columns in the designer</span></span>  
  
1.  <span data-ttu-id="496c0-113">**プロパティ**ウィンドウで、設定コントロールの<xref:System.Windows.Forms.ListView.View%2A>プロパティを<xref:System.Windows.Forms.View.Details>です。</span><span class="sxs-lookup"><span data-stu-id="496c0-113">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="496c0-114">**プロパティ**ウィンドウで、をクリックして、**省略記号**ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に<xref:System.Windows.Forms.ListView.Columns%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="496c0-114">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     <span data-ttu-id="496c0-115">**ColumnHeader コレクション エディター**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="496c0-115">The **ColumnHeader Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="496c0-116">使用して、**追加**を新しい列を追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="496c0-116">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="496c0-117">列ヘッダーを選択し、そのテキスト (列のキャプション)、テキストの配置、および幅を設定できます。</span><span class="sxs-lookup"><span data-stu-id="496c0-117">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="496c0-118">参照</span><span class="sxs-lookup"><span data-stu-id="496c0-118">See Also</span></span>  
 [<span data-ttu-id="496c0-119">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="496c0-119">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="496c0-120">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="496c0-120">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="496c0-121">方法: Windows フォーム ListView コントロールの列にサブ項目を表示する</span><span class="sxs-lookup"><span data-stu-id="496c0-121">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="496c0-122">方法: Windows フォーム ListView コントロールのアイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="496c0-122">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="496c0-123">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="496c0-123">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
