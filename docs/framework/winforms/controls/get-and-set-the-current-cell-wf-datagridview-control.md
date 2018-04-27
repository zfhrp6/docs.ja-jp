---
title: '方法 : Windows フォーム DataGridView コントロールの現在のセルを取得および設定する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b53d135a1d019ce20dfc8c5c2c1ba59e5968306e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e009a-102">方法 : Windows フォーム DataGridView コントロールの現在のセルを取得および設定する</span><span class="sxs-lookup"><span data-stu-id="e009a-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e009a-103">対話、<xref:System.Windows.Forms.DataGridView>多くの場合、ことをプログラムによって検出されるセルが現在アクティブなが必要です。</span><span class="sxs-lookup"><span data-stu-id="e009a-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="e009a-104">また、現在のセルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e009a-104">You may also need to change the current cell.</span></span> <span data-ttu-id="e009a-105">これらのタスクを行うことができます、<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e009a-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e009a-106">行または列を持つ現在のセルを設定することはできません、<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>プロパティに設定`false`です。</span><span class="sxs-lookup"><span data-stu-id="e009a-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="e009a-107">によって、<xref:System.Windows.Forms.DataGridView>現在のセルを変更するコントロールの選択モードが選択を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e009a-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="e009a-108">詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールで選択モード](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="e009a-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="e009a-109">現在のセルをプログラムで取得するには</span><span class="sxs-lookup"><span data-stu-id="e009a-109">To get the current cell programmatically</span></span>  
  
-   <span data-ttu-id="e009a-110">使用して、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e009a-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="e009a-111">現在のセルをコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="e009a-111">To set the current cell programmatically</span></span>  
  
-   <span data-ttu-id="e009a-112">設定、<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e009a-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e009a-113">次のコード例では、現在のセルは行の 0、1 列目に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e009a-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e009a-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e009a-114">Compiling the Code</span></span>  
 <span data-ttu-id="e009a-115">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e009a-115">This example requires:</span></span>  
  
-   <span data-ttu-id="e009a-116"><xref:System.Windows.Forms.Button> という名前のコントロール`getCurrentCellButton`と`setCurrentCellButton`です。</span><span class="sxs-lookup"><span data-stu-id="e009a-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="e009a-117">Visual c# では、割り当てる必要がある、<xref:System.Windows.Forms.Control.Click>のコード例に関連付けられているイベント ハンドラーには、各ボタンのイベントです。</span><span class="sxs-lookup"><span data-stu-id="e009a-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
-   <span data-ttu-id="e009a-118">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="e009a-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="e009a-119"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="e009a-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e009a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e009a-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e009a-121">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="e009a-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="e009a-122">Windows フォーム DataGridView コントロールの選択モード</span><span class="sxs-lookup"><span data-stu-id="e009a-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
