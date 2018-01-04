---
title: "方法 : Windows フォーム DataGridView コントロールの編集モードを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42773e29d7071c5bc5f3d5de3660c9891788b422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="fe9dd-102">方法 : Windows フォーム DataGridView コントロールの編集モードを指定する</span><span class="sxs-lookup"><span data-stu-id="fe9dd-102">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fe9dd-103">既定では、ユーザーが、現在の内容を編集できる<xref:System.Windows.Forms.DataGridView>テキスト ボックスのセルに入力するか、F2 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-103">By default, users can edit the contents of the current <xref:System.Windows.Forms.DataGridView> text box cell by typing in it or pressing F2.</span></span> <span data-ttu-id="fe9dd-104">これにより、セル編集モードで、以下の条件をすべて満たしている場合。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-104">This puts the cell in edit mode if all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="fe9dd-105">基になるデータ ソースは、編集をサポートします。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-105">The underlying data source supports editing.</span></span>  
  
-   <span data-ttu-id="fe9dd-106"><xref:System.Windows.Forms.DataGridView>制御を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-106">The <xref:System.Windows.Forms.DataGridView> control is enabled.</span></span>  
  
-   <span data-ttu-id="fe9dd-107"><xref:System.Windows.Forms.DataGridView.EditMode%2A>プロパティの値が<xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>です。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-107">The <xref:System.Windows.Forms.DataGridView.EditMode%2A> property value is not <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.</span></span>  
  
-   <span data-ttu-id="fe9dd-108">`ReadOnly`セル、行、列、およびコントロールのプロパティは、すべてのセットを`false`です。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-108">The `ReadOnly` properties of the cell, row, column, and control are all set to `false`.</span></span>  
  
 <span data-ttu-id="fe9dd-109">編集モードでは、ユーザーは、セルの値が変更され、セル値は元に戻すには、esc キー、変更をコミットするには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-109">In edit mode, the user can change the cell value and press ENTER to commit the change or ESC to revert the cell to its original value.</span></span>  
  
 <span data-ttu-id="fe9dd-110">構成することができます、<xref:System.Windows.Forms.DataGridView>制御と現在のセルになったらすぐにセルが編集モードに入るようにします。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-110">You can configure a <xref:System.Windows.Forms.DataGridView> control so that a cell enters edit mode as soon as it becomes the current cell.</span></span> <span data-ttu-id="fe9dd-111">ENTER キーおよび ESC キーの動作は変更されていないこのケースが、値がコミットまたは元に戻すした後に、セルが編集モードに残ります。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-111">The behavior of the ENTER and ESC keys is unchanged in this case, but the cell remains in edit mode after the value is committed or reverted.</span></span> <span data-ttu-id="fe9dd-112">セルまたは f2 キーを押すときにのみユーザーが入力されたときにのみセルが編集モードに切り替わるようにコントロールを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-112">You can also configure the control so that cells enter edit mode only when users type in the cell or only when users press F2.</span></span> <span data-ttu-id="fe9dd-113">最後に、セルを防ぐため除くを呼び出すと編集モードに入ることができます、<xref:System.Windows.Forms.DataGridView.BeginEdit%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-113">Finally, you can prevent cells from entering edit mode except when you call the <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> method.</span></span>  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a><span data-ttu-id="fe9dd-114">DataGridView コントロールの編集モードを変更するには</span><span class="sxs-lookup"><span data-stu-id="fe9dd-114">To change the edit mode of a DataGridView control</span></span>  
  
-   <span data-ttu-id="fe9dd-115">設定、<xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>プロパティを適切な<xref:System.Windows.Forms.DataGridViewEditMode>列挙します。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-115">Set the <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> property to the appropriate <xref:System.Windows.Forms.DataGridViewEditMode> enumeration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe9dd-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="fe9dd-116">Compiling the Code</span></span>  
 <span data-ttu-id="fe9dd-117">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-117">This example requires:</span></span>  
  
-   <span data-ttu-id="fe9dd-118">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="fe9dd-119"><xref:System> アセンブリおよび <xref:System.Windows.Forms> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="fe9dd-119">References to the <xref:System> and <xref:System.Windows.Forms> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9dd-120">参照</span><span class="sxs-lookup"><span data-stu-id="fe9dd-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="fe9dd-121">Windows フォーム DataGridView コントロールでのデータ入力</span><span class="sxs-lookup"><span data-stu-id="fe9dd-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
