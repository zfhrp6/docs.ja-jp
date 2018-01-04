---
title: "方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする"
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
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7283ab53121ecf32fc43593d19121cc843b9c27b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8dc04-102">方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする</span><span class="sxs-lookup"><span data-stu-id="8dc04-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8dc04-103">場合によっては、ユーザーが <xref:System.Windows.Forms.DataGridView> コントロールに新しいデータ行を入力したり、既存の行を削除したりできないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc04-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8dc04-104"><xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティは新しいレコードのための行がコントロールの一番下に存在しているかどうかを示し、<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> プロパティは行を削除できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="8dc04-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="8dc04-105">次のコード例は、これらのプロパティを使用し、さらに <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> プロパティも設定して、コントロール全体を読み取り専用にします。</span><span class="sxs-lookup"><span data-stu-id="8dc04-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="8dc04-106">Visual Studio では、このタスクに対するサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8dc04-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="8dc04-107">参照してください[する方法: Windows フォーム DataGridView コントロールを使用して、デザイナーで防ぐ行の追加および削除](http://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="8dc04-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dc04-108">例</span><span class="sxs-lookup"><span data-stu-id="8dc04-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8dc04-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="8dc04-109">Compiling the Code</span></span>  
 <span data-ttu-id="8dc04-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8dc04-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8dc04-111">`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。</span><span class="sxs-lookup"><span data-stu-id="8dc04-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="8dc04-112"><xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="8dc04-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc04-113">参照</span><span class="sxs-lookup"><span data-stu-id="8dc04-113">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8dc04-114">Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能</span><span class="sxs-lookup"><span data-stu-id="8dc04-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
