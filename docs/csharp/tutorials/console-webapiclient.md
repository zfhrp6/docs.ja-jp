---
title: .NET Core を使用した REST クライアントの作成
description: このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 8cca71b9b8e09fd26f80d53618a3f1e278e28390
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="rest-client"></a><span data-ttu-id="37aac-104">REST クライアント</span><span class="sxs-lookup"><span data-stu-id="37aac-104">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="37aac-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="37aac-105">Introduction</span></span>
<span data-ttu-id="37aac-106">このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。</span><span class="sxs-lookup"><span data-stu-id="37aac-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="37aac-107">内容は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37aac-107">You’ll learn:</span></span>
*   <span data-ttu-id="37aac-108">.NET Core コマンド ライン インターフェイス (CLI) の基本</span><span class="sxs-lookup"><span data-stu-id="37aac-108">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="37aac-109">C# 言語機能の概要</span><span class="sxs-lookup"><span data-stu-id="37aac-109">An overview of C# Language features.</span></span>
*   <span data-ttu-id="37aac-110">NuGet での依存関係の管理</span><span class="sxs-lookup"><span data-stu-id="37aac-110">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="37aac-111">HTTP 通信</span><span class="sxs-lookup"><span data-stu-id="37aac-111">HTTP Communications</span></span>
*   <span data-ttu-id="37aac-112">JSON 情報の処理</span><span class="sxs-lookup"><span data-stu-id="37aac-112">Processing JSON information</span></span>
*   <span data-ttu-id="37aac-113">属性を使用した構成の管理</span><span class="sxs-lookup"><span data-stu-id="37aac-113">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="37aac-114">GitHub 上の REST サービスに対して HTTP 要求を発行するアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="37aac-114">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="37aac-115">JSON 形式で情報を読み取り、その JSON パケットを C# オブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="37aac-115">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="37aac-116">最後に、C# オブジェクトを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37aac-116">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="37aac-117">このチュートリアルには、多くの機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37aac-117">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="37aac-118">それらを 1 つずつビルドしてみましょう。</span><span class="sxs-lookup"><span data-stu-id="37aac-118">Let’s build them one by one.</span></span>

<span data-ttu-id="37aac-119">このトピックの[最終的なサンプル](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)も参照したい方は、ダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="37aac-119">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="37aac-120">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37aac-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="37aac-121">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="37aac-121">Prerequisites</span></span>
<span data-ttu-id="37aac-122">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-122">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="37aac-123">インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37aac-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="37aac-124">このアプリケーションは、Windows、Linux、macOS または Docker コンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="37aac-124">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="37aac-125">お好みのコード エディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="37aac-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="37aac-126">次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="37aac-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="37aac-127">しかし、他の使い慣れたツールを使用しても構いません。</span><span class="sxs-lookup"><span data-stu-id="37aac-127">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="37aac-128">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="37aac-128">Create the Application</span></span>
<span data-ttu-id="37aac-129">最初に新しいアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="37aac-129">The first step is to create a new application.</span></span> <span data-ttu-id="37aac-130">コマンド プロンプトを開き、アプリケーション用の新しいディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="37aac-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="37aac-131">それを、現在のディレクトリとしてください。</span><span class="sxs-lookup"><span data-stu-id="37aac-131">Make that the current directory.</span></span> <span data-ttu-id="37aac-132">コマンド プロンプトで `dotnet new console` のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="37aac-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="37aac-133">これで、基本的な "Hello World" アプリケーションのスターター ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="37aac-134">変更を加える前に、このシンプルな Hello World アプリケーションを実行する手順を見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="37aac-134">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="37aac-135">アプリケーション作成後、コマンド プロンプトで「`dotnet restore`」 ([注記を参照](#dotnet-restore-note)) と入力します。</span><span class="sxs-lookup"><span data-stu-id="37aac-135">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="37aac-136">このコマンドにより、NuGet パッケージの復元処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-136">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="37aac-137">NuGet は .NET パッケージ マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="37aac-137">NuGet is a .NET package manager.</span></span> <span data-ttu-id="37aac-138">このコマンドにより、プロジェクトの依存関係のうち欠落しているものがすべてダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="37aac-138">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="37aac-139">これは新しいプロジェクトなので、依存関係は何もなく、最初の実行で .NET Core フレームワークがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="37aac-139">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="37aac-140">この最初の手順の後は、新しい依存パッケージを追加するときに `dotnet restore` ([注記を参照](#dotnet-restore-note)) を実行するか、依存関係のいずれかのバージョンを更新する必要があるだけです。</span><span class="sxs-lookup"><span data-stu-id="37aac-140">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="37aac-141">パッケージを復元したら、`dotnet build` を実行します。</span><span class="sxs-lookup"><span data-stu-id="37aac-141">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="37aac-142">これにより、ビルド エンジンが実行され、アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-142">This executes the build engine and creates your application.</span></span> <span data-ttu-id="37aac-143">最後に、`dotnet run` を実行してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="37aac-143">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="37aac-144">新しい依存関係を追加する</span><span class="sxs-lookup"><span data-stu-id="37aac-144">Adding New Dependencies</span></span>
<span data-ttu-id="37aac-145">.NET Core の重要な設計目標の 1 つは、.NET Framework のインストール サイズを最小限に抑えることです。</span><span class="sxs-lookup"><span data-stu-id="37aac-145">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="37aac-146">.NET Core アプリケーション フレームワークには、.NET Framework の最も一般的な要素だけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37aac-146">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="37aac-147">その一部の機能のための追加ライブラリがアプリケーションで必要な場合は、C# プロジェクト (\*.csproj) ファイルにそれらの依存関係を追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-147">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="37aac-148">ここで示す例の場合は、`System.Runtime.Serialization.Json` パッケージを追加して、アプリケーションが JSON 応答を処理できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-148">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="37aac-149">`csproj` プロジェクト ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="37aac-149">Open your `csproj` project file.</span></span> <span data-ttu-id="37aac-150">ファイルの最初の行は次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-150">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="37aac-151">この行の直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-151">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="37aac-152">ほとんどのコード エディターでは、これらのライブラリの複数のバージョンの入力候補が表示されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-152">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="37aac-153">通常は、追加するパッケージの最新バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="37aac-153">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="37aac-154">ただし、すべてのパッケージのバージョンが一致しており、.NET Core アプリケーション フレームワークのバージョンとも一致していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="37aac-154">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="37aac-155">これらの変更を加えた後で、`dotnet restore` ([注記を参照](#dotnet-restore-note)) をもう一度実行して、システムにパッケージがインストールされるようにします。</span><span class="sxs-lookup"><span data-stu-id="37aac-155">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="37aac-156">Web 要求を作成する</span><span class="sxs-lookup"><span data-stu-id="37aac-156">Making Web Requests</span></span>
<span data-ttu-id="37aac-157">Web サイトからデータの取得を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="37aac-157">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="37aac-158">このアプリケーションでは、[GitHub API](https://developer.github.com/v3/) から情報を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="37aac-158">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="37aac-159">[.NET Foundation](http://www.dotnetfoundation.org/) にあるプロジェクトに関する情報を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="37aac-159">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="37aac-160">最初に、プロジェクトに関する情報を取得する GitHub API に対する要求を作成します。</span><span class="sxs-lookup"><span data-stu-id="37aac-160">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="37aac-161">使用するエンドポイントは [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos) です。</span><span class="sxs-lookup"><span data-stu-id="37aac-161">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="37aac-162">HTTP GET 要求を使用して、これらのプロジェクトに関する情報をすべて取得します。</span><span class="sxs-lookup"><span data-stu-id="37aac-162">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="37aac-163">HTTP GET 要求はブラウザーでも使用されるので、ブラウザーに URL を貼り付けて、取得および処理する情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="37aac-163">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="37aac-164"><xref:System.Net.Http.HttpClient> クラスを使用して Web 要求を作成します。</span><span class="sxs-lookup"><span data-stu-id="37aac-164">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="37aac-165">最新のすべての .NET API と同様に、<xref:System.Net.Http.HttpClient> は実行時間の長い API の非同期メソッドだけをサポートします。</span><span class="sxs-lookup"><span data-stu-id="37aac-165">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="37aac-166">最初に非同期メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="37aac-166">Start by making an async method.</span></span> <span data-ttu-id="37aac-167">アプリケーションの機能をビルドする際に実装を記述します。</span><span class="sxs-lookup"><span data-stu-id="37aac-167">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="37aac-168">最初に、プロジェクト ディレクトリ内の `program.cs` ファイルを開き、`Program` クラスに次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-168">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="37aac-169">`Main` メソッドの先頭に `using` ステートメントを追加して、C# コンパイラに <xref:System.Threading.Tasks.Task> 型を認識させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-169">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="37aac-170">この時点でプロジェクトをビルドすると、このメソッドに対して警告が生成されます。これは、`await` 演算子がメソッドに含まれておらず、メソッドが同期的に実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="37aac-170">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="37aac-171">現時点ではこの警告を無視してください。`await` 演算子は、メソッドを記述する際に追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-171">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="37aac-172">次に、`namespace` ステートメントに定義されている名前空間の名前を、既定値の `ConsoleApp` から `WebAPIClient` に変更します。</span><span class="sxs-lookup"><span data-stu-id="37aac-172">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="37aac-173">後から、この名前空間で `repo` クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="37aac-173">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="37aac-174">次に、`Main` メソッドを更新してこのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="37aac-174">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="37aac-175">`ProcessRepositories` メソッドはタスクを返します。そのタスクが完了する前にプログラムを終了しないでください。</span><span class="sxs-lookup"><span data-stu-id="37aac-175">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="37aac-176">そのため、`Wait` メソッドを使用してブロックし、タスクの完了を待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-176">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="37aac-177">これで、何も実行せず、非同期的に実行されるプログラムの準備ができました。</span><span class="sxs-lookup"><span data-stu-id="37aac-177">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="37aac-178">これを改善しましょう。</span><span class="sxs-lookup"><span data-stu-id="37aac-178">Let's improve it.</span></span>

<span data-ttu-id="37aac-179">まず、Web からデータを取得できるオブジェクトが必要です。この条件に合うものとして、<xref:System.Net.Http.HttpClient> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="37aac-179">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="37aac-180">このオブジェクトは要求と応答を処理します。</span><span class="sxs-lookup"><span data-stu-id="37aac-180">This object handles the request and the responses.</span></span> <span data-ttu-id="37aac-181">Program.cs ファイル内の `Program` クラスで該当する型の単一のインスタンスをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="37aac-181">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

 <span data-ttu-id="37aac-182">`ProcessRepositories` メソッドに戻って、最初のバージョンのプログラムを記述します。</span><span class="sxs-lookup"><span data-stu-id="37aac-182">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="37aac-183">また、ファイルの先頭に 2 つの新しい using ステートメントを追加して、プログラムをコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-183">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="37aac-184">この最初のバージョンでは、.NET Foundation にあるすべてのリポジトリのリストを読み取る Web 要求を作成します </span><span class="sxs-lookup"><span data-stu-id="37aac-184">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="37aac-185">(.NET Foundation の gitHub ID は "dotnet" です)。</span><span class="sxs-lookup"><span data-stu-id="37aac-185">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="37aac-186">最初の数行では、この要求の <xref:System.Net.Http.HttpClient> を設定します。</span><span class="sxs-lookup"><span data-stu-id="37aac-186">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="37aac-187">最初は、GitHub の JSON 応答を受け入れるように構成されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-187">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="37aac-188">この形式は単なる JSON です。</span><span class="sxs-lookup"><span data-stu-id="37aac-188">This format is simply JSON.</span></span> <span data-ttu-id="37aac-189">次の行では、このオブジェクトからのすべての要求にユーザー エージェント ヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-189">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="37aac-190">これらの 2 つのヘッダーは、GitHub サーバー コードによってチェックされ、GitHub から情報を取得するために必要です。</span><span class="sxs-lookup"><span data-stu-id="37aac-190">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="37aac-191"><xref:System.Net.Http.HttpClient> を構成したら、Web 要求を作成して応答を取得します。</span><span class="sxs-lookup"><span data-stu-id="37aac-191">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="37aac-192">この最初のバージョンでは、<xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 簡易メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="37aac-192">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="37aac-193">この簡易メソッドは、Web 要求を作成するタスクを開始し、要求が返されると応答ストリームを読み取って、ストリームからコンテンツを抽出します。</span><span class="sxs-lookup"><span data-stu-id="37aac-193">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="37aac-194">応答の本文は <xref:System.String> として返されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-194">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="37aac-195">この文字列は、タスクが完了すると使用できます。</span><span class="sxs-lookup"><span data-stu-id="37aac-195">The string is available when the task completes.</span></span> 

<span data-ttu-id="37aac-196">このメソッドの最後の 2 行は、そのタスクを待機し、コンソールに応答を出力します。</span><span class="sxs-lookup"><span data-stu-id="37aac-196">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="37aac-197">アプリケーションをビルドして実行してください。</span><span class="sxs-lookup"><span data-stu-id="37aac-197">Build the app, and run it.</span></span> <span data-ttu-id="37aac-198">`ProcessRepositories` に `await` 演算子が含まれているため、ビルドの警告が表示されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="37aac-198">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="37aac-199">JSON 形式の長いテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-199">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="37aac-200">JSON の結果を処理する</span><span class="sxs-lookup"><span data-stu-id="37aac-200">Processing the JSON Result</span></span>

<span data-ttu-id="37aac-201">この時点では、Web サーバーからの応答を取得し、その応答に含まれているテキストを表示するコードの記述が完了しています。</span><span class="sxs-lookup"><span data-stu-id="37aac-201">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="37aac-202">次に、JSON 応答を C# オブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="37aac-202">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="37aac-203">JSON シリアライザーは、JSON データを C# オブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="37aac-203">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="37aac-204">最初のタスクでは、この応答から使用する情報を格納する C# クラスの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="37aac-204">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="37aac-205">最初に、リポジトリの名前を含むシンプルな C# 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="37aac-205">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
``` 

<span data-ttu-id="37aac-206">"repo.cs" という新しいファイルに上記のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="37aac-206">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="37aac-207">このバージョンのクラスは、JSON データを処理する最もシンプルなパスを表します。</span><span class="sxs-lookup"><span data-stu-id="37aac-207">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="37aac-208">クラス名とメンバー名は、C# の規約に従うのではなく、JSON パケットで使用される名前に一致します。</span><span class="sxs-lookup"><span data-stu-id="37aac-208">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="37aac-209">後でいくつかの構成属性を指定して、これを修正します。</span><span class="sxs-lookup"><span data-stu-id="37aac-209">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="37aac-210">このクラスは、JSON のシリアル化と逆シリアル化のもう 1 つの重要な機能を示します。JSON パケット内のすべてのフィールドがこのクラスに含まれているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="37aac-210">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="37aac-211">JSON シリアライザーは、使用されているクラス型に含まれていない情報を無視します。</span><span class="sxs-lookup"><span data-stu-id="37aac-211">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="37aac-212">この機能により、JSON パケット内のフィールドのサブセットのみを操作する型を容易に作成できます。</span><span class="sxs-lookup"><span data-stu-id="37aac-212">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="37aac-213">型の作成が完了したら、逆シリアル化を実行します。</span><span class="sxs-lookup"><span data-stu-id="37aac-213">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="37aac-214"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> オブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-214">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="37aac-215">このオブジェクトは、取得する JSON パケットで必要な CLR 型を認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-215">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="37aac-216">GitHub からのパケットには一連のリポジトリが含まれているため、正しい型は `List<repo>` です。</span><span class="sxs-lookup"><span data-stu-id="37aac-216">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="37aac-217">次の行を `ProcessRepositories` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-217">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="37aac-218">2 つの新しい名前空間を使用しているため、次の行も追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-218">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="37aac-219">次に、シリアライザーを使用して、JSON を C# オブジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="37aac-219">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="37aac-220">`ProcessRepositories` メソッド内の <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> の呼び出しを次の 2 行に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="37aac-220">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="37aac-221"><xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> ではなく、<xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> が使用されていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="37aac-221">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="37aac-222">シリアライザーは、文字列の代わりにストリームをソースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="37aac-222">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="37aac-223">上記の 2 行目で使用されている C# 言語のいくつかの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="37aac-223">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="37aac-224"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> への引数は `await` 式です。</span><span class="sxs-lookup"><span data-stu-id="37aac-224">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="37aac-225">await 式は、コード内のほとんどの場所に表示される可能性があります (これまでは代入ステートメントの一部としてしか表示されていませんでした)。</span><span class="sxs-lookup"><span data-stu-id="37aac-225">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="37aac-226">次に、`as` 演算子がコンパイル時の型である `object` を `List<repo>` に変換します。</span><span class="sxs-lookup"><span data-stu-id="37aac-226">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="37aac-227"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> の宣言は、<xref:System.Object?displayProperty=nameWithType> 型のオブジェクトが返されることを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="37aac-227">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="37aac-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> は、構成時に指定した型 (このチュートリアルでは `List<repo>`) を返します。</span><span class="sxs-lookup"><span data-stu-id="37aac-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="37aac-229">変換が成功しなかった場合、`as` 演算子は例外をスローする代わりに `null` と評価します。</span><span class="sxs-lookup"><span data-stu-id="37aac-229">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="37aac-230">このセクションでの作業はほぼ完了です。</span><span class="sxs-lookup"><span data-stu-id="37aac-230">You're almost done with this section.</span></span> <span data-ttu-id="37aac-231">JSON を C# オブジェクトに変換したので、次は各リポジトリの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="37aac-231">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="37aac-232">次の行があるとします。</span><span class="sxs-lookup"><span data-stu-id="37aac-232">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="37aac-233">この行を次の行に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="37aac-233">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="37aac-234">アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="37aac-234">Compile and run the application.</span></span> <span data-ttu-id="37aac-235">.NET Foundation に含まれるリポジトリの名前が出力されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-235">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="37aac-236">シリアル化を制御する</span><span class="sxs-lookup"><span data-stu-id="37aac-236">Controlling Serialization</span></span>

<span data-ttu-id="37aac-237">機能を追加する前に、`repo` 型を処理して、その型が C# の標準的な規約に従うようにします。</span><span class="sxs-lookup"><span data-stu-id="37aac-237">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="37aac-238">そのためには、JSON シリアライザーの動作を制御する "*属性*" を使用して `repo` 型に注釈を設定します。</span><span class="sxs-lookup"><span data-stu-id="37aac-238">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="37aac-239">ここでは、これらの属性を使用して、JSON キー名と C# のクラスおよびメンバーの名前との間のマッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="37aac-239">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="37aac-240">使用する 2 つの属性は `DataContract` および `DataMember` です。</span><span class="sxs-lookup"><span data-stu-id="37aac-240">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="37aac-241">慣例により、すべての属性クラスはサフィックス `Attribute` で終わります。</span><span class="sxs-lookup"><span data-stu-id="37aac-241">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="37aac-242">ただし、属性の適用時にそのサフィックスを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="37aac-242">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="37aac-243">`DataContract` 属性と `DataMember` 属性は別のライブラリにあるため、C# プロジェクト ファイルにそのライブラリを依存関係として追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-243">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="37aac-244">プロジェクト ファイルの `<ItemGroup>` セクションに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-244">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="37aac-245">ファイルを保存したら、`dotnet restore` ([注記を参照](#dotnet-restore-note))を実行してこのパッケージを取得します。</span><span class="sxs-lookup"><span data-stu-id="37aac-245">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="37aac-246">次に、`repo.cs` ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="37aac-246">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="37aac-247">パスカル ケースを使用するように名前を変更し、`Repository` という名前を記述します。</span><span class="sxs-lookup"><span data-stu-id="37aac-247">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="37aac-248">この型に JSON の "repo" ノードをマップするために、クラス宣言に `DataContract` 属性を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-248">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="37aac-249">属性の `Name` プロパティを、この型にマップする JSON ノードの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="37aac-249">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="37aac-250"><xref:System.Runtime.Serialization.DataContractAttribute> は <xref:System.Runtime.Serialization> 名前空間のメンバーであるため、ファイルの先頭に適切な `using` ステートメントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-250">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="37aac-251">`repo` クラスの名前を `Repository` に変更したので、Program.cs でも同じ名前の変更を行う必要があります (一部のエディターでは名前変更のリファクタリングがサポートされているため、この変更が自動的に行われます)。</span><span class="sxs-lookup"><span data-stu-id="37aac-251">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="37aac-252">次に、<xref:System.Runtime.Serialization.DataMemberAttribute> クラスを使用して、`name` フィールドで同じ変更を行います。</span><span class="sxs-lookup"><span data-stu-id="37aac-252">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="37aac-253">repo.cs の `name` フィールドの宣言を次のように変更してください。</span><span class="sxs-lookup"><span data-stu-id="37aac-253">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="37aac-254">この変更により、program.cs で各リポジトリの名前を記述するコードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-254">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="37aac-255">`dotnet build` に続けて `dotnet run` を実行し、マッピングが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="37aac-255">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="37aac-256">前と同じ出力が表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="37aac-256">You should see the same output as before.</span></span> <span data-ttu-id="37aac-257">Web サーバーから他のプロパティを処理する前に、`Repository` クラスに対してもう 1 つの変更を行います。</span><span class="sxs-lookup"><span data-stu-id="37aac-257">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="37aac-258">`Name` メンバーはパブリックにアクセスできるフィールドです。</span><span class="sxs-lookup"><span data-stu-id="37aac-258">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="37aac-259">これはオブジェクト指向においては適切な手法でないため、このフィールドをプロパティに変更します。</span><span class="sxs-lookup"><span data-stu-id="37aac-259">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="37aac-260">プロパティの取得または設定の際に実行するコードは不要ですが、プロパティを変更すると、これらの変更を後から容易に追加できます (`Repository` クラスを使用するコードを中断する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="37aac-260">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="37aac-261">フィールド定義を削除して、"[自動実装プロパティ](../programming-guide/classes-and-structs/auto-implemented-properties.md)" に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="37aac-261">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="37aac-262">コンパイラは、`get` アクセサーと `set` アクセサーの本文および名前を格納するプライベート フィールドを生成します。</span><span class="sxs-lookup"><span data-stu-id="37aac-262">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="37aac-263">次のようなコードを手動で入力できます。</span><span class="sxs-lookup"><span data-stu-id="37aac-263">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="37aac-264">新機能を追加する前に、もう 1 つの変更を行います。</span><span class="sxs-lookup"><span data-stu-id="37aac-264">Let's make one more change before adding new features.</span></span> <span data-ttu-id="37aac-265">`ProcessRepositories` メソッドは非同期作業を行って、リポジトリのコレクションを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="37aac-265">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="37aac-266">そのメソッドから `List<Repository>` を返して、情報を記述するコードを `Main` メソッドに移動します。</span><span class="sxs-lookup"><span data-stu-id="37aac-266">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="37aac-267">結果が `Repository` オブジェクトのリストであるタスクを返すように `ProcessRepositories` のシグネチャを変更します。</span><span class="sxs-lookup"><span data-stu-id="37aac-267">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="37aac-268">続いて、JSON 応答の処理後にリポジトリを返します。</span><span class="sxs-lookup"><span data-stu-id="37aac-268">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="37aac-269">このメソッドを `async` とマークしたので、コンパイラは戻り値として `Task<T>` オブジェクトを生成します。</span><span class="sxs-lookup"><span data-stu-id="37aac-269">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="37aac-270">次に、`Main` メソッドを変更して、それらの結果をキャプチャし、各リポジトリ名をコンソールに書き込むようにします。</span><span class="sxs-lookup"><span data-stu-id="37aac-270">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="37aac-271">`Main` メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="37aac-271">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="37aac-272">Task ブロックの `Result` プロパティへのアクセスは、タスクが完了するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="37aac-272">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="37aac-273">通常、`ProcessRepositories` メソッドなどではタスクの完了に対して `await` の実行を選択しますが、`Main` メソッドでは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="37aac-273">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="37aac-274">詳細情報を確認する</span><span class="sxs-lookup"><span data-stu-id="37aac-274">Reading More Information</span></span>

<span data-ttu-id="37aac-275">最後に、GitHub API から送信される JSON パケット内のいくつかのプロパティを処理します。</span><span class="sxs-lookup"><span data-stu-id="37aac-275">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="37aac-276">すべてのプロパティを追加する必要はありませんが、いくつかのプロパティを追加することで C# 言語のさらなる機能を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="37aac-276">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="37aac-277">最初に、いくつかの単純型を `Repository` クラスの定義に追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-277">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="37aac-278">そのクラスに次のプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-278">Add these properties to that class:</span></span>

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="37aac-279">これらのプロパティには、(JSON パケットに格納されている) 文字列型からターゲット型への組み込みの変換があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-279">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="37aac-280"><xref:System.Uri> 型はおそらく初めて使用する型でしょう。</span><span class="sxs-lookup"><span data-stu-id="37aac-280">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="37aac-281">これは URI (ここでは URL) を表します。</span><span class="sxs-lookup"><span data-stu-id="37aac-281">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="37aac-282">`Uri` 型と `int` 型では、ターゲット型に変換しないデータが JSON パケットに含まれている場合、シリアル化アクションで例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="37aac-282">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="37aac-283">プロパティの追加が完了したら、それらの要素を表示するように `Main` メソッドを更新してください。</span><span class="sxs-lookup"><span data-stu-id="37aac-283">Once you've added these, update the `Main` method to display those elements:</span></span>

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```
<span data-ttu-id="37aac-284">最後の手順として、最後のプッシュ操作に関する情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-284">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="37aac-285">この情報は、JSON 応答では次のように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="37aac-285">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="37aac-286">この形式は .NET の標準の <xref:System.DateTime> 形式に従っていません。</span><span class="sxs-lookup"><span data-stu-id="37aac-286">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="37aac-287">そのため、カスタムの変換メソッドを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-287">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="37aac-288">また、`Repository` クラスのユーザーに公開されている未加工の文字列もおそらく不要でしょう。</span><span class="sxs-lookup"><span data-stu-id="37aac-288">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="37aac-289">この文字列も属性を使用して制御できます。</span><span class="sxs-lookup"><span data-stu-id="37aac-289">Attributes can help control that as well.</span></span> <span data-ttu-id="37aac-290">最初に、日時の文字列表現を `Repository` クラスに保持する `private` プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="37aac-290">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="37aac-291">`DataMember` 属性は、このプロパティがパブリック メンバーでないとしても処理する必要があることをシリアライザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="37aac-291">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="37aac-292">次に、文字列を有効な <xref:System.DateTime> オブジェクトに変換してその <xref:System.DateTime> を返す読み取り専用のパブリック プロパティを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-292">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

<span data-ttu-id="37aac-293">上記の新しいコンストラクトについて詳しく見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="37aac-293">Let's go over the new constructs above.</span></span> <span data-ttu-id="37aac-294">`IgnoreDataMember` 属性は、JSON オブジェクトとの間でこの型の読み取りまたは書き込みを行わないようにシリアライザーに指示します。</span><span class="sxs-lookup"><span data-stu-id="37aac-294">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="37aac-295">このプロパティには `get` アクセサーだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37aac-295">This property contains only a `get` accessor.</span></span> <span data-ttu-id="37aac-296">`set` アクセサーがない。</span><span class="sxs-lookup"><span data-stu-id="37aac-296">There is no `set` accessor.</span></span> <span data-ttu-id="37aac-297">C# では、この方法で "*読み取り専用*" プロパティを定義します </span><span class="sxs-lookup"><span data-stu-id="37aac-297">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="37aac-298">(C# では "*書き込み専用*" プロパティを作成できますが、その値は制限されています)。<xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> メソッドは、指定された日付形式を使用して文字列を解析し、<xref:System.DateTime> オブジェクトを作成します。次に、`CultureInfo` オブジェクトを使用して `DateTime` にメタデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="37aac-298">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="37aac-299">解析操作が失敗した場合、プロパティのアクセサーは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="37aac-299">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="37aac-300"><xref:System.Globalization.CultureInfo.InvariantCulture> を使用するには、`repo.cs` 内の `using` ステートメントに <xref:System.Globalization> 名前空間を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37aac-300">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="37aac-301">最後に、コンソールで出力ステートメントをもう 1 つ追加すれば、このアプリケーションを再度ビルドして実行する準備は完了です。</span><span class="sxs-lookup"><span data-stu-id="37aac-301">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="37aac-302">以上で、作成してきたバージョンは[最終的なサンプル](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)と同じになるはずです。</span><span class="sxs-lookup"><span data-stu-id="37aac-302">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="37aac-303">まとめ</span><span class="sxs-lookup"><span data-stu-id="37aac-303">Conclusion</span></span>

<span data-ttu-id="37aac-304">このチュートリアルでは、Web 要求を作成する方法、結果を解析する方法、およびそれらの結果のプロパティを表示する方法を紹介しました。</span><span class="sxs-lookup"><span data-stu-id="37aac-304">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="37aac-305">また、依存関係として新しいパッケージをプロジェクトに追加しました。</span><span class="sxs-lookup"><span data-stu-id="37aac-305">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="37aac-306">さらに、オブジェクト指向の手法をサポートする C# 言語の一部の機能について確認しました。</span><span class="sxs-lookup"><span data-stu-id="37aac-306">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
