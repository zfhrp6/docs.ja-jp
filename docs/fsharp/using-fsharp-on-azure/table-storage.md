---
title: F# を使用して Azure テーブル ストレージの概要します。
description: Azure テーブル ストレージまたは Azure Cosmos DB を使用して、クラウドに構造化データを格納します。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: ac81bc88db1436aa4d5f576da61a90839df04b99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575402"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="d80be-103">Azure テーブル ストレージと f# を使用して Azure Cosmos DB テーブル API の概要します。</span><span class="sxs-lookup"><span data-stu-id="d80be-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="d80be-104">Azure テーブル ストレージは、クラウドで構造化された NoSQL データを格納するサービスです。</span><span class="sxs-lookup"><span data-stu-id="d80be-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="d80be-105">テーブル ストレージは、schemaless 設計により、キー/属性ストアです。</span><span class="sxs-lookup"><span data-stu-id="d80be-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="d80be-106">テーブル ストレージは schemaless であるためには、アプリケーションするの必要に応じて、データを適応させる簡単です。</span><span class="sxs-lookup"><span data-stu-id="d80be-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="d80be-107">データへのアクセスは、高速でコスト効果の高いアプリケーションのすべての種類です。</span><span class="sxs-lookup"><span data-stu-id="d80be-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="d80be-108">テーブル ストレージでは、コストと比べて著しく低く従来の SQL のようなデータのボリュームを通常します。</span><span class="sxs-lookup"><span data-stu-id="d80be-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="d80be-109">テーブル ストレージを使用して、web アプリケーション、アドレス帳、デバイス情報、およびサービスを必要とするメタデータの他の種類のユーザー データなどの柔軟なデータセットを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="d80be-110">テーブルのエンティティの任意の数を格納することができ、ストレージ アカウントは、ストレージ アカウントの容量の上限に達するまで、テーブルの任意の数を含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="d80be-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="d80be-111">Cosmos の azure DB には、Azure テーブル ストレージに書き込まれ、premium 機能をなどが必要なアプリケーション用のテーブルの API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d80be-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="d80be-112">すぐに使用できるグローバル配布します。</span><span class="sxs-lookup"><span data-stu-id="d80be-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="d80be-113">世界中の専用スループット。</span><span class="sxs-lookup"><span data-stu-id="d80be-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="d80be-114">99 パーセンタイル値に 1 桁のミリ秒遅延します。</span><span class="sxs-lookup"><span data-stu-id="d80be-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="d80be-115">高可用性を保証します。</span><span class="sxs-lookup"><span data-stu-id="d80be-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="d80be-116">自動セカンダリ インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d80be-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="d80be-117">Azure テーブル ストレージ用に記述されたアプリケーションでは、コード変更せずにテーブルの API を使用して、Azure Cosmos DB に移行でき、premium 機能を活用することができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="d80be-118">テーブルの API では、.NET、Java、Python、および Node.js の使用可能なクライアント Sdk があります。</span><span class="sxs-lookup"><span data-stu-id="d80be-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="d80be-119">詳細については、次を参照してください。 [Azure Cosmos DB テーブル API の概要](https://docs.microsoft.com/azure/cosmos-db/table-introduction)です。</span><span class="sxs-lookup"><span data-stu-id="d80be-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="d80be-120">このチュートリアルについて</span><span class="sxs-lookup"><span data-stu-id="d80be-120">About this tutorial</span></span>

<span data-ttu-id="d80be-121">このチュートリアルでは、Azure テーブル ストレージまたは Azure Cosmos DB テーブル API などを作成してテーブルの削除し挿入、更新、削除、およびテーブル データのクエリを使用して一般的なタスクを実行する f# コードを記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d80be-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d80be-122">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d80be-122">Prerequisites</span></span>

<span data-ttu-id="d80be-123">このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)または[Azure Cosmos DB アカウント](https://azure.microsoft.com/try/cosmosdb/)です。</span><span class="sxs-lookup"><span data-stu-id="d80be-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="d80be-124">作成、f# スクリプトと開始 f# 対話型</span><span class="sxs-lookup"><span data-stu-id="d80be-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="d80be-125">この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d80be-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="d80be-126">F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`tables.fsx`、f# 開発環境でします。</span><span class="sxs-lookup"><span data-stu-id="d80be-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="d80be-127">次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="d80be-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="d80be-128">用にもう一度行う`Microsoft.WindowsAzure.ConfigurationManager`Microsoft.Azure 名前空間を取得するためにします。</span><span class="sxs-lookup"><span data-stu-id="d80be-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="d80be-129">名前空間の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="d80be-129">Add namespace declarations</span></span>

<span data-ttu-id="d80be-130">次の追加`open`ステートメントの先頭に、`tables.fsx`ファイル。</span><span class="sxs-lookup"><span data-stu-id="d80be-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="d80be-131">Azure ストレージ接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="d80be-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="d80be-132">Azure ストレージ テーブル サービスに接続する場合は、このチュートリアルでは、接続文字列を必要があります。</span><span class="sxs-lookup"><span data-stu-id="d80be-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="d80be-133">Azure ポータルから、接続文字列をコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="d80be-134">接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。</span><span class="sxs-lookup"><span data-stu-id="d80be-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="d80be-135">Azure Cosmos DB 接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="d80be-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="d80be-136">Azure Cosmos DB に接続する場合は、このチュートリアルでは、接続文字列を必要があります。</span><span class="sxs-lookup"><span data-stu-id="d80be-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="d80be-137">Azure ポータルから、接続文字列をコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="d80be-138">Cosmos DB アカウントに、Azure ポータルに移動**設定** > **接続文字列**、 をクリックし、**コピー**のプライマリ接続をコピーする ボタン文字列。</span><span class="sxs-lookup"><span data-stu-id="d80be-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="d80be-139">このチュートリアルでは、スクリプトでは、次の例のように、接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="d80be-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="d80be-140">ただし、これは**しないで**実際のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="d80be-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="d80be-141">ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="d80be-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="d80be-142">常に、ストレージ アカウント キーを保護するように注意します。</span><span class="sxs-lookup"><span data-stu-id="d80be-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="d80be-143">ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。</span><span class="sxs-lookup"><span data-stu-id="d80be-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="d80be-144">侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="d80be-145">実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。</span><span class="sxs-lookup"><span data-stu-id="d80be-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="d80be-146">構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="d80be-147">Azure 構成マネージャーを使用することはオプションです。</span><span class="sxs-lookup"><span data-stu-id="d80be-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="d80be-148">.NET Framework のなどの API を使用することも`ConfigurationManager`型です。</span><span class="sxs-lookup"><span data-stu-id="d80be-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="d80be-149">接続文字列を解析します。</span><span class="sxs-lookup"><span data-stu-id="d80be-149">Parse the connection string</span></span>

<span data-ttu-id="d80be-150">接続文字列を解析するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d80be-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="d80be-151">これを返します、`CloudStorageAccount`です。</span><span class="sxs-lookup"><span data-stu-id="d80be-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="d80be-152">Table サービス クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="d80be-152">Create the Table service client</span></span>

<span data-ttu-id="d80be-153">`CloudTableClient`クラスでは、テーブルとテーブル ストレージ内のエンティティを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="d80be-154">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d80be-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="d80be-155">テーブル ストレージへのデータを読み書きするコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="d80be-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="d80be-156">テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="d80be-156">Create a table</span></span>

<span data-ttu-id="d80be-157">この例では、存在しない場合、テーブルを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d80be-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="d80be-158">テーブルにエンティティを追加します。</span><span class="sxs-lookup"><span data-stu-id="d80be-158">Add an entity to a table</span></span>

<span data-ttu-id="d80be-159">継承する型を持つエンティティがある`TableEntity`です。</span><span class="sxs-lookup"><span data-stu-id="d80be-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="d80be-160">拡張できます`TableEntity`、好きなようには、型で*必要があります*パラメーターなしのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="d80be-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="d80be-161">両方があるプロパティのみ`get`と`set`は、Azure テーブルに格納します。</span><span class="sxs-lookup"><span data-stu-id="d80be-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="d80be-162">エンティティのパーティションと行キーは、テーブル内のエンティティを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="d80be-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="d80be-163">同じパーティション キーを持つエンティティは、別のパーティション キーを持つものよりも高速に問い合わせることができますが、並列操作のスケーラビリティを高めるため、さまざまなパーティション キーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d80be-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="d80be-164">例を次に示します、`Customer`を使用して、`lastName`パーティション キーとして、`firstName`行キーとして。</span><span class="sxs-lookup"><span data-stu-id="d80be-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="d80be-165">ここで追加`Customer`テーブルにします。</span><span class="sxs-lookup"><span data-stu-id="d80be-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="d80be-166">これを行うには、作成、`TableOperation`テーブル上で実行します。</span><span class="sxs-lookup"><span data-stu-id="d80be-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="d80be-167">この場合、作成する、`Insert`操作します。</span><span class="sxs-lookup"><span data-stu-id="d80be-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="d80be-168">エンティティのバッチを挿入します。</span><span class="sxs-lookup"><span data-stu-id="d80be-168">Insert a batch of entities</span></span>

<span data-ttu-id="d80be-169">エンティティのバッチは、1 回の書き込み操作を使用してテーブルに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="d80be-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="d80be-170">バッチ操作では、操作を 1 回の実行にまとめることができますが、いくつかの制限。</span><span class="sxs-lookup"><span data-stu-id="d80be-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="d80be-171">更新を行うことができます、削除し、同じバッチ操作でを挿入します。</span><span class="sxs-lookup"><span data-stu-id="d80be-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="d80be-172">バッチ操作では、最大 100 個のエンティティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="d80be-173">すべてのエンティティのバッチ処理の同じパーティション キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="d80be-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="d80be-174">バッチ操作でクエリを実行することはできますが、バッチ内にのみ操作があります。</span><span class="sxs-lookup"><span data-stu-id="d80be-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="d80be-175">バッチ操作に 2 つの insert を結合する一部のコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d80be-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="d80be-176">パーティション内のすべてのエンティティを取得します。</span><span class="sxs-lookup"><span data-stu-id="d80be-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="d80be-177">クエリを実行するすべてのエンティティのパーティション内のテーブルを使用して、`TableQuery`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d80be-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="d80be-178">ここでは、フィルター処理するエンティティをパーティション分割キーは、"Smith"。</span><span class="sxs-lookup"><span data-stu-id="d80be-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="d80be-179">結果を印刷するようになりました。</span><span class="sxs-lookup"><span data-stu-id="d80be-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="d80be-180">パーティション内のエンティティの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="d80be-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="d80be-181">パーティション内のすべてのエンティティのクエリを実行しない場合は、行キー フィルターのパーティション キーのフィルタを組み合わせることによって、範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d80be-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="d80be-182">ここでは、使用する 2 つのフィルター"Smith"パーティション内のすべてのエンティティを取得するのに、行キー (名) から始まり、文字、アルファベットでは、"M"より前です。</span><span class="sxs-lookup"><span data-stu-id="d80be-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="d80be-183">結果を印刷するようになりました。</span><span class="sxs-lookup"><span data-stu-id="d80be-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="d80be-184">1 つのエンティティを取得します。</span><span class="sxs-lookup"><span data-stu-id="d80be-184">Retrieve a single entity</span></span>

<span data-ttu-id="d80be-185">特定の 1 つのエンティティを取得するクエリを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="d80be-186">ここを使用する、`TableOperation`顧客"Ben Smith"を指定します。</span><span class="sxs-lookup"><span data-stu-id="d80be-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="d80be-187">コレクションは、代わりに戻る、`Customer`です。</span><span class="sxs-lookup"><span data-stu-id="d80be-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="d80be-188">テーブル サービスから 1 つのエンティティを取得する最も簡単な方法は、クエリで、パーティション キーと行キーの両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="d80be-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="d80be-189">結果を印刷するようになりました。</span><span class="sxs-lookup"><span data-stu-id="d80be-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="d80be-190">エンティティを置き換えます</span><span class="sxs-lookup"><span data-stu-id="d80be-190">Replace an entity</span></span>

<span data-ttu-id="d80be-191">エンティティを更新するにテーブル サービスから取得、エンティティ オブジェクトを変更し、サービスを使用してテーブルに変更を保存、`Replace`操作します。</span><span class="sxs-lookup"><span data-stu-id="d80be-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="d80be-192">これにより、それが取得されてから、操作が失敗する場合に、サーバー上のエンティティが変更された場合を除き、サーバーで、完全に置き換えられるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="d80be-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="d80be-193">この失敗は、アプリケーション、その他のソースからの変更を誤って上書きしないようにします。</span><span class="sxs-lookup"><span data-stu-id="d80be-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="d80be-194">エンティティ挿入または置換</span><span class="sxs-lookup"><span data-stu-id="d80be-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="d80be-195">場合によっては、テーブル内のエンティティが存在するかどうかがわからない。</span><span class="sxs-lookup"><span data-stu-id="d80be-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="d80be-196">それに格納されている現在の値が不要になった場合は、します。</span><span class="sxs-lookup"><span data-stu-id="d80be-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="d80be-197">使用することができます`InsertOrReplace`に、エンティティを作成するか、その状態に関係なく、存在する場合に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d80be-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="d80be-198">エンティティのプロパティのサブセットのクエリ</span><span class="sxs-lookup"><span data-stu-id="d80be-198">Query a subset of entity properties</span></span>

<span data-ttu-id="d80be-199">テーブル クエリでは、それらのすべてではなくエンティティからプロパティをいくつかを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d80be-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="d80be-200">投影法と呼ばれる、この手法は、特に大規模なエンティティの場合、クエリのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="d80be-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="d80be-201">ここでは、のみ用の電子メール アドレスを使用して返す`DynamicTableEntity`と`EntityResolver`です。</span><span class="sxs-lookup"><span data-stu-id="d80be-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="d80be-202">このコードは、テーブル サービスでアカウントを使用している場合にのみが実行されるように、プロジェクションがローカル ストレージ エミュレーターでサポートされないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d80be-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="d80be-203">ページ内のエンティティを非同期に取得します。</span><span class="sxs-lookup"><span data-stu-id="d80be-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="d80be-204">場合は、エンティティの数が多いお読みになっており、それらすべてで返されるを待機しているセグメント化されたクエリを使用するのではなく、取得した、それらを処理する場合します。</span><span class="sxs-lookup"><span data-stu-id="d80be-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="d80be-205">ここでは、結果は、非同期ワークフローを使用すると、豊富な結果が返されるを待っているときに実行がブロックされていないにページに返します。</span><span class="sxs-lookup"><span data-stu-id="d80be-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="d80be-206">今すぐ実行するこの計算に同期的に。</span><span class="sxs-lookup"><span data-stu-id="d80be-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="d80be-207">エンティティを削除します。</span><span class="sxs-lookup"><span data-stu-id="d80be-207">Delete an entity</span></span>

<span data-ttu-id="d80be-208">取得した後は、エンティティを削除できます。</span><span class="sxs-lookup"><span data-stu-id="d80be-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="d80be-209">同様に、エンティティを更新するには、取得した後、エンティティが変更された場合は、これが失敗します。</span><span class="sxs-lookup"><span data-stu-id="d80be-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="d80be-210">テーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="d80be-210">Delete a table</span></span>

<span data-ttu-id="d80be-211">ストレージ アカウントからテーブルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="d80be-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="d80be-212">削除されたテーブルは削除されるまでの期間の再作成に使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d80be-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="d80be-213">次の手順</span><span class="sxs-lookup"><span data-stu-id="d80be-213">Next steps</span></span>

<span data-ttu-id="d80be-214">これで、テーブル ストレージの基本を学習したより複雑な記憶域タスクと Azure Cosmos DB テーブル API についてこれらのリンクに従います。</span><span class="sxs-lookup"><span data-stu-id="d80be-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="d80be-215">Azure Cosmos DB テーブル API の概要</span><span class="sxs-lookup"><span data-stu-id="d80be-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="d80be-216">参照を .NET 用 storage クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d80be-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="d80be-217">Azure ストレージの型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d80be-217">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="d80be-218">Azure ストレージ チーム ブログ</span><span class="sxs-lookup"><span data-stu-id="d80be-218">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="d80be-219">接続文字列を構成します。</span><span class="sxs-lookup"><span data-stu-id="d80be-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="d80be-220">.NET で Azure テーブル ストレージの概要</span><span class="sxs-lookup"><span data-stu-id="d80be-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
