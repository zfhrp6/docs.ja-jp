---
title: dotnet publish コマンド - .NET Core CLI
description: dotnet publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 38224aa8472f99df107e523667e18892384a20b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696661"
---
# <a name="dotnet-publish"></a><span data-ttu-id="76096-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="76096-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="76096-104">name</span><span class="sxs-lookup"><span data-stu-id="76096-104">Name</span></span>

<span data-ttu-id="76096-105">`dotnet publish` - ホスティング システムへの展開のため、アプリケーションとその依存関係をフォルダーにパックします。</span><span class="sxs-lookup"><span data-stu-id="76096-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="76096-106">構文</span><span class="sxs-lookup"><span data-stu-id="76096-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="76096-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="76096-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="76096-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="76096-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="76096-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="76096-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="76096-110">説明</span><span class="sxs-lookup"><span data-stu-id="76096-110">Description</span></span>

<span data-ttu-id="76096-111">`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="76096-112">出力には次のアセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="76096-112">The output includes the following assets:</span></span>

* <span data-ttu-id="76096-113">アセンブリの中間言語 (IL) コード (*dll* 拡張子)。</span><span class="sxs-lookup"><span data-stu-id="76096-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="76096-114">*.deps.json* ファイル。プロジェクトのすべての依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="76096-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="76096-115">*.runtime.config.json* ファイル。アプリケーションが想定する共有ランタイムと、ランタイムの他の構成オプション (ガベージ コレクションの種類など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="76096-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="76096-116">アプリケーションの依存関係。NuGet キャッシュから出力フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="76096-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="76096-117">`dotnet publish` コマンドの出力は、実行のためにホスト システム (サーバー、PC、Mac、ラップトップなど) にすぐに展開できます。</span><span class="sxs-lookup"><span data-stu-id="76096-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="76096-118">これは、アプリケーションの展開を準備するための正式にサポートされている唯一の方法です。</span><span class="sxs-lookup"><span data-stu-id="76096-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="76096-119">プロジェクトに指定されている展開の種類によっては、ホスティング システムに .NET Core 共有ランタイムがインストールされている場合とされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="76096-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="76096-120">詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76096-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="76096-121">発行されるアプリケーションのディレクトリ構造については、「[Directory structure](/aspnet/core/hosting/directory-structure)」 (ディレクトリ構造) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76096-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="76096-122">引数</span><span class="sxs-lookup"><span data-stu-id="76096-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="76096-123">発行するプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="76096-123">The project to publish.</span></span> <span data-ttu-id="76096-124">指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="76096-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="76096-125">オプション</span><span class="sxs-lookup"><span data-stu-id="76096-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="76096-126">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="76096-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="76096-127">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="76096-127">Defines the build configuration.</span></span> <span data-ttu-id="76096-128">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="76096-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="76096-129">指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="76096-130">ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76096-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="76096-131">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="76096-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="76096-132">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="76096-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="76096-133">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="76096-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="76096-134">アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。</span><span class="sxs-lookup"><span data-stu-id="76096-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="76096-135">マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="76096-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="76096-136">複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。</span><span class="sxs-lookup"><span data-stu-id="76096-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="76096-137">このオプションは、.NET Core 2.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="76096-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="76096-138">発行の前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="76096-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="76096-139">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="76096-139">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="76096-140">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="76096-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="76096-141">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="76096-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="76096-142">出力ディレクトリのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="76096-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="76096-143">指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/publish/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]/publish/* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="76096-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="76096-144">パスが相対的である場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。</span><span class="sxs-lookup"><span data-stu-id="76096-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="76096-145">アプリケーションと一緒に .NET Core ランタイムを発行します。これにより、ランタイムをターゲット コンピューターにインストールする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="76096-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="76096-146">ランタイム識別子を指定した場合、その既定値は `true` となります。</span><span class="sxs-lookup"><span data-stu-id="76096-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="76096-147">さまざまな展開方法の詳細については、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76096-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="76096-148">指定されたランタイムのアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="76096-149">これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。</span><span class="sxs-lookup"><span data-stu-id="76096-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="76096-150">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76096-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="76096-151">既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。</span><span class="sxs-lookup"><span data-stu-id="76096-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="76096-152">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="76096-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="76096-153">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="76096-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="76096-154">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="76096-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="76096-155">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="76096-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="76096-156">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="76096-156">Defines the build configuration.</span></span> <span data-ttu-id="76096-157">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="76096-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="76096-158">指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="76096-159">ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76096-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="76096-160">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="76096-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="76096-161">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="76096-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="76096-162">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="76096-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="76096-163">アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。</span><span class="sxs-lookup"><span data-stu-id="76096-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="76096-164">マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="76096-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="76096-165">複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。</span><span class="sxs-lookup"><span data-stu-id="76096-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="76096-166">このオプションは、.NET Core 2.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="76096-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="76096-167">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="76096-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="76096-168">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="76096-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="76096-169">出力ディレクトリのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="76096-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="76096-170">指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/publish/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]/publish/* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="76096-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="76096-171">パスが相対的である場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。</span><span class="sxs-lookup"><span data-stu-id="76096-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="76096-172">アプリケーションと一緒に .NET Core ランタイムを発行します。これにより、ランタイムをターゲット コンピューターにインストールする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="76096-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="76096-173">ランタイム識別子を指定した場合、その既定値は `true` となります。</span><span class="sxs-lookup"><span data-stu-id="76096-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="76096-174">さまざまな展開方法の詳細については、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76096-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="76096-175">指定されたランタイムのアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="76096-176">これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。</span><span class="sxs-lookup"><span data-stu-id="76096-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="76096-177">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76096-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="76096-178">既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。</span><span class="sxs-lookup"><span data-stu-id="76096-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="76096-179">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="76096-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="76096-180">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="76096-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="76096-181">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="76096-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="76096-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="76096-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="76096-183">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="76096-183">Defines the build configuration.</span></span> <span data-ttu-id="76096-184">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="76096-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="76096-185">指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="76096-186">ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76096-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="76096-187">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="76096-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="76096-188">アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。</span><span class="sxs-lookup"><span data-stu-id="76096-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="76096-189">マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="76096-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="76096-190">複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。</span><span class="sxs-lookup"><span data-stu-id="76096-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="76096-191">このオプションは、.NET Core 2.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="76096-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="76096-192">出力ディレクトリのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="76096-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="76096-193">指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/publish/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]/publish/* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="76096-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="76096-194">パスが相対的である場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。</span><span class="sxs-lookup"><span data-stu-id="76096-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="76096-195">指定されたランタイムのアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="76096-196">これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。</span><span class="sxs-lookup"><span data-stu-id="76096-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="76096-197">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="76096-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="76096-198">既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。</span><span class="sxs-lookup"><span data-stu-id="76096-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="76096-199">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="76096-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="76096-200">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="76096-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="76096-201">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="76096-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="76096-202">使用例</span><span class="sxs-lookup"><span data-stu-id="76096-202">Examples</span></span>

<span data-ttu-id="76096-203">現在のディレクトリのプロジェクトを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="76096-204">指定されたプロジェクト ファイルを使用して、アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="76096-205">`netcoreapp1.1` フレームワークを使って現在のディレクトリ内のプロジェクトを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="76096-206">`netcoreapp1.1` フレームワークと `OS X 10.10` のランタイム (この RID はプロジェクト ファイルに列挙しておく必要があります) を使って、現在のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="76096-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="76096-207">現在のアプリケーションを発行します。ただし、復元操作中はルート プロジェクトのみを復元し、プロジェクト間 (P2P) 参照は復元しないでください (.NET Core SDK 2.0 以降のバージョン)。</span><span class="sxs-lookup"><span data-stu-id="76096-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="76096-208">関連項目</span><span class="sxs-lookup"><span data-stu-id="76096-208">See also</span></span>

* [<span data-ttu-id="76096-209">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="76096-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="76096-210">ランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="76096-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
