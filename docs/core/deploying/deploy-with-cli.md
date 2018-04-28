---
title: CLI ツールで .NET Core アプリを展開する
description: コマンド ライン インターフェイス (CLI) ツールを使用して .NET Core アプリを展開する方法を説明します。
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 21e824e6092b0d30e0499ff05c5471a291c8d269
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="b9572-103">コマンド ライン インターフェイス (CLI) ツールを使用して .NET Core アプリを展開する</span><span class="sxs-lookup"><span data-stu-id="b9572-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="b9572-104">.NET Core アプリケーションは、アプリケーション バイナリは含むが対象のシステムに .NET Core バイナリが存在することに依存する*フレームワークに依存する展開*か、アプリケーションと .NET Core のバイナリの両方を含む*自己完結型の配置*のいずれかで展開できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="b9572-105">概要については、「[.NET Core アプリケーション展開](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9572-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="b9572-106">以降のセクションでは、次のような展開を作成するために [.NET Core コマンド ライン インターフェイス ツール](../tools/index.md)を使用する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b9572-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="b9572-107">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="b9572-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="b9572-108">サードパーティの依存関係を含む、フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="b9572-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="b9572-109">自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="b9572-109">Self-contained deployment</span></span>
- <span data-ttu-id="b9572-110">サードパーティの依存関係を含む、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="b9572-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="b9572-111">コマンド ラインを使用する場合は、任意のプログラム エディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="b9572-112">プログラム エディターが [Visual Studio Code](https://code.visualstudio.com) の場合、**[表示]** > **[統合ターミナル]** を選択して、Visual Studio Code 環境内にコマンド コンソールを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="b9572-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="b9572-113">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="b9572-113">Framework-dependent deployment</span></span>

<span data-ttu-id="b9572-114">サードパーティの依存関係を含まない、フレームワークに依存する展開を展開するプロセスには、アプリのビルド、テスト、および発行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9572-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="b9572-115">C# で記述された次の単純な例は、このプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="b9572-115">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="b9572-116">プロジェクトのディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-116">Create a project directory.</span></span>

   <span data-ttu-id="b9572-117">プロジェクトのディレクトリを作成し、それを現在のディレクトリにします。</span><span class="sxs-lookup"><span data-stu-id="b9572-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="b9572-118">プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-118">Create the project.</span></span>

   <span data-ttu-id="b9572-119">コマンド ラインに [dotnet new console](../tools/dotnet-new.md) と入力して、そのディレクトリに新しい C# コンソール プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="b9572-120">アプリケーションのソース コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9572-120">Add the application's source code.</span></span>

   <span data-ttu-id="b9572-121">エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b9572-121">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="b9572-122">テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9572-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="b9572-123">正規表現 `\w+` を使用して、入力テキストの単語を分離します。</span><span class="sxs-lookup"><span data-stu-id="b9572-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="b9572-124">プロジェクトの依存関係とツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="b9572-124">Update the project's dependencies and tools.</span></span>
 
   <span data-ttu-id="b9572-125">[dotnet restore](../tools/dotnet-restore.md) コマンドを実行して、プロジェクトで指定された依存関係を復元します ([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="b9572-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="b9572-126">アプリのデバッグ ビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="b9572-127">[dotnet build](../tools/dotnet-build.md) コマンドを使用すると、アプリケーションをビルドでき、[dotnet run](../tools/dotnet-run.md) コマンドを使用すると、それをビルドして実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="b9572-128">アプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="b9572-128">Deploy your app.</span></span>

   <span data-ttu-id="b9572-129">プログラムをテストし、デバッグした後は、次のコマンドを使用して、展開を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="b9572-130">これにより、リリース (デバッグではなく) バージョンのアプリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b9572-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="b9572-131">作成されたファイルは、プロジェクトの *bin* ディレクトリのサブディレクトリ内にある *publish* という名前のディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="b9572-131">The resulting files are placed in a directory named *publish* that's in a subdirectory of your project's *bin* directory.</span></span>

<span data-ttu-id="b9572-132">アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="b9572-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b9572-133">このファイルは、主に例外のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b9572-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b9572-134">これは、アプリケーションのファイルと一緒には配布しないよう選択できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="b9572-135">ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b9572-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b9572-136">アプリケーション ファイルの完全なセットは、任意の方法で展開できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="b9572-137">たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="b9572-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="b9572-138">一度インストールすると、ユーザーは `dotnet` コマンドを使用して、`dotnet fdd.dll` などのアプリケーションのファイル名を入力してアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-138">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="b9572-139">また、アプリケーション インストールの一環として、インストーラーはアプリケーション バイナリに加えて、共有フレームワーク インストーラーをバンドルするか、または前提条件として共有フレームワークがあるか確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9572-139">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="b9572-140">共有フレームワークをインストールするには、管理者またはルートの権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9572-140">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="b9572-141">サードパーティの依存関係を含む、フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="b9572-141">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="b9572-142">1 つ以上のサードパーティの依存関係を備えたフレームワークに依存する展開を展開するには、それらの依存関係がプロジェクトで使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9572-142">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="b9572-143">`dotnet restore` コマンドを実行する前に、次の 2 つの追加手順を実行する必要があります([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="b9572-143">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="b9572-144">*csproj* ファイルの `<ItemGroup>` セクションに、必要なサードパーティ ライブラリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="b9572-144">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="b9572-145">次の `<ItemGroup>` セクションには、サードパーティ ライブラリとして [Json.NET](http://www.newtonsoft.com/json) への依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="b9572-145">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="b9572-146">サードパーティの依存関係を含む NuGet パッケージをまだダウンロードしていない場合は、ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b9572-146">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="b9572-147">パッケージをダウンロードするには、依存関係を追加した後で `dotnet restore` コマンドを実行します ([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="b9572-147">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="b9572-148">発行時に依存関係はローカルの NuGet キャッシュからが解決されるので、システムで使用可能になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9572-148">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="b9572-149">サードパーティの依存関係を含む、フレームワークに依存する展開は、サードパーティの依存関係と同じ移植性を持つことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9572-149">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="b9572-150">たとえば、サードパーティ ライブラリが macOS のみをサポートする場合、そのアプリを Windows システムに移植することはできません。</span><span class="sxs-lookup"><span data-stu-id="b9572-150">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="b9572-151">この状況は、サードパーティの依存関係自体がネイティブ コードに依存する場合に生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9572-151">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="b9572-152">このよい例は、[libuv](https://github.com/libuv/libuv) に対してネイティブの依存関係が必要な [Kestrel サーバー](/aspnet/core/fundamentals/servers/kestrel)です。</span><span class="sxs-lookup"><span data-stu-id="b9572-152">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="b9572-153">このようなサードパーティの依存関係を含むアプリケーションに対して FDD が作成されると、発行された出力には、ネイティブの依存関係がサポートする (そして、その NuGet パッケージ内に存在する) 各[ランタイム識別子 (RID)](../rid-catalog.md) のフォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9572-153">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="b9572-154">サードパーティの依存関係を含まない、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="b9572-154">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="b9572-155">サードパーティの依存関係を含まない自己完結型の展開を展開するプロセスには、プロジェクトの作成、*csproj* ファイルの変更、アプリのビルド、テスト、および発行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9572-155">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="b9572-156">C# で記述された次の単純な例は、このプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="b9572-156">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="b9572-157">この例では、コマンド ラインから [dotnet ユーティリティ](../tools/dotnet.md)を使用して、自己完結型の展開を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9572-157">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="b9572-158">プロジェクトのディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-158">Create a directory for the project.</span></span>

   <span data-ttu-id="b9572-159">プロジェクトのディレクトリを作成し、それを現在のディレクトリにします。</span><span class="sxs-lookup"><span data-stu-id="b9572-159">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="b9572-160">プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-160">Create the project.</span></span>

   <span data-ttu-id="b9572-161">コマンド ラインに [dotnet new console](../tools/dotnet-new.md) と入力して、そのディレクトリに新しい C# コンソール プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-161">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="b9572-162">アプリケーションのソース コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9572-162">Add the application's source code.</span></span>

   <span data-ttu-id="b9572-163">エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b9572-163">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="b9572-164">テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9572-164">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="b9572-165">正規表現 `\w+` を使用して、入力テキストの単語を分離します。</span><span class="sxs-lookup"><span data-stu-id="b9572-165">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="b9572-166">アプリの対象プラットフォームを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9572-166">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="b9572-167">*csproj* ファイルで、アプリが対象とするプラットフォームを定義する `<RuntimeIdentifiers>` タグを `<PropertyGroup>` セクションに作成し、対象とする各プラットフォームのランタイム識別子 (RID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9572-167">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="b9572-168">なお、RID の分離にはセミコロンを追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9572-168">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="b9572-169">ランタイム識別子の一覧については、「[Runtime IDentifier catalog](../rid-catalog.md)」 (ランタイム識別子のカタログ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9572-169">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="b9572-170">たとえば、次の `<PropertyGroup>` セクションは、アプリが 64 ビット Windows 10 オペレーティング システムおよび 64 ビット OS X バージョン 10.11 オペレーティング システムで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="b9572-170">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="b9572-171">`<RuntimeIdentifiers>` 要素は、*csproj* ファイルの任意の `<PropertyGroup>` に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b9572-171">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="b9572-172">*csproj* ファイルの完全なサンプルは、このセクションの後の部分で示しています。</span><span class="sxs-lookup"><span data-stu-id="b9572-172">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="b9572-173">プロジェクトの依存関係とツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="b9572-173">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="b9572-174">[dotnet restore](../tools/dotnet-restore.md) コマンドを実行して、プロジェクトで指定された依存関係を復元します ([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="b9572-174">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="b9572-175">アプリのデバッグ ビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-175">Create a Debug build of your app.</span></span>

   <span data-ttu-id="b9572-176">コマンド ラインから、[dotnet build](../tools/dotnet-build.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9572-176">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="b9572-177">プログラムをデバッグしてテストしたら、アプリと共に展開するファイルをアプリの対象のプラットフォームごとに作成します。</span><span class="sxs-lookup"><span data-stu-id="b9572-177">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="b9572-178">両方の対象プラットフォームに、次のように `dotnet publish` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9572-178">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="b9572-179">これにより、各ターゲット プラットフォームに対してアプリのリリース (デバッグではなく) バージョンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b9572-179">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="b9572-180">作成されたファイルは、プロジェクトの *.\bin\Release\netcoreapp1.1\<runtime_identifier>* サブディレクトリにある *publish* という名前のサブディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="b9572-180">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="b9572-181">各サブディレクトリには、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9572-181">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="b9572-182">アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="b9572-182">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b9572-183">このファイルは、主に例外のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b9572-183">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b9572-184">これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-184">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="b9572-185">ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b9572-185">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b9572-186">発行したファイルは、任意の方法で展開できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-186">Deploy the published files in any way you like.</span></span> <span data-ttu-id="b9572-187">たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="b9572-187">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="b9572-188">このプロジェクトの完全な *csproj* ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9572-188">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="b9572-189">サードパーティの依存関係を含む、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="b9572-189">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="b9572-190">1 つまたは複数のサードパーティの依存関係を含む自己完結型の展開を展開するプロセスには、依存関係の追加が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9572-190">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="b9572-191">`dotnet restore` コマンドを実行する前に、次の 2 つの追加手順を実行する必要があります([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="b9572-191">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="b9572-192">任意のサードパーティ ライブラリへの参照を *csproj* ファイルの `<ItemGroup>` セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="b9572-192">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="b9572-193">次の `<ItemGroup>` セクションは、サードパーティ ライブラリとして Json.NET を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9572-193">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="b9572-194">サードパーティの依存関係を含む NuGet パッケージをシステムにまだダウンロードしていない場合は、ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b9572-194">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="b9572-195">依存関係をアプリで使用できるようにするには、依存関係を追加してから、`dotnet restore` コマンドを実行します ([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="b9572-195">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="b9572-196">発行時に依存関係はローカルの NuGet キャッシュからが解決されるので、システムで使用可能になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9572-196">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="b9572-197">このプロジェクトの完全な *csproj* ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b9572-197">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="b9572-198">アプリケーションを展開すると、アプリで使用されるすべてのサードパーティの依存関係も、アプリケーション ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9572-198">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="b9572-199">アプリが実行されているシステムには、サードパーティ ライブラリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b9572-199">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="b9572-200">サードパーティ ライブラリを含む自己完結型の展開は、そのライブラリでサポートされるプラットフォームにのみ展開できます。</span><span class="sxs-lookup"><span data-stu-id="b9572-200">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="b9572-201">これは、フレームワークに依存する展開にサード パーティの依存関係とネイティブの依存関係があり、ネイティブの依存関係はアプリがインストールされたプラットフォームと対応している必要がある場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="b9572-201">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a><span data-ttu-id="b9572-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9572-202">See also</span></span>

<span data-ttu-id="b9572-203">[.NET Core アプリケーションの展開](index.md) </span><span class="sxs-lookup"><span data-stu-id="b9572-203">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="b9572-204">.NET Core のランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="b9572-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   

