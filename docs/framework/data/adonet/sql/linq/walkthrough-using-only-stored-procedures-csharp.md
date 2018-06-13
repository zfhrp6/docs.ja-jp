---
title: 'チュートリアル : ストアド プロシージャのみを使用する (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 223c93a790e610414aa48c2aea8e884b9d841666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365424"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="e18f2-102">チュートリアル : ストアド プロシージャのみを使用する (C#)</span><span class="sxs-lookup"><span data-stu-id="e18f2-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="e18f2-103">このチュートリアルでは、ストアド プロシージャを実行することでのみデータにアクセスする、基本的な [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="e18f2-104">この方法は、データ ストアへのアクセス方法を制限する目的で、データベース管理者によってよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e18f2-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションでストアド プロシージャを使用して、既定の動作をオーバーライドすることもできます。これは、`Create`、`Update`、および `Delete` の各プロセスで特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="e18f2-106">詳細については、次を参照してください。[のカスタマイズを挿入、更新、および削除を行う](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="e18f2-107">このチュートリアルでは、Northwind サンプル データベース内のストアド プロシージャにマップされた 2 つのメソッド (CustOrdersDetail および CustOrderHist) を使用します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="e18f2-108">このマップは、SqlMetal コマンド ライン ツールを実行して C# ファイルを生成したときに作成されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="e18f2-109">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e18f2-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="e18f2-110">このチュートリアルは、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]には依存しません。</span><span class="sxs-lookup"><span data-stu-id="e18f2-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="e18f2-111">Visual Studio を使用している開発者が使用することも、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]ストアド プロシージャの機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="e18f2-112">参照してください[LINQ to Visual Studio での SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="e18f2-113">このチュートリアルは、Visual C# 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="e18f2-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e18f2-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e18f2-114">Prerequisites</span></span>  
 <span data-ttu-id="e18f2-115">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e18f2-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="e18f2-116">このチュートリアルでは、専用フォルダー ("c:\linqtest7") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="e18f2-117">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="e18f2-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="e18f2-118">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="e18f2-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="e18f2-119">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="e18f2-120">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="e18f2-121">データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest7 フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="e18f2-122">Northwind データベースから生成された C# コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="e18f2-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="e18f2-123">このチュートリアルは、SqlMetal ツールを使用して次のコマンド ラインで作成されています。</span><span class="sxs-lookup"><span data-stu-id="e18f2-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="e18f2-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="e18f2-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="e18f2-125">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e18f2-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e18f2-126">概要</span><span class="sxs-lookup"><span data-stu-id="e18f2-126">Overview</span></span>  
 <span data-ttu-id="e18f2-127">このチュートリアルは、主に次の 6 つのタスクで構成されています。</span><span class="sxs-lookup"><span data-stu-id="e18f2-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="e18f2-128">セットアップ、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio でソリューションです。</span><span class="sxs-lookup"><span data-stu-id="e18f2-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="e18f2-129">プロジェクトに System.Data.Linq アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="e18f2-130">プロジェクトにデータベース コード ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="e18f2-131">データベースへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="e18f2-132">ユーザー インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="e18f2-133">アプリケーションを実行およびテストします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="e18f2-134">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="e18f2-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="e18f2-135">この最初のタスクでは、ビルドおよび実行するために必要な参照を含む Visual Studio ソリューションを作成、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="e18f2-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="e18f2-136">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="e18f2-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="e18f2-137">Visual Studio で**ファイル** メニューのをポイント**新規**、クリックして**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="e18f2-138">**プロジェクトの種類**ペインで、**新しいプロジェクト**ダイアログ ボックスで、をクリックして**Visual c#** です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="e18f2-139">**[テンプレート]** ペインの **[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="e18f2-140">**名前**ボックスに、入力**sproconlyapp」と入力**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="e18f2-141">**場所**ボックスで、プロジェクト ファイルを格納することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="e18f2-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="e18f2-143">Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="e18f2-144">LINQ to SQL アセンブリ参照を追加する</span><span class="sxs-lookup"><span data-stu-id="e18f2-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="e18f2-145">標準の Windows フォーム アプリケーション テンプレートには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アセンブリは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="e18f2-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="e18f2-146">次の手順に従って、アセンブリを自分で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e18f2-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="e18f2-147">System.Data.Linq.dll を追加するには</span><span class="sxs-lookup"><span data-stu-id="e18f2-147">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="e18f2-148">**ソリューション エクスプ ローラー**を右クリックして**参照**、クリックして**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="e18f2-149">**参照の追加**ダイアログ ボックスで、をクリックして **.NET**を System.Data.Linq アセンブリをクリックし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e18f2-150">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e18f2-151">プロジェクトに Northwind コード ファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="e18f2-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="e18f2-152">この手順では、事前に SqlMetal ツールを使用して、Northwind サンプル データベースからコード ファイルを生成していることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="e18f2-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="e18f2-153">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e18f2-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e18f2-154">プロジェクトに Northwind コード ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="e18f2-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="e18f2-155">**プロジェクト** メニューのをクリックして**既存項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="e18f2-156">**既存項目の追加**ダイアログ ボックスで、c:\linqtest7\northwind.cs に移動し、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e18f2-157">northwind.cs ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="e18f2-158">データベース接続を作成する</span><span class="sxs-lookup"><span data-stu-id="e18f2-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="e18f2-159">この手順では、Northwind サンプル データベースへの接続を定義します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="e18f2-160">このチュートリアルでは、パスとして "c:\linqtest7\northwnd.mdf" を使用します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="e18f2-161">データベース接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="e18f2-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="e18f2-162">**ソリューション エクスプ ローラー**を右クリックして**Form1.cs**、クリックして**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="e18f2-163">`Form1` クラスに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="e18f2-164">ユーザー インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="e18f2-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="e18f2-165">この手順では、ユーザーがストアド プロシージャを実行してデータベース内のデータにアクセスできるように、インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="e18f2-166">このチュートリアルで作成するアプリケーションでは、ユーザーがデータベース内のデータにアクセスできる手段は、アプリケーションに埋め込まれたストアド プロシージャを使用することだけです。</span><span class="sxs-lookup"><span data-stu-id="e18f2-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="e18f2-167">ユーザー インターフェイスを設定するには</span><span class="sxs-lookup"><span data-stu-id="e18f2-167">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="e18f2-168">戻り値を Windows フォーム デザイナー (**Form1.cs[Design]**)。</span><span class="sxs-lookup"><span data-stu-id="e18f2-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2.  <span data-ttu-id="e18f2-169">**[表示]** メニューの **[ツールボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="e18f2-170">ツールボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e18f2-171">をクリックして、**自動的に隠す**このセクションの手順を残りの実行中に、ツールボックスを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="e18f2-172">2 つのボタン、2 つのテキスト ボックス、および 2 つのラベルをツールボックスからドラッグ**Form1**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="e18f2-173">図のようにコントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="e18f2-174">展開**Form1**コントロールを簡単に配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="e18f2-175">右クリック**label1**、クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e18f2-176">変更、**テキスト**プロパティから**label1**に**Enter OrderID:** です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="e18f2-177">に対して同じ方法で**label2**、変更、**テキスト**プロパティから**label2**に**Enter CustomerID:** です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="e18f2-178">同じ方法で変更、**テキスト**プロパティを**button1**に**Order Details**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="e18f2-179">変更、**テキスト**プロパティ**button2**に**注文履歴**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="e18f2-180">すべてのテキストが表示されるように、ボタン コントロールの幅を広げます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="e18f2-181">ボタン クリックを処理するには</span><span class="sxs-lookup"><span data-stu-id="e18f2-181">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="e18f2-182">ダブルクリックして**Order Details**で**Form1**をコード エディターに button1 のイベント ハンドラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2.  <span data-ttu-id="e18f2-183">`button1` のハンドラーに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  <span data-ttu-id="e18f2-184">ダブルクリックして**button2**で**Form1**を開くには、`button2`ハンドラー</span><span class="sxs-lookup"><span data-stu-id="e18f2-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4.  <span data-ttu-id="e18f2-185">`button2` のハンドラーに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="e18f2-186">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="e18f2-186">Testing the Application</span></span>  
 <span data-ttu-id="e18f2-187">次に、アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="e18f2-187">Now it is time to test your application.</span></span> <span data-ttu-id="e18f2-188">データ ストアに対する操作は、2 つのストアド プロシージャで実行できる処理に制限されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e18f2-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="e18f2-189">つまり、入力した orderID に含まれている製品を返す処理と、入力した CustomerID の注文製品の履歴を返す処理のみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="e18f2-190">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="e18f2-190">To test the application</span></span>  
  
1.  <span data-ttu-id="e18f2-191">F5 キーを押してデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="e18f2-192">Form1 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-192">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="e18f2-193">**Enter OrderID**ボックスに、入力`10249`、クリックして**Order Details**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="e18f2-194">注文 10249 に含まれている製品がメッセージ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="e18f2-195">をクリックして**OK**メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-195">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="e18f2-196">**Enter CustomerID**ボックスに、入力`ALFKI`、クリックして**注文履歴**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="e18f2-197">顧客 ALFKI の注文履歴がメッセージ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="e18f2-198">をクリックして**OK**メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-198">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="e18f2-199">**Enter OrderID**ボックスに、入力`123`、クリックして**Order Details**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="e18f2-200">"No results" というメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="e18f2-201">をクリックして**OK**メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-201">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="e18f2-202">**デバッグ** メニューのをクリックして**デバッグを停止**です。</span><span class="sxs-lookup"><span data-stu-id="e18f2-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="e18f2-203">デバッグ セッションが終了します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-203">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="e18f2-204">実験が完了したらをクリックして**プロジェクトを閉じる**上、**ファイル**] メニューの [入力を求められたら、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="e18f2-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e18f2-205">次の手順</span><span class="sxs-lookup"><span data-stu-id="e18f2-205">Next Steps</span></span>  
 <span data-ttu-id="e18f2-206">いくつかの変更を加えることによって、このプロジェクトを強化できます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="e18f2-207">たとえば、使用できるストアド プロシージャの一覧をリスト ボックスに表示し、実行するプロシージャをユーザーに選択させることができます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="e18f2-208">レポートの出力をテキスト ファイルに送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="e18f2-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18f2-209">関連項目</span><span class="sxs-lookup"><span data-stu-id="e18f2-209">See Also</span></span>  
 [<span data-ttu-id="e18f2-210">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="e18f2-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="e18f2-211">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e18f2-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
