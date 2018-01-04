---
title: "Windows フォームの DataGridView コントロールでのデータの並べ替え"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2327c6d9696bc5fb54943eb8bbce9d4795a378b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="658de-102">Windows フォームの DataGridView コントロールでのデータの並べ替え</span><span class="sxs-lookup"><span data-stu-id="658de-102">Sorting Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="658de-103">既定では、ユーザーが内のデータを並べ替えることができます、`DataGridView`テキスト ボックスの列の見出しをクリックして制御します。</span><span class="sxs-lookup"><span data-stu-id="658de-103">By default, users can sort the data in a `DataGridView` control by clicking the header of a text box column.</span></span> <span data-ttu-id="658de-104">変更することができます、`SortMode`これを行う方が良い場合、その他の列の型を並べ替えるにはユーザーを許可する特定の列のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="658de-104">You can modify the `SortMode` property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="658de-105">並べ替えることもできますデータ プログラムで、任意の列または複数の列です。</span><span class="sxs-lookup"><span data-stu-id="658de-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="658de-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="658de-106">In This Section</span></span>  
 [<span data-ttu-id="658de-107">Windows フォーム DataGridView コントロール内の列の並べ替えモード</span><span class="sxs-lookup"><span data-stu-id="658de-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="658de-108">コントロール内のデータを並べ替えるためのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="658de-108">Describes the options for sorting data in the control.</span></span>  
  
 [<span data-ttu-id="658de-109">方法: Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する</span><span class="sxs-lookup"><span data-stu-id="658de-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 <span data-ttu-id="658de-110">既定では並べ替えできない列で並べ替えを行うユーザーを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="658de-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>  
  
 [<span data-ttu-id="658de-111">方法: Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="658de-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="658de-112">プログラムでデータを並べ替える方法を使用して並べ替えをカスタマイズする方法について説明、<xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType>イベントまたは実装することによって、<xref:System.Collections.IComparer>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="658de-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="658de-113">参照</span><span class="sxs-lookup"><span data-stu-id="658de-113">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="658de-114"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="658de-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <span data-ttu-id="658de-115">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="658de-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="658de-116">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="658de-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumnSortMode>  
 <span data-ttu-id="658de-117">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumnSortMode>列挙します。</span><span class="sxs-lookup"><span data-stu-id="658de-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658de-118">参照</span><span class="sxs-lookup"><span data-stu-id="658de-118">See Also</span></span>  
 [<span data-ttu-id="658de-119">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="658de-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="658de-120">Windows フォーム DataGridView コントロールの列型</span><span class="sxs-lookup"><span data-stu-id="658de-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
