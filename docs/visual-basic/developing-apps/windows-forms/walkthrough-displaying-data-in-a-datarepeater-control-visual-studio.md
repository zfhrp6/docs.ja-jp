---
title: "チュートリアル: DataRepeater コントロール (Visual Studio) でのデータの表示 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b795b8f3bb42aecdbdfade62f4943239fec6eac4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="ac2ae-102">チュートリアル : DataRepeater コントロールでのデータの表示 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ac2ae-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="ac2ae-103">このチュートリアルでは、基本的な開始から終了までにバインドされたデータを表示するため、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="ac2ae-104">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ac2ae-104">Prerequisite</span></span>  
 <span data-ttu-id="ac2ae-105">このチュートリアルには、Northwind サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="ac2ae-106">開発用コンピューターにこのデータベースがない場合は、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-106">If you do not have this database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span></span> <span data-ttu-id="ac2ae-107">手順については、次を参照してください。[サンプル データベースのダウンロード](https://msdn.microsoft.com/library/bb399411)します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-107">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ac2ae-108">概要</span><span class="sxs-lookup"><span data-stu-id="ac2ae-108">Overview</span></span>  
 <span data-ttu-id="ac2ae-109">このチュートリアルの前半部分は、次の&4; つの主要なタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="ac2ae-110">ソリューションを作成する。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="ac2ae-111">追加する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="ac2ae-112">データ ソースを追加する。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="ac2ae-113">データ バインドされたコントロールを追加する。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="ac2ae-114">DataRepeater ソリューションの作成</span><span class="sxs-lookup"><span data-stu-id="ac2ae-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="ac2ae-115">最初に、プロジェクトとソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="ac2ae-116">DataRepeater ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="ac2ae-117">Visual Studio で **[ファイル]** メニューの **[新しいプロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="ac2ae-118">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual Basic]**を展開し、 **[Windows]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="ac2ae-119">**[テンプレート]** ペインの **[Windows フォーム アプリケーション]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="ac2ae-120">**[名前]** ボックスに「 `DataRepeaterApp`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="ac2ae-121">**[OK]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="ac2ae-122">Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="ac2ae-123">Windows フォーム デザイナーでフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="ac2ae-124">**[プロパティ]** ウィンドウで、 **Size** プロパティを `800, 700`に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="ac2ae-125">DataRepeater コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="ac2ae-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="ac2ae-126">この手順で追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールをフォーム</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="ac2ae-127">DataRepeater コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="ac2ae-128">**[表示]** メニューの **[ツールボックス]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="ac2ae-129">**ツールボックス** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="ac2ae-130">**[Visual Basic PowerPacks]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="ac2ae-131">ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを**Form1**</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="ac2ae-132">[プロパティ] ウィンドウで、 **Location** プロパティを `0, 25`に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="ac2ae-133">**Size** プロパティを `460, 600`に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="ac2ae-134">データ ソースの追加</span><span class="sxs-lookup"><span data-stu-id="ac2ae-134">Adding a Data Source</span></span>  
 <span data-ttu-id="ac2ae-135">このステップでのデータ ソースを追加する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="ac2ae-136">データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="ac2ae-137">**[データ]** メニューの **[データ ソースの表示]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="ac2ae-138">**[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="ac2ae-139">**[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ac2ae-140">**[データ接続の選択]** ページで、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="ac2ae-141">Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="ac2ae-142">または</span><span class="sxs-lookup"><span data-stu-id="ac2ae-142">-or-</span></span>  
  
    -   <span data-ttu-id="ac2ae-143">**[新しい接続]** をクリックし、新しいデータ接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="ac2ae-144">詳細については、次を参照してください。[方法: SQL Server データベースへの接続を作成する](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d)です。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-144">For more information, see [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span></span>  
  
5.  <span data-ttu-id="ac2ae-145">データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、 **[次へ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac2ae-146">ダイアログ ボックスが表示された場合は、 **[はい]** をクリックしてファイルをプロジェクトに保存します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="ac2ae-147">**[アプリケーション構成ファイルに接続文字列を保存]** ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="ac2ae-148">**[データベース オブジェクトの選択]** ページの **[テーブル]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="ac2ae-149">**Customers** テーブルと **Orders** テーブルの横のチェック ボックスをオンにし、 **[完了]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="ac2ae-150">プロジェクトに**NorthwindDataSet** が追加され、 **[データ ソース]** ウィンドウに **Customers** テーブルと **Orders** テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="ac2ae-151">データ バインドされたコントロールの追加</span><span class="sxs-lookup"><span data-stu-id="ac2ae-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="ac2ae-152">この手順で<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>データ バインド コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="ac2ae-153">データ バインディング コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="ac2ae-154">**[データ ソース]** ウィンドウで、 **Customers** テーブルの最上位ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="ac2ae-155">テーブル ノードのドロップダウン リストの **[詳細]** をクリックして、テーブルのドロップ タイプを **[詳細]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="ac2ae-156">選択、**顧客**ノードにテーブルが表示され、項目テンプレート (上の領域) の領域にドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="ac2ae-157">A<xref:System.Windows.Forms.BindingNavigator>コントロールがフォームに追加され、 **NorthwindDataSet**、 **CustomersBindingSource**、 **CustomersTableAdapter**、 **TableAdapterManager**、および**CustomersBindingNavigator**のコンポーネントがコンポーネント トレイに追加されます</xref:System.Windows.Forms.BindingNavigator>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="ac2ae-158">すべてのフィールドとそれらに関連付けられているラベルを選択し、項目テンプレート領域の左端近くに配置します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="ac2ae-159">後半の&5; つのフィールド (**Region**、 **Postal Code**、 **Country**、 **Phone**、 **Fax**) とそれらに関連付けられているラベルを選択し、上へ移動して前半の&6; つのフィールドの右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="ac2ae-160">項目テンプレート (コントロールの上部領域) を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="ac2ae-161">[プロパティ] ウィンドウで、 **Size** プロパティを `427, 170`に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="ac2ae-162">この時点で、顧客の繰り返しの一覧が表示される作業アプリケーションが作成されました。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="ac2ae-163">F5 キーを押してこのアプリケーションを実行し、データの変更、および顧客レコードの追加と削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="ac2ae-164">次の省略可能な手順では、カスタマイズする方法を説明します、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="ac2ae-165">次の手順 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="ac2ae-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="ac2ae-166">このチュートリアルの後半部分は、次の&4; つの省略可能な手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="ac2ae-167">外観の変更、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="ac2ae-168">ユーザーがレコードを追加または削除できないようにする。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="ac2ae-169">検索機能を追加する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="ac2ae-170">マスター/詳細テーブルを追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="ac2ae-171">DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="ac2ae-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="ac2ae-172">このオプションの手順で変更する、`BackColor`の<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールをデザイン時</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="ac2ae-173">また、行の色を交互にし、条件に応じてラベルの `ForeColor` を変更するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="ac2ae-174">コントロールの外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="ac2ae-175">Windows フォーム デザイナーでのメインの (下部) の領域を選択して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="ac2ae-176">[プロパティ] ウィンドウで、 `BackColor` プロパティを白に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="ac2ae-177">ダブルクリックして、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コード エディターを開きます</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="ac2ae-178">コード エディターで、[イベント] ボックスの一覧の **[DrawItem]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="ac2ae-179"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベント ハンドラーを交互に使用する次のコードを追加、 `BackColor`:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="ac2ae-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     <span data-ttu-id="ac2ae-180">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac2ae-180">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]</span></span>  
  
6.  <span data-ttu-id="ac2ae-181"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベント ハンドラーを変更するには、次のコードを追加、`ForeColor`条件に応じてラベルの:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="ac2ae-181">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     <span data-ttu-id="ac2ae-182">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac2ae-182">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]</span></span>  
  
7.  <span data-ttu-id="ac2ae-183">F5 キーを押してアプリケーションを実行し、カスタマイズを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-183">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="ac2ae-184">ユーザーがレコードを追加または削除できないようにする</span><span class="sxs-lookup"><span data-stu-id="ac2ae-184">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="ac2ae-185">この省略可能な手順は、ユーザーが追加または内のレコードを削除できないようにするコードを追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-185">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="ac2ae-186">ユーザーがレコードを追加または削除できないようにするには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-186">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="ac2ae-187">Windows フォーム デザイナーで、フォームをダブルクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-187">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="ac2ae-188">`Form_Load` イベントに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-188">Add the following code to the `Form_Load` event:</span></span>  
  
     <span data-ttu-id="ac2ae-189">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac2ae-189">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]</span></span>  
  
3.  <span data-ttu-id="ac2ae-190">[クラス名] ボックスの一覧で **[BindingNavigatorDeleteItem]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-190">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="ac2ae-191">[メソッド名] ボックスの一覧で **[EnabledChanged]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-191">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="ac2ae-192">`BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-192">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     <span data-ttu-id="ac2ae-193">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac2ae-193">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac2ae-194">この手順は必要なため、<xref:System.Windows.Forms.BindingSource>有効にするには、 **DeleteItem**現在のレコードが変更されるたびにボタンをクリックします</xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-194">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="ac2ae-195">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-195">Press F5 to run the application.</span></span> <span data-ttu-id="ac2ae-196">**DeleteItem** ボタンが無効になっていて、Del キーを押しても項目を削除できないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-196">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="ac2ae-197">DataRepeater コントロールに検索機能を追加する</span><span class="sxs-lookup"><span data-stu-id="ac2ae-197">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="ac2ae-198">この省略可能な手順の値を検索する機能を実装する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-198">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="ac2ae-199">検索文字列が見つかると、このコントロールはその値を含む項目を選択し、スクロールして表示します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-199">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="ac2ae-200">検索機能を追加するには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-200">To add search capability</span></span>  
  
1.  <span data-ttu-id="ac2ae-201">ドラッグ、<xref:System.Windows.Forms.TextBox>コントロールから、**ツールボックス**を含むフォーム上に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-201">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="ac2ae-202">位置の下に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-202">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="ac2ae-203">[プロパティ] ウィンドウで、 **Name** プロパティを **SearchTextBox**に変更します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-203">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="ac2ae-204">ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**を含むフォーム上に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-204">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="ac2ae-205">位置の下に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-205">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="ac2ae-206">[プロパティ] ウィンドウで、 **Name** プロパティを **SearchButton**に変更します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-206">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="ac2ae-207">**Text** プロパティを **Search**に変更します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-207">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="ac2ae-208">ダブルクリックして、<xref:System.Windows.Forms.Button>を開くには、コード エディターを制御し、次のコードを追加、`SearchButton_Click`イベント ハンドラー</xref:System.Windows.Forms.Button> 。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-208">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     <span data-ttu-id="ac2ae-209">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac2ae-209">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]</span></span>  
  
6.  <span data-ttu-id="ac2ae-210">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-210">Press F5 to run the application.</span></span> <span data-ttu-id="ac2ae-211">**[SearchTextBox]** に顧客 ID を入力し、 **[Search]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-211">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="ac2ae-212">DataRepeater にマスター/詳細テーブルを追加する</span><span class="sxs-lookup"><span data-stu-id="ac2ae-212">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="ac2ae-213">この省略可能な手順では、1 秒あたり追加<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>各顧客に関連する注文を表示するコントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-213">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="ac2ae-214">マスター/詳細テーブルを追加するには</span><span class="sxs-lookup"><span data-stu-id="ac2ae-214">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="ac2ae-215">1 秒間をドラッグして<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールから、 **Visual Basic power Packs**  タブで、**ツールボックス**フォーム上にします</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-215">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="ac2ae-216">[プロパティ] ウィンドウで、 **Location** プロパティを `465, 25`に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-216">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="ac2ae-217">**Size** プロパティを `315, 600`に設定します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-217">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="ac2ae-218">**[データ ソース]** ウィンドウで、 **[Customers]** テーブル ノードを展開し、 **Orders** テーブルの詳細ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-218">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="ac2ae-219">この **Orders** テーブルのドロップ タイプを、テーブル ノードのドロップダウン リストの **[詳細]** をクリックして [詳細] に変更します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-219">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="ac2ae-220">これをドラッグして**注文**テーブル ノードを&2; 番目の項目テンプレートの領域 (上の領域) に<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-220">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="ac2ae-221">**OrdersBindingSource** コンポーネントおよび **OrdersTableAdapter** コンポーネントがコンポーネント トレイに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-221">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="ac2ae-222">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-222">Press F5 to run the application.</span></span> <span data-ttu-id="ac2ae-223">最初のそれぞれの顧客を選択すると<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>制御の場合は、その顧客は、2 番目に表示されるの注文<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="ac2ae-223">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2ae-224">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac2ae-224">See Also</span></span>  
 <span data-ttu-id="ac2ae-225">[DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-225">[Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-226"> [方法: DataRepeater コントロールにバインドされたデータの表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-226"> [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-227"> [方法: DataRepeater コントロールでコントロールが画面にバインドされていません。](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-227"> [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-228"> [方法: DataRepeater コントロールのレイアウトを変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-228"> [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-229"> [方法: DataRepeater コントロールに項目ヘッダーを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-229"> [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-230"> [方法: DataRepeater コントロールでデータを検索](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-230"> [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-231"> [方法:&2; つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-231"> [How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span></span>  
<span data-ttu-id="ac2ae-232"> [方法: DataRepeater コントロールの外観を変更します。](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-232"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-233"> [方法: 追加と削除 DataRepeater の項目を無効にします。](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ac2ae-233"> [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md) </span></span>  
<span data-ttu-id="ac2ae-234"> [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="ac2ae-234"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
