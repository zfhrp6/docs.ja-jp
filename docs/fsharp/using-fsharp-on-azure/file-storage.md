---
title: "F# を使用して Azure File storage の概要します。"
description: "クラウド内の Azure File storage の場合は、ファイル データを格納およびから Azure の仮想マシン (VM) クラウドのファイル共有をマウントまたは内部設置型アプリケーションから Windows を実行します。"
keywords: "visual f#、f#、関数型プログラミングでは、.NET では、.NET Core では、Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5c26a0aa-186e-476c-9f87-e0191754579e
ms.openlocfilehash: 5e1f6914acad5ae8c7148a7238e2d1d6a8ca5867
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="86236-104">F# を使用して Azure File storage の概要します。</span><span class="sxs-lookup"><span data-stu-id="86236-104">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="86236-105">Azure のファイル ストレージが標準を使用して、クラウド内のファイル共有を提供するサービスで[サーバー メッセージ ブロック (SMB) プロトコル](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="86236-105">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="86236-106">SMB 2.1 と SMB 3.0 の両方がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="86236-106">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="86236-107">Azure File storage では、迅速かつ高コストの再作成せずに、Azure へのファイル共有に依存するレガシ アプリケーションを移行できます。</span><span class="sxs-lookup"><span data-stu-id="86236-107">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="86236-108">Azure の仮想マシンまたはクラウド サービスや内部設置型のクライアントを実行しているアプリケーションは、デスクトップ アプリケーションの一般的な SMB 共有のマウントと同様に、クラウド内のファイル共有をマウントできます。</span><span class="sxs-lookup"><span data-stu-id="86236-108">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="86236-109">アプリケーション コンポーネントの任意の数をマウントし、同時にファイル記憶域共有にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="86236-109">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="86236-110">ファイル ストレージの概念的概要についてを参照してください[ファイル記憶域として .NET ガイド](/azure/storage/storage-dotnet-how-to-use-files)です。</span><span class="sxs-lookup"><span data-stu-id="86236-110">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="86236-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="86236-111">Prerequisites</span></span>

<span data-ttu-id="86236-112">このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。</span><span class="sxs-lookup"><span data-stu-id="86236-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="86236-113">ストレージ アクセス キーは、このアカウントにも必要です。</span><span class="sxs-lookup"><span data-stu-id="86236-113">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="86236-114">作成、f# スクリプトと開始 f# 対話型</span><span class="sxs-lookup"><span data-stu-id="86236-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="86236-115">この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="86236-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="86236-116">F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`files.fsx`、f# 開発環境でします。</span><span class="sxs-lookup"><span data-stu-id="86236-116">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="86236-117">次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="86236-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="86236-118">名前空間の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="86236-118">Add namespace declarations</span></span>

<span data-ttu-id="86236-119">次の追加`open`ステートメントの先頭に、`files.fsx`ファイル。</span><span class="sxs-lookup"><span data-stu-id="86236-119">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="86236-120">接続文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="86236-120">Get your connection string</span></span>

<span data-ttu-id="86236-121">このチュートリアルでは、Azure ストレージ接続文字列を必要があります。</span><span class="sxs-lookup"><span data-stu-id="86236-121">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="86236-122">接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。</span><span class="sxs-lookup"><span data-stu-id="86236-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="86236-123">このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="86236-123">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="86236-124">ただし、これは**しないで**実際のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="86236-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="86236-125">ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。</span><span class="sxs-lookup"><span data-stu-id="86236-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="86236-126">常に、ストレージ アカウント キーを保護するように注意します。</span><span class="sxs-lookup"><span data-stu-id="86236-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="86236-127">ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。</span><span class="sxs-lookup"><span data-stu-id="86236-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="86236-128">侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。</span><span class="sxs-lookup"><span data-stu-id="86236-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="86236-129">実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。</span><span class="sxs-lookup"><span data-stu-id="86236-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="86236-130">構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="86236-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="86236-131">Azure 構成マネージャーを使用することはオプションです。</span><span class="sxs-lookup"><span data-stu-id="86236-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="86236-132">.NET Framework のなどの API を使用することも`ConfigurationManager`型です。</span><span class="sxs-lookup"><span data-stu-id="86236-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="86236-133">接続文字列を解析します。</span><span class="sxs-lookup"><span data-stu-id="86236-133">Parse the connection string</span></span>

<span data-ttu-id="86236-134">接続文字列を解析するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="86236-134">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="86236-135">これは、戻り値は、`CloudStorageAccount`です。</span><span class="sxs-lookup"><span data-stu-id="86236-135">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="86236-136">ファイル サービス クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="86236-136">Create the File service client</span></span>

<span data-ttu-id="86236-137">`CloudFileClient`型では、ファイル ストレージに格納されているファイルをプログラムで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="86236-137">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="86236-138">サービス クライアントを作成する方法の 1 つを次に示します。</span><span class="sxs-lookup"><span data-stu-id="86236-138">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="86236-139">ファイル記憶域にデータを読み書きするコードを記述する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="86236-139">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="86236-140">ファイル共有を作成します。</span><span class="sxs-lookup"><span data-stu-id="86236-140">Create a file share</span></span>

<span data-ttu-id="86236-141">この例が既に存在しない場合は、ファイル共有を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="86236-141">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="86236-142">ルート ディレクトリとサブディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="86236-142">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="86236-143">ここでは、ルート ディレクトリを取得し、ディレクトリ、ルートのサブディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="86236-143">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="86236-144">まだ存在しない場合は、両方ともタイプを作成します。</span><span class="sxs-lookup"><span data-stu-id="86236-144">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="86236-145">テキストをファイルとしてアップロードします。</span><span class="sxs-lookup"><span data-stu-id="86236-145">Upload text as a file</span></span>

<span data-ttu-id="86236-146">この例では、テキストとしてファイルをアップロードする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="86236-146">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="86236-147">ファイルをダウンロードするファイルのローカル コピーする</span><span class="sxs-lookup"><span data-stu-id="86236-147">Download a file to a local copy of the file</span></span>

<span data-ttu-id="86236-148">先ほど作成したファイルをダウンロードするここで、ローカル ファイルに内容を追加します。</span><span class="sxs-lookup"><span data-stu-id="86236-148">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="86236-149">ファイル共有の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="86236-149">Set the maximum size for a file share</span></span>

<span data-ttu-id="86236-150">次の例では、共有の現在の使用状況を確認する方法と、共有のクォータを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="86236-150">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="86236-151">`FetchAttributes` 共有の設定を呼び出す必要があります`Properties`、および`SetProperties`Azure File storage にローカルの変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="86236-151">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="86236-152">ファイルまたはファイル共有の共有アクセス署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="86236-152">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="86236-153">ファイル共有または個々 のファイルの共有アクセス署名 (SAS) を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="86236-153">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="86236-154">共有アクセス署名を管理するファイル共有上の共有アクセス ポリシーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="86236-154">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="86236-155">共有アクセス ポリシーを作成する、推奨されてを侵害する必要がある場合に、SAS を取り消す手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="86236-155">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="86236-156">共有を作成するここでは、共有上のポリシーにアクセスし、そのポリシーを使用して、共有のファイルの SAS の制約を指定します。</span><span class="sxs-lookup"><span data-stu-id="86236-156">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="86236-157">詳細については、作成して、共有アクセス署名を使用して、次を参照してください。[を使用して共有アクセス署名 (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1)と[作成して使用して Blob ストレージの SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2)です。</span><span class="sxs-lookup"><span data-stu-id="86236-157">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="86236-158">ファイルのコピー</span><span class="sxs-lookup"><span data-stu-id="86236-158">Copy files</span></span>

<span data-ttu-id="86236-159">ファイルを別のファイルまたは blob または blob にファイルをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="86236-159">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="86236-160">ファイル、または、blob にファイルを blob をコピーしている場合、*必要があります*同じストレージ アカウント内にコピーする場合でも、ソース オブジェクトの認証に shared access signature (SAS) を使用します。</span><span class="sxs-lookup"><span data-stu-id="86236-160">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="86236-161">別のファイルにファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="86236-161">Copy a file to another file</span></span>

<span data-ttu-id="86236-162">ここでは、同じ共有内の別のファイルにファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="86236-162">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="86236-163">このコピー操作は、同じストレージ アカウント内のファイル間でコピーするので、コピーを実行するのに共有キー認証を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="86236-163">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="86236-164">ファイルを blob にコピーします。</span><span class="sxs-lookup"><span data-stu-id="86236-164">Copy a file to a blob</span></span>

<span data-ttu-id="86236-165">ここで、ファイルを作成し、同じストレージ アカウント内の blob にコピーします。</span><span class="sxs-lookup"><span data-stu-id="86236-165">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="86236-166">コピー操作中にソース ファイルへのアクセスを認証するサービスを使用するソース ファイルの SAS を作成します。</span><span class="sxs-lookup"><span data-stu-id="86236-166">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="86236-167">同じ方法でファイルに blob をコピーできます。</span><span class="sxs-lookup"><span data-stu-id="86236-167">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="86236-168">ソース オブジェクトが blob の場合は、コピー操作中にその blob へのアクセスの認証に SAS を作成します。</span><span class="sxs-lookup"><span data-stu-id="86236-168">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="86236-169">メトリックを使用してファイルの記憶域のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="86236-169">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="86236-170">Azure Storage Analytics は、ファイル ストレージのメトリックをサポートします。</span><span class="sxs-lookup"><span data-stu-id="86236-170">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="86236-171">メトリック データと要求のトレースし、問題を診断できます。</span><span class="sxs-lookup"><span data-stu-id="86236-171">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="86236-172">ファイル ストレージのメトリックを有効にすることができます、 [Azure Portal](https://portal.azure.com)、または次のように F# から行うことができます。</span><span class="sxs-lookup"><span data-stu-id="86236-172">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="86236-173">次の手順</span><span class="sxs-lookup"><span data-stu-id="86236-173">Next steps</span></span>

<span data-ttu-id="86236-174">Azure File storage の詳細については、これらのリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86236-174">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="86236-175">概念に関する記事やビデオ</span><span class="sxs-lookup"><span data-stu-id="86236-175">Conceptual articles and videos</span></span>

- [<span data-ttu-id="86236-176">Windows と Linux の azure のファイル ストレージ: 摩擦のないクラウド SMB のファイル システム</span><span class="sxs-lookup"><span data-stu-id="86236-176">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="86236-177">Linux で Azure File Storage を使用する方法</span><span class="sxs-lookup"><span data-stu-id="86236-177">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="86236-178">ツールのファイル記憶域のサポート</span><span class="sxs-lookup"><span data-stu-id="86236-178">Tooling support for File storage</span></span>

- [<span data-ttu-id="86236-179">Azure ストレージで Azure PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="86236-179">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="86236-180">Microsoft Azure Storage で AzCopy を使用する方法</span><span class="sxs-lookup"><span data-stu-id="86236-180">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="86236-181">Azure ストレージと Azure CLI を使用します。</span><span class="sxs-lookup"><span data-stu-id="86236-181">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="86236-182">参照</span><span class="sxs-lookup"><span data-stu-id="86236-182">Reference</span></span>

- [<span data-ttu-id="86236-183">参照を .NET 用 storage クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="86236-183">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="86236-184">ファイル サービス REST API リファレンス</span><span class="sxs-lookup"><span data-stu-id="86236-184">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="86236-185">ブログの投稿</span><span class="sxs-lookup"><span data-stu-id="86236-185">Blog posts</span></span>

- [<span data-ttu-id="86236-186">Azure のファイル ストレージが一般的に使用できるようになりました</span><span class="sxs-lookup"><span data-stu-id="86236-186">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="86236-187">Azure 内のファイル ストレージ</span><span class="sxs-lookup"><span data-stu-id="86236-187">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="86236-188">Microsoft Azure ファイル サービスの概要</span><span class="sxs-lookup"><span data-stu-id="86236-188">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="86236-189">Microsoft Azure ファイルへの接続を保持します。</span><span class="sxs-lookup"><span data-stu-id="86236-189">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
