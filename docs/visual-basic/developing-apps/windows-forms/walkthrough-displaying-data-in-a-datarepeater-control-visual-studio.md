---
title: 'チュートリアル : DataRepeater コントロールでのデータの表示 (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231512"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="5e3ca-102">チュートリアル : DataRepeater コントロールでのデータの表示 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5e3ca-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="5e3ca-103">このチュートリアルでは、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにバインドされたデータを表示する基本的なシナリオ全体を示します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="5e3ca-104">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5e3ca-104">Prerequisite</span></span>  
 <span data-ttu-id="5e3ca-105">このチュートリアルには、Northwind サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="5e3ca-106">開発用コンピューターにこのデータベースがいない場合は、Microsoft ダウンロード センターからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="5e3ca-107">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-107">For instructions, see [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5e3ca-108">概要</span><span class="sxs-lookup"><span data-stu-id="5e3ca-108">Overview</span></span>  
 <span data-ttu-id="5e3ca-109">このチュートリアルの前半部分は、次の 4 つの主要なタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="5e3ca-110">ソリューションを作成する。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="5e3ca-111"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを追加する。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="5e3ca-112">データ ソースを追加する。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="5e3ca-113">データ バインドされたコントロールを追加する。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="5e3ca-114">DataRepeater ソリューションの作成</span><span class="sxs-lookup"><span data-stu-id="5e3ca-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="5e3ca-115">最初に、プロジェクトとソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="5e3ca-116">DataRepeater ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="5e3ca-117">Visual Studio で **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="5e3ca-118">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual Basic]** を展開し、 **[Windows]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="5e3ca-119">**[テンプレート]** ペインの **[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="5e3ca-120">**[名前]** ボックスに「 `DataRepeaterApp`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="5e3ca-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="5e3ca-122">Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="5e3ca-123">Windows フォーム デザイナーでフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="5e3ca-124">**[プロパティ]** ウィンドウで、 **Size** プロパティを `800, 700`に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="5e3ca-125">DataRepeater コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="5e3ca-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="5e3ca-126">この手順では、フォームに <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="5e3ca-127">DataRepeater コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="5e3ca-128">**[表示]** メニューの **[ツールボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="5e3ca-129">**ツールボックス** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="5e3ca-130">**[Visual Basic PowerPacks]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="5e3ca-131"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを **Form1**にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="5e3ca-132">[プロパティ] ウィンドウで、 **Location** プロパティを `0, 25`に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="5e3ca-133">**Size** プロパティを `460, 600`に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="5e3ca-134">データ ソースの追加</span><span class="sxs-lookup"><span data-stu-id="5e3ca-134">Adding a Data Source</span></span>  
 <span data-ttu-id="5e3ca-135">この手順では、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールのデータ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="5e3ca-136">データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="5e3ca-137">**[データ]** メニューの **[データ ソースの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="5e3ca-138">**[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="5e3ca-139">**[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="5e3ca-140">**[データ接続の選択]** ページで、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="5e3ca-141">Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="5e3ca-142">- または -</span><span class="sxs-lookup"><span data-stu-id="5e3ca-142">-or-</span></span>  
  
    -   <span data-ttu-id="5e3ca-143">**[新しい接続]** をクリックし、新しいデータ接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="5e3ca-144">詳細については、次を参照してください。[新しい接続を追加](/visualstudio/data-tools/add-new-connections)です。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-144">For more information, see [Add new connections](/visualstudio/data-tools/add-new-connections).</span></span>  
  
5.  <span data-ttu-id="5e3ca-145">データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e3ca-146">ダイアログ ボックスが表示された場合は、 **[はい]** をクリックしてファイルをプロジェクトに保存します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="5e3ca-147">**[アプリケーション構成ファイルに接続文字列を保存]** ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="5e3ca-148">**[データベース オブジェクトの選択]** ページの **[テーブル]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="5e3ca-149">**Customers** テーブルと **Orders** テーブルの横のチェック ボックスをオンにし、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="5e3ca-150">プロジェクトに**NorthwindDataSet** が追加され、 **[データ ソース]** ウィンドウに **Customers** テーブルと **Orders** テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="5e3ca-151">データ バインドされたコントロールの追加</span><span class="sxs-lookup"><span data-stu-id="5e3ca-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="5e3ca-152">この手順では、データ バインドされたコントロールを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>に追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="5e3ca-153">データ バインディング コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="5e3ca-154">**[データ ソース]** ウィンドウで、 **Customers** テーブルの最上位ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="5e3ca-155">テーブル ノードのドロップダウン リストの **[詳細]** をクリックして、テーブルのドロップ タイプを **[詳細]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="5e3ca-156">**[Customers]** テーブル ノードを選択し、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域 (上部領域) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="5e3ca-157">フォームに <xref:System.Windows.Forms.BindingNavigator> コントロールが追加され、コンポーネント トレイに **NorthwindDataSet**、 **CustomersBindingSource**、 **CustomersTableAdapter**、 **TableAdapterManager**、および **CustomersBindingNavigator** の各コンポーネントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="5e3ca-158">すべてのフィールドとそれらに関連付けられているラベルを選択し、項目テンプレート領域の左端近くに配置します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="5e3ca-159">後半の 5 つのフィールド (**Region**、 **Postal Code**、 **Country**、 **Phone**、 **Fax**) とそれらに関連付けられているラベルを選択し、上へ移動して前半の 6 つのフィールドの右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="5e3ca-160">項目テンプレート (コントロールの上部領域) を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="5e3ca-161">[プロパティ] ウィンドウで、 **Size** プロパティを `427, 170`に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="5e3ca-162">この時点で、顧客の繰り返しの一覧が表示される作業アプリケーションが作成されました。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="5e3ca-163">F5 キーを押してこのアプリケーションを実行し、データの変更、および顧客レコードの追加と削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="5e3ca-164">次の省略可能な手順では、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="5e3ca-165">次の手順 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="5e3ca-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="5e3ca-166">このチュートリアルの後半部分は、次の 4 つの省略可能な手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="5e3ca-167"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの外観を変更する。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="5e3ca-168">ユーザーがレコードを追加または削除できないようにする。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="5e3ca-169"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールに検索機能を追加する。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="5e3ca-170"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにマスター/詳細テーブルを追加する。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="5e3ca-171">DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="5e3ca-172">この省略可能な手順では、デザイン時に `BackColor` コントロールの <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> を変更します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="5e3ca-173">また、行の色を交互にし、条件に応じてラベルの `ForeColor` を変更するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="5e3ca-174">コントロールの外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="5e3ca-175">Windows フォーム デザイナーで、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールのメイン (下部) 領域を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="5e3ca-176">[プロパティ] ウィンドウで、 `BackColor` プロパティを白に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="5e3ca-177"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> をダブルクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="5e3ca-178">コード エディターで、[イベント] ボックスの一覧の **[DrawItem]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="5e3ca-179"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベント ハンドラーで、 `BackColor`を交互にする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="5e3ca-180"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベント ハンドラーで、条件に応じてラベルの `ForeColor` を変更する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="5e3ca-181">F5 キーを押してアプリケーションを実行し、カスタマイズを確認します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="5e3ca-182">ユーザーがレコードを追加または削除できないようにする</span><span class="sxs-lookup"><span data-stu-id="5e3ca-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="5e3ca-183">この省略可能な手順では、ユーザーが <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールでレコードを追加または削除できないようにするコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="5e3ca-184">ユーザーがレコードを追加または削除できないようにするには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="5e3ca-185">Windows フォーム デザイナーで、フォームをダブルクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="5e3ca-186">`Form_Load` イベントに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="5e3ca-187">[クラス名] ボックスの一覧で **[BindingNavigatorDeleteItem]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="5e3ca-188">[メソッド名] ボックスの一覧で **[EnabledChanged]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="5e3ca-189">`BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5e3ca-190">この手順が必要なのは、現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるためです。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="5e3ca-191">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-191">Press F5 to run the application.</span></span> <span data-ttu-id="5e3ca-192">**DeleteItem** ボタンが無効になっていて、Del キーを押しても項目を削除できないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="5e3ca-193">DataRepeater コントロールに検索機能を追加する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="5e3ca-194">この省略可能な手順では、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールで値を検索する機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="5e3ca-195">検索文字列が見つかると、このコントロールはその値を含む項目を選択し、スクロールして表示します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="5e3ca-196">検索機能を追加するには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="5e3ca-197"><xref:System.Windows.Forms.TextBox> コントロールが含まれるフォーム上に、 **ツールボックス** から <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="5e3ca-198">それを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの下に配置します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="5e3ca-199">[プロパティ] ウィンドウで、 **Name** プロパティを **SearchTextBox**に変更します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="5e3ca-200"><xref:System.Windows.Forms.Button> コントロールが含まれるフォーム上に、 **ツールボックス** から <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="5e3ca-201">それを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの下に配置します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="5e3ca-202">[プロパティ] ウィンドウで、 **Name** プロパティを **SearchButton**に変更します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="5e3ca-203">**Text** プロパティを **Search**に変更します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="5e3ca-204"><xref:System.Windows.Forms.Button> コントロールをダブルクリックしてコード エディターを開き、 `SearchButton_Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="5e3ca-205">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-205">Press F5 to run the application.</span></span> <span data-ttu-id="5e3ca-206">**[SearchTextBox]** に顧客 ID を入力し、 **[Search]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="5e3ca-207">DataRepeater にマスター/詳細テーブルを追加する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="5e3ca-208">この省略可能な手順では、顧客ごとに関連する注文を表示するために、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをもう 1 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="5e3ca-209">マスター/詳細テーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="5e3ca-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="5e3ca-210"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ツールボックス **の** [Visual Basic PowerPacks] **タブから** コントロールをもう 1 つ、フォーム上にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="5e3ca-211">[プロパティ] ウィンドウで、 **Location** プロパティを `465, 25`に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="5e3ca-212">**Size** プロパティを `315, 600`に設定します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="5e3ca-213">**[データ ソース]** ウィンドウで、 **[Customers]** テーブル ノードを展開し、 **Orders** テーブルの詳細ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="5e3ca-214">この **Orders** テーブルのドロップ タイプを、テーブル ノードのドロップダウン リストの **[詳細]** をクリックして [詳細] に変更します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="5e3ca-215">この **[Orders]** テーブル ノードを 2 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域 (上部領域) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="5e3ca-216">**OrdersBindingSource** コンポーネントおよび **OrdersTableAdapter** コンポーネントがコンポーネント トレイに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="5e3ca-217">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-217">Press F5 to run the application.</span></span> <span data-ttu-id="5e3ca-218">1 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールで顧客を選択すると、2 番目の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにその顧客の注文が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3ca-219">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e3ca-219">See Also</span></span>  
 [<span data-ttu-id="5e3ca-220">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="5e3ca-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e3ca-221">方法: DataRepeater コントロールに、バインドされたデータを表示する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e3ca-222">方法: DataRepeater コントロールに非バインド コントロールを表示する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e3ca-223">方法: DataRepeater コントロールのレイアウトを変更する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e3ca-224">方法: DataRepeater コントロールに項目ヘッダーを表示する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e3ca-225">方法: DataRepeater コントロールでデータを検索する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e3ca-226">方法: 2 つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e3ca-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="5e3ca-227">方法: DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="5e3ca-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5e3ca-228">方法: DataRepeater の項目の追加と削除を無効にする</span><span class="sxs-lookup"><span data-stu-id="5e3ca-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="5e3ca-229">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5e3ca-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
