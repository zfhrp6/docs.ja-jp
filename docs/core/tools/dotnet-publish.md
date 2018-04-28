---
title: dotnet publish コマンド - .NET Core CLI
description: dotnet publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: fca05b22495f41ed85e89b077faad367a901e009
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-publish"></a><span data-ttu-id="cbe22-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="cbe22-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cbe22-104">name</span><span class="sxs-lookup"><span data-stu-id="cbe22-104">Name</span></span>

<span data-ttu-id="cbe22-105">`dotnet publish` - ホスティング システムへの展開のため、アプリケーションとその依存関係をフォルダーにパックします。</span><span class="sxs-lookup"><span data-stu-id="cbe22-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cbe22-106">構文</span><span class="sxs-lookup"><span data-stu-id="cbe22-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cbe22-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="cbe22-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cbe22-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cbe22-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="cbe22-109">説明</span><span class="sxs-lookup"><span data-stu-id="cbe22-109">Description</span></span>

<span data-ttu-id="cbe22-110">`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-110">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="cbe22-111">出力の内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cbe22-111">The output will contain the following:</span></span>

* <span data-ttu-id="cbe22-112">アセンブリの中間言語 (IL) コード (*dll* 拡張子)。</span><span class="sxs-lookup"><span data-stu-id="cbe22-112">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="cbe22-113">*.deps.json* ファイル。プロジェクトのすべての依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-113">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="cbe22-114">*.runtime.config.json* ファイル。アプリケーションが想定する共有ランタイムと、ランタイムの他の構成オプション (ガベージ コレクションの種類など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-114">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="cbe22-115">アプリケーションの依存関係。</span><span class="sxs-lookup"><span data-stu-id="cbe22-115">The application's dependencies.</span></span> <span data-ttu-id="cbe22-116">これらは NuGet キャッシュから出力フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-116">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="cbe22-117">`dotnet publish` コマンドの出力は、ホスティング システム (サーバー、PC、Mac、ラップトップなど) に展開して実行できる状態になっており、展開用にアプリケーションを準備するための正式にサポートされる唯一の方法です。</span><span class="sxs-lookup"><span data-stu-id="cbe22-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="cbe22-118">プロジェクトに指定されている展開の種類によっては、ホスティング システムに .NET Core 共有ランタイムがインストールされている場合とされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="cbe22-118">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="cbe22-119">詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cbe22-119">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="cbe22-120">発行されるアプリケーションのディレクトリ構造については、「[Directory structure](/aspnet/core/hosting/directory-structure)」 (ディレクトリ構造) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cbe22-120">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="cbe22-121">引数</span><span class="sxs-lookup"><span data-stu-id="cbe22-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="cbe22-122">発行するプロジェクトです。指定されていない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-122">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="cbe22-123">オプション</span><span class="sxs-lookup"><span data-stu-id="cbe22-123">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cbe22-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="cbe22-124">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="cbe22-125">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-125">Defines the build configuration.</span></span> <span data-ttu-id="cbe22-126">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="cbe22-126">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cbe22-127">指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-127">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cbe22-128">ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbe22-128">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="cbe22-129">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-129">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cbe22-130">これは、*project.assets.json* ファイルを削除する処理に相当します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="cbe22-131">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-131">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="cbe22-132">アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-132">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="cbe22-133">マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="cbe22-133">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="cbe22-134">複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-134">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="cbe22-135">このオプションは、.NET Core 2.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-135">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="cbe22-136">プロジェクト間参照を無視し、ルート プロジェクトのみを復元します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="cbe22-137">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="cbe22-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cbe22-138">出力ディレクトリのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-138">Specifies the path for the output directory.</span></span> <span data-ttu-id="cbe22-139">指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-139">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="cbe22-140">相対パスが指定された場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。</span><span class="sxs-lookup"><span data-stu-id="cbe22-140">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="cbe22-141">アプリケーションと一緒に .NET Core ランタイムを発行します。これにより、ランタイムをターゲット コンピューターにインストールする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="cbe22-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="cbe22-142">ランタイム識別子を指定した場合、その既定値は `true` となります。</span><span class="sxs-lookup"><span data-stu-id="cbe22-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="cbe22-143">さまざまな展開方法の詳細については、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbe22-143">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="cbe22-144">指定されたランタイムのアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="cbe22-145">これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="cbe22-146">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cbe22-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cbe22-147">既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cbe22-148">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cbe22-149">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="cbe22-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="cbe22-150">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cbe22-151">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cbe22-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="cbe22-152">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-152">Defines the build configuration.</span></span> <span data-ttu-id="cbe22-153">既定値は `Debug` です。</span><span class="sxs-lookup"><span data-stu-id="cbe22-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cbe22-154">指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cbe22-155">ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbe22-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="cbe22-156">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="cbe22-157">アプリによって公開された一連のパッケージをトリミングするために使用する[ターゲット マニフェスト](../deploying/runtime-store.md)を 1 つまたは複数指定します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="cbe22-158">マニフェスト ファイルは、[`dotnet store` コマンド](dotnet-store.md)の出力の一部です。</span><span class="sxs-lookup"><span data-stu-id="cbe22-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="cbe22-159">複数のマニフェストを指定するには、マニフェストごとに `--manifest` を追加します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="cbe22-160">このオプションは、.NET Core 2.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="cbe22-161">出力ディレクトリのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="cbe22-162">指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]* に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-162">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="cbe22-163">相対パスが指定された場合、生成された出力ディレクトリは、現在の作業ディレクトリではなく、プロジェクト ファイルの場所に相対的なパスとなります。</span><span class="sxs-lookup"><span data-stu-id="cbe22-163">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="cbe22-164">指定されたランタイムのアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-164">Publishes the application for a given runtime.</span></span> <span data-ttu-id="cbe22-165">これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-165">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="cbe22-166">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cbe22-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cbe22-167">既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。</span><span class="sxs-lookup"><span data-stu-id="cbe22-167">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="cbe22-168">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cbe22-169">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="cbe22-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="cbe22-170">プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-170">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="cbe22-171">使用例</span><span class="sxs-lookup"><span data-stu-id="cbe22-171">Examples</span></span>

<span data-ttu-id="cbe22-172">現在のディレクトリのプロジェクトを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-172">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="cbe22-173">指定されたプロジェクト ファイルを使用して、アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-173">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="cbe22-174">`netcoreapp1.1` フレームワークを使って現在のディレクトリ内のプロジェクトを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-174">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="cbe22-175">`netcoreapp1.1` フレームワークと `OS X 10.10` のランタイム (この RID はプロジェクト ファイルに列挙しておく必要があります) を使って、現在のアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="cbe22-175">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="cbe22-176">現在のアプリケーションを発行します。ただし、復元操作中はルート プロジェクトのみを復元し、プロジェクト間 (P2P) 参照は復元しないでください (.NET Core SDK 2.0 以降のバージョン)。</span><span class="sxs-lookup"><span data-stu-id="cbe22-176">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="cbe22-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="cbe22-177">See also</span></span>

* [<span data-ttu-id="cbe22-178">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="cbe22-178">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="cbe22-179">ランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="cbe22-179">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)