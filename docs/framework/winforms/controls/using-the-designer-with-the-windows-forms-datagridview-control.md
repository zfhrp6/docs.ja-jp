---
title: "Windows フォーム DataGridView コントロールでのデザイナーの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tables [Windows Forms]
- DataGridView control [Windows Forms], designer support
- formatting [Windows Forms]
ms.assetid: b66057a6-5983-4864-b4e7-8cbc88a7010c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9df10ecabc8f61c3ef984adb6466f195395fd181
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-designer-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="ca266-102">Windows フォーム DataGridView コントロールでのデザイナーの使用</span><span class="sxs-lookup"><span data-stu-id="ca266-102">Using the Designer with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ca266-103">Visual Studio のデザイナーのサポートを提供、`DataGridView`コントロールのコードを記述することがなく多数のセットアップ タスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="ca266-103">Visual Studio provides designer support for the `DataGridView` control that enables you to perform many setup tasks without writing code.</span></span> <span data-ttu-id="ca266-104">これらのタスクには、データを表示する列の変更、データ ソースにコントロールが使用されるバインディングとコントロールの基本的な動作と外観を調整することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ca266-104">These tasks include binding the control to a data source, modifying the columns used to display data, and adjusting the appearance and basic behavior of the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca266-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ca266-105">In This Section</span></span>  
 [<span data-ttu-id="ca266-106">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="ca266-106">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-107">使用する方法について説明します、**列の追加**と**列の編集** ダイアログ ボックスを作成し、列のコレクションを変更します。</span><span class="sxs-lookup"><span data-stu-id="ca266-107">Describes how to use the **Add Columns** and **Edit Columns** dialog boxes to populate and modify the columns collection.</span></span>  
  
 [<span data-ttu-id="ca266-108">方法: デザイナーを使用してデータを Windows フォーム DataGridView コントロールにバインドする</span><span class="sxs-lookup"><span data-stu-id="ca266-108">How to: Bind Data to the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-data-to-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-109">使用する方法について説明します、**データ ソースの選択**データに接続するコントロールのスマート タグ オプション。</span><span class="sxs-lookup"><span data-stu-id="ca266-109">Describes how to use the **Choose Data Source** option on the control's smart tag to connect to data.</span></span>  
  
 [<span data-ttu-id="ca266-110">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する</span><span class="sxs-lookup"><span data-stu-id="ca266-110">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-111">使用する方法について説明します、**列の編集**列を並べ替える ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="ca266-111">Describes how to use the **Edit Columns** dialog box to rearrange columns.</span></span>  
  
 [<span data-ttu-id="ca266-112">方法: デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する</span><span class="sxs-lookup"><span data-stu-id="ca266-112">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 <span data-ttu-id="ca266-113">使用する方法について説明します、**列の編集**列の型を変更するダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="ca266-113">Describes how to use the **Edit Columns** dialog box to change column types.</span></span>  
  
 [<span data-ttu-id="ca266-114">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列の並べ替えを有効にする</span><span class="sxs-lookup"><span data-stu-id="ca266-114">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-115">コントロールのスマート タグを使用して、ユーザーが列を再配置を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca266-115">Describes how to use the control's smart tag to enable users to rearrange columns.</span></span>  
  
 [<span data-ttu-id="ca266-116">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する</span><span class="sxs-lookup"><span data-stu-id="ca266-116">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-117">使用する方法について説明します、**列の編集**を特定の列がスクロールすることを防ぐために ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="ca266-117">Describes how to use the **Edit Columns** dialog box to prevent specific columns from scrolling.</span></span>  
  
 [<span data-ttu-id="ca266-118">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を非表示にする</span><span class="sxs-lookup"><span data-stu-id="ca266-118">How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-119">使用する方法について説明します、**列の編集** ダイアログ ボックスの特定の列を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="ca266-119">Describes how to use the **Edit Columns** dialog box to hide specific columns.</span></span>  
  
 [<span data-ttu-id="ca266-120">方法: デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする</span><span class="sxs-lookup"><span data-stu-id="ca266-120">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-121">使用する方法について説明します、**列の編集**特定の列に値を編集できないようにする ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="ca266-121">Describes how to use the **Edit Columns** dialog box to prevent users from editing values in specific columns.</span></span>  
  
 [<span data-ttu-id="ca266-122">方法: デザイナーを使用して Windows フォーム DataGridView コントロールで行が追加および削除されないようにする</span><span class="sxs-lookup"><span data-stu-id="ca266-122">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-123">コントロールのスマート タグを使用してユーザーを追加または行の削除を防止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca266-123">Describes how to use the control's smart tag to prevent users from adding or deleting rows.</span></span>  
  
 [<span data-ttu-id="ca266-124">方法: デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する</span><span class="sxs-lookup"><span data-stu-id="ca266-124">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 <span data-ttu-id="ca266-125">使用する方法について説明します、 **CellStyle ビルダー**  ダイアログ ボックス コントロールの帳簿のような外観を作成します。</span><span class="sxs-lookup"><span data-stu-id="ca266-125">Describes how to use the **CellStyle Builder** dialog box to create a ledger-like appearance in the control.</span></span>  
  
 [<span data-ttu-id="ca266-126">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する</span><span class="sxs-lookup"><span data-stu-id="ca266-126">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/default-cell-styles-datagridview.md)  
 <span data-ttu-id="ca266-127">使用する方法について説明します、 **CellStyle ビルダー**データ表示と基本的な外観を設定する ダイアログ ボックス コントロールの書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="ca266-127">Describes how to use the **CellStyle Builder** dialog box to set up the basic appearance and data-display formats for the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ca266-128">参照</span><span class="sxs-lookup"><span data-stu-id="ca266-128">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="ca266-129"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="ca266-129">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca266-130">参照</span><span class="sxs-lookup"><span data-stu-id="ca266-130">See Also</span></span>  
 [<span data-ttu-id="ca266-131">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="ca266-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
