---
title: "F# を使用して Azure テーブル ストレージの概要します。"
description: "Azure テーブル ストレージ、NoSQL データ ストアを使用してクラウドに構造化データを格納します。"
keywords: "visual f#、f#、関数型プログラミングでは、.NET では、.NET Core では、Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 905374a60261b0c2a863edb956943d41ae80f04d
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a><span data-ttu-id="bb901-104">F# を使用して Azure テーブル ストレージの概要します。</span><span class="sxs-lookup"><span data-stu-id="bb901-104">Get started with Azure Table storage using F#</span></span> #

<span data-ttu-id="bb901-105">Azure テーブル ストレージは、クラウドで構造化された NoSQL データを格納するサービスです。</span><span class="sxs-lookup"><span data-stu-id="bb901-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="bb901-106">テーブル ストレージは、schemaless 設計により、キー/属性ストアです。</span><span class="sxs-lookup"><span data-stu-id="bb901-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="bb901-107">テーブル ストレージは schemaless であるためには、アプリケーションするの必要に応じて、データを適応させる簡単です。</span><span class="sxs-lookup"><span data-stu-id="bb901-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="bb901-108">データへのアクセスは、高速でコスト効果の高いアプリケーションのすべての種類です。</span><span class="sxs-lookup"><span data-stu-id="bb901-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="bb901-109">テーブル ストレージでは、コストと比べて著しく低く従来の SQL のようなデータのボリュームを通常します。</span><span class="sxs-lookup"><span data-stu-id="bb901-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="bb901-110">テーブル ストレージを使用して、web アプリケーション、アドレス帳、デバイス情報、およびサービスを必要とするメタデータの他の種類のユーザー データなどの柔軟なデータセットを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="bb901-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="bb901-111">テーブルのエンティティの任意の数を格納することができ、ストレージ アカウントは、ストレージ アカウントの容量の上限に達するまで、テーブルの任意の数を含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="bb901-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="bb901-112">このチュートリアルについて</span><span class="sxs-lookup"><span data-stu-id="bb901-112">About this tutorial</span></span>

<span data-ttu-id="bb901-113">このチュートリアルでは、f# を作成してテーブルの削除し挿入、更新、削除、およびテーブル データのクエリを含む、Azure テーブル ストレージを使用した一般的なタスクを実行するコードを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bb901-113">This tutorial shows how to write F# code to do some common tasks using Azure Table storage, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

<span data-ttu-id="bb901-114">テーブル ストレージの概念的概要についてを参照してください[テーブル ストレージは、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-tables)</span><span class="sxs-lookup"><span data-stu-id="bb901-114">For a conceptual overview of table storage, please see [the .NET guide for table storage](/azure/storage/storage-dotnet-how-to-use-tables)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb901-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bb901-115">Prerequisites</span></span>

<span data-ttu-id="bb901-116">このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。</span><span class="sxs-lookup"><span data-stu-id="bb901-116">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="bb901-117">ストレージ アクセス キーは、このアカウントにも必要です。</span><span class="sxs-lookup"><span data-stu-id="bb901-117">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="bb901-118">作成、f# スクリプトと開始 f# 対話型</span><span class="sxs-lookup"><span data-stu-id="bb901-118">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="bb901-119">この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb901-119">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="bb901-120">F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`tables.fsx`、f# 開発環境でします。</span><span class="sxs-lookup"><span data-stu-id="bb901-120">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="bb901-121">次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="bb901-121">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="bb901-122">Microsoft.Azure 名前空間を取得するために、'Microsoft.WindowsAzure.ConfigurationManager' に対して再度操作を行います。</span><span class="sxs-lookup"><span data-stu-id="bb901-122">Do it again for \`Microsoft.WindowsAzure.ConfigurationManager' in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="bb901-123">名前空間の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="bb901-123">Add namespace declarations</span></span>

<span data-ttu-id="bb901-124">次の追加`open`ステートメントの先頭に、`tables.fsx`ファイル。</span><span class="sxs-lookup"><span data-stu-id="bb901-124">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="bb901-125">接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="bb901-125">Get your connection string</span></span>

<span data-ttu-id="bb901-126">このチュートリアルでは、Azure ストレージ接続文字列を必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb901-126">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="bb901-127">接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。</span><span class="sxs-lookup"><span data-stu-id="bb901-127">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="bb901-128">このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb901-128">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="bb901-129">ただし、これは**しないで**実際のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="bb901-129">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="bb901-130">ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="bb901-130">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="bb901-131">常に、ストレージ アカウント キーを保護するように注意します。</span><span class="sxs-lookup"><span data-stu-id="bb901-131">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="bb901-132">ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。</span><span class="sxs-lookup"><span data-stu-id="bb901-132">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="bb901-133">侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。</span><span class="sxs-lookup"><span data-stu-id="bb901-133">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="bb901-134">実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。</span><span class="sxs-lookup"><span data-stu-id="bb901-134">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="bb901-135">構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bb901-135">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="bb901-136">Azure 構成マネージャーを使用することはオプションです。</span><span class="sxs-lookup"><span data-stu-id="bb901-136">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="bb901-137">.NET Framework のなどの API を使用することも`ConfigurationManager`型です。</span><span class="sxs-lookup"><span data-stu-id="bb901-137">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="bb901-138">接続文字列を解析します。</span><span class="sxs-lookup"><span data-stu-id="bb901-138">Parse the connection string</span></span>

<span data-ttu-id="bb901-139">接続文字列を解析するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb901-139">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="bb901-140">これは、戻り値は、`CloudStorageAccount`です。</span><span class="sxs-lookup"><span data-stu-id="bb901-140">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="bb901-141">Table サービス クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb901-141">Create the Table service client</span></span>

<span data-ttu-id="bb901-142">`CloudTableClient`クラスでは、テーブルおよびテーブル ストレージに格納されているエンティティを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="bb901-142">The `CloudTableClient` class enables you to retrieve tables and entities stored in Table storage.</span></span> <span data-ttu-id="bb901-143">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bb901-143">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="bb901-144">テーブル ストレージへのデータを読み書きするコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="bb901-144">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

## <a name="create-a-table"></a><span data-ttu-id="bb901-145">テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb901-145">Create a table</span></span>

<span data-ttu-id="bb901-146">この例では、存在しない場合、テーブルを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bb901-146">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a><span data-ttu-id="bb901-147">テーブルにエンティティを追加します。</span><span class="sxs-lookup"><span data-stu-id="bb901-147">Add an entity to a table</span></span>

<span data-ttu-id="bb901-148">継承する型を持つエンティティがある`TableEntity`です。</span><span class="sxs-lookup"><span data-stu-id="bb901-148">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="bb901-149">拡張できます`TableEntity`、好きなようには、型で*必要があります*パラメーターなしのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="bb901-149">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="bb901-150">両方があるプロパティのみ`get`と`set`は、Azure テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bb901-150">Only properties that have both `get` and `set` will be stored in your Azure Table.</span></span>

<span data-ttu-id="bb901-151">エンティティのパーティションと行キーは、テーブル内のエンティティを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="bb901-151">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="bb901-152">同じパーティション キーを持つエンティティは、別のパーティション キーを持つものよりも高速に問い合わせることができますが、並列操作のスケーラビリティを高めるため、さまざまなパーティション キーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb901-152">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="bb901-153">例を次に示します、`Customer`を使用して、`lastName`パーティション キーとして、`firstName`行キーとして。</span><span class="sxs-lookup"><span data-stu-id="bb901-153">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="bb901-154">これで、追加、`Customer`テーブルにします。</span><span class="sxs-lookup"><span data-stu-id="bb901-154">Now we'll add our `Customer` to the table.</span></span> <span data-ttu-id="bb901-155">作成するためには、`TableOperation`は、テーブルでを実行します。</span><span class="sxs-lookup"><span data-stu-id="bb901-155">To do so, you create a `TableOperation` that will execute on the table.</span></span> <span data-ttu-id="bb901-156">この場合、作成する、`Insert`操作します。</span><span class="sxs-lookup"><span data-stu-id="bb901-156">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a><span data-ttu-id="bb901-157">エンティティのバッチを挿入します。</span><span class="sxs-lookup"><span data-stu-id="bb901-157">Insert a batch of entities</span></span>

<span data-ttu-id="bb901-158">エンティティのバッチは、1 回の書き込み操作を使用してテーブルに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="bb901-158">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="bb901-159">バッチ操作では、操作を 1 回の実行にまとめることができますが、いくつかの制限。</span><span class="sxs-lookup"><span data-stu-id="bb901-159">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="bb901-160">更新を行うことができます、削除し、同じバッチ操作でを挿入します。</span><span class="sxs-lookup"><span data-stu-id="bb901-160">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="bb901-161">バッチ操作では、最大 100 個のエンティティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bb901-161">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="bb901-162">すべてのエンティティのバッチ処理の同じパーティション キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="bb901-162">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="bb901-163">バッチ操作でクエリを実行することはできますが、バッチ内にのみ操作があります。</span><span class="sxs-lookup"><span data-stu-id="bb901-163">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="bb901-164">バッチ操作に 2 つの insert を結合する一部のコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bb901-164">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="bb901-165">パーティション内のすべてのエンティティを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb901-165">Retrieve all entities in a partition</span></span>

<span data-ttu-id="bb901-166">クエリを実行するすべてのエンティティのパーティション内のテーブルを使用して、`TableQuery`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bb901-166">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="bb901-167">ここでは、フィルター処理するエンティティ「排除」が、パーティション キーが。</span><span class="sxs-lookup"><span data-stu-id="bb901-167">Here, you filter for entities where "Buster" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

<span data-ttu-id="bb901-168">結果を印刷するようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb901-168">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="bb901-169">パーティション内のエンティティの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="bb901-169">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="bb901-170">パーティション内のすべてのエンティティのクエリを実行しない場合は、行キー フィルターのパーティション キーのフィルタを組み合わせることによって、範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb901-170">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="bb901-171">ここでは、使用する 2 つのフィルター「排除」パーティション内のすべてのエンティティを取得するのに、行キー (名) から始まり、文字、アルファベットでは、"M"より前です。</span><span class="sxs-lookup"><span data-stu-id="bb901-171">Here, you use two filters to get all entities in the "Buster" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="bb901-172">結果を印刷するようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb901-172">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a><span data-ttu-id="bb901-173">1 つのエンティティを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb901-173">Retrieve a single entity</span></span>

<span data-ttu-id="bb901-174">特定の 1 つのエンティティを取得するクエリを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="bb901-174">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="bb901-175">ここを使用する、`TableOperation`顧客「Larry 排除」を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb901-175">Here, you use a `TableOperation` to specify the customer "Larry Buster".</span></span> <span data-ttu-id="bb901-176">コレクションは、代わりに戻る、`Customer`です。</span><span class="sxs-lookup"><span data-stu-id="bb901-176">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="bb901-177">テーブル サービスから 1 つのエンティティを取得する最も簡単な方法は、クエリで、パーティション キーと行キーの両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb901-177">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="bb901-178">結果を印刷するようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb901-178">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a><span data-ttu-id="bb901-179">エンティティを置き換えます</span><span class="sxs-lookup"><span data-stu-id="bb901-179">Replace an entity</span></span>

<span data-ttu-id="bb901-180">エンティティを更新するにテーブル サービスから取得、エンティティ オブジェクトを変更し、サービスを使用してテーブルに変更を保存、`Replace`操作します。</span><span class="sxs-lookup"><span data-stu-id="bb901-180">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="bb901-181">これにより、それが取得されてから、操作が失敗する場合、サーバー上のエンティティが変更された場合を除き、サーバーで、完全に置き換えられるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="bb901-181">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation will fail.</span></span> <span data-ttu-id="bb901-182">この失敗は、アプリケーション、その他のソースからの変更を誤って上書きしないようにします。</span><span class="sxs-lookup"><span data-stu-id="bb901-182">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a><span data-ttu-id="bb901-183">エンティティ挿入または置換</span><span class="sxs-lookup"><span data-stu-id="bb901-183">Insert-or-replace an entity</span></span>

<span data-ttu-id="bb901-184">場合によっては、エンティティが存在するかどうか、テーブル内かがわからない。</span><span class="sxs-lookup"><span data-stu-id="bb901-184">Sometimes, you don't know if the entity exists in the table or not.</span></span> <span data-ttu-id="bb901-185">それに格納されている現在の値が不要になった場合は、します。</span><span class="sxs-lookup"><span data-stu-id="bb901-185">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="bb901-186">使用することができます`InsertOrReplace`に、エンティティを作成するか、その状態に関係なく、存在する場合に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bb901-186">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="bb901-187">エンティティのプロパティのサブセットのクエリ</span><span class="sxs-lookup"><span data-stu-id="bb901-187">Query a subset of entity properties</span></span>

<span data-ttu-id="bb901-188">テーブル クエリでは、それらのすべてではなくエンティティからプロパティをいくつかを取得できます。</span><span class="sxs-lookup"><span data-stu-id="bb901-188">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="bb901-189">投影法と呼ばれる、この手法は、特に大規模なエンティティの場合、クエリのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="bb901-189">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="bb901-190">ここでは、のみ用の電子メール アドレスを使用して返す`DynamicTableEntity`と`EntityResolver`です。</span><span class="sxs-lookup"><span data-stu-id="bb901-190">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="bb901-191">このコードは、テーブル サービスでアカウントを使用している場合にのみが実行されるように、プロジェクションがローカル ストレージ エミュレーターでサポートされないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bb901-191">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="bb901-192">ページ内のエンティティを非同期に取得します。</span><span class="sxs-lookup"><span data-stu-id="bb901-192">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="bb901-193">場合は、エンティティの数が多いお読みになっており、それらすべてで返されるを待機しているセグメント化されたクエリを使用するのではなく、取得した、それらを処理する場合します。</span><span class="sxs-lookup"><span data-stu-id="bb901-193">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="bb901-194">ここでは、結果は、非同期ワークフローを使用すると、豊富な結果が返されるを待っているときに実行がブロックされていないにページに返します。</span><span class="sxs-lookup"><span data-stu-id="bb901-194">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

<span data-ttu-id="bb901-195">今すぐ実行するこの計算に同期的に。</span><span class="sxs-lookup"><span data-stu-id="bb901-195">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a><span data-ttu-id="bb901-196">エンティティを削除します。</span><span class="sxs-lookup"><span data-stu-id="bb901-196">Delete an entity</span></span>

<span data-ttu-id="bb901-197">取得した後は、エンティティを削除できます。</span><span class="sxs-lookup"><span data-stu-id="bb901-197">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="bb901-198">同様に、エンティティを更新するには、取得した後、エンティティが変更された場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="bb901-198">As with updating an entity, this will fail if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a><span data-ttu-id="bb901-199">テーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="bb901-199">Delete a table</span></span>

<span data-ttu-id="bb901-200">ストレージ アカウントからテーブルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="bb901-200">You can delete a table from a storage account.</span></span> <span data-ttu-id="bb901-201">削除されたテーブルは削除されるまでの期間の再作成に使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bb901-201">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a><span data-ttu-id="bb901-202">次の手順</span><span class="sxs-lookup"><span data-stu-id="bb901-202">Next steps</span></span>

<span data-ttu-id="bb901-203">これで、テーブル ストレージの基本を学習したより複雑な記憶域タスクについて学習するこれらのリンクに従います。</span><span class="sxs-lookup"><span data-stu-id="bb901-203">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks:</span></span>

- [<span data-ttu-id="bb901-204">.NET 用 azure ストレージ Api</span><span class="sxs-lookup"><span data-stu-id="bb901-204">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="bb901-205">Azure ストレージの型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="bb901-205">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="bb901-206">Azure ストレージ チーム ブログ</span><span class="sxs-lookup"><span data-stu-id="bb901-206">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/b/windowsazurestorage/)
- [<span data-ttu-id="bb901-207">Azure ストレージ接続文字列を構成します。</span><span class="sxs-lookup"><span data-stu-id="bb901-207">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="bb901-208">.NET で Azure テーブル ストレージの概要</span><span class="sxs-lookup"><span data-stu-id="bb901-208">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
