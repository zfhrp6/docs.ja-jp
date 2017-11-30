---
title: "方法 : Windows フォーム BindingSource コンポーネントを使用してルックアップ テーブルを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27c1c6cd0e617c0940a734e7e16a3ec5d12f920d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="a6e85-102">方法 : Windows フォーム BindingSource コンポーネントを使用してルックアップ テーブルを作成する</span><span class="sxs-lookup"><span data-stu-id="a6e85-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="a6e85-103">ルックアップ テーブルは、関連するテーブル内のレコードのデータを表示する列を持つ、データ テーブルです。</span><span class="sxs-lookup"><span data-stu-id="a6e85-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="a6e85-104">以下の手順では、<xref:System.Windows.Forms.ComboBox> コントロールを使用して、親テーブルから子テーブルへの外部キー リレーションシップを持つフィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="a6e85-105">これらの 2 つのテーブルとこの関係をわかりやすく視覚化するために、親テーブルと子テーブルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="a6e85-106">CustomersTable (親テーブル)</span><span class="sxs-lookup"><span data-stu-id="a6e85-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="a6e85-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="a6e85-107">CustomerID</span></span>|<span data-ttu-id="a6e85-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="a6e85-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="a6e85-109">712</span><span class="sxs-lookup"><span data-stu-id="a6e85-109">712</span></span>|<span data-ttu-id="a6e85-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="a6e85-110">Paul Koch</span></span>|  
|<span data-ttu-id="a6e85-111">713</span><span class="sxs-lookup"><span data-stu-id="a6e85-111">713</span></span>|<span data-ttu-id="a6e85-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="a6e85-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="a6e85-113">OrdersTable (子テーブル)</span><span class="sxs-lookup"><span data-stu-id="a6e85-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="a6e85-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="a6e85-114">OrderID</span></span>|<span data-ttu-id="a6e85-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="a6e85-115">OrderDate</span></span>|<span data-ttu-id="a6e85-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="a6e85-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="a6e85-117">903</span><span class="sxs-lookup"><span data-stu-id="a6e85-117">903</span></span>|<span data-ttu-id="a6e85-118">February 12, 2004</span><span class="sxs-lookup"><span data-stu-id="a6e85-118">February 12, 2004</span></span>|<span data-ttu-id="a6e85-119">712</span><span class="sxs-lookup"><span data-stu-id="a6e85-119">712</span></span>|  
|<span data-ttu-id="a6e85-120">904</span><span class="sxs-lookup"><span data-stu-id="a6e85-120">904</span></span>|<span data-ttu-id="a6e85-121">February 13, 2004</span><span class="sxs-lookup"><span data-stu-id="a6e85-121">February 13, 2004</span></span>|<span data-ttu-id="a6e85-122">713</span><span class="sxs-lookup"><span data-stu-id="a6e85-122">713</span></span>|  
  
 <span data-ttu-id="a6e85-123">このシナリオでは、一方のテーブル (CustomersTable) に、表示および保存する実際の情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="a6e85-124">ただし領域を節約するために、このテーブルには情報を明確化するデータは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="a6e85-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="a6e85-125">もう一方のテーブル (OrdersTable) には、どの顧客 ID 番号がどの発注日および発注 ID に相当するか、について表示関連の情報のみが格納されます。</span><span class="sxs-lookup"><span data-stu-id="a6e85-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="a6e85-126">顧客名の記述は含まれません。</span><span class="sxs-lookup"><span data-stu-id="a6e85-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="a6e85-127">ルックアップ テーブルを作成するには、[ComboBox コントロール](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)で次の 4 つの重要なプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-127">Four important properties are set on the [ComboBox Control](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="a6e85-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> プロパティには、テーブルの名前が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a6e85-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="a6e85-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> プロパティには、コントロール テキスト (顧客名) に対して表示する、テーブルのデータ列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a6e85-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="a6e85-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> プロパティには、格納された情報 (親テーブルの ID 番号) を持つ、テーブルのデータ列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a6e85-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="a6e85-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> プロパティは、<xref:System.Windows.Forms.ListControl.ValueMember%2A> に基づいて子テーブルのルックアップ値を提供します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="a6e85-132">以下の手順では、フォームをルックアップ テーブルとしてレイアウトし、フォームのコントロールにデータをバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="a6e85-133">この手順を完了するには、データ ソース、および前述の外部キー リレーションシップを持つ親テーブルと子テーブルから構成されるデータ ソースが必要です。</span><span class="sxs-lookup"><span data-stu-id="a6e85-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="a6e85-134">ユーザー インターフェイスを作成するには</span><span class="sxs-lookup"><span data-stu-id="a6e85-134">To create the user interface</span></span>  
  
1.  <span data-ttu-id="a6e85-135">**ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ComboBox>コントロールをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="a6e85-136">このコントロールは、親テーブルの列を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-136">This control will display the column from parent table.</span></span>  
  
2.  <span data-ttu-id="a6e85-137">子テーブルの詳細を表示する他のコントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="a6e85-138">テーブル内のデータの形式によって、選択するコントロールが決まります。</span><span class="sxs-lookup"><span data-stu-id="a6e85-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="a6e85-139">詳細については、「[Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6e85-139">For more information, see [Windows Forms Controls by Function](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span></span>  
  
3.  <span data-ttu-id="a6e85-140"><xref:System.Windows.Forms.BindingNavigator> コントロールをフォームにドラッグします。これにより、子テーブル内のデータを移動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a6e85-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="a6e85-141">データに接続し、コントロールにバインドするには</span><span class="sxs-lookup"><span data-stu-id="a6e85-141">To connect to the data and bind it to controls</span></span>  
  
1.  <span data-ttu-id="a6e85-142"><xref:System.Windows.Forms.ComboBox> を選択し、スマート タスク グリフをクリックして [スマート タスク] ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2.  <span data-ttu-id="a6e85-143">**[データ バインド項目を使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-143">Select **Use data bound items**.</span></span>  
  
3.  <span data-ttu-id="a6e85-144">**[データ ソース]** ドロップダウン ボックスの横の矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="a6e85-145">プロジェクトまたはフォームに対してデータ ソースがすでに構成されている場合はデータ ソースが表示されますが、設定されていない場合は、次の手順を実行します (この例では、Northwind サンプル データベースの Customers テーブルと Orders テーブルを使用します。これらのテーブルについては括弧の中で参照します)。</span><span class="sxs-lookup"><span data-stu-id="a6e85-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="a6e85-146">**[プロジェクト データ ソースの追加]** をクリックしてデータに接続し、データ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="a6e85-147">**データ ソース構成ウィザード**の開始ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="a6e85-148">**[データソースの種類を選択]** ページで、**[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="a6e85-149">**[データ接続の選択]** ページの利用可能な接続の一覧から、データ接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="a6e85-150">目的のデータ接続を選択できない場合は、**[新しい接続]** を選択して新しいデータ接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="a6e85-151">**[次の名前で接続を保存する]** をオンにして、接続文字列をアプリケーション構成ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="a6e85-152">アプリケーションで使用するデータベース オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="a6e85-153">この場合、外部キー リレーションシップを持つ親テーブルと子テーブル (Customers と Orders など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="a6e85-154">必要な場合は、既定のデータセット名を変更します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="a6e85-155">**[完了]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-155">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="a6e85-156">**[表示メンバー]** ドロップダウン ボックスで、コンボ ボックスに表示する列名 (ContactName など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5.  <span data-ttu-id="a6e85-157">**[値メンバー]** ドロップダウン ボックスで、子テーブルでルックアップ操作を実行する列 (CustomerID など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6.  <span data-ttu-id="a6e85-158">**[選択された値]** ドロップダウン ボックスで **[プロジェクト データ ソース]** に移動し、親テーブルと子テーブルを含む、作成したばかりのデータセットに移動します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="a6e85-159">親テーブルの Value Member に対応する、子テーブルのプロパティ (Orders.CustomerID など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6e85-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="a6e85-160">適切な <xref:System.Windows.Forms.BindingSource>、データ セット、およびテーブル アダプタ コンポーネントが作成され、フォームに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a6e85-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7.  <span data-ttu-id="a6e85-161"><xref:System.Windows.Forms.BindingNavigator> コントロールを子テーブルの <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource` など) にバインドします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8.  <span data-ttu-id="a6e85-162"><xref:System.Windows.Forms.ComboBox> および <xref:System.Windows.Forms.BindingNavigator> コントロール以外のコントロールを、表示する子テーブルの <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource` など) の詳細フィールドにバインドします。</span><span class="sxs-lookup"><span data-stu-id="a6e85-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e85-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6e85-163">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="a6e85-164">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a6e85-164">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="a6e85-165">ComboBox コントロール</span><span class="sxs-lookup"><span data-stu-id="a6e85-165">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [<span data-ttu-id="a6e85-166">Visual Studio でのデータへのコントロールのバインド</span><span class="sxs-lookup"><span data-stu-id="a6e85-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
