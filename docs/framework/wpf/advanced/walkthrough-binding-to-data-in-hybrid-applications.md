---
title: "チュートリアル : ハイブリッド アプリケーションでのデータへのバインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 957559cbc88855700471cc457f76d69ef5a296d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="570e9-102">チュートリアル : ハイブリッド アプリケーションでのデータへのバインディング</span><span class="sxs-lookup"><span data-stu-id="570e9-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="570e9-103">使用しているかどうかをコントロールにデータ ソースのバインドは、基になるデータへのアクセス権を持つユーザーを提供するために不可欠な[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="570e9-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="570e9-104">このチュートリアルでは、両方を格納するハイブリッド アプリケーションのデータ バインディングを使用するどの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="570e9-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="570e9-105">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="570e9-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="570e9-106">プロジェクトの作成。</span><span class="sxs-lookup"><span data-stu-id="570e9-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="570e9-107">データ テンプレートを定義します。</span><span class="sxs-lookup"><span data-stu-id="570e9-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="570e9-108">フォームのレイアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="570e9-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="570e9-109">データ バインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="570e9-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="570e9-110">相互運用を使用してデータを表示しています。</span><span class="sxs-lookup"><span data-stu-id="570e9-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="570e9-111">プロジェクトへのデータ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="570e9-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="570e9-112">データ ソースにバインドします。</span><span class="sxs-lookup"><span data-stu-id="570e9-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="570e9-113">このチュートリアルでタスクの完全なコードについては、次を参照してください。[ハイブリッド アプリケーションのサンプルでのデータ バインディング](http://go.microsoft.com/fwlink/?LinkID=159983)です。</span><span class="sxs-lookup"><span data-stu-id="570e9-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](http://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="570e9-114">完了したら、ハイブリッド アプリケーションでのデータ バインディング機能について理解があります。</span><span class="sxs-lookup"><span data-stu-id="570e9-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="570e9-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="570e9-115">Prerequisites</span></span>  
 <span data-ttu-id="570e9-116">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="570e9-116">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="570e9-117">。</span><span class="sxs-lookup"><span data-stu-id="570e9-117">.</span></span>  
  
-   <span data-ttu-id="570e9-118">Microsoft SQL Server で実行されている、Northwind サンプル データベースへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="570e9-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="570e9-119">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="570e9-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="570e9-120">プロジェクトを作成し、設定するには</span><span class="sxs-lookup"><span data-stu-id="570e9-120">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="570e9-121">という名前の WPF アプリケーション プロジェクトを作成する`WPFWithWFAndDatabinding`です。</span><span class="sxs-lookup"><span data-stu-id="570e9-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2.  <span data-ttu-id="570e9-122">ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="570e9-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="570e9-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="570e9-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="570e9-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="570e9-124">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="570e9-125">MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="570e9-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="570e9-126"><xref:System.Windows.Window>要素では、次の追加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名前空間マッピング。</span><span class="sxs-lookup"><span data-stu-id="570e9-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="570e9-127">既定値の名前を付けます<xref:System.Windows.Controls.Grid>要素`mainGrid`を割り当てることによって、<xref:System.Windows.FrameworkElement.Name%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="570e9-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="570e9-128">データ テンプレートの定義</span><span class="sxs-lookup"><span data-stu-id="570e9-128">Defining the Data Template</span></span>  
 <span data-ttu-id="570e9-129">顧客のマスター一覧に表示されます、<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="570e9-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="570e9-130">次のコード例を定義、<xref:System.Windows.DataTemplate>という名前のオブジェクト`ListItemsTemplate`のビジュアル ツリーを制御する、<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="570e9-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="570e9-131">これは、<xref:System.Windows.DataTemplate>に割り当てられている、<xref:System.Windows.Controls.ListBox>コントロールの<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="570e9-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="570e9-132">データ テンプレートを定義するには</span><span class="sxs-lookup"><span data-stu-id="570e9-132">To define the data template</span></span>  
  
-   <span data-ttu-id="570e9-133">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。</span><span class="sxs-lookup"><span data-stu-id="570e9-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="570e9-134">フォーム レイアウトの指定</span><span class="sxs-lookup"><span data-stu-id="570e9-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="570e9-135">フォームのレイアウトは、次の 3 つの行と 3 つの列を含むグリッドによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="570e9-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="570e9-136"><xref:System.Windows.Controls.Label>コントロールは、Customers テーブル内の各列の識別に提供されます。</span><span class="sxs-lookup"><span data-stu-id="570e9-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="570e9-137">グリッド レイアウトを設定するには</span><span class="sxs-lookup"><span data-stu-id="570e9-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="570e9-138">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。</span><span class="sxs-lookup"><span data-stu-id="570e9-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="570e9-139">ラベル コントロールを設定するには</span><span class="sxs-lookup"><span data-stu-id="570e9-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="570e9-140">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。</span><span class="sxs-lookup"><span data-stu-id="570e9-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="570e9-141">データ バインディングの指定</span><span class="sxs-lookup"><span data-stu-id="570e9-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="570e9-142">顧客のマスター一覧に表示されます、<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="570e9-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="570e9-143">アタッチされた`ListItemsTemplate`バインド、<xref:System.Windows.Controls.TextBlock>コントロールを`ContactName`データベースからフィールドです。</span><span class="sxs-lookup"><span data-stu-id="570e9-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="570e9-144">各顧客レコードの詳細は、いくつか表示されます<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="570e9-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="570e9-145">データ バインディングを指定するには</span><span class="sxs-lookup"><span data-stu-id="570e9-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="570e9-146">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。</span><span class="sxs-lookup"><span data-stu-id="570e9-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="570e9-147"><xref:System.Windows.Data.Binding>クラスのバインド、<xref:System.Windows.Controls.TextBox>データベース内の該当フィールドへのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="570e9-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="570e9-148">相互運用を使用してデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="570e9-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="570e9-149">選択した顧客に対応する注文が表示される、<xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>という名前のコントロール`dataGridView1`です。</span><span class="sxs-lookup"><span data-stu-id="570e9-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="570e9-150">`dataGridView1`分離コード ファイル内のデータ ソースにコントロールをバインドします。</span><span class="sxs-lookup"><span data-stu-id="570e9-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="570e9-151">A<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールの親では、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="570e9-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="570e9-152">DataGridView コントロールにデータを表示するには</span><span class="sxs-lookup"><span data-stu-id="570e9-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="570e9-153">次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。</span><span class="sxs-lookup"><span data-stu-id="570e9-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="570e9-154">データ ソースをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="570e9-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="570e9-155">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]プロジェクトにデータ ソースを簡単に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="570e9-155">With [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can easily add a data source to your project.</span></span> <span data-ttu-id="570e9-156">このプロシージャは、プロジェクトに厳密に型指定されたデータ セットを追加します。</span><span class="sxs-lookup"><span data-stu-id="570e9-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="570e9-157">いくつか他のサポートなどのクラスを選択したテーブルの各テーブルのアダプターも追加されます。</span><span class="sxs-lookup"><span data-stu-id="570e9-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="570e9-158">データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="570e9-158">To add the data source</span></span>  
  
1.  <span data-ttu-id="570e9-159">**データ**メニューの **新しいデータ ソースの追加**です。</span><span class="sxs-lookup"><span data-stu-id="570e9-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2.  <span data-ttu-id="570e9-160">**データ ソース構成ウィザード**データセットを使用して、Northwind データベースへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="570e9-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="570e9-161">詳細については、次を参照してください。[する方法: データベース内のデータへの接続](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)です。</span><span class="sxs-lookup"><span data-stu-id="570e9-161">For more information, see [How to: Connect to Data in a Database](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span></span>  
  
3.  <span data-ttu-id="570e9-162">によってメッセージが表示されたら、**データ ソース構成ウィザード**、接続文字列として保存`NorthwindConnectionString`です。</span><span class="sxs-lookup"><span data-stu-id="570e9-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4.  <span data-ttu-id="570e9-163">データベース オブジェクトの選択画面が表示されたら、選択、`Customers`と`Orders`テーブル、および生成されたデータ セットの名前`NorthwindDataSet`です。</span><span class="sxs-lookup"><span data-stu-id="570e9-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="570e9-164">データ ソースにバインドします。</span><span class="sxs-lookup"><span data-stu-id="570e9-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="570e9-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>コンポーネントは、アプリケーションのデータ ソースの統一されたインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="570e9-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="570e9-166">データ ソースへのバインディングは、分離コード ファイルに実装されます。</span><span class="sxs-lookup"><span data-stu-id="570e9-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="570e9-167">データ ソースにバインドするには</span><span class="sxs-lookup"><span data-stu-id="570e9-167">To bind to the data source</span></span>  
  
1.  <span data-ttu-id="570e9-168">MainWindow.xaml.vb または MainWindow.xaml.cs の名前は、分離コード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="570e9-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="570e9-169">次のコードをコピー、`MainWindow`クラス定義です。</span><span class="sxs-lookup"><span data-stu-id="570e9-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="570e9-170">このコードで宣言、<xref:System.Windows.Forms.BindingSource>コンポーネントとデータベースへの接続を関連付けられているヘルパー クラス。</span><span class="sxs-lookup"><span data-stu-id="570e9-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  <span data-ttu-id="570e9-171">コンス トラクターに次のコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="570e9-171">Copy the following code into the constructor.</span></span>  
  
     <span data-ttu-id="570e9-172">このコードを作成して、初期化、<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="570e9-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  <span data-ttu-id="570e9-173">MainWindow.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="570e9-173">Open MainWindow.xaml.</span></span>  
  
5.  <span data-ttu-id="570e9-174">[デザイン] ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>要素。</span><span class="sxs-lookup"><span data-stu-id="570e9-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="570e9-175">[プロパティ] ウィンドウ、**イベント**タブです。</span><span class="sxs-lookup"><span data-stu-id="570e9-175">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="570e9-176">ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。</span><span class="sxs-lookup"><span data-stu-id="570e9-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="570e9-177">次のコードをコピー、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="570e9-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
     <span data-ttu-id="570e9-178">このコードに割り当てます、<xref:System.Windows.Forms.BindingSource>データ コンテキストとしてコンポーネントに入力し、`Customers`と`Orders`アダプター オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="570e9-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. <span data-ttu-id="570e9-179">次のコードをコピー、`MainWindow`クラス定義です。</span><span class="sxs-lookup"><span data-stu-id="570e9-179">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="570e9-180">このメソッドは、処理、<xref:System.Windows.Data.CollectionView.CurrentChanged>イベントとデータ バインディングの現在の項目を更新します。</span><span class="sxs-lookup"><span data-stu-id="570e9-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="570e9-181">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="570e9-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570e9-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="570e9-182">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="570e9-183">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="570e9-183">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="570e9-184">ハイブリッド アプリケーションのサンプルでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="570e9-184">Data Binding in Hybrid Applications Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [<span data-ttu-id="570e9-185">チュートリアル: WPF での Windows フォーム複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="570e9-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="570e9-186">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="570e9-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
