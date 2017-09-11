---
title: ".NET Core 2.0 の新機能"
description: ".NET Core の新機能について。"
keywords: .NET, .NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.translationtype: HT
ms.sourcegitcommit: b47d4c74a01b99d743b69328c201096bc8d89794
ms.openlocfilehash: e43f72ebd26c34636c239d8ac9f749d52d3f60a0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/14/2017

---
# <a name="whats-new-in-net-core"></a><span data-ttu-id="ceb42-104">.NET Core の新機能</span><span class="sxs-lookup"><span data-stu-id="ceb42-104">What's new in .NET Core</span></span>

<span data-ttu-id="ceb42-105">.NET core 2.0 には、次のことの拡張機能や新機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-105">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="ceb42-106">ツール</span><span class="sxs-lookup"><span data-stu-id="ceb42-106">Tooling</span></span>](#tooling)
- [<span data-ttu-id="ceb42-107">言語サポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-107">Language support</span></span>](#language-support)
- [<span data-ttu-id="ceb42-108">プラットフォームの機能強化</span><span class="sxs-lookup"><span data-stu-id="ceb42-108">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="ceb42-109">API の変更</span><span class="sxs-lookup"><span data-stu-id="ceb42-109">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="ceb42-110">Visual Studio の統合</span><span class="sxs-lookup"><span data-stu-id="ceb42-110">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="ceb42-111">ドキュメントの改善</span><span class="sxs-lookup"><span data-stu-id="ceb42-111">Documentation improvements</span></span>](#documentation-improvements) 

## <a name="tooling"></a><span data-ttu-id="ceb42-112">ツール</span><span class="sxs-lookup"><span data-stu-id="ceb42-112">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="ceb42-113">dotnet restore の暗黙的な実行</span><span class="sxs-lookup"><span data-stu-id="ceb42-113">dotnet restore runs implicitly</span></span>

<span data-ttu-id="ceb42-114">以前のバージョンの .NET Core では、[dotnet new](../tools/dotnet-new.md) コマンドで新しいプロジェクトを作成した直後に、またはプロジェクトに新しい依存関係を追加したときに、[dotnet restore](../tools/dotnet-restore.md) コマンドを実行して、依存関係をダウンロードする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="ceb42-114">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span> <span data-ttu-id="ceb42-115">.NET Core 2.0 では、`dotnet new` コマンドを実行したときに暗黙的に `dotnet restore` が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-115">In .NET Core 2.0, `dotnet restore` runs implicitly when the `dotnet new` command executes.</span></span> <span data-ttu-id="ceb42-116">`run`、`build`、`publish` など他のコマンドを実行したときにも、依存関係の更新が必要であれば暗黙的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-116">It also runs implicitly if dependencies need to be updated when other commands, such as the `run`, `build`, and `publish` commands, execute.</span></span>

<span data-ttu-id="ceb42-117">この `dotnet restore` の自動実行は、`--no-restore` スイッチを `new`、`run`、`build`、`publish`、`pack`、`test` コマンドに渡すことで、無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-117">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span> 

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="ceb42-118">.NET Core 2.0 への再ターゲット</span><span class="sxs-lookup"><span data-stu-id="ceb42-118">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="ceb42-119">.NET Core 2.0 SDK がインストールされていれば、.NET Core 1.x をターゲットしているプロジェクトを .NET Core 2.0 に再ターゲットすることができます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-119">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span> 

<span data-ttu-id="ceb42-120">.NET Core 2.0 に再ターゲットするには、プロジェクト ファイルを編集して `<TargetFramework>` 要素 (または、プロジェクト ファイルに複数のターゲットがある場合は `<TargetFrameworks>` 要素) の値を 1.x から 2.0 に変更します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-120">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="ceb42-121">同じ方法で、.NET Standard ライブラリを .NET Standard 2.0 に再ターゲットすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-121">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="ceb42-122">.NET Core 2.0 へのプロジェクトの移行の詳細については、「[Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0 (ASP.NET Core 1.x から ASP.NET Core 2.0 への移行)](/aspnet/core/migration/1x-to-2x/index)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ceb42-122">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="ceb42-123">言語サポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-123">Language support</span></span>

<span data-ttu-id="ceb42-124">.NET Core 2.0 では、C# と F# に加えて Visual Basic もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-124">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="ceb42-125">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ceb42-125">Visual Basic</span></span>

<span data-ttu-id="ceb42-126">.NET Core のバージョン 2.0 では、Visual Basic 2017 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-126">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="ceb42-127">Visual Basic を使用して、次の種類のプロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-127">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="ceb42-128">.NET Core コンソール アプリ</span><span class="sxs-lookup"><span data-stu-id="ceb42-128">.NET Core console apps</span></span>
- <span data-ttu-id="ceb42-129">.NET Core クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="ceb42-129">.NET Core class libraries</span></span>
- <span data-ttu-id="ceb42-130">.NET Standard クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="ceb42-130">.NET Standard class libraries</span></span>
- <span data-ttu-id="ceb42-131">.NET Core 単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="ceb42-131">.NET Core unit test projects</span></span>
- <span data-ttu-id="ceb42-132">.NET Core xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="ceb42-132">.NET Core xUnit test projects</span></span> 

<span data-ttu-id="ceb42-133">たとえば、Visual Basic で "Hello World" アプリケーションを作成するには、コマンドラインから次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-133">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="ceb42-134">コンソール ウィンドウを開き、プロジェクトにディレクトリを作成し、そのディレクトリを現在のディレクトリにします。</span><span class="sxs-lookup"><span data-stu-id="ceb42-134">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="ceb42-135">`dotnet new console -lang vb` コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-135">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="ceb42-136">このコマンドにより、*Program.vb* というファイル名の Visual Basic ソース コードとともに、ファイル拡張子が `.vbproj` のプロジェクト ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-136">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="ceb42-137">このファイル内に、"Hello World!" という文字列を</span><span class="sxs-lookup"><span data-stu-id="ceb42-137">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="ceb42-138">コンソール ウィンドウに表示するためのソース コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-138">to the console window.</span></span>
  
1.  <span data-ttu-id="ceb42-139">`dotnet run` コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-139">Enter the command `dotnet run`.</span></span> <span data-ttu-id="ceb42-140">[.NET Core CLI ツール](../tools/index.md)によりアプリケーションが自動的にコンパイルされて実行され、"Hello World!" メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-140">The [.NET Core CLI tools](../tools/index.md) automatically compile and execute the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="ceb42-141">コンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-141">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="ceb42-142">C# 7.1 のサポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-142">Support for C# 7.1</span></span>

<span data-ttu-id="ceb42-143">.NET core 2.0 では、次のような新機能が追加された C# 7.1 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-143">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="ceb42-144">アプリケーション エントリ ポイントである `Main` メソッドを、[async](../../csharp/language-reference/keywords/async.md) キーワードでマークできます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-144">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="ceb42-145">推定タプル名。</span><span class="sxs-lookup"><span data-stu-id="ceb42-145">Inferred tuple names.</span></span>
- <span data-ttu-id="ceb42-146">既定の式。</span><span class="sxs-lookup"><span data-stu-id="ceb42-146">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="ceb42-147">プラットフォームの機能強化</span><span class="sxs-lookup"><span data-stu-id="ceb42-147">Platform improvements</span></span>

<span data-ttu-id="ceb42-148">.NET core 2.0 には、.NET Core のインストールを簡略化し、サポートされているオペレーティング システム上で .NET Core を使用する機能がいくつか含まれています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-148">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="ceb42-149">.NET Core for Linux は単一実装</span><span class="sxs-lookup"><span data-stu-id="ceb42-149">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="ceb42-150">.NET core 2.0 では、複数の Linux ディストリビューションで動作する単一の Linux 実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-150">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="ceb42-151">.NET core 1.x では、ディストリビューション固有の Linux 実装をダウンロードする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="ceb42-151">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="ceb42-152">単一のオペレーティング システムとしての Linux をターゲットするアプリを開発することもできます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-152">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="ceb42-153">.NET Core 1.x では、ディストリビューションごとに別の Linux をターゲットする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="ceb42-153">.NET Core 1.x required that you target each Linux distribution separately.</span></span> 

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="ceb42-154">Apple 暗号化ライブラリのサポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-154">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="ceb42-155">macOS の .NET Core 1.x では、OpenSSL ツールキットの暗号化ライブラリが必要でした。</span><span class="sxs-lookup"><span data-stu-id="ceb42-155">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="ceb42-156">.NET Core 2.0 では、Apple 暗号化ライブラリを使用し、OpenSSL を必要としないため、OpenSSL をインストールする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="ceb42-156">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span> 

## <a name="api-changes-and-library-support"></a><span data-ttu-id="ceb42-157">API の変更とライブラリのサポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-157">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="ceb42-158">.NET Standard 2.0 のサポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-158">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="ceb42-159">.NET Standard は、そのバージョンの標準に準拠した .NET 実装で使用する必要がある、バージョン管理された API のセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-159">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="ceb42-160">.NET Standard はライブラリ開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-160">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="ceb42-161">.NET Standard の目的は、.NET 実装ごとの .NET Standard のバージョンに対応するライブラリで使用できる機能を保証することです。</span><span class="sxs-lookup"><span data-stu-id="ceb42-161">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="ceb42-162">.NET Core 1.x では、.NET Standard バージョン 1.6 がサポートされており、.NET Core 2.0 では最新の .NET Standard 2.0 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-162">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="ceb42-163">詳細については、「[.NET Standard](../../standard/net-standard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ceb42-163">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="ceb42-164">.NET Standard 2.0 には、.NET Standard 1.6 で使用できた 20,000 個以上の API が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-164">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="ceb42-165">この拡張されたアクセス領域の多くは、.NET Framework と Xamarin に共通する API を .NET Standard に組み込んだ結果です。</span><span class="sxs-lookup"><span data-stu-id="ceb42-165">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="ceb42-166">.NET Standard 2.0 クラス ライブラリは、.NET Framework クラス ライブラリを参照することもできます。ただし、呼び出す API が .NET Standard 2.0 内に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceb42-166">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="ceb42-167">.NET Framework ライブラリを再コンパイルする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ceb42-167">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="ceb42-168">最新バージョンの .NET Standard 1.6 以降に、.NET Standard に追加された API の一覧については、「[.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ceb42-168">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="ceb42-169">拡張されたアクセス領域</span><span class="sxs-lookup"><span data-stu-id="ceb42-169">Expanded surface area</span></span>

<span data-ttu-id="ceb42-170">.NET Core 2.0 で使用できる API の数は、.NET Core 1.1 の 2 倍以上です。</span><span class="sxs-lookup"><span data-stu-id="ceb42-170">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span> 

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="ceb42-171">.NET Framework ライブラリのサポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-171">Support for .NET Framework libraries</span></span>

<span data-ttu-id="ceb42-172">.NET Core のコードは、既存の NuGet パッケージなど、既存の .NET Framework ライブラリを参照できます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-172">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="ceb42-173">ライブラリは .NET Standard にある API を使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ceb42-173">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="ceb42-174">Visual Studio の統合環境</span><span class="sxs-lookup"><span data-stu-id="ceb42-174">Visual Studio integration</span></span>

<span data-ttu-id="ceb42-175">Visual Studio 2017 バージョン 15.3 (場合によって Visual Studio for Mac) では、.NET Core 開発者のために十分な数の拡張機能をご用意しています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-175">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="ceb42-176">.NET Core アプリと .NET Standard ライブラリの再ターゲット</span><span class="sxs-lookup"><span data-stu-id="ceb42-176">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="ceb42-177">.NET Core 2.0 SDK がインストールされていれば、.NET Core 1.x プロジェクトを .NET Core 2.0 に、.NET Standard 1.x ライブラリを .NET Standard 2.0 に再ターゲットすることができます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-177">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span> 

<span data-ttu-id="ceb42-178">Visual Studio のプロジェクトを再ターゲットするには、そのプロジェクトのプロパティ ダイアログの **[アプリケーション]** タブを開き、**[ターゲット フレームワーク]** の値を「**.NET Core 2.0**」または「**.NET Standard 2.0**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-178">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="ceb42-179">プロジェクトを右クリックして**編集\*.csproj ファイル** オプションを選択することで、変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-179">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="ceb42-180">詳細については、前述の「[ツール](#tooling)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ceb42-180">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="ceb42-181">.NET Core のライブ単体テスト対応</span><span class="sxs-lookup"><span data-stu-id="ceb42-181">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="ceb42-182">コードを変更すると常に、Live Unit Testing は影響を受ける単体テストをバックグラウンドで自動的に実行して、テスト結果とコード カバレッジをライブで Visual Studio 環境に表示します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-182">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="ceb42-183">.NET core 2.0 では現在、Live Unit Testing がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-183">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="ceb42-184">以前は、.NET Framework アプリケーションでのみ Live Unit Testing が使用できました。</span><span class="sxs-lookup"><span data-stu-id="ceb42-184">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span> 

<span data-ttu-id="ceb42-185">詳細については、「[Visual Studio 2017 での Live Unit Testing](/visualstudio/test/live-unit-testing)」と「[Live Unit Testing についてよく寄せられる質問](/visualstudio/test/live-unit-testing-faq)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ceb42-185">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="ceb42-186">複数のターゲット フレームワークのサポートを向上</span><span class="sxs-lookup"><span data-stu-id="ceb42-186">Better support for multiple target frameworks</span></span>

<span data-ttu-id="ceb42-187">複数のターゲット フレームワークのプロジェクトをビルドする場合は、トップレベルのメニューからターゲット プラットフォームを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-187">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="ceb42-188">次の図では、SCD1 という名前のプロジェクトが 64 ビット Mac OS X 10.11 (`osx.10.11-x64`) と 64 ビット Windows 10/Windows Server 2016 (`win10-x64`) をターゲットしています。</span><span class="sxs-lookup"><span data-stu-id="ceb42-188">In the following figure, a project named SCD1 targets 64-bit Mac OS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="ceb42-189">プロジェクト ボタンを選択する前にターゲット フレームワークを選択できます。今回はデバッグ ビルドを実行するために選択します。</span><span class="sxs-lookup"><span data-stu-id="ceb42-189">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![プロジェクト作成時のターゲット フレームワークの選択](media/multitarget.png) 

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="ceb42-191">.NET Core SDK の side-by-side サポート</span><span class="sxs-lookup"><span data-stu-id="ceb42-191">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="ceb42-192">.NET Core SDK を Visual Studio とは別にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-192">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="ceb42-193">これにより、異なるバージョンの.NET Core をターゲットしているプロジェクトを 1 つのバージョンの Visual Studio でビルドできます。</span><span class="sxs-lookup"><span data-stu-id="ceb42-193">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="ceb42-194">以前は、Visual Studio と .NET Core SDK は密接に連携していました (特定のバージョンの Visual Studio に特定のバージョンの SDK が付属していました)。</span><span class="sxs-lookup"><span data-stu-id="ceb42-194">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="ceb42-195">ドキュメントの改善</span><span class="sxs-lookup"><span data-stu-id="ceb42-195">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="ceb42-196">.NET アプリケーション アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ceb42-196">.NET Application Architecture</span></span>

<span data-ttu-id="ceb42-197">.NET を使用して次のものをビルドする際は、[.NET アプリケーション アーキテクチャ](https://www.microsoft.com/net/learn/architecture)にある、ガイダンス、ベスト プラクティス、サンプル アプリケーションを掲載した電子ブックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ceb42-197">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of eBooks that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- <span data-ttu-id="ceb42-198">マイクロサービスと Docker コンテナー。</span><span class="sxs-lookup"><span data-stu-id="ceb42-198">Microservices and Docker containers.</span></span>
- <span data-ttu-id="ceb42-199">ASP.NET を使用した Web アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="ceb42-199">Web applications with ASP.NET.</span></span>
- <span data-ttu-id="ceb42-200">Xamarin を使用したモバイル アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="ceb42-200">Mobile applications with Xamarin.</span></span>
- <span data-ttu-id="ceb42-201">Azure Cloud にデプロイされたアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="ceb42-201">Applications that are deployed to the Cloud with Azure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ceb42-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceb42-202">See also</span></span>
 [<span data-ttu-id="ceb42-203">ASP.NET Core 2.0 の新機能</span><span class="sxs-lookup"><span data-stu-id="ceb42-203">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)

