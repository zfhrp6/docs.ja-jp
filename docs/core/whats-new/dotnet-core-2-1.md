---
title: .NET Core 2.1 の新機能
description: .NET Core 2.1 の新機能について。
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 241ac0195e5edcd17ac67ea7ea0fac159af97414
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826933"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="c5c8f-103">.NET Core 2.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="c5c8f-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="c5c8f-104">.NET Core 2.1 には、次の分野の拡張機能と新機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="c5c8f-105">ツール</span><span class="sxs-lookup"><span data-stu-id="c5c8f-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="c5c8f-106">ロールフォワード</span><span class="sxs-lookup"><span data-stu-id="c5c8f-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="c5c8f-107">配置</span><span class="sxs-lookup"><span data-stu-id="c5c8f-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="c5c8f-108">Windows 互換機能パック</span><span class="sxs-lookup"><span data-stu-id="c5c8f-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="c5c8f-109">JIT コンパイルの改良</span><span class="sxs-lookup"><span data-stu-id="c5c8f-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="c5c8f-110">API の変更</span><span class="sxs-lookup"><span data-stu-id="c5c8f-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="c5c8f-111">ツール</span><span class="sxs-lookup"><span data-stu-id="c5c8f-111">Tooling</span></span>

<span data-ttu-id="c5c8f-112">.NET Core 2.1 に付属のツールである .NET Core 2.1 SDK (v 2.1.300) には次の変更点と拡張機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="c5c8f-113">ビルドのパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="c5c8f-113">Build performance improvements</span></span>

<span data-ttu-id="c5c8f-114">.NET Core 2.1 の大きな注目点はビルド時 (特にインクリメンタル ビルド) のパフォーマンスの向上です。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="c5c8f-115">このようなパフォーマンスの向上は、`dotnet build` を使用したコマンドライン ビルドと Visual Studio でのビルドの両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="c5c8f-116">各分野の向上点の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="c5c8f-117">(パッケージ資産の解決) すべての資産ではなく、ビルドで使用される資産のみ解決する。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="c5c8f-118">アセンブリ参照のキャッシュ。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-118">Caching of assembly references.</span></span>

- <span data-ttu-id="c5c8f-119">長時間にわたる SDK ビルド サーバー (`dotnet build` の個々の呼び出しにまたがるプロセス) の使用。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="c5c8f-120">これにより、`dotnet build` が実行されるたびに大きなコード ブロックを JIT コンパイルする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="c5c8f-121">ビルド サーバー プロセスは、次のコマンドで自動的に終了することができます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="c5c8f-122">新しい CLI コマンド</span><span class="sxs-lookup"><span data-stu-id="c5c8f-122">New CLI commands</span></span>

<span data-ttu-id="c5c8f-123">[`DotnetCliToolReference`](../tools/extensibility.md) を使用してプロジェクト単位でのみ入手可能であった複数のツールを .NET Core SDK の一部として入手できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="c5c8f-124">それらのツールを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-124">These tools include:</span></span>

- <span data-ttu-id="c5c8f-125">`dotnet watch` は、ファイルの変更を待機してから、指定された一連のコマンドを実行するファイル システム ウォッチャーを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="c5c8f-126">たとえば、次のコマンドは現在のプロジェクト内のファイルが変更されるたびにプロジェクトを自動的にリビルドして、詳細な出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```
  
   <span data-ttu-id="c5c8f-127">`--verbose` オプションの前にある `--` オプションに注目してください。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="c5c8f-128">これは、子プロセスである `dotnet` に渡される引数から `dotnet watch` コマンドに直接渡されるオプションを区切るものです。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="c5c8f-129">このオプションを使用しないと、`--verbose` オプションが `dotnet build` コマンドではなく `dotnet watch` コマンドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="c5c8f-130">詳細については、「[dotnet watch を使用した ASP.NET Core アプリの開発](/aspnet/core/tutorials/dotnet-watch)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="c5c8f-131">`dotnet dev-certs` は、ASP.NET Core アプリケーションでの開発時に使用される証明書を生成および管理します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="c5c8f-132">`dotnet user-secrets` は、ASP.NET Core アプリケーションでユーザー シークレット ストアのシークレットを管理します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="c5c8f-133">`dotnet sql-cache` は、分散キャッシュに使用する Microsoft SQL Server データベースでテーブルとインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="c5c8f-134">`dotnet ef` は、データベース、<xref:Microsoft.EntityFrameworkCore.DbContext> オブジェクト、および Entity Framework Core アプリケーションにおける移行を管理するためのツールです。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="c5c8f-135">詳細については、「[EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet)」(EF Core .NET コマンドライン ツール) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="c5c8f-136">グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="c5c8f-136">Global Tools</span></span>

<span data-ttu-id="c5c8f-137">.NET Core 2.1 では、*グローバル ツール* (コマンドラインからグローバルに使用できるカスタム ツール) がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="c5c8f-138">以前のバージョンの .NET Core の拡張モデルでは、[`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools) を使用してカスタム ツールをプロジェクト単位で入手することのみ可能でした。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="c5c8f-139">グローバル ツールをインストールするには、[dotnet tool install](..\tools\dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-139">To install a Global Tool, you use the [dotnet tool install](..\tools\dotnet-tool-install.md) command.</span></span> <span data-ttu-id="c5c8f-140">例:</span><span class="sxs-lookup"><span data-stu-id="c5c8f-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="c5c8f-141">インストールしたツールは、ツール名を指定してコマンドラインから実行できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="c5c8f-142">詳細については、「[.NET Core Global Tools overview](../tools/global-tools.md)」(.NET Core グローバル ツールの概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="c5c8f-143">`dotnet tool` コマンドによるツールの管理</span><span class="sxs-lookup"><span data-stu-id="c5c8f-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="c5c8f-144">.NET Core SDK 2.1 (v 2.1.300) では、すべてのツール操作で `dotnet tool` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-144">In .NET Core SDK 2.1 (v 2.1.300), all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="c5c8f-145">次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-145">The following options are available:</span></span>

- <span data-ttu-id="c5c8f-146">[`dotnet tool install`](../tools/dotnet-tool-install.md): ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="c5c8f-147">[`dotnet tool update`](../tools/dotnet-tool-update.md): ツールをアンインストールおよび再インストールします。これにより、ツールが効果的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="c5c8f-148">[`dotnet tool list`](../tools/dotnet-tool-list.md): 現在インストールされているツールの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="c5c8f-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md): 現在インストールされているツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="c5c8f-150">ロールフォワード</span><span class="sxs-lookup"><span data-stu-id="c5c8f-150">Roll forward</span></span>

<span data-ttu-id="c5c8f-151">.NET Core 2.0 以降のすべての .NET Core アプリケーションは、システムにインストールされている最新の*マイナー バージョン*に自動的にロールフォワードされます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-151">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span> 

<span data-ttu-id="c5c8f-152">.NET Core 2.0 以降では、アプリケーションのビルドに使用した .NET Core のバージョンが実行時に存在しない場合、インストールされている .NET Core の最新の*マイナー バージョン*に対してアプリケーションが自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="c5c8f-153">つまり、アプリケーションが .NET Core 2.0 を使用してビルドされ、ホスト システムにインストールされているのが .NET Core 2.0 ではなく .NET Core 2.1 である場合は、.NET Core 2.1 を使用してアプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5c8f-154">このロールフォワードの動作はプレビュー リリースには適用されません。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="c5c8f-155">また、メジャー リリースにも適用されません。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-155">Nor does it apply to major releases.</span></span> <span data-ttu-id="c5c8f-156">たとえば、.NET Core 1.0 アプリケーションは .NET Core 2.0 または .NET Core 2.1 にロールフォワードされません。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-156">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="c5c8f-157">次に示す 3 つのいずれかの方法でマイナー バージョンのロールフォワードを無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-157">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="c5c8f-158">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` 環境変数を 0 に設定する。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-158">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to 0.</span></span>

- <span data-ttu-id="c5c8f-159">次の行を runtimeconfig.json ファイルに追加する。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-159">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="c5c8f-160">[.NET Core CLI ツール](../tools/index.md)の使用時に、.NET Core コマンド (`run` など) に次のオプションを追加する。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-160">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="c5c8f-161">配置</span><span class="sxs-lookup"><span data-stu-id="c5c8f-161">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="c5c8f-162">自己完結型アプリケーションのサービス提供</span><span class="sxs-lookup"><span data-stu-id="c5c8f-162">Self-contained application servicing</span></span>

<span data-ttu-id="c5c8f-163">`dotnet publish` は、サービス提供されたランタイム バージョンを含む自己完結型アプリケーションをパブリッシュするようになりました。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-163">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="c5c8f-164">.NET Core 2.1 SDK (v 2.1.300) を含む自己完結型アプリケーションをパブリッシュする場合、その SDK で認識済みである最新のサービス提供されたランタイム バージョンがアプリケーションに含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-164">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="c5c8f-165">最新の SDK にアップグレードする場合は、最新の .NET Core ランタイム バージョンでパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-165">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="c5c8f-166">これに該当するのは .NET Core 1.0 以降のランタイムです。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-166">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="c5c8f-167">自己完結型のパブリッシュは、NuGet.org のランタイム バージョンに依存します。マシンにはサービス提供されたランタイムは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-167">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="c5c8f-168">.NET Core 2.0 SDK を使用すると、`RuntimeFrameworkVersion` プロパティで別のバージョンが指定されている場合を除き、自己完結型アプリケーションが .NET Core 2.0.0 ランタイムでパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-168">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="c5c8f-169">この新しい動作により、このプロパティを設定して、より新しいバージョンのランタイムを自己完結型アプリケーションに対して選択する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-169">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="c5c8f-170">今後は常に .NET Core 2.1 SDK (v 2.1.300) でパブリッシュするのが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-170">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="c5c8f-171">Windows 互換機能パック</span><span class="sxs-lookup"><span data-stu-id="c5c8f-171">Windows Compatibility Pack</span></span>

<span data-ttu-id="c5c8f-172">既存のコードを .NET Framework から .NET Core に移植する場合は、[Windows 互換機能パック](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-172">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="c5c8f-173">この Windows 互換機能パックでは、.NET Core よりも 20,000 個も多い API にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-173">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="c5c8f-174">これらの API には、<xref:System.Drawing?displayProperty="nameWithType"> 名前空間の型、<xref:System.Diagnostics.EventLog> クラス、WMI、パフォーマンス カウンター、Windows サービス、および Windows レジストリの型とメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-174">These APIs include types in the <xref:System.Drawing?displayProperty="nameWithType"> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="c5c8f-175">JIT コンパイラの機能強化</span><span class="sxs-lookup"><span data-stu-id="c5c8f-175">JIT compiler improvements</span></span>

<span data-ttu-id="c5c8f-176">.NET Core には*階層型コンパイル* (*適応型最適化*とも呼ばれる) という新しい JIT コンパイラ テクノロジが組み込まれており、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-176">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="c5c8f-177">階層型コンパイルはオプトイン設定です。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-177">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="c5c8f-178">JIT コンパイラで実行される重要なタスクの 1 つはコード実行の最適化です。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-178">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="c5c8f-179">ただし、使用頻度の低いコード パスについては、最適化されていないコードの実行にランタイムが費やす時間よりも、コードの最適化にコンパイラが費やす時間の方が多くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-179">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="c5c8f-180">階層型コンパイルによって JIT コンパイルに次の 2 つのステージが導入されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-180">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="c5c8f-181">**第 1 階層**: コードをできるだけ早く生成します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-181">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="c5c8f-182">**第 2 階層**: 頻繁に実行されるメソッドに対して、最適化されたコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-182">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="c5c8f-183">コンパイルの第 2 階層は、パフォーマンスの向上と並行して実行されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-183">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="c5c8f-184">次に示す 2 つのいずれかの方法で階層型コンパイルをオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-184">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="c5c8f-185">.NET Core 2.1 SDK を使用するすべてのプロジェクトで階層型コンパイルを使用するには、次の環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-185">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="c5c8f-186">プロジェクト単位で階層型コンパイルを使用するには、次の例に示すように、MSBuild プロジェクト ファイルの `<PropertyGroup>` セクションに `<TieredCompilation>` プロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-186">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="c5c8f-187">API の変更</span><span class="sxs-lookup"><span data-stu-id="c5c8f-187">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="c5c8f-188">`Span<T>` および `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="c5c8f-188">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="c5c8f-189">.NET Core 2.1 には、配列とその他の種類のメモリを使用する作業を大幅に効率的に行えるようにするいくつかの新しい型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-189">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="c5c8f-190">新しい型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-190">The new types include:</span></span>

- <span data-ttu-id="c5c8f-191"><xref:System.Span%601?displayProperty=nameWithType> および <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-191"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="c5c8f-192"><xref:System.Memory%601?displayProperty=nameWithType> および <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-192"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c5c8f-193">これらの型を使用しない場合は、アレイの一部やメモリ バッファーのセクションなどの項目を渡すときに、一部のデータのコピーを作成してからメソッドに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-193">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="c5c8f-194">これらの型はデータを仮想的に表示します。これにより、追加メモリの割り当てとコピーの操作の必要性が排除されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-194">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="c5c8f-195">次の例では、<xref:System.Span%601> インスタンスを使用して配列の 10 個の要素を仮想的に表示します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-195">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="c5c8f-196">Brotli 圧縮</span><span class="sxs-lookup"><span data-stu-id="c5c8f-196">Brotli compression</span></span>

<span data-ttu-id="c5c8f-197">.NET Core 2.1 には、Brotli 圧縮と展開のサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-197">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="c5c8f-198">Brotli は、[RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) で定義されており、ほとんどの Web ブラウザーと主要な Web サーバーでサポートされている汎用の無損失圧縮アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-198">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="c5c8f-199">ストリーム ベースの <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> クラスまたは高性能なスパン ベースの <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> クラスと <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-199">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="c5c8f-200">次の例は、<xref:System.IO.Compression.BrotliStream> クラスによる圧縮を示しています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-200">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="c5c8f-201"><xref:System.IO.Compression.BrotliStream> の動作は、<xref:System.IO.Compression.DeflateStream> および <xref:System.IO.Compression.GZipStream> と同じです。そのため、これらの API を呼び出すコードを簡単に <xref:System.IO.Compression.BrotliStream> に変換できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-201">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="c5c8f-202">新しい暗号化 API と暗号化の機能強化</span><span class="sxs-lookup"><span data-stu-id="c5c8f-202">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="c5c8f-203">.NET Core 2.1 には、暗号化 API に対する多数の拡張機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-203">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="c5c8f-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> は System.Security.Cryptography.Pkcs パッケージにあります。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="c5c8f-205">実装は .NET Framework の <xref:System.Security.Cryptography.Pkcs.SignedCms> クラスと同じです。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-205">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="c5c8f-206"><xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> メソッドと <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> メソッドの新しいオーバーロードは、ハッシュ アルゴリズム識別子を受け入れ、SHA-1 以外のアルゴリズムを使用して呼び出し元が証明書の拇印の値を取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-206">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="c5c8f-207">新しい <xref:System.Span%601> ベースの暗号化 API をハッシュ、HMAC、暗号乱数の生成、非対称署名の生成、非対称署名の処理、および RSA 暗号化に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-207">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="c5c8f-208"><xref:System.Span%601> ベースの実装を使用することにより、<xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> のパフォーマンスが約 15% 向上しました。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-208">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="c5c8f-209">新しい <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> クラスには、次に示す 2 つの新しいメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-209">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="c5c8f-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> は、同じ長さの任意の 2 つの入力に対して一定の時間を費やして戻ります。これは暗号化の検証での使用に適しており、サイド チャネル情報のタイミング攻撃の一因となることを避けることができます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="c5c8f-211"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> はメモリ クリアのルーチンであり、最適化はできません。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-211"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="c5c8f-212">静的メソッドである <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> は <xref:System.Span%601> にランダムな値を入力します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-212">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="c5c8f-213"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> が Linux と maxOS でサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-213">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="c5c8f-214">Elliptic-Curve Diffie-Hellman (ECDH) を <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> クラス ファミリーで使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-214">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="c5c8f-215">セキュリティ、外部からのアクセスは .NET Framework の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-215">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="c5c8f-216"><xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> から返されるインスタンスは、SHA-2 ダイジェストを使用して OAEP で暗号化または暗号化解除できます。また、RSA-PSS を使用して署名を生成または検証できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-216">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="c5c8f-217">ソケットの機能強化</span><span class="sxs-lookup"><span data-stu-id="c5c8f-217">Sockets improvements</span></span>

<span data-ttu-id="c5c8f-218">.NET Core には、新しい型である <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>、および高度なネットワーク API の基盤となる書き換えられた <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-218">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="c5c8f-219">たとえば、<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> は <xref:System.Net.Http.HttpClient> 実装の基盤です。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-219"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="c5c8f-220">以前のバージョンの .NET Core の高度な API は、ネイティブのネットワーク実装を基盤としていました。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-220">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="c5c8f-221">.NET Core 2.1 に導入されたソケットの実装には多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-221">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="c5c8f-222">以前の実装と比較して、パフォーマンスが大幅に向上しています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-222">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="c5c8f-223">プラットフォームの依存関係を排除したため、配置やサービス提供が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-223">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="c5c8f-224">すべての .NET Core プラットフォームで動作が一貫しています。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-224">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="c5c8f-225"><xref:System.Net.Http.SocketsHttpHandler> は .NET Core 2.1 における既定の実装です。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-225"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="c5c8f-226">ただし、<xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> メソッドを呼び出すことで、古い <xref:System.Net.Http.HttpClientHandler> クラスを使用するようにアプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-226">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", False)
```

<span data-ttu-id="c5c8f-227">環境変数を使用して、<xref:System.Net.Http.SocketsHttpHandler> に基づくソケットの実装の使用をオプトアウトすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-227">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="c5c8f-228">そのためには、`DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` を `false` または 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-228">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="c5c8f-229">Windows では、ネイティブ実装に依存する <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType> を使用するか、または <xref:System.Net.Http.HttpClient> コンストラクターにクラスのインスタンスを渡すことにより <xref:System.Net.Http.SocketsHttpHandler> クラスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-229">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="c5c8f-230">Linux と macOS では、<xref:System.Net.Http.HttpClient> をプロセス単位でのみ構成できます。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-230">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="c5c8f-231">Linux で古い <xref:System.Net.Http.HttpClient> 実装を使用する場合は、[libcurl](https://curl.haxx.se/libcurl/) を配置する必要があります </span><span class="sxs-lookup"><span data-stu-id="c5c8f-231">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="c5c8f-232">(これは .NET Core 2.0 と共にインストールされています)。</span><span class="sxs-lookup"><span data-stu-id="c5c8f-232">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="c5c8f-233">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5c8f-233">See also</span></span>

[<span data-ttu-id="c5c8f-234">.NET Core の新機能</span><span class="sxs-lookup"><span data-stu-id="c5c8f-234">What's new in .NET Core</span></span>](index.md)  
[<span data-ttu-id="c5c8f-235">EF Core 2.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="c5c8f-235">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
[<span data-ttu-id="c5c8f-236">ASP.NET Core 2.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="c5c8f-236">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
