---
title: コンソール アプリケーション
description: このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: dba6125dd359a47115b0f363a081dc000ce29e6a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="console-application"></a><span data-ttu-id="48b76-104">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="48b76-104">Console Application</span></span>

<span data-ttu-id="48b76-105">このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。</span><span class="sxs-lookup"><span data-stu-id="48b76-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="48b76-106">内容は以下の通りです。</span><span class="sxs-lookup"><span data-stu-id="48b76-106">You’ll learn:</span></span>

- <span data-ttu-id="48b76-107">.NET Core コマンド ライン インターフェイス (CLI) の基本</span><span class="sxs-lookup"><span data-stu-id="48b76-107">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="48b76-108">C# コンソール アプリケーションの構造</span><span class="sxs-lookup"><span data-stu-id="48b76-108">The structure of a C# Console Application</span></span>
- <span data-ttu-id="48b76-109">コンソール入出力</span><span class="sxs-lookup"><span data-stu-id="48b76-109">Console I/O</span></span>
- <span data-ttu-id="48b76-110">.NET でのファイル入出力 API の基本</span><span class="sxs-lookup"><span data-stu-id="48b76-110">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="48b76-111">.NET でのタスクベースの非同期プログラミングの基本</span><span class="sxs-lookup"><span data-stu-id="48b76-111">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="48b76-112">テキスト ファイルを読み取って、そのテキスト ファイルの内容をコンソールにエコーするアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="48b76-112">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="48b76-113">コンソールへの出力は、内容を読み上げる速度に一致します。</span><span class="sxs-lookup"><span data-stu-id="48b76-113">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="48b76-114">‘<’ または ‘>’ キーを押して、速度を速めたり遅めたりできます。</span><span class="sxs-lookup"><span data-stu-id="48b76-114">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="48b76-115">このチュートリアルには、多くの機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="48b76-115">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="48b76-116">それらを 1 つずつビルドしてみましょう。</span><span class="sxs-lookup"><span data-stu-id="48b76-116">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48b76-117">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="48b76-117">Prerequisites</span></span>

<span data-ttu-id="48b76-118">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-118">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="48b76-119">インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48b76-119">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="48b76-120">このアプリケーションは、Windows、Linux、macOS または Docker コンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="48b76-120">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="48b76-121">お好みのコード エディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="48b76-121">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="48b76-122">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="48b76-122">Create the Application</span></span>

<span data-ttu-id="48b76-123">最初に新しいアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="48b76-123">The first step is to create a new application.</span></span> <span data-ttu-id="48b76-124">コマンド プロンプトを開き、アプリケーション用の新しいディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="48b76-124">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="48b76-125">それを、現在のディレクトリとしてください。</span><span class="sxs-lookup"><span data-stu-id="48b76-125">Make that the current directory.</span></span> <span data-ttu-id="48b76-126">コマンド プロンプトで `dotnet new console` のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="48b76-126">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="48b76-127">これで、基本的な "Hello World" アプリケーションのスターター ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-127">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="48b76-128">変更を加える前に、このシンプルな Hello World アプリケーションを実行する手順を見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="48b76-128">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="48b76-129">アプリケーション作成後、コマンド プロンプトで `dotnet restore` と入力します。</span><span class="sxs-lookup"><span data-stu-id="48b76-129">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="48b76-130">このコマンドにより、NuGet パッケージの復元処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-130">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="48b76-131">NuGet は .NET パッケージ マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="48b76-131">NuGet is a .NET package manager.</span></span> <span data-ttu-id="48b76-132">このコマンドにより、プロジェクトの依存関係のうち欠落しているものがすべてダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="48b76-132">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="48b76-133">これは新しいプロジェクトなので、依存関係は何もなく、最初の実行で .NET Core フレームワークがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="48b76-133">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="48b76-134">この初期手順の後に必要なのは、新しい依存パッケージを追加するときに `dotnet restore` を実行するか、いずれかの依存関係のバージョンを更新するだけです。</span><span class="sxs-lookup"><span data-stu-id="48b76-134">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="48b76-135">パッケージを復元したら、`dotnet build` を実行します。</span><span class="sxs-lookup"><span data-stu-id="48b76-135">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="48b76-136">これにより、ビルド エンジンが実行され、アプリケーション実行可能ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-136">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="48b76-137">最後に、`dotnet run` を実行してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="48b76-137">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="48b76-138">シンプルな Hello World アプリケーションのコードはすべて Program.cs に含まれています。</span><span class="sxs-lookup"><span data-stu-id="48b76-138">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="48b76-139">使い慣れたテキスト エディターでそのファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="48b76-139">Open that file with your favorite text editor.</span></span> <span data-ttu-id="48b76-140">最初の変更を加えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="48b76-140">We’re about to make our first changes.</span></span>
<span data-ttu-id="48b76-141">ファイルの上部に、using ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="48b76-141">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="48b76-142">このステートメントは、`System` 名前空間からのいずれの型もスコープ内にあることをコンパイラに伝えています。</span><span class="sxs-lookup"><span data-stu-id="48b76-142">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="48b76-143">お使いになったことのある他のオブジェクト指向の言語と同じく、C# では名前空間を使用して型を整理します。</span><span class="sxs-lookup"><span data-stu-id="48b76-143">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="48b76-144">この Hello World プログラムも同様です。</span><span class="sxs-lookup"><span data-stu-id="48b76-144">This Hello World program is no different.</span></span> <span data-ttu-id="48b76-145">プログラムは現在のディレクトリの名前に基づく名前を持つ名前空間で囲まれていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="48b76-145">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="48b76-146">このチュートリアルでは、名前空間の名前を `TeleprompterConsole` に変更します。</span><span class="sxs-lookup"><span data-stu-id="48b76-146">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="48b76-147">ファイルの読み取りとエコー</span><span class="sxs-lookup"><span data-stu-id="48b76-147">Reading and Echoing the File</span></span>

<span data-ttu-id="48b76-148">最初に追加する機能は、テキスト ファイルを読み取り、そのテキストすべてをコンソールに表示する機能です。</span><span class="sxs-lookup"><span data-stu-id="48b76-148">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="48b76-149">まず、テキスト ファイルを追加しましょう。</span><span class="sxs-lookup"><span data-stu-id="48b76-149">First, let’s add a text file.</span></span> <span data-ttu-id="48b76-150">この[サンプル](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter)の GitHub リポジトリから、[sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) ファイルをプロジェクト ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="48b76-150">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="48b76-151">これがアプリケーションのスクリプトとして機能します。</span><span class="sxs-lookup"><span data-stu-id="48b76-151">This will serve as the script for your application.</span></span> <span data-ttu-id="48b76-152">このトピックのサンプル アプリをダウンロードする方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="48b76-152">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="48b76-153">次に、以下のメソッドを `Program` クラス (`Main` メソッドの真下) に追加します。</span><span class="sxs-lookup"><span data-stu-id="48b76-153">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="48b76-154">このメソッドは、2 つの新しい名前空間の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="48b76-154">This method uses types from two new namespaces.</span></span> <span data-ttu-id="48b76-155">これをコンパイルするには、ファイルの先頭に次の 2 行を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-155">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="48b76-156"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスは <xref:System.Collections.Generic> 名前空間で定義されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-156">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="48b76-157"><xref:System.IO.File> クラスは <xref:System.IO> 名前空間で定義されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-157">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="48b76-158">このメソッドは*反復子メソッド*と呼ばれる特殊な型の C# メソッドです。</span><span class="sxs-lookup"><span data-stu-id="48b76-158">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="48b76-159">列挙子メソッドは、遅延評価されるシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="48b76-159">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="48b76-160">つまり、シーケンスを使用するコードによって要求されると、そのシーケンス内の各項目が生成されことになります。</span><span class="sxs-lookup"><span data-stu-id="48b76-160">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="48b76-161">列挙子メソッドは、1 つまたは複数の [`yield return`](../language-reference/keywords/yield.md) ステートメントを含むメソッドです。</span><span class="sxs-lookup"><span data-stu-id="48b76-161">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="48b76-162">`ReadFrom` メソッドによって返されるオブジェクトには、シーケンス内の各項目を生成するコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="48b76-162">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="48b76-163">この例では、ソース ファイルからテキストの次の行を読み取り、その文字列を返す処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48b76-163">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="48b76-164">呼び出し元のコードがシーケンスから次の項目を要求するたびに、コードはファイルからテキストの次の行を読み取り、それを返します。</span><span class="sxs-lookup"><span data-stu-id="48b76-164">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="48b76-165">ファイルが完全に読み取られたら、シーケンスはこれ以上項目がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="48b76-165">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="48b76-166">新機能としてさらに、C# 構文要素が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="48b76-166">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="48b76-167">このメソッド内の [`using`](../language-reference/keywords/using-statement.md) ステートメントは、リソースのクリーンアップを管理するものです。</span><span class="sxs-lookup"><span data-stu-id="48b76-167">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="48b76-168">`using` ステートメント内で初期化された変数 (この例では `reader`) は、<xref:System.IDisposable> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-168">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="48b76-169">そのインターフェイスは、リソースの解放が必要なときに呼び出す必要がある 1 つのメソッド `Dispose` を定義します。</span><span class="sxs-lookup"><span data-stu-id="48b76-169">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="48b76-170">実行が `using` ステートメントの右中かっこに達したときに、コンパイラがその呼び出しを生成します。</span><span class="sxs-lookup"><span data-stu-id="48b76-170">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="48b76-171">コンパイラによって生成されたコードでは、using ステートメントによって定義されたブロック内のコードから例外がスローされた場合でも、確実にリソースを解放させます。</span><span class="sxs-lookup"><span data-stu-id="48b76-171">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="48b76-172">`reader` 変数は `var` キーワードを使用して定義されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-172">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="48b76-173">[`var`](../language-reference/keywords/var.md) は*暗黙的に型指定されたローカル変数*を定義します。</span><span class="sxs-lookup"><span data-stu-id="48b76-173">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="48b76-174">つまり、変数の型は、変数に割り当てられているオブジェクトのコンパイル時の型によって決まるということです。</span><span class="sxs-lookup"><span data-stu-id="48b76-174">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="48b76-175">ここでは、<xref:System.IO.File.OpenText(System.String)> メソッドからの戻り値のことで、これは <xref:System.IO.StreamReader> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="48b76-175">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="48b76-176">ここで、`Main` メソッドにファイルを読み取るコードを入力してみましょう。</span><span class="sxs-lookup"><span data-stu-id="48b76-176">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="48b76-177">プログラム (`dotnet run` を使用) を実行すると、コンソールに出力されるすべての行を確認できます。</span><span class="sxs-lookup"><span data-stu-id="48b76-177">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="48b76-178">遅延の追加と出力の書式設定</span><span class="sxs-lookup"><span data-stu-id="48b76-178">Adding Delays and Formatting output</span></span>

<span data-ttu-id="48b76-179">コードは今の状態だと、表示が早すぎて読み上げることができません。</span><span class="sxs-lookup"><span data-stu-id="48b76-179">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="48b76-180">出力に遅延を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-180">Now you need to add the delays in the output.</span></span> <span data-ttu-id="48b76-181">非同期処理を可能にするコア コードを作成していくことになります。</span><span class="sxs-lookup"><span data-stu-id="48b76-181">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="48b76-182">しかしここでの手順では、アンチパターンをいくつか使います。</span><span class="sxs-lookup"><span data-stu-id="48b76-182">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="48b76-183">このアンチパターンは、コードを追加しながらコメントで指摘され、コードは後の手順で更新されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-183">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="48b76-184">このセクションでは 2 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-184">There are two steps to this section.</span></span> <span data-ttu-id="48b76-185">最初に、行全体ではなく単一の語を返すように反復子メソッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="48b76-185">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="48b76-186">そのために、次の変更をします。</span><span class="sxs-lookup"><span data-stu-id="48b76-186">That’s done with these modifications.</span></span> <span data-ttu-id="48b76-187">`yield return line;` ステートメントを、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="48b76-187">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="48b76-188">次に、ファイルの行を使用する方法を変更し、各語を書き込んだ後に遅延を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-188">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="48b76-189">`Main` メソッドの `Console.WriteLine(line)` ステートメントを、次のブロックに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="48b76-189">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="48b76-190"><xref:System.Threading.Tasks.Task> クラスは <xref:System.Threading.Tasks> 名前空間にあるので、`using` ステートメントをファイルの先頭に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-190">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="48b76-191">このサンプルを実行し、出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="48b76-191">Run the sample, and check the output.</span></span> <span data-ttu-id="48b76-192">これで、各語が出力されるたびに 200 ミリ秒の遅延が発生するようになりました。</span><span class="sxs-lookup"><span data-stu-id="48b76-192">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="48b76-193">しかし、表示される出力には問題があります。ソース テキスト ファイルには、改行なしで 80 文字を超える行が複数あるからです。</span><span class="sxs-lookup"><span data-stu-id="48b76-193">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="48b76-194">スクロール中にそれを読み取るのは困難です。</span><span class="sxs-lookup"><span data-stu-id="48b76-194">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="48b76-195">これは簡単に修正できます。</span><span class="sxs-lookup"><span data-stu-id="48b76-195">That’s easy to fix.</span></span> <span data-ttu-id="48b76-196">各行の長さを追跡して、行の長さが特定のしきい値に達したら新しい行を生成するだけです。</span><span class="sxs-lookup"><span data-stu-id="48b76-196">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="48b76-197">行の長さを保持する `ReadFrom` メソッドの `words` の宣言の後に、ローカル変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="48b76-197">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="48b76-198">そして、次のコードを `yield return word + " ";` ステートメントの後 (右中かっこの前) に追加します。</span><span class="sxs-lookup"><span data-stu-id="48b76-198">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="48b76-199">サンプルを実行すると、事前に設定されていたペースで読み上げることができます。</span><span class="sxs-lookup"><span data-stu-id="48b76-199">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="48b76-200">非同期タスク</span><span class="sxs-lookup"><span data-stu-id="48b76-200">Async Tasks</span></span>

<span data-ttu-id="48b76-201">この最後の手順では、1 つのタスク内で非同期的に出力を記述し、あわせて別のタスクを実行してテキスト表示の速度を上げ下げするユーザーからの命令を読み取る、というコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="48b76-201">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="48b76-202">これは少しの手順だけで済み、これで必要な変更はすべて完了となります。</span><span class="sxs-lookup"><span data-stu-id="48b76-202">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="48b76-203">最初に、ここまでで作成したファイルを読み取り表示するコードを表す、非同期の <xref:System.Threading.Tasks.Task> を返すメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="48b76-203">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="48b76-204">このメソッドを `Program` クラス (`Main` メソッドの本体から取得したもの) に追加します。</span><span class="sxs-lookup"><span data-stu-id="48b76-204">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="48b76-205">2 点、変更されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-205">You’ll notice two changes.</span></span> <span data-ttu-id="48b76-206">1 点目は、メソッドの本体で、<xref:System.Threading.Tasks.Task.Wait> を呼び出してタスクが終了するのを同期的に待つかわりに、このバージョンでは `await` キーワードを使用することです。</span><span class="sxs-lookup"><span data-stu-id="48b76-206">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="48b76-207">そのためには、`async` 修飾子をメソッド シグネチャに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-207">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="48b76-208">このメソッドは `Task` を返します。</span><span class="sxs-lookup"><span data-stu-id="48b76-208">This method returns a `Task`.</span></span> <span data-ttu-id="48b76-209">`Task` オブジェクトを返す return ステートメントがないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="48b76-209">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="48b76-210">かわりに、その `Task` オブジェクトは `await` 演算子を使用した時にコンパイラが生成したコードによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-210">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="48b76-211">このメソッドは `await` に達するときに戻ることが想像できます。</span><span class="sxs-lookup"><span data-stu-id="48b76-211">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="48b76-212">`Task` が返されたということは、作業が完了していないことを表しています。</span><span class="sxs-lookup"><span data-stu-id="48b76-212">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="48b76-213">このメソッドは、待機中のタスクが完了したときに再開します。</span><span class="sxs-lookup"><span data-stu-id="48b76-213">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="48b76-214">それが完了すると `Task` が返され、タスクが完了したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="48b76-214">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="48b76-215">コード呼び出しでは、その返された `Task` を監視して、いつ完了したのか判断します。</span><span class="sxs-lookup"><span data-stu-id="48b76-215">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="48b76-216">この新しいメソッドは `Main` メソッドで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="48b76-216">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="48b76-217">ここで、`Main` では、コードは同期的に待機します。</span><span class="sxs-lookup"><span data-stu-id="48b76-217">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="48b76-218">可能なときは同期的に待機しないで、`await` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="48b76-218">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="48b76-219">しかし、コンソール アプリケーションの `Main` メソッドでは、`await` 演算子を使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="48b76-219">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="48b76-220">それでは、すべてのタスクが完了する前にアプリケーションが終了することになります。</span><span class="sxs-lookup"><span data-stu-id="48b76-220">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="48b76-221">C# 7.1 以降を使用している場合は、[`async` `Main` メソッド](../whats-new/csharp-7-1.md#async-main)でコンソール アプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="48b76-221">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="48b76-222">次に、2 つ目の非同期メソッドを記述して、コンソールを読み取り、‘<’ キーおよび ‘>’ キーを監視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-222">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="48b76-223">そのタスクに追加するメソッドは次の通りです。</span><span class="sxs-lookup"><span data-stu-id="48b76-223">Here’s the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="48b76-224">ここでは、ラムダ式を作成して、コンソールからキーを読み取り、ユーザーが ‘<’ または ‘>’ キーを押したときの遅延を表すローカル変数を変更する <xref:System.Action> デリゲートを表します。</span><span class="sxs-lookup"><span data-stu-id="48b76-224">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="48b76-225">このメソッドは <xref:System.Console.ReadKey> を使用してブロックし、ユーザーがキーを押すまで待機します。</span><span class="sxs-lookup"><span data-stu-id="48b76-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="48b76-226">この機能を完成させるには、これら両方のタスク (`GetInput` と `ShowTeleprompter`) を開始し、これら 2 つのタスク間で共有データを管理する、`async Task` を返す新しいメソッドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="48b76-227">これら 2 つのタスク間で共有データを処理するクラスを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="48b76-227">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="48b76-228">このクラスには、2 つのパブリック プロパティが含まれます。遅延、そして、ファイルが完全に読み取られたことを示すフラグ `Done` です。</span><span class="sxs-lookup"><span data-stu-id="48b76-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="48b76-229">そのクラスを新しいファイルに配置し、上記のように、`TeleprompterConsole` 名前空間にそのクラスを囲います。</span><span class="sxs-lookup"><span data-stu-id="48b76-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="48b76-230">さらに `using static` ステートメントを追加して、囲むクラスや名前空間の名前なしで `Min` および `Max` メソッドを参照できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-230">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="48b76-231">[`using static`](../language-reference/keywords/using-static.md) ステートメントは 1 つのクラスからメソッドをインポートします。</span><span class="sxs-lookup"><span data-stu-id="48b76-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="48b76-232">これは、この時点までで使用した、名前空間からすべてのクラスをインポートした `using` ステートメントとは対照的です。</span><span class="sxs-lookup"><span data-stu-id="48b76-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="48b76-233">もう 1 つの新しい言語機能は [`lock`](../language-reference/keywords/lock-statement.md) ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="48b76-233">The other language feature that’s new is the [`lock`](../language-reference/keywords/lock-statement.md) statement.</span></span> <span data-ttu-id="48b76-234">このステートメントは、特定の時点で単一のスレッドのみがそのコードに含まれることを保証します。</span><span class="sxs-lookup"><span data-stu-id="48b76-234">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="48b76-235">1 つのスレッドがロックされているセクションにある場合は、その他のスレッドは、最初のスレッドがそのセクションを終了するのを待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-235">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="48b76-236">`lock` ステートメントは、ロック セクションを保護するオブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="48b76-236">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="48b76-237">このクラスは、標準的な表現形式に従ってクラスのプライベート オブジェクトをロックします。</span><span class="sxs-lookup"><span data-stu-id="48b76-237">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="48b76-238">次に、`ShowTeleprompter` メソッドと `GetInput` メソッドを更新して、新しい `config` オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-238">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="48b76-239">最後の `Task` を返す `async` メソッドを書いて、両方のタスクを開始し、最初のタスクが終了するときに終了させます。</span><span class="sxs-lookup"><span data-stu-id="48b76-239">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="48b76-240">ここでの 1 つの新しいメソッドは <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> の呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="48b76-240">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="48b76-241">これによって、その引数リスト内の任意のタスクが完了したらすぐに終了する `Task` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="48b76-241">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="48b76-242">次に、遅延の `config` オブジェクトを使用するように、`ShowTeleprompter` メソッドと `GetInput` メソッドの両方を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-242">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="48b76-243">この新しいバージョンの `ShowTeleprompter` は、`TeleprompterConfig` クラスの新しいメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="48b76-243">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="48b76-244">ここで、`Main` を更新して `ShowTeleprompter` の代わりに `RunTeleprompter` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="48b76-244">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="48b76-245">まとめ</span><span class="sxs-lookup"><span data-stu-id="48b76-245">Conclusion</span></span>

<span data-ttu-id="48b76-246">このチュートリアルでは、コンソール アプリケーションでの作業に関連する、C# 言語と .NET Core ライブラリについての多くの機能を説明しました。</span><span class="sxs-lookup"><span data-stu-id="48b76-246">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="48b76-247">ここでの知識を基にすれば、この言語やここで紹介したクラスについてさらに理解していけるでしょう。</span><span class="sxs-lookup"><span data-stu-id="48b76-247">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="48b76-248">ファイルとコンソール入出力の基本、タスク ベースの非同期プログラミングのブロック使用と非ブロック使用、C# 言語のツアーと C# プログラムの構成方法、および .NET Core のコマンド ライン インターフェイスとツールについて説明しました。</span><span class="sxs-lookup"><span data-stu-id="48b76-248">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="48b76-249">ファイル入出力の詳細については、「[ファイルおよびストリーム入出力](../../standard/io/index.md)」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48b76-249">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="48b76-250">このチュートリアルで使用される非同期プログラミング モデルの詳細については、「[タスク ベースの非同期プログラミング](../..//standard/parallel-programming/task-based-asynchronous-programming.md)」トピックと「[非同期プログラミング](../async.md)」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48b76-250">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
