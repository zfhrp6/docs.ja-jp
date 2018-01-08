---
title: "CLI を使用する .NET Core に関する概要"
description: "Windows、Linux、または macOS の .NET Core での、.NET Core コマンド ライン インターフェイス (CLI) の使用方法を段階的に説明するチュートリアル。"
keywords: .NET Core, CLI
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
ms.workload: dotnetcore
ms.openlocfilehash: 544274783e8a77f55c8ec7e1da0069bf8bdf7b0b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="a03b2-104">Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要</span><span class="sxs-lookup"><span data-stu-id="a03b2-104">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="a03b2-105">このトピックでは、.NET Core CLI ツールを利用し、自分のコンピューターでプラットフォームに依存しないアプリを開発する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-105">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="a03b2-106">.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../tools/index.md)」(.NET Core SDK の概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a03b2-106">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a03b2-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a03b2-107">Prerequisites</span></span>

- <span data-ttu-id="a03b2-108">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="a03b2-108">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="a03b2-109">ユーザーが選んだテキスト エディターまたはコード エディター。</span><span class="sxs-lookup"><span data-stu-id="a03b2-109">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="a03b2-110">Hello コンソール アプリ</span><span class="sxs-lookup"><span data-stu-id="a03b2-110">Hello, Console App!</span></span>

<span data-ttu-id="a03b2-111">GitHub の dotnet/docs レポジトリから、[サンプル コードを表示またはダウンロード](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild)することができます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-111">You can [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild) from the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="a03b2-112">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a03b2-112">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="a03b2-113">コマンド プロンプトを開き、*Hello* という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-113">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="a03b2-114">作成したフォルダーに移動して、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-114">Navigate to the folder you created and type the following:</span></span>

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="a03b2-115">簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-115">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="a03b2-116">[`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の `Hello.csproj` プロジェクト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-116">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="a03b2-117">また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-117">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="a03b2-118">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="a03b2-118">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   <span data-ttu-id="a03b2-119">プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-119">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="a03b2-120">`OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-120">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="a03b2-121">`TargetFramework` タグは、対象の .NET 実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-121">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="a03b2-122">高度なシナリオでは、複数の対象フレームワークを指定し、1 回の操作でそれらすべてにビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-122">In an advance scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="a03b2-123">このチュートリアルでは、.NET Core 1.0 の場合のビルドについてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-123">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="a03b2-124">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="a03b2-124">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   <span data-ttu-id="a03b2-125">プログラムは `using System` で始まります。これは、"`System` 名前空間のすべてがこのファイルのスコープになる" こと意味します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-125">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="a03b2-126">`System` 名前空間には、`string` などの基本的な構造、または数値型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-126">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="a03b2-127">次に、`Hello` という名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-127">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="a03b2-128">これを必要なものに変更できます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-128">You can change this to anything you want.</span></span> <span data-ttu-id="a03b2-129">`Program` という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-129">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="a03b2-130">この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-130">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="a03b2-131">実際は、この配列は使用されません。プログラムはコンソールに "Hello World!" と</span><span class="sxs-lookup"><span data-stu-id="a03b2-131">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="a03b2-132">記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="a03b2-132">to the console.</span></span> <span data-ttu-id="a03b2-133">後に、この引数を利用するようにコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-133">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="a03b2-134">[`dotnet restore`](../tools/dotnet-restore.md) は、[NuGet](https://www.nuget.org/) (.NET パッケージ マネージャー) を参照して依存関係のツリーを復元します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-134">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="a03b2-135">NuGet は、*Hello.csproj* ファイルを分析し、ファイルに記載されている依存関係をダウンロードして (またはコンピューターのキャッシュから取得して)、*obj/project.assets.json* ファイルを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="a03b2-136">*project.assets.json* ファイルをコンパイルして実行できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a03b2-136">The *project.assets.json* file is necessary to be able to compile and run.</span></span>
   
   <span data-ttu-id="a03b2-137">*project.assets.json* ファイルは、NuGet の依存関係およびアプリについて記述するその他の情報のグラフの永続的で完全なセットです。</span><span class="sxs-lookup"><span data-stu-id="a03b2-137">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="a03b2-138">このファイルは、[`dotnet build`](../tools/dotnet-build.md) や [`dotnet run`](../tools/dotnet-run.md) などの他のツールによって読み取られ、これらのツールが NuGet の依存関係とバインド解決の正しいセットでソース コードを処理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a03b2-138">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="a03b2-139">[`dotnet run`](../tools/dotnet-run.md) は、[`dotnet build`](../tools/dotnet-build.md) を呼び出してビルド ターゲットがビルドされていることを確認した後、`dotnet <assembly.dll>` を呼び出してターゲット アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-139">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
   
    ```
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="a03b2-140">[`dotnet build`](../tools/dotnet-build.md) を実行し、ビルド コンソール アプリケーションを実行しないでコードをコンパイルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-140">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="a03b2-141">これで、Windows で `dotnet bin\Debug\netcoreapp1.0\Hello.dll` を使用して (Windows 以外のシステムの場合は `/` を使用して) 実行できる DLL ファイルとしてアプリケーションがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-141">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="a03b2-142">アプリケーションには引数を指定することもできます。それについてはこのトピックの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-142">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="a03b2-143">高度なシナリオでは、展開可能なプラットフォーム固有のファイルの自己完結型セットとしてアプリケーションをビルドし、.NET Core が必ずしもインストールされているとは限らないコンピューターに対して実行することができます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-143">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="a03b2-144">詳細については、「[.NET Core アプリケーション展開](../deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a03b2-144">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="a03b2-145">プログラムの拡張</span><span class="sxs-lookup"><span data-stu-id="a03b2-145">Augmenting the program</span></span>

<span data-ttu-id="a03b2-146">プログラムを少し変更してみましょう。</span><span class="sxs-lookup"><span data-stu-id="a03b2-146">Let's change the program a bit.</span></span> <span data-ttu-id="a03b2-147">フィボナッチ数は面白いです。アプリを実行した人に挨拶をする引数を使用するためにフィボナッチ数も追加しましょう。</span><span class="sxs-lookup"><span data-stu-id="a03b2-147">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="a03b2-148">*Program.cs* ファイルの内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-148">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. <span data-ttu-id="a03b2-149">[`dotnet build`](../tools/dotnet-build.md) を実行し、変更内容をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="a03b2-149">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="a03b2-150">アプリにパラメーターを渡すプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-150">Run the program passing a parameter to the app:</span></span>

   ```
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

<span data-ttu-id="a03b2-151">以上です。</span><span class="sxs-lookup"><span data-stu-id="a03b2-151">And that's it!</span></span>  <span data-ttu-id="a03b2-152">自由に `Program.cs` を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-152">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="a03b2-153">複数のファイルの操作</span><span class="sxs-lookup"><span data-stu-id="a03b2-153">Working with multiple files</span></span>

<span data-ttu-id="a03b2-154">単純な 1 回だけのプログラムには 1 つのファイルで十分ですが、より複雑なアプリを開発する場合、プロジェクトに複数のソース ファイルを用意する必要があるでしょう。先のフィボナッチのサンプルから作成してみましょう。いくつかのフィボナッチ値をキャッシュしてから、再帰機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-154">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span> 

1. <span data-ttu-id="a03b2-155">次のコードを利用し、*FibonacciGenerator.cs* という名前の *Hello* ディレクトリ内に新しいファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-155">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. <span data-ttu-id="a03b2-156">*Program.cs* ファイルの `Main` メソッドを変更し、次の例のように新しいクラスをインスタンス化し、そのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-156">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="a03b2-157">[`dotnet build`](../tools/dotnet-build.md) を実行し、変更内容をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="a03b2-157">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="a03b2-158">[`dotnet run`](../tools/dotnet-run.md) を実行し、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a03b2-158">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="a03b2-159">プログラムの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a03b2-159">The following shows the program output:</span></span>

   ```
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

<span data-ttu-id="a03b2-160">以上です。</span><span class="sxs-lookup"><span data-stu-id="a03b2-160">And that's it!</span></span> <span data-ttu-id="a03b2-161">これで、ここで学習した基本的な概念を利用し、自分だけのプログラムを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-161">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="a03b2-162">このチュートリアルで紹介した、アプリケーションを実行するコマンドと手順は、開発時にのみ利用されます。</span><span class="sxs-lookup"><span data-stu-id="a03b2-162">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="a03b2-163">アプリの展開に進むときは、.NET Core アプリの別の[展開方法](../deploying/index.md)や [`dotnet publish`](../tools/dotnet-publish.md) コマンドを利用した方が効果的な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a03b2-163">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="a03b2-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="a03b2-164">See also</span></span>

[<span data-ttu-id="a03b2-165">.NET Core CLI ツールを使用したプロジェクトの整理およびテスト</span><span class="sxs-lookup"><span data-stu-id="a03b2-165">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
