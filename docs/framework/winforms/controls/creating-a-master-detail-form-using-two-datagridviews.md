---
title: 'チュートリアル: Windows フォーム DataGridView コントロールの 2 つを使用してマスター/詳細フォームを作成します。'
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
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5c3dfc547fe775b38ad4c2e658755268f791502
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="75180-102">チュートリアル : Windows フォームの 2 つの DataGridView コントロールを使用したマスター/詳細形式のフォームの作成</span><span class="sxs-lookup"><span data-stu-id="75180-102">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="75180-103">使用するための最も一般的なシナリオの 1 つ、<xref:System.Windows.Forms.DataGridView>コントロールは、*マスター/詳細*フォーム、2 つのデータベース テーブル間の親/子リレーションシップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="75180-103">One of the most common scenarios for using the <xref:System.Windows.Forms.DataGridView> control is the *master/detail* form, in which a parent/child relationship between two database tables is displayed.</span></span> <span data-ttu-id="75180-104">詳細テーブルが、対応する子データの更新をマスター テーブルの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="75180-104">Selecting rows in the master table causes the detail table to update with the corresponding child data.</span></span>  
  
 <span data-ttu-id="75180-105">間の相互作用を使用して、簡単には、マスター/詳細形式のフォームを実装する、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="75180-105">Implementing a master/detail form is easy using the interaction between the <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="75180-106">このチュートリアルでは、2 つを使用してフォームを作成します<xref:System.Windows.Forms.DataGridView>コントロールと 2 つ<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="75180-106">In this walkthrough, you will build the form using two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="75180-107">Northwind SQL Server サンプル データベースのテーブルに関連する 2 つのフォームが表示されます:`Customers`と`Orders`です。</span><span class="sxs-lookup"><span data-stu-id="75180-107">The form will show two related tables in the Northwind SQL Server sample database: `Customers` and `Orders`.</span></span> <span data-ttu-id="75180-108">Master データベース内のすべての顧客を表示するフォームが完了したら、<xref:System.Windows.Forms.DataGridView>詳細に選択した顧客のすべての注文<xref:System.Windows.Forms.DataGridView>です。</span><span class="sxs-lookup"><span data-stu-id="75180-108">When you are finished, you will have a form that shows all the customers in the database in the master <xref:System.Windows.Forms.DataGridView> and all the orders for the selected customer in the detail <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
 <span data-ttu-id="75180-109">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法:、マスター/詳細形式を使用して 2 つ Windows フォーム DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)です。</span><span class="sxs-lookup"><span data-stu-id="75180-109">To copy the code in this topic as a single listing, see [How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="75180-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="75180-110">Prerequisites</span></span>  
 <span data-ttu-id="75180-111">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="75180-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="75180-112">SQL Server の Northwind サンプル データベースがあるサーバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="75180-112">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="75180-113">フォームの作成</span><span class="sxs-lookup"><span data-stu-id="75180-113">Creating the form</span></span>  
  
#### <a name="to-create-a-masterdetail-form"></a><span data-ttu-id="75180-114">マスター/詳細フォームを作成するには</span><span class="sxs-lookup"><span data-stu-id="75180-114">To create a master/detail form</span></span>  
  
1.  <span data-ttu-id="75180-115">派生するクラスを作成する<xref:System.Windows.Forms.Form>は 2 つと<xref:System.Windows.Forms.DataGridView>コントロールと 2 つ<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="75180-115">Create a class that derives from <xref:System.Windows.Forms.Form> and contains two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="75180-116">次のコードは、基本的な形式の初期化を提供し、含まれています、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="75180-116">The following code provides basic form initialization and includes a `Main` method.</span></span> <span data-ttu-id="75180-117">フォームを作成する、Visual Studio デザイナーを使用する場合は、このコードの代わりに、デザイナーの生成されたコードを使用しますが、変数の宣言には、ここに表示される名前を使用してください。</span><span class="sxs-lookup"><span data-stu-id="75180-117">If you use the Visual Studio designer to create your form, you can use the designer generated code instead of this code, but be sure to use the names shown in the variable declarations here.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  <span data-ttu-id="75180-118">データベースへの接続の詳細を処理するためのフォームのクラス定義内のメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="75180-118">Implement a method in your form's class definition for handling the detail of connecting to the database.</span></span> <span data-ttu-id="75180-119">この例では、`GetData`メンバーを追加する方法、<xref:System.Data.DataSet>オブジェクトを追加、<xref:System.Data.DataRelation>データ セット、およびバインドするオブジェクト、<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="75180-119">This example uses a `GetData` method that populates a <xref:System.Data.DataSet> object, adds a <xref:System.Data.DataRelation> object to the data set, and binds the <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="75180-120">`connectionString` 変数は、使用しているデータベースに合った値に設定してください。</span><span class="sxs-lookup"><span data-stu-id="75180-120">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="75180-121">接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="75180-121">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="75180-122">データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="75180-122">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="75180-123">詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75180-123">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  <span data-ttu-id="75180-124">フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>をバインドするイベント、<xref:System.Windows.Forms.DataGridView>コントロールを<xref:System.Windows.Forms.BindingSource>コンポーネントとの呼び出し、`GetData`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="75180-124">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that binds the <xref:System.Windows.Forms.DataGridView> controls to the <xref:System.Windows.Forms.BindingSource> components and calls the `GetData` method.</span></span> <span data-ttu-id="75180-125">次の例には、サイズを変更するコードが含まれています。<xref:System.Windows.Forms.DataGridView>に合わせて、表示されるデータの列です。</span><span class="sxs-lookup"><span data-stu-id="75180-125">The following example includes code that resizes <xref:System.Windows.Forms.DataGridView> columns to fit the displayed data.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="75180-126">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="75180-126">Testing the Application</span></span>  
 <span data-ttu-id="75180-127">フォームをテストして、期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="75180-127">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="75180-128">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="75180-128">To test the form</span></span>  
  
-   <span data-ttu-id="75180-129">アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="75180-129">Compile and run the application.</span></span>  
  
     <span data-ttu-id="75180-130">2 つが表示されます<xref:System.Windows.Forms.DataGridView>には、1 つです。</span><span class="sxs-lookup"><span data-stu-id="75180-130">You will see two <xref:System.Windows.Forms.DataGridView> controls, one above the other.</span></span> <span data-ttu-id="75180-131">上では、Northwind から顧客`Customers`テーブル、および下部には、`Orders`選択した顧客に対応します。</span><span class="sxs-lookup"><span data-stu-id="75180-131">On top are the customers from the Northwind `Customers` table, and at the bottom are the `Orders` corresponding to the selected customer.</span></span> <span data-ttu-id="75180-132">上で複数の異なる行を選択すると<xref:System.Windows.Forms.DataGridView>、下の内容<xref:System.Windows.Forms.DataGridView>それに応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="75180-132">As you select different rows in the upper <xref:System.Windows.Forms.DataGridView>, the contents of the lower <xref:System.Windows.Forms.DataGridView> change accordingly.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="75180-133">次の手順</span><span class="sxs-lookup"><span data-stu-id="75180-133">Next Steps</span></span>  
 <span data-ttu-id="75180-134">このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。</span><span class="sxs-lookup"><span data-stu-id="75180-134">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="75180-135">動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。</span><span class="sxs-lookup"><span data-stu-id="75180-135">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="75180-136">境界線とヘッダーのスタイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="75180-136">Change border and header styles.</span></span> <span data-ttu-id="75180-137">詳細については、次を参照してください。[する方法: 境界と Windows フォーム DataGridView コントロールでのグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="75180-137">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="75180-138">有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="75180-138">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="75180-139">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)、と[する方法: Windows フォーム DataGridView コントロールで列読み取り専用のため](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="75180-139">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="75180-140">ユーザー入力を検証して、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="75180-140">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="75180-141">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロール内のデータの検証](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="75180-141">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="75180-142">仮想モードを使用して、非常に大きなデータ セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="75180-142">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="75180-143">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="75180-143">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="75180-144">セルの外観をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="75180-144">Customize the appearance of cells.</span></span> <span data-ttu-id="75180-145">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)と[する方法: Windows フォーム DataGridView コントロールの既定のセル スタイルの設定](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="75180-145">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75180-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="75180-146">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="75180-147">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="75180-147">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="75180-148">方法: Windows フォームの 2 つの DataGridView コントロールを使用してマスター/詳細形式のフォームを作成する</span><span class="sxs-lookup"><span data-stu-id="75180-148">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="75180-149">接続情報の保護</span><span class="sxs-lookup"><span data-stu-id="75180-149">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
