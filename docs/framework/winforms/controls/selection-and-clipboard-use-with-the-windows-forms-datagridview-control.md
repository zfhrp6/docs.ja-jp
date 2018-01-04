---
title: "Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceea4108f39619ccbcbf0286905a94b8236607cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="d6f0f-102">Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用</span><span class="sxs-lookup"><span data-stu-id="d6f0f-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d6f0f-103">`DataGridView`コントロールでは、さまざまなユーザーがセル、行、および列を選択する方法を構成するためのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="d6f0f-104">たとえば、有効にできます 1 つまたは複数選択、行全体またはユーザーがセルをクリックしたときの列の選択または選択行全体または列のユーザーが、ヘッダーをクリックしたときにのみセルの選択もできます。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="d6f0f-105">選択範囲の独自のユーザー インターフェイスを提供する場合は、通常の選択を無効にし、すべての選択項目をプログラムで処理できます。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="d6f0f-106">さらに、選択した値をクリップボードにコピーするユーザーを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6f0f-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d6f0f-107">In This Section</span></span>  
 [<span data-ttu-id="d6f0f-108">Windows フォーム DataGridView コントロールの選択モード</span><span class="sxs-lookup"><span data-stu-id="d6f0f-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d6f0f-109">ユーザーと、コントロール内のプログラムの選択のためのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="d6f0f-110">方法: Windows フォーム DataGridView コントロールの選択モードを設定する</span><span class="sxs-lookup"><span data-stu-id="d6f0f-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d6f0f-111">ユーザーがセルをクリックしたときに、単一行の選択 のコントロールを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="d6f0f-112">方法: Windows フォーム DataGridView コントロールの選択されたセル、行、および列を取得する</span><span class="sxs-lookup"><span data-stu-id="d6f0f-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="d6f0f-113">選択したセル、行、および列のコレクションを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="d6f0f-114">方法: ユーザーが、Windows フォーム DataGridView コントロールからクリップボードに複数のセルをコピーできるようにする</span><span class="sxs-lookup"><span data-stu-id="d6f0f-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="d6f0f-115">コントロールでのクリップボードのサポートを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d6f0f-116">参照</span><span class="sxs-lookup"><span data-stu-id="d6f0f-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="d6f0f-117"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="d6f0f-118">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="d6f0f-119">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="d6f0f-120">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewSelectedCellCollection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="d6f0f-121">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewSelectedRowCollection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="d6f0f-122">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d6f0f-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f0f-123">参照</span><span class="sxs-lookup"><span data-stu-id="d6f0f-123">See Also</span></span>  
 [<span data-ttu-id="d6f0f-124">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="d6f0f-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="d6f0f-125">Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理</span><span class="sxs-lookup"><span data-stu-id="d6f0f-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
