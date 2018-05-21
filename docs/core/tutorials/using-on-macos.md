---
title: macOS での .NET Core の概要
description: このドキュメントでは、Visual Studio Code を使用して .NET Core ソリューションを作成する手順とワークフローを説明します。
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.openlocfilehash: 5a4b2734137f59b29535f302dd17fb94329d676f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="getting-started-with-net-core-on-macos"></a><span data-ttu-id="ba345-103">macOS での .NET Core の概要</span><span class="sxs-lookup"><span data-stu-id="ba345-103">Getting started with .NET Core on macOS</span></span>

<span data-ttu-id="ba345-104">このドキュメントでは、macOS 用の .NET Core ソリューションを作成する手順とワークフローを説明します。</span><span class="sxs-lookup"><span data-stu-id="ba345-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="ba345-105">プロジェクトと単体テストを作成し、デバッグ ツールを使用して、[NuGet](https://www.nuget.org/) からサードパーティ製ライブラリを組み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba345-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="ba345-106">この記事では、macOS で [Visual Studio Code](http://code.visualstudio.com) を使用します。</span><span class="sxs-lookup"><span data-stu-id="ba345-106">This article uses [Visual Studio Code](http://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba345-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ba345-107">Prerequisites</span></span>

<span data-ttu-id="ba345-108">[.NET Core SDK](https://www.microsoft.com/net/core) のインストール。</span><span class="sxs-lookup"><span data-stu-id="ba345-108">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="ba345-109">.NET Core SDK には、.NET Core のフレームワークとランタイムの最新リリースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ba345-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="ba345-110">[Visual Studio Code](http://code.visualstudio.com) のインストール。</span><span class="sxs-lookup"><span data-stu-id="ba345-110">Install [Visual Studio Code](http://code.visualstudio.com).</span></span> <span data-ttu-id="ba345-111">この記事の中では、.NET Core の開発エクスペリエンスが向上する Visual Studio Code 拡張機能もインストールします。</span><span class="sxs-lookup"><span data-stu-id="ba345-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="ba345-112">Visual Studio Code C# 拡張機能をインストールするには、Visual Studio Code を開き、<kbd>F1</kbd> を押して Visual Studio Code パレットを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba345-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="ba345-113">「**ext install**」と入力して、拡張機能の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="ba345-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="ba345-114">C# 拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="ba345-114">Select the C# extension.</span></span> <span data-ttu-id="ba345-115">Visual Studio Code を再起動して、拡張機能をアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="ba345-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="ba345-116">詳細については、[Visual Studio Code C# 拡張機能のドキュメント](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba345-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="getting-started"></a><span data-ttu-id="ba345-117">作業の開始</span><span class="sxs-lookup"><span data-stu-id="ba345-117">Getting started</span></span>

<span data-ttu-id="ba345-118">このチュートリアルでは 3 つのプロジェクト (ライブラリ プロジェクト、そのライブラリ プロジェクトのテスト、およびライブラリを使用するコンソール アプリケーション) を作成します。</span><span class="sxs-lookup"><span data-stu-id="ba345-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="ba345-119">GitHub の dotnet/samples レポジトリで、このトピックの[ソースを表示またはダウンロード](https://github.com/dotnet/samples/tree/master/core/getting-started/golden)することができます。</span><span class="sxs-lookup"><span data-stu-id="ba345-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="ba345-120">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba345-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ba345-121">Visual Studio Code を開始します。</span><span class="sxs-lookup"><span data-stu-id="ba345-121">Start Visual Studio Code.</span></span> <span data-ttu-id="ba345-122"><kbd>Ctrl</kbd>+<kbd>\`</kbd> (バッククォートまたはアクサン グラーブ) キーを押すか、メニューから **[表示]、[統合ターミナル]** の順に選択し、Visual Studio Code で埋め込みターミナルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba345-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="ba345-123">Visual Studio Code の外部で作業を行う場合は、エクスプローラーの **[コマンド プロンプトで開く]** コマンド (Ma または Linux の場合は **[ターミナルで開く]**) を使用して外部シェルを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="ba345-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="ba345-124">1 つ以上の .NET Core プロジェクトのコンテナーとして機能する、ソリューション ファイルの作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="ba345-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="ba345-125">ターミナルで、*golden* フォルダーを作成し、そのフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba345-125">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="ba345-126">このフォルダーはソリューションのルートです。</span><span class="sxs-lookup"><span data-stu-id="ba345-126">This folder is the root of your solution.</span></span> <span data-ttu-id="ba345-127">以下のように、[`dotnet new`](../tools/dotnet-new.md) コマンドを実行して新しいソリューション *golden.sln* を作成します。</span><span class="sxs-lookup"><span data-stu-id="ba345-127">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="ba345-128">*golden* フォルダーから以下のコマンドを実行して、ライブラリ プロジェクトを作成します。*library* フォルダーには、*library.csproj* と *Class1.cs* という 2 つのファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba345-128">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="ba345-129">以下のように、[`dotnet sln`](../tools/dotnet-sln.md) コマンドを実行し、新しく作成された *library.csproj* プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-129">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="ba345-130">*library.csproj* ファイルには、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ba345-130">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="ba345-131">このライブラリ メソッドでは、JSON 形式でオブジェクトのシリアル化と逆シリアル化を行います。</span><span class="sxs-lookup"><span data-stu-id="ba345-131">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="ba345-132">JSON のシリアル化および逆シリアル化をサポートするには、`Newtonsoft.Json` NuGet パッケージへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-132">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="ba345-133">`dotnet add` コマンドにより、新しい項目がプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ba345-133">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="ba345-134">NuGet パッケージへの参照を追加するには、[`dotnet add package`](../tools/dotnet-add-package.md) コマンドを使用して、パッケージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba345-134">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="ba345-135">これにより、`Newtonsoft.Json` とその依存関係がライブラリ プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ba345-135">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="ba345-136">あるいは、*library.csproj* ファイルを手動で編集し、次のノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-136">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="ba345-137">[`dotnet restore`](../tools/dotnet-restore.md) を実行します ([注記参照](#dotnet-restore-note))。これにより、依存関係が復元され、*project.assets.json* ファイルなどの 3 つのファイルを含む *obj* フォルダーが *library* 内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ba345-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="ba345-138">*library* フォルダーで、ファイル *Class1.cs* の名前を *Thing.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="ba345-138">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="ba345-139">このコードを次のコードを使って置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ba345-139">Replace the code with the following:</span></span>

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

<span data-ttu-id="ba345-140">`Thing` クラスには、`Get` という 1 つのパブリック メソッドが含まれます。このメソッドは 2 つの数値の合計を返しますが、そのためには合計値を文字列に変換した後、それを整数に逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="ba345-140">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="ba345-141">このコードでは、[`using static` ディレクティブ](../../csharp/language-reference/keywords/using-static.md)、[式本体のメンバー](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)、および[文字列補間](../../csharp/language-reference/tokens/interpolated.md)など、C# の最新の機能をいくつか利用しています。</span><span class="sxs-lookup"><span data-stu-id="ba345-141">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="ba345-142">[`dotnet build`](../tools/dotnet-build.md) コマンドを使用して、ライブラリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ba345-142">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="ba345-143">これにより、*golden/library/bin/Debug/netstandard1.4* に *library.dll* ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba345-143">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="ba345-144">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="ba345-144">Create the test project</span></span>

<span data-ttu-id="ba345-145">ライブラリのテスト プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ba345-145">Build a test project for the library.</span></span> <span data-ttu-id="ba345-146">*golden* フォルダーから、次のようにして新しいテスト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba345-146">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="ba345-147">次のようにしてテスト プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-147">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="ba345-148">コンパイラがライブラリ プロジェクトを見つけて使用できるように、前のセクションで作成したライブラリにプロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-148">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="ba345-149">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba345-149">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="ba345-150">あるいは、*test-library.csproj* ファイルを手動で編集し、次のノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-150">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="ba345-151">これで依存関係が正しく構成されました。次は、ライブラリのテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba345-151">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="ba345-152">*UnitTest1.cs* を開き、内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ba345-152">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="ba345-153">最初に失敗する単体テスト (`Assert.NotEqual`) を作成する場合、値 42 は 19+23 (つまり、42) と等しくないことをアサートすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ba345-153">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="ba345-154">単体テストのビルドにおける重要な手順は、最初に一度失敗するテストを作成して、そのロジックを確認することです。</span><span class="sxs-lookup"><span data-stu-id="ba345-154">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="ba345-155">*golden* フォルダーから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ba345-155">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="ba345-156">これらのコマンドは、再帰的にすべてのプロジェクトを検出し、依存関係を復元してビルドし、xUnit テスト ランナーをアクティブにしてテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="ba345-156">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="ba345-157">予期したとおり、1 つのテストに失敗します。</span><span class="sxs-lookup"><span data-stu-id="ba345-157">The single test fails, as you expect.</span></span>

<span data-ttu-id="ba345-158">*UnitTest1.cs* ファイルを編集し、アサーションを `Assert.NotEqual` から `Assert.Equal` に変更します。</span><span class="sxs-lookup"><span data-stu-id="ba345-158">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="ba345-159">*golden* フォルダーから次のコマンドを実行し、テストを再実行します。今回は成功します。</span><span class="sxs-lookup"><span data-stu-id="ba345-159">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="ba345-160">コンソール アプリの作成</span><span class="sxs-lookup"><span data-stu-id="ba345-160">Create the console app</span></span>

<span data-ttu-id="ba345-161">次の手順で作成するコンソール アプリは、前の手順で作成したライブラリ プロジェクトに対する依存関係を認識し、実行時にそのライブラリ メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ba345-161">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="ba345-162">この開発パターンを使用して、複数のプロジェクトで再利用可能なライブラリの作成方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="ba345-162">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="ba345-163">次のように、*golden* フォルダーから新しいコンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ba345-163">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="ba345-164">次のように、コンソール アプリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-164">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="ba345-165">次のように `dotnet add reference` コマンドを実行して、ライブラリに対する依存関係を作成します。</span><span class="sxs-lookup"><span data-stu-id="ba345-165">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="ba345-166">`dotnet restore` を実行し、ソリューションの 3 つのプロジェクトの依存関係を復元します ([注記参照](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="ba345-166">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="ba345-167">*Program.cs* を開き、`Main` メソッドの内容を次の行に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ba345-167">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="ba345-168">次のように、2 つの `using` ディレクティブを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="ba345-168">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="ba345-169">次の `dotnet run` コマンドを実行して、実行可能ファイルを実行します。`dotnet run` の `-p` オプションは、メイン アプリケーションのプロジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba345-169">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="ba345-170">アプリは "The answer is 42" という文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="ba345-170">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="ba345-171">アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="ba345-171">Debug the application</span></span>

<span data-ttu-id="ba345-172">`Main` メソッドの `WriteLine` ステートメントにブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="ba345-172">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="ba345-173">そのためには、カーソルが `WriteLine` 行にある状態で <kbd>F9</kbd> キーを押すか、ブレークポイントを設定する行の左余白でマウスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba345-173">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="ba345-174">コード行の横の余白に赤い丸が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba345-174">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="ba345-175">ブレークポイントに達した場合、ブレークポイント行が実行される*前*にコードの実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="ba345-175">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="ba345-176">Visual Studio Code ツール バーでデバッグ アイコンを選択するか、メニュー バーから **[表示]、[デバッグ]** の順に選択するか、あるいはキーボード ショートカットの <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> を使用して、デバッガー タブを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba345-176">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio Code デバッガー](./media/using-on-macos/vscodedebugger.png)

<span data-ttu-id="ba345-178">[再生] ボタンを押して、デバッガーでアプリケーションを開始します。</span><span class="sxs-lookup"><span data-stu-id="ba345-178">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="ba345-179">アプリは実行を開始し、ブレークポイントに達した時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="ba345-179">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="ba345-180">`Get` メソッドにステップ インし、正しい引数を渡したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ba345-180">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="ba345-181">答えが 42 であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ba345-181">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]