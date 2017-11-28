---
title: "Windows フォーム DataGridView コントロールでのデータ入力"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39d5f7763ac7b5923f0eaec757df13d675971789
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d2faa-102">Windows フォーム DataGridView コントロールでのデータ入力</span><span class="sxs-lookup"><span data-stu-id="d2faa-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d2faa-103">`DataGridView`コントロールはユーザーが追加またはコントロール内のデータを変更する方法を変更することができますいくつかの機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="d2faa-104">たとえば、することができますデータ エントリ効率的と新しい行の既定値を提供することによってエラーが発生したとき、ユーザーに警告します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d2faa-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d2faa-105">In This Section</span></span>  
 [<span data-ttu-id="d2faa-106">方法: Windows フォーム DataGridView コントロールの編集モードを指定する</span><span class="sxs-lookup"><span data-stu-id="d2faa-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d2faa-107">ユーザーがセルの編集を開始する方法を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="d2faa-108">方法: Windows フォーム DataGridView コントロールの新しい行に既定値を指定する</span><span class="sxs-lookup"><span data-stu-id="d2faa-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="d2faa-109">データ エントリの時間を節約する新しいレコードの行を事前に設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="d2faa-110">Windows フォーム DataGridView コントロールにおける新規レコード行の使用</span><span class="sxs-lookup"><span data-stu-id="d2faa-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d2faa-111">非表示に、その外観をカスタマイズする方法のおよびとの関係の情報を含む、新しいレコードの行について説明します、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="d2faa-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="d2faa-112">チュートリアル: Windows フォーム DataGridView コントロールのデータの妥当性検査</span><span class="sxs-lookup"><span data-stu-id="d2faa-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d2faa-113">データ エントリの形式エラーを防ぐためにユーザー入力を検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="d2faa-114">チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理</span><span class="sxs-lookup"><span data-stu-id="d2faa-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="d2faa-115">ユーザーが新しい値をコミットしようとしたときに、データ ソースから送られたデータ エントリ エラーを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d2faa-116">参照</span><span class="sxs-lookup"><span data-stu-id="d2faa-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="d2faa-117"><xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="d2faa-118">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.EditMode%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d2faa-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="d2faa-119">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>イベント。</span><span class="sxs-lookup"><span data-stu-id="d2faa-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="d2faa-120">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.DataError>イベント。</span><span class="sxs-lookup"><span data-stu-id="d2faa-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="d2faa-121">リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.CellValidating>イベント。</span><span class="sxs-lookup"><span data-stu-id="d2faa-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d2faa-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2faa-122">Related Sections</span></span>  
 [<span data-ttu-id="d2faa-123">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="d2faa-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d2faa-124">手動または外部データ ソースからコントロールにデータを設定する方法を説明するトピックを提供します。</span><span class="sxs-lookup"><span data-stu-id="d2faa-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2faa-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2faa-125">See Also</span></span>  
 [<span data-ttu-id="d2faa-126">DataGridView コントロール</span><span class="sxs-lookup"><span data-stu-id="d2faa-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="d2faa-127">Windows フォーム DataGridView コントロールの列型</span><span class="sxs-lookup"><span data-stu-id="d2faa-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
