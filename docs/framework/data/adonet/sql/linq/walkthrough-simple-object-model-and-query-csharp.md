---
title: "チュートリアル : 簡単なオブジェクト モデルとクエリ (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d082b7d53330bf755f9f4322ae24d8ad3dc0ac7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="68625-102">チュートリアル : 簡単なオブジェクト モデルとクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="68625-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="68625-103">このチュートリアルでは、複雑さを抑えた、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 全体の基本的なシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="68625-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="68625-104">サンプルの Northwind データベースにある Customers テーブルのモデル化を行うエンティティ クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="68625-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="68625-105">次に、住所がロンドンの顧客を表示するための簡単なクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="68625-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="68625-106">このチュートリアルでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の考え方を示すために、コード中心の方法をあえて使用しています。</span><span class="sxs-lookup"><span data-stu-id="68625-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="68625-107">通常は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用してオブジェクト モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="68625-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="68625-108">このチュートリアルは、Visual C# 開発設定を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="68625-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="68625-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="68625-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="68625-110">このチュートリアルでは、専用フォルダー ("c:\linqtest5") を使用してファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="68625-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="68625-111">チュートリアルを開始する前に、このフォルダーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="68625-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="68625-112">このチュートリアルには、Northwind サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="68625-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="68625-113">開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード サイトからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="68625-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="68625-114">手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。</span><span class="sxs-lookup"><span data-stu-id="68625-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="68625-115">データベースをダウンロードしたら、ファイルを c:\linqtest5 フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="68625-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="68625-116">概要</span><span class="sxs-lookup"><span data-stu-id="68625-116">Overview</span></span>  
 <span data-ttu-id="68625-117">このチュートリアルは、主に次の 6 つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="68625-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="68625-118">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="68625-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="68625-119">データベース テーブルにクラスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="68625-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="68625-120">クラスに対し、データベース列を表すプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="68625-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="68625-121">Northwind データベースへの接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="68625-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="68625-122">データベースに対して実行する簡単なクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="68625-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="68625-123">クエリを実行して結果を観察する。</span><span class="sxs-lookup"><span data-stu-id="68625-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="68625-124">LINQ to SQL ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="68625-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="68625-125">最初に、[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] プロジェクトをビルドおよび実行するために必要な参照を含む [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="68625-125">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="68625-126">LINQ to SQL ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="68625-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="68625-127">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **ファイル** メニューのをポイント**新規**、クリックして**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="68625-127">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="68625-128">**プロジェクトの種類**のペイン、**新しいプロジェクト**ダイアログ ボックスで、をクリックして**Visual c#**です。</span><span class="sxs-lookup"><span data-stu-id="68625-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="68625-129">**[テンプレート]** ペインの **[コンソール アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68625-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="68625-130">**名前**ボックスに、入力**linqconsoleapp」と入力**です。</span><span class="sxs-lookup"><span data-stu-id="68625-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="68625-131">**場所**ボックスで、プロジェクト ファイルを格納することを確認します。</span><span class="sxs-lookup"><span data-stu-id="68625-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="68625-132">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="68625-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="68625-133">LINQ の参照とディレクティブを追加する</span><span class="sxs-lookup"><span data-stu-id="68625-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="68625-134">このチュートリアルで使用するアセンブリは、既定ではプロジェクトにインストールされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="68625-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="68625-135">かどうか System.Data.Linq がプロジェクトに参照として一覧表示されません (展開、**参照**内のノード**ソリューション エクスプ ローラー**)、次の手順に従って追加します。</span><span class="sxs-lookup"><span data-stu-id="68625-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="68625-136">System.Data.Linq を追加するには</span><span class="sxs-lookup"><span data-stu-id="68625-136">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="68625-137">**ソリューション エクスプ ローラー**を右クリックして**参照**、クリックして**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="68625-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="68625-138">**参照の追加**ダイアログ ボックスで、をクリックして**.NET**を System.Data.Linq アセンブリをクリックし、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="68625-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="68625-139">アセンブリがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="68625-139">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="68625-140">上部にある次のディレクティブを追加**Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="68625-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="68625-141">データベース テーブルにクラスを対応付ける</span><span class="sxs-lookup"><span data-stu-id="68625-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="68625-142">この手順では、クラスを作成して、データベース テーブルに対応付けます。</span><span class="sxs-lookup"><span data-stu-id="68625-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="68625-143">このようなクラスと呼ばれる、*エンティティ クラス*です。</span><span class="sxs-lookup"><span data-stu-id="68625-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="68625-144">対応付けは、<xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加するだけで完了します。</span><span class="sxs-lookup"><span data-stu-id="68625-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="68625-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> プロパティを使用して、データベースのテーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="68625-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="68625-146">エンティティ クラスを作成し、データベース テーブルに対応付けるには</span><span class="sxs-lookup"><span data-stu-id="68625-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="68625-147">Program.cs の `Program` クラス宣言の直前に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="68625-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="68625-148">データベース列を表すプロパティをクラスに追加する</span><span class="sxs-lookup"><span data-stu-id="68625-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="68625-149">この手順では、いくつかのタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="68625-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="68625-150"><xref:System.Data.Linq.Mapping.ColumnAttribute> 属性を使用して、エンティティ クラスの `CustomerID` プロパティおよび `City` プロパティを、データベース テーブルの列を表すものとして指定します。</span><span class="sxs-lookup"><span data-stu-id="68625-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="68625-151">`CustomerID` プロパティを、データベースの主キー列を表すものとして指定します。</span><span class="sxs-lookup"><span data-stu-id="68625-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="68625-152">プライベートでの格納用として `_CustomerID` フィールドおよび `_City` フィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="68625-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> <span data-ttu-id="68625-153">これで、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、ビジネス ロジックを含む場合があるパブリック アクセサーを使用せずに、値を直接格納および取得できます。</span><span class="sxs-lookup"><span data-stu-id="68625-153">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="68625-154">2 つのデータベース列の特性を指定するには</span><span class="sxs-lookup"><span data-stu-id="68625-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="68625-155">Program.cs の `Customer` クラスの中かっこ内に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="68625-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="68625-156">Northwind データベースへの接続を指定する</span><span class="sxs-lookup"><span data-stu-id="68625-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="68625-157">この手順では、<xref:System.Data.Linq.DataContext> オブジェクトを使用して、コードで作成したデータ構造とデータベース本体との間の接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="68625-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="68625-158">データベースからのオブジェクトの取得や、変更内容の送信では、<xref:System.Data.Linq.DataContext> を仲介役として使用します。</span><span class="sxs-lookup"><span data-stu-id="68625-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="68625-159">また、データベースの Customers テーブルに対するクエリ用として、型指定された論理的なテーブルの役割を果たす `Table<Customer>` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="68625-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="68625-160">これらのクエリの作成と実行は後の手順で行います。</span><span class="sxs-lookup"><span data-stu-id="68625-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="68625-161">データベース接続を指定するには</span><span class="sxs-lookup"><span data-stu-id="68625-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="68625-162">`Main` メソッドに次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="68625-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="68625-163">`northwnd.mdf` ファイルは、linqtest5 フォルダーにあるものとします。</span><span class="sxs-lookup"><span data-stu-id="68625-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="68625-164">詳細については、このチュートリアルの「前提条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68625-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="68625-165">簡単なクエリの作成</span><span class="sxs-lookup"><span data-stu-id="68625-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="68625-166">この手順では、データベースの Customers テーブルから、住所が London の顧客を検索するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="68625-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="68625-167">この手順で作成するクエリ コードは、クエリを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="68625-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="68625-168">実行は行いません。</span><span class="sxs-lookup"><span data-stu-id="68625-168">It does not execute it.</span></span> <span data-ttu-id="68625-169">このアプローチと呼ばれる*遅延実行*です。</span><span class="sxs-lookup"><span data-stu-id="68625-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="68625-170">詳細については、「[LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68625-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="68625-171">また、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が生成した SQL コマンドをログに出力します。</span><span class="sxs-lookup"><span data-stu-id="68625-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="68625-172"><xref:System.Data.Linq.DataContext.Log%2A> を使用したこのログ機能は、デバッグに有効で、データベースに送信されたコマンドが目的のクエリを正確に表しているかどうかを確認するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="68625-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="68625-173">簡単なクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="68625-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="68625-174">`Main` メソッドの `Table<Customer>` 宣言の後に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="68625-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="68625-175">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="68625-175">Executing the Query</span></span>  
 <span data-ttu-id="68625-176">この手順では、実際にクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="68625-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="68625-177">ここまでの手順で作成したクエリ式は、結果が必要になるまでは評価されません。</span><span class="sxs-lookup"><span data-stu-id="68625-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="68625-178">`foreach` の反復処理を開始した時点で、データベースに対して SQL コマンドが実行され、オブジェクトが実体化されます。</span><span class="sxs-lookup"><span data-stu-id="68625-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="68625-179">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="68625-179">To execute the query</span></span>  
  
1.  <span data-ttu-id="68625-180">`Main` メソッドの末尾 (クエリ指定の後) に次のコードを入力または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="68625-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="68625-181">F5 キーを押してアプリケーションをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="68625-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="68625-182">アプリケーションでは、実行時エラーを生成する場合のトラブルシューティングに関するセクションを参照してください。[チュートリアルによる学習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)です。</span><span class="sxs-lookup"><span data-stu-id="68625-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="68625-183">クエリの結果は、以下のようにコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="68625-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  <span data-ttu-id="68625-184">コンソール ウィンドウで Enter キーを押してアプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="68625-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="68625-185">次の手順</span><span class="sxs-lookup"><span data-stu-id="68625-185">Next Steps</span></span>  
 <span data-ttu-id="68625-186">[チュートリアル: リレーションシップ間でクエリを実行する (c#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)トピックでは、このチュートリアルの終了が続行されます。</span><span class="sxs-lookup"><span data-stu-id="68625-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="68625-187">チュートリアルの「リレーションシップ間でのクエリ方法[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]と同様に、テーブル全体を照会できます*結合*リレーショナル データベースにします。</span><span class="sxs-lookup"><span data-stu-id="68625-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="68625-188">「リレーションシップ間でクエリを実行する」のチュートリアルに進む場合は、必要条件として、ここで完了したチュートリアルのソリューションを保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="68625-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68625-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="68625-189">See Also</span></span>  
 [<span data-ttu-id="68625-190">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="68625-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
