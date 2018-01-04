---
title: "Windows フォーム DataGridView コントロール内の列と行のサイズ変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1c11ca487003e57a499b3ff46178350e6aad404
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="baa0d-102">Windows フォーム DataGridView コントロール内の列と行のサイズ変更</span><span class="sxs-lookup"><span data-stu-id="baa0d-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="baa0d-103">`DataGridView`コントロールには、その列と行のサイズ変更動作をカスタマイズするためのさまざまなオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="baa0d-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="baa0d-104">通常、`DataGridView`セル サイズを変更しないでその内容を基にします。</span><span class="sxs-lookup"><span data-stu-id="baa0d-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="baa0d-105">代わりに、それらはクリップ表示値があるセルよりも大きいです。</span><span class="sxs-lookup"><span data-stu-id="baa0d-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="baa0d-106">コンテンツは、文字列として表示されることができます、セルにより、ツールヒントに表示します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="baa0d-107">既定では、ユーザーは、行、列、および詳細情報を表示するには、マウスでのヘッダー区分線をドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="baa0d-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="baa0d-108">ユーザーは、サイズが自動的にその内容に基づいて関連付けられている行、列、またはヘッダーのバンドの区分線をダブルクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="baa0d-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="baa0d-109">`DataGridView`コントロールには、プロパティ、メソッド、およびカスタマイズしたり、これらすべてのユーザー向け動作を無効にするようにイベントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="baa0d-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="baa0d-110">さらに、プログラムでサイズを変更する行、列、およびその内容に合わせてヘッダーまたはサイズが自動的に自身の内容が変更されるたびにそれらを構成できます。</span><span class="sxs-lookup"><span data-stu-id="baa0d-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="baa0d-111">指定した比率で、コントロールの使用可能な幅を自動的に分割する列を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="baa0d-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="baa0d-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="baa0d-112">In This Section</span></span>  
 [<span data-ttu-id="baa0d-113">Windows フォーム DataGridView コントロールのサイズ変更オプション</span><span class="sxs-lookup"><span data-stu-id="baa0d-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="baa0d-114">サイズ変更行、列、およびヘッダーのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="baa0d-115">また、サイズ変更に関連するプロパティやメソッドの詳細を提供し、一般的な使用シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="baa0d-116">Windows フォーム DataGridView コントロールの列フィル モード</span><span class="sxs-lookup"><span data-stu-id="baa0d-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="baa0d-117">列フィル モードの詳細、および列フィル モードおよびその他のモードを実験に使用できるデモ用のコードを説明します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="baa0d-118">方法: Windows フォーム DataGridView コントロールのサイズ変更モードを設定する</span><span class="sxs-lookup"><span data-stu-id="baa0d-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="baa0d-119">一般的な用途のサイズ変更モードを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="baa0d-120">方法: Windows フォームの DataGridView コントロールの内容に合わせてセルのサイズをプログラムで変更する</span><span class="sxs-lookup"><span data-stu-id="baa0d-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="baa0d-121">プログラムによるサイズ変更をテストに使用できるデモ用のコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="baa0d-122">方法: Windows フォームの DataGridView コントロールの内容変更時にセルのサイズを自動的に変更する</span><span class="sxs-lookup"><span data-stu-id="baa0d-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="baa0d-123">自動サイズ変更モードを実験に使用できるデモ用のコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="baa0d-124">参照</span><span class="sxs-lookup"><span data-stu-id="baa0d-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="baa0d-125"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="baa0d-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa0d-126">参照</span><span class="sxs-lookup"><span data-stu-id="baa0d-126">See Also</span></span>  
 [<span data-ttu-id="baa0d-127">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="baa0d-127">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
