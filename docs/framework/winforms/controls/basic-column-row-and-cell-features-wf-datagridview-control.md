---
title: "Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eebd0f36fbf1bf3bfc37b8fa836d318a9b8ac007
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e99bf-102">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="e99bf-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e99bf-103">多くの基本的な動作の`DataGridView`セル、行、および列は、1 つのプロパティを設定して変更できます。</span><span class="sxs-lookup"><span data-stu-id="e99bf-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="e99bf-104">このセクションのトピックでは、いくつかの最も一般的に使用されるこれらの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e99bf-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e99bf-105">In This Section</span></span>  
 [<span data-ttu-id="e99bf-106">方法: Windows フォームの DataGridView コントロールの列を非表示にする</span><span class="sxs-lookup"><span data-stu-id="e99bf-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e99bf-107">特定の列をコントロールに表示されないようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="e99bf-108">方法: Windows フォーム DataGridView コントロールの列ヘッダーを非表示にする</span><span class="sxs-lookup"><span data-stu-id="e99bf-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e99bf-109">列ヘッダーをコントロールに表示されないようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="e99bf-110">方法: Windows フォーム DataGridView コントロールの列の並べ替えを有効にする</span><span class="sxs-lookup"><span data-stu-id="e99bf-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e99bf-111">ユーザーがコントロール内の列を再配置を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="e99bf-112">方法: Windows フォーム DataGridView コントロールの列を固定する</span><span class="sxs-lookup"><span data-stu-id="e99bf-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e99bf-113">説明 1 つまたは複数の隣接する列をスクロールできないようにする方法です。</span><span class="sxs-lookup"><span data-stu-id="e99bf-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="e99bf-114">方法: Windows フォームの DataGridView コントロールで列を読み取り専用にする</span><span class="sxs-lookup"><span data-stu-id="e99bf-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e99bf-115">ユーザーがコントロール内の特定の列を編集することを防止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="e99bf-116">方法: Windows フォーム DataGridView コントロールで行が追加および削除されないようにする</span><span class="sxs-lookup"><span data-stu-id="e99bf-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="e99bf-117">ユーザーが行を追加することを防止するコントロールの下部にある新しいレコードの行を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="e99bf-118">ユーザーが行を削除することを防止する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="e99bf-119">方法: Windows フォーム DataGridView コントロールの現在のセルを取得および設定する</span><span class="sxs-lookup"><span data-stu-id="e99bf-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="e99bf-120">現在フォーカスがコントロール内のセルにアクセスする方法をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="e99bf-121">方法: Windows フォーム DataGridView コントロールのセルにイメージを表示する</span><span class="sxs-lookup"><span data-stu-id="e99bf-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e99bf-122">すべてのセルにアイコンを表示するイメージ列を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e99bf-123">参照</span><span class="sxs-lookup"><span data-stu-id="e99bf-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="e99bf-124">コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e99bf-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e99bf-125">Related Sections</span></span>  
 [<span data-ttu-id="e99bf-126">Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定</span><span class="sxs-lookup"><span data-stu-id="e99bf-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e99bf-127">コントロールの基本の外観およびセル データの書式設定を変更する方法を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="e99bf-128">Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="e99bf-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="e99bf-129">セル、行、および列オブジェクトを使用したプログラミング方法を説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="e99bf-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e99bf-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="e99bf-130">See Also</span></span>  
 [<span data-ttu-id="e99bf-131">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="e99bf-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="e99bf-132">Windows フォーム DataGridView コントロールの列型</span><span class="sxs-lookup"><span data-stu-id="e99bf-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
