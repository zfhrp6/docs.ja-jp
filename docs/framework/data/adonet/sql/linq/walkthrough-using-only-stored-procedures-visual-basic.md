---
title: "チュートリアル : ストアド プロシージャのみの使用 (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2eed4db8ee76d6f7bea8b0628219e858a1db9695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="15917-102">チュートリアル : ストアド プロシージャのみの使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15917-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="15917-103">このチュートリアルでは、ストアド プロシージャのみを使用してデータにアクセスする、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。</span><span class="sxs-lookup"><span data-stu-id="15917-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="15917-104">この方法は、データ ストアへのアクセス方法を制限する目的で、データベース管理者によってよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="15917-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15917-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションでストアド プロシージャを使用して、既定の動作をオーバーライドすることもできます。これは、`Create`、`Update`、および `Delete` の各プロセスで特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="15917-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="15917-106">詳細については、次を参照してください。[のカスタマイズを挿入、更新、および削除を行う](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="15917-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="15917-107">このチュートリアルでは、Northwind サンプル データベース内のストアド プロシージャにマップされた 2 つのメソッド (CustOrdersDetail および CustOrderHist) を使用します。</span><span class="sxs-lookup"><span data-stu-id="15917-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="15917-108">SqlMetal コマンド ライン ツールを実行して [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ファイルを生成すると、対応付けが発生します。</span><span class="sxs-lookup"><span data-stu-id="15917-108">The mapping occurs when you run the SqlMetal command-line tool to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] file.</span></span> <span data-ttu-id="15917-109">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15917-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="15917-110">このチュートリアルは、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]には依存しません。</span><span class="sxs-lookup"><span data-stu-id="15917-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="15917-111">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している開発者は、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]を使用して、ストアド プロシージャの機能を実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="15917-111">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="15917-112">参照してください[LINQ to Visual Studio での SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)です。</span><span class="sxs-lookup"><span data-stu-id="15917-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="15917-113">このチュートリアルは、Visual Basic 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="15917-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="15917-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="15917-114">Prerequisites</span></span>  
 <span data-ttu-id="15917-115">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="15917-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="15917-116">このチュートリアルでは、専用フォルダー ("c:\linqtest3") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="15917-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="15917-117">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="15917-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="15917-118">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="15917-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="15917-119">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="15917-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="15917-120">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="15917-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="15917-121">データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest3 フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="15917-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="15917-122">Northwind データベースから生成された [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="15917-122">A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="15917-123">このチュートリアルは、SqlMetal ツールを使用して次のコマンド ラインで作成されています。</span><span class="sxs-lookup"><span data-stu-id="15917-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="15917-124">**sqlmetal/code:"c:\linqtest3\northwind.vb"/language:vb"c:\linqtest3\northwnd.mdf"さらに、/sprocs/functions/pluralize**</span><span class="sxs-lookup"><span data-stu-id="15917-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="15917-125">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="15917-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="15917-126">概要</span><span class="sxs-lookup"><span data-stu-id="15917-126">Overview</span></span>  
 <span data-ttu-id="15917-127">このチュートリアルは、主に次の 6 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="15917-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="15917-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ソリューションを設定します。</span><span class="sxs-lookup"><span data-stu-id="15917-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="15917-129">プロジェクトに System.Data.Linq アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="15917-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="15917-130">プロジェクトにデータベース コード ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="15917-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="15917-131">データベースへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="15917-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="15917-132">ユーザー インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="15917-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="15917-133">アプリケーションを実行およびテストします。</span><span class="sxs-lookup"><span data-stu-id="15917-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="15917-134">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="15917-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="15917-135">最初に、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="15917-135">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="15917-136">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="15917-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="15917-137">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **ファイル** メニューのをクリックして**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="15917-137">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="15917-138">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、 **[Visual Basic]**を展開し、 **[Windows]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15917-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="15917-139">**[テンプレート]** ペインの **[Windows フォーム アプリケーション]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15917-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="15917-140">**名前**ボックスに、入力**sproconlyapp」と入力**です。</span><span class="sxs-lookup"><span data-stu-id="15917-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="15917-141">**[OK]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15917-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="15917-142">Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="15917-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="15917-143">LINQ to SQL アセンブリ参照を追加する</span><span class="sxs-lookup"><span data-stu-id="15917-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="15917-144">標準の Windows フォーム アプリケーション テンプレートには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アセンブリは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="15917-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="15917-145">次の手順に従って、アセンブリを自分で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15917-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="15917-146">System.Data.Linq.dll を追加するには</span><span class="sxs-lookup"><span data-stu-id="15917-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="15917-147">**ソリューション エクスプ ローラー**をクリックして**すべてのファイル**です。</span><span class="sxs-lookup"><span data-stu-id="15917-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="15917-148">**ソリューション エクスプ ローラー**を右クリックして**参照**、クリックして**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="15917-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="15917-149">**参照の追加**ダイアログ ボックスで、をクリックして**.NET**を System.Data.Linq アセンブリをクリックし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="15917-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="15917-150">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="15917-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="15917-151">プロジェクトに Northwind コード ファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="15917-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="15917-152">この手順では、事前に SqlMetal ツールを使用して、Northwind サンプル データベースからコード ファイルを生成していることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="15917-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="15917-153">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15917-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="15917-154">プロジェクトに Northwind コード ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="15917-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="15917-155">**プロジェクト** メニューのをクリックして**既存項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="15917-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="15917-156">**既存項目の追加**ダイアログ ボックスで c:\linqtest3\northwind.vb に移動し、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="15917-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="15917-157">プロジェクトに northwind.vb ファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="15917-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="15917-158">データベース接続を作成する</span><span class="sxs-lookup"><span data-stu-id="15917-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="15917-159">この手順では、Northwind サンプル データベースへの接続を定義します。</span><span class="sxs-lookup"><span data-stu-id="15917-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="15917-160">このチュートリアルでは、パスとして "c:\linqtest3\northwnd.mdf" を使用します。</span><span class="sxs-lookup"><span data-stu-id="15917-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="15917-161">データベース接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="15917-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="15917-162">**ソリューション エクスプ ローラー**を右クリックして**Form1.vb**、クリックして**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="15917-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="15917-163">コード エディターに `Class Form1` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="15917-163">`Class Form1` appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="15917-164">`Form1` コード ブロックに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="15917-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="15917-165">ユーザー インターフェイスを設定する</span><span class="sxs-lookup"><span data-stu-id="15917-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="15917-166">この手順では、ユーザーがストアド プロシージャを実行してデータベース内のデータにアクセスできるように、インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="15917-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="15917-167">このチュートリアルで作成するアプリケーションでは、ユーザーはアプリケーションに埋め込まれているストアド プロシージャを使用してのみ、データベース内のデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="15917-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="15917-168">ユーザー インターフェイスを設定するには</span><span class="sxs-lookup"><span data-stu-id="15917-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="15917-169">戻り値を Windows フォーム デザイナー (**form1.vb [デザイン]**)。</span><span class="sxs-lookup"><span data-stu-id="15917-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="15917-170">**[表示]** メニューの **[ツールボックス]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15917-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="15917-171">ツールボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="15917-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15917-172">をクリックして、**自動的に隠す**このセクションの手順を残りの実行中に、ツールボックスを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="15917-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="15917-173">2 つのボタン、2 つのテキスト ボックス、および 2 つのラベルをツールボックスからドラッグ**Form1**です。</span><span class="sxs-lookup"><span data-stu-id="15917-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="15917-174">図のようにコントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="15917-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="15917-175">展開**Form1**コントロールを簡単に配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="15917-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="15917-176">右クリック**Label1**、クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="15917-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="15917-177">変更、**テキスト**プロパティから**Label1**に**Enter OrderID:**です。</span><span class="sxs-lookup"><span data-stu-id="15917-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="15917-178">に対して同じ方法で**Label2**、変更、**テキスト**プロパティから**Label2**に**Enter CustomerID:**です。</span><span class="sxs-lookup"><span data-stu-id="15917-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="15917-179">同じ方法で変更、**テキスト**プロパティを**Button1**に**Order Details**です。</span><span class="sxs-lookup"><span data-stu-id="15917-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="15917-180">変更、**テキスト**プロパティ**Button2**に**注文履歴**です。</span><span class="sxs-lookup"><span data-stu-id="15917-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="15917-181">すべてのテキストが表示されるように、ボタン コントロールの幅を広げます。</span><span class="sxs-lookup"><span data-stu-id="15917-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="15917-182">ボタン クリックを処理するには</span><span class="sxs-lookup"><span data-stu-id="15917-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="15917-183">ダブルクリックして**Order Details**で**Form1**を作成する、`Button1`イベント ハンドラーと、コード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="15917-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="15917-184">`Button1` のハンドラーに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="15917-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="15917-185">ダブルクリックして**Button2**を作成する Form1 に、`Button2`イベント ハンドラーと、コード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="15917-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="15917-186">`Button2` のハンドラーに次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="15917-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="15917-187">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="15917-187">Testing the Application</span></span>  
 <span data-ttu-id="15917-188">次に、アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="15917-188">Now it is time to test your application.</span></span> <span data-ttu-id="15917-189">データ ストアに対する操作は、2 つのストアド プロシージャで実行できる処理に制限されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="15917-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="15917-190">つまり、入力した orderID に含まれている製品を返す処理と、入力した CustomerID の注文製品の履歴を返す処理のみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="15917-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="15917-191">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="15917-191">To test the application</span></span>  
  
1.  <span data-ttu-id="15917-192">F5 キーを押してデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="15917-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="15917-193">Form1 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="15917-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="15917-194">**Enter OrderID**ボックスに、入力**10249**  をクリックし、 **Order Details**です。</span><span class="sxs-lookup"><span data-stu-id="15917-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="15917-195">注文 10249 に含まれている製品がメッセージ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="15917-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="15917-196">をクリックして**OK**メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="15917-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="15917-197">**Enter CustomerID**ボックスに、入力`ALFKI`、クリックして**注文履歴**です。</span><span class="sxs-lookup"><span data-stu-id="15917-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="15917-198">メッセージ ボックスに、顧客 ALFKI の注文履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="15917-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="15917-199">をクリックして**OK**メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="15917-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="15917-200">**Enter OrderID**ボックスに、入力`123`、クリックして**Order Details**です。</span><span class="sxs-lookup"><span data-stu-id="15917-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="15917-201">メッセージ ボックスに "No results" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="15917-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="15917-202">をクリックして**OK**メッセージ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="15917-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="15917-203">**デバッグ** メニューのをクリックして**デバッグを停止**です。</span><span class="sxs-lookup"><span data-stu-id="15917-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="15917-204">デバッグ セッションが終了します。</span><span class="sxs-lookup"><span data-stu-id="15917-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="15917-205">実験が完了したらをクリックして**プロジェクトを閉じる**上、**ファイル**] メニューの [入力を求められたら、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="15917-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="15917-206">次の手順</span><span class="sxs-lookup"><span data-stu-id="15917-206">Next Steps</span></span>  
 <span data-ttu-id="15917-207">いくつかの変更を加えることによって、このプロジェクトを強化できます。</span><span class="sxs-lookup"><span data-stu-id="15917-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="15917-208">たとえば、使用できるストアド プロシージャの一覧をリスト ボックスに表示し、実行するプロシージャをユーザーに選択させることができます。</span><span class="sxs-lookup"><span data-stu-id="15917-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="15917-209">レポートの出力をテキスト ファイルに送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="15917-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15917-210">参照</span><span class="sxs-lookup"><span data-stu-id="15917-210">See Also</span></span>  
 [<span data-ttu-id="15917-211">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="15917-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="15917-212">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="15917-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
