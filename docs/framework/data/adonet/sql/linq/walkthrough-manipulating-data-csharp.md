---
title: "チュートリアル : データの操作 (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 502023c3929ffaa6766c906ca32489b43915f0ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="f8d11-102">チュートリアル : データの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f8d11-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="f8d11-103">このチュートリアルでは、データベースに対してデータの追加、変更、および削除を行う、基本の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] シナリオ全体を示します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="f8d11-104">顧客の追加、顧客名の変更、および注文の削除を行うため、サンプルの Northwind データベースのコピーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="f8d11-105">このチュートリアルは、Visual C# 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="f8d11-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8d11-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f8d11-106">Prerequisites</span></span>  
 <span data-ttu-id="f8d11-107">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f8d11-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="f8d11-108">このチュートリアルでは、専用フォルダー ("c:\linqtest6") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="f8d11-109">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="f8d11-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="f8d11-110">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="f8d11-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="f8d11-111">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="f8d11-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="f8d11-112">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="f8d11-113">データベースをダウンロードしたら、northwnd.mdf ファイルを c:\linqtest6 フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="f8d11-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
-   <span data-ttu-id="f8d11-114">Northwind データベースから生成された C# コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="f8d11-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="f8d11-115">このファイルを生成するには、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]または SQLMetal ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="f8d11-116">このチュートリアルは、SQLMetal ツールを使用して次のコマンド ラインで作成されています。</span><span class="sxs-lookup"><span data-stu-id="f8d11-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="f8d11-117">**sqlmetal/code:"c:\linqtest6\northwind.cs"/language:csharp"C:\linqtest6\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="f8d11-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="f8d11-118">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f8d11-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="f8d11-119">概要</span><span class="sxs-lookup"><span data-stu-id="f8d11-119">Overview</span></span>  
 <span data-ttu-id="f8d11-120">このチュートリアルは、主に次の 6 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="f8d11-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="f8d11-121">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="f8d11-122">プロジェクトにデータベース コード ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="f8d11-123">新しい顧客オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="f8d11-124">顧客の連絡先名を変更します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="f8d11-125">注文を削除します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="f8d11-126">これらの変更を Northwind データベースに送信します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="f8d11-127">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="f8d11-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="f8d11-128">最初に、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-128">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="f8d11-129">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="f8d11-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="f8d11-130">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **ファイル** メニューのをポイント**新規**、クリックして**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-130">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f8d11-131">**プロジェクトの種類**ペインで、**新しいプロジェクト**ダイアログ ボックスで、をクリックして**Visual c#**です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="f8d11-132">**[テンプレート]** ペインの **[コンソール アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8d11-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="f8d11-133">**名前**ボックスに、入力**linqdatamanipulationapp」と入力**です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="f8d11-134">**場所**ボックスで、プロジェクト ファイルを格納することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="f8d11-135">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8d11-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="f8d11-136">LINQ の参照とディレクティブを追加する</span><span class="sxs-lookup"><span data-stu-id="f8d11-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="f8d11-137">このチュートリアルで使用するアセンブリは、既定ではプロジェクトにインストールされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8d11-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="f8d11-138">System.Data.Linq がプロジェクトの参照として表示されない場合は、次に説明する手順に従って追加してください。</span><span class="sxs-lookup"><span data-stu-id="f8d11-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="f8d11-139">System.Data.Linq を追加するには</span><span class="sxs-lookup"><span data-stu-id="f8d11-139">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="f8d11-140">**ソリューション エクスプ ローラー**を右クリックして**参照**、クリックして**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="f8d11-141">**参照の追加**ダイアログ ボックスで、をクリックして**.NET**を System.Data.Linq アセンブリをクリックし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f8d11-142">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f8d11-142">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="f8d11-143">Program.cs の冒頭に、次のディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f8d11-144">プロジェクトに Northwind コード ファイルを追加する</span><span class="sxs-lookup"><span data-stu-id="f8d11-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="f8d11-145">これらの手順では、SQLMetal ツールを使用して Northwind サンプル データベースからコード ファイルを生成していることが前提です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="f8d11-146">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8d11-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f8d11-147">プロジェクトに Northwind コード ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="f8d11-147">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="f8d11-148">**プロジェクト** メニューのをクリックして**既存項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="f8d11-149">**既存項目の追加**ダイアログ ボックスで c:\linqtest6\northwind.cs に移動し、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f8d11-150">northwind.cs ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f8d11-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="f8d11-151">データベース接続の設定</span><span class="sxs-lookup"><span data-stu-id="f8d11-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="f8d11-152">最初に、データベースへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="f8d11-152">First, test your connection to the database.</span></span> <span data-ttu-id="f8d11-153">データベースの名前 Northwnd に i の文字が欠けていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f8d11-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="f8d11-154">次の手順でエラーが生成された後で、northwind.cs ファイルを調べて、Northwind 部分クラスのスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="f8d11-155">データベース接続を設定してテストするには</span><span class="sxs-lookup"><span data-stu-id="f8d11-155">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="f8d11-156">Program クラスの `Main` メソッドに次のコードを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f8d11-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  <span data-ttu-id="f8d11-157">この時点でアプリケーションをテストするには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="f8d11-158">A**コンソール**ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="f8d11-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="f8d11-159">Enter キーを押してアプリケーションを閉じることができます、**コンソール**ウィンドウ、またはをクリックして**デバッグの停止**上、 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **デバッグ**メニュー。</span><span class="sxs-lookup"><span data-stu-id="f8d11-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="f8d11-160">新しいエンティティの作成</span><span class="sxs-lookup"><span data-stu-id="f8d11-160">Creating a New Entity</span></span>  
 <span data-ttu-id="f8d11-161">新しいエンティティを作成する手順は簡単です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="f8d11-162">`Customer` キーワードを使用してオブジェクト (`new` など) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="f8d11-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="f8d11-163">以降のセクションでは、ローカル キャッシュのみに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="f8d11-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="f8d11-164">このチュートリアルの終盤で <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すまで、変更内容はデータベースに送信されません。</span><span class="sxs-lookup"><span data-stu-id="f8d11-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="f8d11-165">新しい Customer エンティティ オブジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="f8d11-165">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="f8d11-166">次のコードを `Customer` メソッド内の `Console.ReadLine();` の前に追加することで、新しい `Main` を作成します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="f8d11-167">F5 キーを押してソリューションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="f8d11-167">Press F5 to debug the solution.</span></span>  
  
3.  <span data-ttu-id="f8d11-168">Enter キーを押して、**コンソール**ウィンドウがデバッグを停止し、このチュートリアルを続行します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="f8d11-169">エンティティの更新</span><span class="sxs-lookup"><span data-stu-id="f8d11-169">Updating an Entity</span></span>  
 <span data-ttu-id="f8d11-170">以降の手順では、`Customer` オブジェクトを取得し、そのプロパティの 1 つを変更します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="f8d11-171">顧客の名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="f8d11-171">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="f8d11-172">`Console.ReadLine();` の前に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="f8d11-173">エンティティの削除</span><span class="sxs-lookup"><span data-stu-id="f8d11-173">Deleting an Entity</span></span>  
 <span data-ttu-id="f8d11-174">同じ顧客オブジェクトを使用して、最初の注文を削除できます。</span><span class="sxs-lookup"><span data-stu-id="f8d11-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="f8d11-175">行間のリレーションシップを切断し、データベースから行を削除する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="f8d11-176">オブジェクトを削除できることを確認するため、次のコードを `Console.ReadLine` の前に追加します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="f8d11-177">行を削除するには</span><span class="sxs-lookup"><span data-stu-id="f8d11-177">To delete a row</span></span>  
  
-   <span data-ttu-id="f8d11-178">`Console.ReadLine();` の直前に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="f8d11-179">変更内容のデータベースへの送信</span><span class="sxs-lookup"><span data-stu-id="f8d11-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="f8d11-180">最後の手順は、オブジェクトの作成、更新、および削除を実際にデータベースに送信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="f8d11-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="f8d11-181">この手順を行わないと、変更はローカルのみに留まり、クエリの結果には反映されません。</span><span class="sxs-lookup"><span data-stu-id="f8d11-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="f8d11-182">データベースに変更内容を送信するには</span><span class="sxs-lookup"><span data-stu-id="f8d11-182">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="f8d11-183">`Console.ReadLine` の直前に次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="f8d11-184">変更内容の送信前と送信後の変化を示すために、次のコードを (`SubmitChanges` の後に) 挿入します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  <span data-ttu-id="f8d11-185">F5 キーを押してソリューションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="f8d11-185">Press F5 to debug the solution.</span></span>  
  
4.  <span data-ttu-id="f8d11-186">Enter キーを押して、**コンソール**アプリケーションを終了するウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="f8d11-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8d11-187">変更内容を送信して新しい顧客を追加した後で、このソリューションを再度実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="f8d11-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="f8d11-188">ソリューションを再度実行するには、追加する顧客の名前と顧客 ID を変更します。</span><span class="sxs-lookup"><span data-stu-id="f8d11-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d11-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8d11-189">See Also</span></span>  
 [<span data-ttu-id="f8d11-190">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="f8d11-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
