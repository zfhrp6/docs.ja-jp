---
title: "チュートリアル: BatchBlock および BatchedJoinBlock を使用した効率の向上"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="c73c5-102">チュートリアル: BatchBlock および BatchedJoinBlock を使用した効率の向上</span><span class="sxs-lookup"><span data-stu-id="c73c5-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="c73c5-103">TPL データ フロー ライブラリが提供する <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> および <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> クラスを使って、1 つ以上のソースからデータを受信してバッファーに格納し、それを 1 つのコレクションとして反映することができます。</span><span class="sxs-lookup"><span data-stu-id="c73c5-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="c73c5-104">このバッチ メカニズムは、1 つ以上のソースからデータを収集し、複数のデータ要素をバッチとして処理する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c73c5-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="c73c5-105">例として、データフローを使ってレコードをデータベースに挿入するアプリケーションについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="c73c5-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="c73c5-106">この操作は、1 つずつ順番にではなく、複数の項目が同時に挿入される場合により効率的となります。</span><span class="sxs-lookup"><span data-stu-id="c73c5-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="c73c5-107">このドキュメントでは、<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> クラスを使用して、そのようなデータベースの挿入操作を効率的に行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="c73c5-108">また、<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> クラスを使用して、プログラムでデータベースを読み取る場合に、その結果と発生する例外の両方をキャプチャする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="c73c5-109">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="c73c5-109">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="c73c5-110">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="c73c5-110">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c73c5-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c73c5-111">Prerequisites</span></span>  
  
1.  <span data-ttu-id="c73c5-112">ブロックの結合」セクションを読み、[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)このチュートリアルを開始する前に文書化します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-112">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="c73c5-113">コンピューターに Northwind データベース (Northwind.sdf) のコピーがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-113">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="c73c5-114">このファイルは通常、フォルダーにプログラム Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\です。</span><span class="sxs-lookup"><span data-stu-id="c73c5-114">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c73c5-115">Windows のバージョンによっては、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] が管理者以外のモードで実行されている場合には、Northwind.sdf に接続できません。</span><span class="sxs-lookup"><span data-stu-id="c73c5-115">In some versions of Windows, you cannot connect to Northwind.sdf if [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] is running in a non-administrator mode.</span></span> <span data-ttu-id="c73c5-116">Northwind.sdf に接続するには、開始[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]または[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]のコマンド プロンプトで、**管理者として実行**モード。</span><span class="sxs-lookup"><span data-stu-id="c73c5-116">To connect to Northwind.sdf, start [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="c73c5-117">このチュートリアルは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c73c5-117">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="c73c5-118">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="c73c5-118">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="c73c5-119">Employee クラスの定義</span><span class="sxs-lookup"><span data-stu-id="c73c5-119">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="c73c5-120">従業員データベースの操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-120">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="c73c5-121">バッファリングを使用しない従業員データをデータベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-121">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="c73c5-122">バッファリングを使用して、従業員データをデータベースに追加するには</span><span class="sxs-lookup"><span data-stu-id="c73c5-122">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="c73c5-123">バッファリングされた結合を使用して、データベースから従業員データを読み取る</span><span class="sxs-lookup"><span data-stu-id="c73c5-123">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="c73c5-124">コード例全体</span><span class="sxs-lookup"><span data-stu-id="c73c5-124">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="c73c5-125">コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="c73c5-125">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="c73c5-126">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]、Visual c# または Visual Basic 作成**コンソール アプリケーション**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="c73c5-126">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="c73c5-127">このドキュメントでは、プロジェクトの名前を `DataflowBatchDatabase` とします。</span><span class="sxs-lookup"><span data-stu-id="c73c5-127">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="c73c5-128">プロジェクトで、System.Data.SqlServerCe.dll への参照と System.Threading.Tasks.Dataflow.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-128">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="c73c5-129">Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) が次の `using` (`Imports` の [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ステートメントを含むことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-129">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="c73c5-130">`Program` クラスに次のデータ メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-130">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="c73c5-131">Employee クラスの定義</span><span class="sxs-lookup"><span data-stu-id="c73c5-131">Defining the Employee Class</span></span>  
 <span data-ttu-id="c73c5-132">`Program` クラスに `Employee` クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-132">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="c73c5-133">`Employee` クラスには、`EmployeeID`、`LastName`、および `FirstName` という 3 つのプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c73c5-133">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="c73c5-134">これらのプロパティは、Northwind データベースの `Employee ID` テーブルの `Last Name`、`First Name` および `Employees` の列に対応します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-134">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="c73c5-135">このデモでは、`Employee` クラスは、プロパティに任意の値を持つ `Random` オブジェクトを作成する、`Employee` メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-135">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="c73c5-136">従業員データベースの操作の定義</span><span class="sxs-lookup"><span data-stu-id="c73c5-136">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="c73c5-137">`Program` クラスに `InsertEmployees`、`GetEmployeeCount` および `GetEmployeeID` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-137">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="c73c5-138">`InsertEmployees` メソッドは、データベースに新しい従業員レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-138">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="c73c5-139">`GetEmployeeCount` メソッドは `Employees` テーブルのエントリの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-139">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="c73c5-140">`GetEmployeeID` メソッドは、指定された名前を持つ最初の従業員 ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-140">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="c73c5-141">これらの各メソッドは、Northwind データベースへの接続文字列を受け取り、`System.Data.SqlServerCe` 名前空間の機能を使用して、データベースと通信します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-141">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="c73c5-142">バッファリングを使用しない従業員データのデータベースへの追加</span><span class="sxs-lookup"><span data-stu-id="c73c5-142">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="c73c5-143">`Program` クラスに `AddEmployees` および `PostRandomEmployees` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-143">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="c73c5-144">`AddEmployees` メソッドは、データベースにデータ フローを使用して任意の従業員データを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-144">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="c73c5-145">それは、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> メソッドを呼び出す `InsertEmployees` オブジェクトを作成して、従業員のエントリをデータベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-145">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="c73c5-146">次に `AddEmployees` メソッドは、`PostRandomEmployees` メソッドを呼び出して、複数の `Employee` オブジェクトを <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトへポストします。</span><span class="sxs-lookup"><span data-stu-id="c73c5-146">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="c73c5-147">次に `AddEmployees` メソッドは、すべての挿入操作が終了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-147">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="c73c5-148">バッファリングを使用した従業員データのデータベースへの追加</span><span class="sxs-lookup"><span data-stu-id="c73c5-148">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="c73c5-149">`Program` クラスに `AddEmployeesBatched` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-149">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="c73c5-150">このメソッドは `AddEmployees` に似ていますが、<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> クラスを使用して複数の `Employee` オブジェクトをバッファリングしてから、それらのオブジェクトを <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトに送信する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="c73c5-150">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="c73c5-151"><xref:System.Threading.Tasks.Dataflow.BatchBlock%601> クラスは複数の要素を 1 つのコレクションとして反映させるため、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトは `Employee` オブジェクトの配列として動作するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c73c5-151">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="c73c5-152">`AddEmployees` メソッドと同様に、`AddEmployeesBatched` は `PostRandomEmployees` メソッドを呼び出して複数の `Employee` オブジェクトをポストしますが、`AddEmployeesBatched` はこれらのオブジェクトを <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> オブジェクトにポストします。</span><span class="sxs-lookup"><span data-stu-id="c73c5-152">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="c73c5-153">`AddEmployeesBatched`メソッドは、すべての insert 操作を完了するのにも待機します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-153">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="c73c5-154">バッファリングされた結合を使用した従業員データのデータベースからの読み込み</span><span class="sxs-lookup"><span data-stu-id="c73c5-154">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="c73c5-155">`Program` クラスに `GetRandomEmployees` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-155">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="c73c5-156">このメソッドは任意の従業員の情報をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-156">This method prints information about random employees to the console.</span></span> <span data-ttu-id="c73c5-157">それは複数の任意の `Employee` オブジェクトを作成し、`GetEmployeeID` メソッドを呼び出して、各オブジェクトの一意の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-157">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="c73c5-158">指定された姓名に一致する従業員がいない場合には `GetEmployeeID` メソッドは例外をスローするため、`GetRandomEmployees` メソッドは <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> クラスを使用して、`Employee` の呼び出しが成功した場合には `GetEmployeeID` オブジェクトを格納し、呼び出しが失敗した場合には <xref:System.Exception?displayProperty=nameWithType> オブジェクトを格納します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-158">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="c73c5-159">この例では、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトは、<xref:System.Tuple%602> オブジェクトのリストと `Employee` オブジェクトのリストを持つ <xref:System.Exception> オブジェクトで動作します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-159">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="c73c5-160"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> オブジェクトは、受け取った `Employee` および <xref:System.Exception> オブジェクトの数の合計がバッチのサイズと等しくなったときに、このデータを反映します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-160">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="c73c5-161">完全な例</span><span class="sxs-lookup"><span data-stu-id="c73c5-161">The Complete Example</span></span>  
 <span data-ttu-id="c73c5-162">完全なコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-162">The following example shows the complete code.</span></span> <span data-ttu-id="c73c5-163">`Main` メソッドは、バッチされたデータベースの挿入の実行に必要な時間と、非バッチでのデータベースの挿入の実行時間を比較します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-163">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="c73c5-164">また、バッファリングされた結合を使用した従業員データのデータベースから読み取りと、エラーの報告についても示します。</span><span class="sxs-lookup"><span data-stu-id="c73c5-164">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="c73c5-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="c73c5-165">See Also</span></span>  
 [<span data-ttu-id="c73c5-166">データフロー</span><span class="sxs-lookup"><span data-stu-id="c73c5-166">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
