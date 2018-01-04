---
title: "チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査"
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
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2ede616b311119d174534e53cb3aaf9e366c7c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="98540-102">チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査</span><span class="sxs-lookup"><span data-stu-id="98540-102">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="98540-103">データ エントリの機能をユーザーに表示するときに頻繁に、フォームに入力データを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98540-103">When you display data entry functionality to users, you frequently have to validate the data entered into your form.</span></span> <span data-ttu-id="98540-104"><xref:System.Windows.Forms.DataGridView>クラスには、データがデータ ストアにコミットする前に検証を実行する便利な方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="98540-104">The <xref:System.Windows.Forms.DataGridView> class provides a convenient way to perform validation before data is committed to the data store.</span></span> <span data-ttu-id="98540-105">データを検証するには、処理することにより、<xref:System.Windows.Forms.DataGridView.CellValidating>によって発生するイベント、<xref:System.Windows.Forms.DataGridView>現在のセルが変更されたとき。</span><span class="sxs-lookup"><span data-stu-id="98540-105">You can validate data by handling the <xref:System.Windows.Forms.DataGridView.CellValidating> event, which is raised by the <xref:System.Windows.Forms.DataGridView> when the current cell changes.</span></span>  
  
 <span data-ttu-id="98540-106">このチュートリアルから行を取得する、 `Customers` 、Northwind サンプル データベースのテーブルに表示して、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="98540-106">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="98540-107">ユーザーが内のセルを編集するときに、`CompanyName`列と、セルのままにすると、<xref:System.Windows.Forms.DataGridView.CellValidating>イベント ハンドラーは新しい会社名の文字列を新しい値が空の文字列である場合は空ではありません確認を検査して、<xref:System.Windows.Forms.DataGridView>により、ユーザーのカーソル。セルから空でない文字列を入力するまでです。</span><span class="sxs-lookup"><span data-stu-id="98540-107">When a user edits a cell in the `CompanyName` column and tries to leave the cell, the <xref:System.Windows.Forms.DataGridView.CellValidating> event handler will examine new company name string to make sure it is not empty; if the new value is an empty string, the <xref:System.Windows.Forms.DataGridView> will prevent the user's cursor from leaving the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="98540-108">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: Windows フォーム DataGridView コントロール内データの検証](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98540-108">To copy the code in this topic as a single listing, see [How to: Validate Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="98540-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="98540-109">Prerequisites</span></span>  
 <span data-ttu-id="98540-110">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="98540-110">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="98540-111">SQL Server の Northwind サンプル データベースがあるサーバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="98540-111">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="98540-112">フォームの作成</span><span class="sxs-lookup"><span data-stu-id="98540-112">Creating the Form</span></span>  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a><span data-ttu-id="98540-113">DataGridView で入力したデータを検証するには</span><span class="sxs-lookup"><span data-stu-id="98540-113">To validate data entered in a DataGridView</span></span>  
  
1.  <span data-ttu-id="98540-114">派生するクラスを作成する<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="98540-114">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="98540-115">次のコード例は、基本的な初期化を提供しが含まれています、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98540-115">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  <span data-ttu-id="98540-116">データベースへの接続の詳細を処理するためのフォームのクラス定義内のメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="98540-116">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="98540-117">このコード例では、`GetData`設定されてを返すメソッド<xref:System.Data.DataTable>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="98540-117">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="98540-118">設定することを必ず、`connectionString`変数をデータベースを適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="98540-118">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="98540-119">接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="98540-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="98540-120">データベースへのアクセスを制御するより安全な方法は、Windows 認証とも呼ばれる統合セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="98540-120">Using Windows Authentication, also known as integrated security, is a more secure way to control access to a database.</span></span> <span data-ttu-id="98540-121">詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98540-121">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  <span data-ttu-id="98540-122">フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>し、データ バインディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="98540-122">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  <span data-ttu-id="98540-123">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellValidating>と<xref:System.Windows.Forms.DataGridView.CellEndEdit>イベント。</span><span class="sxs-lookup"><span data-stu-id="98540-123">Implement handlers for the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellValidating> and <xref:System.Windows.Forms.DataGridView.CellEndEdit> events.</span></span>  
  
     <span data-ttu-id="98540-124"><xref:System.Windows.Forms.DataGridView.CellValidating>イベント ハンドラーが判断したかどうかのセルの値、`CompanyName`列は空です。</span><span class="sxs-lookup"><span data-stu-id="98540-124">The <xref:System.Windows.Forms.DataGridView.CellValidating> event handler is where you determine whether the value of a cell in the `CompanyName` column is empty.</span></span> <span data-ttu-id="98540-125">セルの値には、検証が失敗した場合、設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>クラスを`true`です。</span><span class="sxs-lookup"><span data-stu-id="98540-125">If the cell value fails validation, set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property of the <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> class to `true`.</span></span> <span data-ttu-id="98540-126">これにより、<xref:System.Windows.Forms.DataGridView>コントロールをセルからカーソルを防ぐためにします。</span><span class="sxs-lookup"><span data-stu-id="98540-126">This causes the <xref:System.Windows.Forms.DataGridView> control to prevent the cursor from leaving the cell.</span></span> <span data-ttu-id="98540-127">設定、<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>説明の文字列には、行のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="98540-127">Set the <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> property on the row to an explanatory string.</span></span> <span data-ttu-id="98540-128">これには、エラー テキストを含むツールヒントにエラー アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98540-128">This displays an error icon with a ToolTip that contains the error text.</span></span> <span data-ttu-id="98540-129"><xref:System.Windows.Forms.DataGridView.CellEndEdit> 、イベント ハンドラーを設定、<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>の行に空の文字列のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="98540-129">In the <xref:System.Windows.Forms.DataGridView.CellEndEdit> event handler, set the <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> property on the row to the empty string.</span></span> <span data-ttu-id="98540-130"><xref:System.Windows.Forms.DataGridView.CellEndEdit>セルが編集モードは、検証が失敗した場合に行うことはできませんに終了する場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="98540-130">The <xref:System.Windows.Forms.DataGridView.CellEndEdit> event occurs only when the cell exits edit mode, which it cannot do if it fails validation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="98540-131">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="98540-131">Testing the Application</span></span>  
 <span data-ttu-id="98540-132">フォームをテストして、期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="98540-132">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="98540-133">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="98540-133">To test the form</span></span>  
  
-   <span data-ttu-id="98540-134">アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="98540-134">Compile and run the application.</span></span>  
  
     <span data-ttu-id="98540-135">表示されます、<xref:System.Windows.Forms.DataGridView>からのデータが格納された、`Customers`テーブル。</span><span class="sxs-lookup"><span data-stu-id="98540-135">You will see a <xref:System.Windows.Forms.DataGridView> filled with data from the `Customers` table.</span></span> <span data-ttu-id="98540-136">内のセルをダブルクリックすると、`CompanyName`列、値を編集することができます。</span><span class="sxs-lookup"><span data-stu-id="98540-136">When you double-click a cell in the `CompanyName` column, you can edit the value.</span></span> <span data-ttu-id="98540-137">すべての文字を削除して、セルを終了する TAB キーを押して、<xref:System.Windows.Forms.DataGridView>終了できないようにします。</span><span class="sxs-lookup"><span data-stu-id="98540-137">If you delete all the characters and hit the TAB key to exit the cell, the <xref:System.Windows.Forms.DataGridView> prevents you from exiting.</span></span> <span data-ttu-id="98540-138">セルに空でない文字列を入力すると、<xref:System.Windows.Forms.DataGridView>コントロールでは、セルを終了することができます。</span><span class="sxs-lookup"><span data-stu-id="98540-138">When you type a non-empty string into the cell, the <xref:System.Windows.Forms.DataGridView> control lets you exit the cell.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="98540-139">次の手順</span><span class="sxs-lookup"><span data-stu-id="98540-139">Next Steps</span></span>  
 <span data-ttu-id="98540-140">このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。</span><span class="sxs-lookup"><span data-stu-id="98540-140">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="98540-141">動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。</span><span class="sxs-lookup"><span data-stu-id="98540-141">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="98540-142">境界線とヘッダーのスタイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="98540-142">Change border and header styles.</span></span> <span data-ttu-id="98540-143">詳細については、次を参照してください。[する方法: 境界と Windows フォーム DataGridView コントロールでのグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="98540-143">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="98540-144">有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="98540-144">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="98540-145">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)、と[する方法: Windows フォーム DataGridView コントロールで列読み取り専用のため](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98540-145">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="98540-146">データベースに関連するエラーのユーザー入力を確認してください。</span><span class="sxs-lookup"><span data-stu-id="98540-146">Check user input for database-related errors.</span></span> <span data-ttu-id="98540-147">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="98540-147">For more information, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="98540-148">仮想モードを使用して、非常に大きなデータ セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="98540-148">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="98540-149">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98540-149">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="98540-150">セルの外観をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="98540-150">Customize the appearance of cells.</span></span> <span data-ttu-id="98540-151">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)と[する方法: フォントの設定と Windows フォーム DataGridView コントロールでの色のスタイル](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98540-151">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Font and Color Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98540-152">参照</span><span class="sxs-lookup"><span data-stu-id="98540-152">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="98540-153">Windows フォーム DataGridView コントロールでのデータ入力</span><span class="sxs-lookup"><span data-stu-id="98540-153">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="98540-154">方法: Windows フォーム DataGridView コントロールのデータを検証する</span><span class="sxs-lookup"><span data-stu-id="98540-154">How to: Validate Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="98540-155">チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理</span><span class="sxs-lookup"><span data-stu-id="98540-155">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="98540-156">接続情報の保護</span><span class="sxs-lookup"><span data-stu-id="98540-156">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
