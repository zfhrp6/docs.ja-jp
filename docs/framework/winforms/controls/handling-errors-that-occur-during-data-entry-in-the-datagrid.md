---
title: "チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理"
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
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c602af6799da57fec904c87da7bed77c0040eff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="98059-102">チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理</span><span class="sxs-lookup"><span data-stu-id="98059-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="98059-103">データ エントリのアプリケーションに必要な機能は、基になるデータ ストアからのエラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="98059-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="98059-104">Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロール、これにより、簡単を公開する、<xref:System.Windows.Forms.DataGridView.DataError>データ ストアは、制約違反または破損したビジネス ルールが検出されたときに発生するイベントです。</span><span class="sxs-lookup"><span data-stu-id="98059-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>  
  
 <span data-ttu-id="98059-105">このチュートリアルから行を取得する、 `Customers` 、Northwind サンプル データベースのテーブルに表示して、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="98059-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="98059-106">重複しているときに`CustomerID`の新しい行または編集された既存の行の値が検出された、<xref:System.Windows.Forms.DataGridView.DataError>イベントが発生する、表示することによって処理される<xref:System.Windows.Forms.MessageBox>例外を説明します。</span><span class="sxs-lookup"><span data-stu-id="98059-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>  
  
 <span data-ttu-id="98059-107">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: 処理エラーを発生中にデータ入力 Windows フォーム DataGridView コントロールで](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="98059-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="98059-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="98059-108">Prerequisites</span></span>  
 <span data-ttu-id="98059-109">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="98059-109">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="98059-110">SQL Server の Northwind サンプル データベースがあるサーバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="98059-110">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="98059-111">フォームの作成</span><span class="sxs-lookup"><span data-stu-id="98059-111">Creating the Form</span></span>  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="98059-112">DataGridView コントロールでのデータ エントリ エラーを処理するには</span><span class="sxs-lookup"><span data-stu-id="98059-112">To handle data-entry errors in the DataGridView control</span></span>  
  
1.  <span data-ttu-id="98059-113">派生するクラスを作成する<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="98059-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="98059-114">次のコード例は、基本的な初期化を提供しが含まれています、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98059-114">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  <span data-ttu-id="98059-115">データベースへの接続の詳細を処理するためのフォームのクラス定義内のメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="98059-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="98059-116">このコード例では、`GetData`設定されてを返すメソッド<xref:System.Data.DataTable>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="98059-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="98059-117">設定することを必ず、`connectionString`変数をデータベースを適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="98059-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="98059-118">接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="98059-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="98059-119">データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="98059-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="98059-120">詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98059-120">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  <span data-ttu-id="98059-121">フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>し、データ バインディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="98059-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  <span data-ttu-id="98059-122">処理、<xref:System.Windows.Forms.DataGridView.DataError>でイベントを<xref:System.Windows.Forms.DataGridView>です。</span><span class="sxs-lookup"><span data-stu-id="98059-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="98059-123">コミット操作の場合は、エラーのコンテキストでエラーを表示、<xref:System.Windows.Forms.MessageBox>です。</span><span class="sxs-lookup"><span data-stu-id="98059-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="98059-124">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="98059-124">Testing the Application</span></span>  
 <span data-ttu-id="98059-125">フォームをテストして、期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="98059-125">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="98059-126">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="98059-126">To test the form</span></span>  
  
-   <span data-ttu-id="98059-127">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="98059-127">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="98059-128">表示されます、<xref:System.Windows.Forms.DataGridView>コントロール Customers テーブルからデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="98059-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="98059-129">重複した値を入力する場合`CustomerID`編集をコミットし、セルの値が自動的に元に戻すおよびが表示されます、<xref:System.Windows.Forms.MessageBox>データ エントリ エラーを表示します。</span><span class="sxs-lookup"><span data-stu-id="98059-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="98059-130">次の手順</span><span class="sxs-lookup"><span data-stu-id="98059-130">Next Steps</span></span>  
 <span data-ttu-id="98059-131">このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。</span><span class="sxs-lookup"><span data-stu-id="98059-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="98059-132">動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。</span><span class="sxs-lookup"><span data-stu-id="98059-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="98059-133">境界線とヘッダーのスタイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="98059-133">Change border and header styles.</span></span> <span data-ttu-id="98059-134">詳細については、次を参照してください。[する方法: 境界と Windows フォーム DataGridView コントロールでのグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="98059-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="98059-135">有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="98059-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="98059-136">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)、と[する方法: Windows フォーム DataGridView コントロールで列読み取り専用のため](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98059-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="98059-137">ユーザー入力を検証して、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="98059-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="98059-138">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロール内のデータの検証](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98059-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="98059-139">仮想モードを使用して、非常に大きなデータ セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="98059-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="98059-140">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98059-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="98059-141">セルの外観をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="98059-141">Customize the appearance of cells.</span></span> <span data-ttu-id="98059-142">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)と[する方法: Windows フォーム DataGridView コントロールの既定のセル スタイルの設定](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="98059-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98059-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="98059-143">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="98059-144">Windows フォーム DataGridView コントロールでのデータ入力</span><span class="sxs-lookup"><span data-stu-id="98059-144">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="98059-145">方法: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーを処理する</span><span class="sxs-lookup"><span data-stu-id="98059-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="98059-146">チュートリアル: Windows フォーム DataGridView コントロールのデータの妥当性検査</span><span class="sxs-lookup"><span data-stu-id="98059-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="98059-147">接続情報の保護</span><span class="sxs-lookup"><span data-stu-id="98059-147">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
