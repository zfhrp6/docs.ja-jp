---
title: "F# を使用して Azure Blob ストレージの概要します。"
description: "Azure Blob ストレージとクラウドには、非構造化データを格納します。"
keywords: "visual f#、f#、関数型プログラミングでは、.NET では、.NET Core では、Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 9011bdceabd1b5e0541ecb94f3e812871688025b
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="a5263-104">F# を使用して Azure Blob ストレージの概要します。</span><span class="sxs-lookup"><span data-stu-id="a5263-104">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="a5263-105">Azure BLOB Storage は、非構造化データをオブジェクト/BLOB としてクラウドに格納するサービスです。</span><span class="sxs-lookup"><span data-stu-id="a5263-105">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="a5263-106">Blob Storage は、ドキュメント、メディア ファイル、アプリケーション インストーラーなど、任意の種類のテキストまたはバイナリ データを格納できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-106">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="a5263-107">Blob Storage は、オブジェクト ストレージとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a5263-107">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="a5263-108">この記事では、Blob ストレージを使用した共通タスクを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a5263-108">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="a5263-109">サンプルは、.NET 用 Azure ストレージ クライアント ライブラリを使用して f# を使用して書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a5263-109">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="a5263-110">対象タスクには、アップロード、一覧表示、ダウンロード、および blob を削除する方法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a5263-110">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="a5263-111">Blob ストレージの概念的概要については、次を参照してください。 [blob ストレージは、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-blobs)です。</span><span class="sxs-lookup"><span data-stu-id="a5263-111">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5263-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a5263-112">Prerequisites</span></span>

<span data-ttu-id="a5263-113">このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。</span><span class="sxs-lookup"><span data-stu-id="a5263-113">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="a5263-114">このアカウントのストレージ アクセス キーも必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5263-114">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="a5263-115">作成、f# スクリプトと開始 f# 対話型</span><span class="sxs-lookup"><span data-stu-id="a5263-115">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="a5263-116">この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-116">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="a5263-117">F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`blobs.fsx`、f# 開発環境でします。</span><span class="sxs-lookup"><span data-stu-id="a5263-117">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="a5263-118">次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`と`Microsoft.WindowsAzure.ConfigurationManager`パッケージと参照`WindowsAzure.Storage.dll`と`Microsoft.WindowsAzure.Configuration.dll` 、スクリプトを使用して、`#r`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="a5263-118">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="a5263-119">名前空間の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="a5263-119">Add namespace declarations</span></span>

<span data-ttu-id="a5263-120">次の追加`open`ステートメントの先頭に、`blobs.fsx`ファイル。</span><span class="sxs-lookup"><span data-stu-id="a5263-120">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="a5263-121">接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5263-121">Get your connection string</span></span>

<span data-ttu-id="a5263-122">このチュートリアルでは、Azure ストレージ接続文字列を必要とします。</span><span class="sxs-lookup"><span data-stu-id="a5263-122">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="a5263-123">接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。</span><span class="sxs-lookup"><span data-stu-id="a5263-123">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="a5263-124">このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="a5263-124">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="a5263-125">ただし、これは**しないで**実際のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a5263-125">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="a5263-126">ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="a5263-126">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="a5263-127">常に、ストレージ アカウント キーを保護するように注意します。</span><span class="sxs-lookup"><span data-stu-id="a5263-127">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="a5263-128">ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。</span><span class="sxs-lookup"><span data-stu-id="a5263-128">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="a5263-129">侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。</span><span class="sxs-lookup"><span data-stu-id="a5263-129">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="a5263-130">実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。</span><span class="sxs-lookup"><span data-stu-id="a5263-130">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="a5263-131">構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a5263-131">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="a5263-132">Azure 構成マネージャーを使用することはオプションです。</span><span class="sxs-lookup"><span data-stu-id="a5263-132">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="a5263-133">.NET Framework のなどの API を使用することも`ConfigurationManager`型です。</span><span class="sxs-lookup"><span data-stu-id="a5263-133">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="a5263-134">接続文字列を解析します。</span><span class="sxs-lookup"><span data-stu-id="a5263-134">Parse the connection string</span></span>

<span data-ttu-id="a5263-135">接続文字列を解析するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a5263-135">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="a5263-136">これを返します、`CloudStorageAccount`です。</span><span class="sxs-lookup"><span data-stu-id="a5263-136">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="a5263-137">ローカル ダミー データの一部を作成します。</span><span class="sxs-lookup"><span data-stu-id="a5263-137">Create some local dummy data</span></span>

<span data-ttu-id="a5263-138">開始する前に、スクリプトのディレクトリにダミーのローカル データの一部を作成します。</span><span class="sxs-lookup"><span data-stu-id="a5263-138">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="a5263-139">後でこのデータをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="a5263-139">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="a5263-140">Blob サービス クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="a5263-140">Create the Blob service client</span></span>

<span data-ttu-id="a5263-141">`CloudBlobClient`型では、コンテナーと Blob ストレージに格納された blob を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="a5263-141">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="a5263-142">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a5263-142">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="a5263-143">Blob ストレージからデータを読み書きするコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="a5263-143">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="a5263-144">コンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a5263-144">Create a container</span></span>

<span data-ttu-id="a5263-145">この例が既に存在しない場合は、コンテナーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a5263-145">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="a5263-146">既定では、新しいコンテナーがプライベート、つまり、このコンテナーから blob をダウンロードするストレージ アクセス キーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5263-146">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="a5263-147">すべてのユーザーに、コンテナー内のファイルを使用できるようにする場合は、次のコードを使用して公開するコンテナーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-147">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="a5263-148">インターネット上のだれも、パブリック コンテナー内の blob を参照してくださいが、変更したり、適切なアカウント アクセス キーまたは共有アクセス署名がある場合にのみ、それらを削除します。</span><span class="sxs-lookup"><span data-stu-id="a5263-148">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="a5263-149">Blob コンテナーをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="a5263-149">Upload a blob into a container</span></span>

<span data-ttu-id="a5263-150">Azure Blob ストレージには、ブロック blob とページ blob がサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a5263-150">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="a5263-151">ほとんどの場合、ブロック blob は、推奨される型を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5263-151">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="a5263-152">ブロック blob にファイルをアップロードするには、コンテナーの参照を取得し、ブロック blob 参照を取得するを使用します。</span><span class="sxs-lookup"><span data-stu-id="a5263-152">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="a5263-153">Blob の参照を作成したらにアップロードできる任意のデータのストリームに呼び出すことによって、`UploadFromFile`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a5263-153">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="a5263-154">この操作は、しなかった以前存在、または存在する場合は上書きしますか場合、blob を作成します。</span><span class="sxs-lookup"><span data-stu-id="a5263-154">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="a5263-155">コンテナー内の blob を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a5263-155">List the blobs in a container</span></span>

<span data-ttu-id="a5263-156">コンテナー内の blob を一覧表示するには、コンテナー参照をまず取得します。</span><span class="sxs-lookup"><span data-stu-id="a5263-156">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="a5263-157">コンテナーを使用することができますし、 `ListBlobs` blob やその中のディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="a5263-157">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="a5263-158">豊富なプロパティと、返されるためのメソッドにアクセスする`IListBlobItem`にキャストする必要があります、 `CloudBlockBlob`、 `CloudPageBlob`、または`CloudBlobDirectory`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a5263-158">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="a5263-159">型が不明な場合は、キャストを決定するため、型チェックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-159">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="a5263-160">次のコードを取得し、内の各項目の URI を出力する方法を示しています、`mydata`コンテナー。</span><span class="sxs-lookup"><span data-stu-id="a5263-160">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="a5263-161">名前の blob パスについては、名前にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a5263-161">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="a5263-162">これにより、整理したり、従来のファイル システムと同様に走査できる仮想ディレクトリ構造が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a5263-162">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="a5263-163">ディレクトリ構造は、仮想のみ - Blob ストレージで使用できる唯一のリソースがコンテナーと blob ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a5263-163">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="a5263-164">ただし、ストレージ クライアント ライブラリが用意されています、`CloudBlobDirectory`仮想ディレクトリを参照し、この方法で構成されている blob を操作するプロセスを簡略化するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a5263-164">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="a5263-165">たとえば、次の一連のという名前のコンテナーにブロック blob `photos`:</span><span class="sxs-lookup"><span data-stu-id="a5263-165">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="a5263-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="a5263-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="a5263-167">呼び出すと`ListBlobs`(上記のサンプル) のように、コンテナー階層の一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="a5263-167">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="a5263-168">両方が含まれている場合`CloudBlobDirectory`と`CloudBlockBlob`結果の出力は次のように検索し、ディレクトリと、コンテナー内の blob をそれぞれ表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a5263-168">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="a5263-169">必要に応じて、設定することができます、`UseFlatBlobListing`のパラメーター、`ListBlobs`メソッドを`true`です。</span><span class="sxs-lookup"><span data-stu-id="a5263-169">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="a5263-170">この場合、コンテナー内のすべての blob として返されます、`CloudBlockBlob`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a5263-170">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="a5263-171">呼び出し`ListBlobs`を次のようなフラット リストを返します。</span><span class="sxs-lookup"><span data-stu-id="a5263-171">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="a5263-172">また、結果は次のように、表示、コンテナーの現在の内容に応じて。</span><span class="sxs-lookup"><span data-stu-id="a5263-172">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="a5263-173">Blob をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="a5263-173">Download blobs</span></span>

<span data-ttu-id="a5263-174">Blob をダウンロードするには、最初に blob の参照を取得およびを呼び出す、`DownloadToStream`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a5263-174">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="a5263-175">次の例では、 `DownloadToStream` blob の内容をローカル ファイルに永続化することができますし、ストリーム オブジェクトに転送する方法です。</span><span class="sxs-lookup"><span data-stu-id="a5263-175">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="a5263-176">使用することも、`DownloadToStream`メソッドを文字列として blob のコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="a5263-176">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="a5263-177">Blob を削除します。</span><span class="sxs-lookup"><span data-stu-id="a5263-177">Delete blobs</span></span>

<span data-ttu-id="a5263-178">Blob を削除するには、まず blob 参照を取得しを呼び出す、`Delete`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a5263-178">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="a5263-179">非同期的にページ内の blob を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a5263-179">List blobs in pages asynchronously</span></span>

<span data-ttu-id="a5263-180">Blob の数が多い一覧を作成する、または 1 つの一覧作成操作で返す結果の数を制御する場合、結果のページ内の blob を一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-180">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="a5263-181">この例は、大量の結果セットを返すを待機中に実行がブロックされていないようにに非同期的に、ページに結果を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a5263-181">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="a5263-182">この例は、この一覧を表示するには、フラットな blob を示していますが、設定して、階層的な一覧についてを実行することも、`useFlatBlobListing`のパラメーター、`ListBlobsSegmentedAsync`メソッドを`false`です。</span><span class="sxs-lookup"><span data-stu-id="a5263-182">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="a5263-183">サンプルは、非同期メソッドを定義を使用して、`async`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="a5263-183">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="a5263-184">``let!``キーワードは、一覧のタスクが完了するまでに、サンプル メソッドの実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="a5263-184">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="a5263-185">次のようにこの非同期ルーチンここで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-185">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="a5263-186">最初に、ダミー データ (このチュートリアルで以前に作成されたローカル ファイルを使用) をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="a5263-186">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="a5263-187">ここで、ルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a5263-187">Now, call the routine.</span></span> <span data-ttu-id="a5263-188">使用する``Async.RunSynchronously``非同期操作の実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="a5263-188">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="a5263-189">追加 blob への書き込み</span><span class="sxs-lookup"><span data-stu-id="a5263-189">Writing to an append blob</span></span>

<span data-ttu-id="a5263-190">追加 blob には、ログ記録などの追加操作は適しています。</span><span class="sxs-lookup"><span data-stu-id="a5263-190">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="a5263-191">ブロック blob と同様に、追加 blob は、ブロックで構成が blob の末尾に追加されます常に、追加 blob に新しいブロックを追加するとき。</span><span class="sxs-lookup"><span data-stu-id="a5263-191">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="a5263-192">更新するか、追加 blob に既存のブロックを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="a5263-192">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="a5263-193">ブロック blob には、追加 blob のブロック Id は公開されません。</span><span class="sxs-lookup"><span data-stu-id="a5263-193">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="a5263-194">追加 blob 内の各ブロックは、最大 4 MB は、他のサイズを指定でき、追加 blob は最大 50,000 ブロックを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a5263-194">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="a5263-195">追加 blob の最大サイズよりも少し 195 GB (4 MB X 50,000 ブロック) ではこのためです。</span><span class="sxs-lookup"><span data-stu-id="a5263-195">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="a5263-196">次の例では、追加して、新しい blob を作成し、単純なログ記録操作をシミュレートする、いくつかのデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="a5263-196">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="a5263-197">参照してください[Understanding ブロック Blob、ページ Blob、および追加 Blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) blob の 3 つの種類の違いの詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="a5263-197">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="a5263-198">同時実行のアクセス</span><span class="sxs-lookup"><span data-stu-id="a5263-198">Concurrent access</span></span>

<span data-ttu-id="a5263-199">使用することがサポートするには同時アクセスを blob に複数のクライアントまたは複数のプロセスのインスタンスから**Etag**または**リース**です。</span><span class="sxs-lookup"><span data-stu-id="a5263-199">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="a5263-200">**Etag** -blob またはコンテナーが変更されたことで別のプロセスを検出する方法を提供</span><span class="sxs-lookup"><span data-stu-id="a5263-200">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="a5263-201">**リース**-取得だけで、更新可能な書き込み、または一定の時間の blob へのアクセスを削除する方法を提供</span><span class="sxs-lookup"><span data-stu-id="a5263-201">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="a5263-202">詳細については、次を参照してください。[同時実行制御を管理する Microsoft Azure ストレージに](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)です。</span><span class="sxs-lookup"><span data-stu-id="a5263-202">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="a5263-203">名前付けコンテナー</span><span class="sxs-lookup"><span data-stu-id="a5263-203">Naming containers</span></span>

<span data-ttu-id="a5263-204">Azure ストレージ内のすべての blob は、コンテナー内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5263-204">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="a5263-205">コンテナーは、blob 名の一部を形成します。</span><span class="sxs-lookup"><span data-stu-id="a5263-205">The container forms part of the blob name.</span></span> <span data-ttu-id="a5263-206">たとえば、`mydata`これらのサンプル blob Uri 内のコンテナーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a5263-206">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="a5263-207">コンテナー名には、有効な DNS 名、次の名前付け規則に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5263-207">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="a5263-208">コンテナー名は文字または数字で始める必要があり、文字、数字、およびダッシュ (-) 文字のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a5263-208">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="a5263-209">すべてのダッシュ (-) 文字必要があります直前および後にアルファベットまたは数字です。コンテナー名では、連続するダッシュ文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="a5263-209">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="a5263-210">コンテナー名のすべての文字を小文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5263-210">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="a5263-211">コンテナー名は 3 ~ 63 文字の長さでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a5263-211">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="a5263-212">コンテナーの名前が小文字で常にする必要がありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a5263-212">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="a5263-213">コンテナー名に、大文字を含めるか、それ以外の場合、コンテナーの名前付け規則に違反した場合 400 (Bad Request) エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5263-213">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="a5263-214">Blob のセキュリティを管理します。</span><span class="sxs-lookup"><span data-stu-id="a5263-214">Managing security for blobs</span></span>

<span data-ttu-id="a5263-215">既定では、Azure ストレージ データを維持、セキュリティで保護されたアカウント アクセス キーを所有しているであるアカウント所有者へのアクセスを制限することによってです。</span><span class="sxs-lookup"><span data-stu-id="a5263-215">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="a5263-216">ストレージ アカウント内の blob データを共有する必要がある場合、アカウント アクセス キーのセキュリティを損なうことがなくこれを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5263-216">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="a5263-217">さらに、ネットワーク経由でと Azure ストレージに安全であることを確認する blob データを暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-217">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="a5263-218">Blob データへのアクセスを制御</span><span class="sxs-lookup"><span data-stu-id="a5263-218">Controlling access to blob data</span></span>

<span data-ttu-id="a5263-219">既定では、ストレージ アカウント内の blob データはストレージ アカウント所有者にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a5263-219">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="a5263-220">Blob ストレージに対する要求を認証すると、既定では、アカウント アクセス キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="a5263-220">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="a5263-221">ただし、他のユーザーに特定の blob データを使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="a5263-221">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="a5263-222">Blob ストレージへのアクセスを制御する方法の詳細については、「[アクセス制御の blob ストレージ セクションについては、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data)です。</span><span class="sxs-lookup"><span data-stu-id="a5263-222">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="a5263-223">Blob データの暗号化</span><span class="sxs-lookup"><span data-stu-id="a5263-223">Encrypting blob data</span></span>

<span data-ttu-id="a5263-224">Azure ストレージでは、クライアントとサーバーの両方の blob データの暗号化をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a5263-224">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="a5263-225">Blob データの暗号化の詳細については、「[暗号化を blob ストレージのセクションでは、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data)です。</span><span class="sxs-lookup"><span data-stu-id="a5263-225">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a5263-226">次の手順</span><span class="sxs-lookup"><span data-stu-id="a5263-226">Next steps</span></span>

<span data-ttu-id="a5263-227">これで、Blob ストレージの基本を学習した次の詳細については、これらのリンク。</span><span class="sxs-lookup"><span data-stu-id="a5263-227">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="a5263-228">ツール</span><span class="sxs-lookup"><span data-stu-id="a5263-228">Tools</span></span>
- <span data-ttu-id="a5263-229">[F# AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/)の f# 型プロバイダー Blob、テーブルおよびキューの Azure ストレージの資産を探索し、それらに対する CRUD 操作を簡単に適用するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5263-229">[F# AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="a5263-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)用 Microsoft Azure テーブル ストレージ サービスを使用して、f# API</span><span class="sxs-lookup"><span data-stu-id="a5263-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="a5263-231">[Microsoft Azure ストレージ エクスプ ローラー (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)は free、スタンドアロンのアプリから Microsoft Windows、OS X、Linux で、Azure ストレージのデータを視覚的に処理することができます。</span><span class="sxs-lookup"><span data-stu-id="a5263-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="a5263-232">Blob ストレージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="a5263-232">Blob storage reference</span></span>

- [<span data-ttu-id="a5263-233">.NET 用 azure ストレージ Api</span><span class="sxs-lookup"><span data-stu-id="a5263-233">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="a5263-234">Azure ストレージ サービス REST API リファレンス</span><span class="sxs-lookup"><span data-stu-id="a5263-234">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="a5263-235">関連ガイド</span><span class="sxs-lookup"><span data-stu-id="a5263-235">Related guides</span></span>

- [<span data-ttu-id="a5263-236">C# での Azure Blob ストレージの概要</span><span class="sxs-lookup"><span data-stu-id="a5263-236">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/documentation/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="a5263-237">Windows 上の AzCopy コマンド ライン ユーティリティでのデータを転送します。</span><span class="sxs-lookup"><span data-stu-id="a5263-237">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="a5263-238">Linux 上の AzCopy コマンド ライン ユーティリティでのデータを転送します。</span><span class="sxs-lookup"><span data-stu-id="a5263-238">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="a5263-239">Azure ストレージ接続文字列を構成します。</span><span class="sxs-lookup"><span data-stu-id="a5263-239">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="a5263-240">Azure ストレージ チーム ブログ</span><span class="sxs-lookup"><span data-stu-id="a5263-240">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
