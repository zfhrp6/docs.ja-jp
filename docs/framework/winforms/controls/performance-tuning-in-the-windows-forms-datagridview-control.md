---
title: "Windows フォーム DataGridView コントロールでのパフォーマンス チューニング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452c55d38a896ec96e0992a4b9826f08dc4caa0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="72db6-102">Windows フォーム DataGridView コントロールでのパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="72db6-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="72db6-103">大量のデータを使用するときに、`DataGridView`コントロールが大量のオーバーヘッドが、メモリを使用できるは、慎重に使用する場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="72db6-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="72db6-104">メモリの制限とのクライアントではメモリ消費の多い機能を回避することでこのオーバーヘッドの一部を回避できます。</span><span class="sxs-lookup"><span data-stu-id="72db6-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="72db6-105">データ メンテナンスの一部またはすべてを管理することもでき、シナリオでは、メモリ使用量をカスタマイズするために仮想モードを使用して自分でタスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="72db6-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72db6-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="72db6-106">In This Section</span></span>  
 [<span data-ttu-id="72db6-107">Windows フォーム DataGridView コントロールを拡張するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="72db6-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="72db6-108">使用する方法について説明します、`DataGridView`大量のデータを操作するときに、不要なメモリの使用状況とパフォーマンスの低下を回避する方法で制御します。</span><span class="sxs-lookup"><span data-stu-id="72db6-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="72db6-109">Windows フォーム DataGridView コントロールでの仮想モード</span><span class="sxs-lookup"><span data-stu-id="72db6-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="72db6-110">仮想モードを使用して補完したり、標準的なデータ バインディング機構を置換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72db6-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="72db6-111">チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードの実装</span><span class="sxs-lookup"><span data-stu-id="72db6-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="72db6-112">複数の仮想モード イベントのハンドラーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72db6-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="72db6-113">行レベルのロールバックとユーザーを編集するためのコミットを実装する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="72db6-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="72db6-114">Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装</span><span class="sxs-lookup"><span data-stu-id="72db6-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="72db6-115">必要に応じて、使用可能なクライアントのメモリを格納できるよりもを表示する複数のデータがある場合に有用なデータを読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72db6-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="72db6-116">参照</span><span class="sxs-lookup"><span data-stu-id="72db6-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="72db6-117"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="72db6-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="72db6-118">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="72db6-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72db6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="72db6-119">See Also</span></span>  
 [<span data-ttu-id="72db6-120">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="72db6-120">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="72db6-121">Windows フォーム DataGridView コントロールでのデータ表示モード</span><span class="sxs-lookup"><span data-stu-id="72db6-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
