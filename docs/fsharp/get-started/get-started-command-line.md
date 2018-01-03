---
title: "コマンド ライン ツールを使用して f# の概要します。"
description: "クロス プラットフォームの .NET Core CLI を使用してすべての OS (Windows、MacOS、Linux) で f# を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング, .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: 4820a8a306bd478429b497a8b7c70ff170c1c655
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="ce7e8-104">.NET Core CLI を使用して f# の概要します。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-104">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="ce7e8-105">この記事では、どのように開始できます (Windows、macOS、または Linux) のすべての OS で .NET Core CLI で f# を使用してについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-105">This article covers how you can get started on any OS (Windows, macOS, or Linux) by using F# with the .NET Core CLI.</span></span> <span data-ttu-id="ce7e8-106">これを通過コンソール アプリケーションによって呼び出されるクラス ライブラリとマルチ プロジェクト ソリューションを構築します。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-106">It will go through building a multi-project solution with a Class Library that is called by a Console Application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce7e8-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ce7e8-107">Prerequisites</span></span>

<span data-ttu-id="ce7e8-108">最初に、インストールする必要があります、 [.NET Core SDK 1.0 以降](https://dot.net/core)です。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-108">To begin, you must install the [.NET Core SDK 1.0 or later](https://dot.net/core).</span></span> <span data-ttu-id="ce7e8-109">サイド バイ サイド インストールがサポートされていること、.NET Core SDK の以前のバージョンをアンインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-109">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="ce7e8-110">この記事では、方法を知っているコマンドラインを使用して、任意のテキスト エディターを前提としています。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-110">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="ce7e8-111">既にコマンドを使用しない場合[Visual Studio Code](https://code.visualstudio.com) f# のテキスト エディターとして優れたオプションです。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-111">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="ce7e8-112">IntelliSense より優れた構文の強調表示、および詳細などの優れた機能を取得するには、ダウンロードすることができます、 [Ionide 拡張子](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)です。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-112">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="building-a-simple-multi-project-solution"></a><span data-ttu-id="ce7e8-113">単純なマルチ プロジェクト ソリューションを構築します。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-113">Building a Simple Multi-project Solution</span></span>

<span data-ttu-id="ce7e8-114">コマンド プロンプト/ターミナルを開いて使用して、`dotnet new`と呼ばれる新しいソリューション ファイルを作成するコマンドを`FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="ce7e8-114">Open a command prompt/terminal and use the `dotnet new` command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="ce7e8-115">次のディレクトリ構造は、コマンドの完了の結果として生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-115">The folowing directory structure is produced as a result of the command completing:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

<span data-ttu-id="ce7e8-116">ディレクトリに移動*FSNetCore*およびソリューション フォルダーをプロジェクトの追加を開始します。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-116">Change directories to *FSNetCore* and start adding projects to the solution folder.</span></span>
 
### <a name="writing-a-class-library"></a><span data-ttu-id="ce7e8-117">クラス ライブラリを作成</span><span class="sxs-lookup"><span data-stu-id="ce7e8-117">Writing a Class library</span></span>

<span data-ttu-id="ce7e8-118">使用して、`dotnet new`コマンドで、クラス ライブラリ プロジェクトを作成、 **src**ライブラリをという名前のフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-118">Use the `dotnet new` command, create a Class Library project in the **src** folder named Library.</span></span> 

```bash
dotnet new lib -lang F# -o src/Library 
```

<span data-ttu-id="ce7e8-119">次のディレクトリ構造は、コマンドの完了の結果として生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-119">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="ce7e8-120">内容を置き換える`Library.fs`次。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-120">Replace the contents of `Library.fs` with the following:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="ce7e8-121">Newtonsoft.Json NuGet パッケージをライブラリ プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-121">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="ce7e8-122">追加、`Library`プロジェクトを`FSNetCore`ソリューションを使用して、`dotnet sln add`コマンド。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-122">Add the `Library` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="ce7e8-123">NuGet の依存関係を復元`dotnet restore`([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-123">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="writing-a-console-application-which-consumes-the-class-library"></a><span data-ttu-id="ce7e8-124">クラス ライブラリを使用するコンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ce7e8-124">Writing a Console Application which Consumes the Class Library</span></span>

<span data-ttu-id="ce7e8-125">使用して、`dotnet new`コマンドで、コンソール アプリケーションを作成、 **src**アプリをという名前のフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-125">Use the `dotnet new` command, create a Console app in the **src** folder named App.</span></span> 

```bash
dotnet new console -lang F# -o src/App 
```

<span data-ttu-id="ce7e8-126">次のディレクトリ構造は、コマンドの完了の結果として生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-126">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="ce7e8-127">変更`Program.fs`に。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-127">Change `Program.fs` to:</span></span>

```fsharp
open System
open Library

[<EntryPoint>]
let main argv = 
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

<span data-ttu-id="ce7e8-128">参照を追加、`Library`を使用してプロジェクト`dotnet add reference`です。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-128">Add a reference to the `Library` project using `dotnet add reference`.</span></span>

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="ce7e8-129">追加、`App`プロジェクトを`FSNetCore`ソリューションを使用して、`dotnet sln add`コマンド。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-129">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="ce7e8-130">NuGet の依存関係を復元`dotnet restore`([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-130">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="ce7e8-131">ディレクトリを変更、`src/App`コンソール プロジェクト プロジェクトと実行を渡す`Hello World`引数として。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-131">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments.</span></span>

```bash
cd src/App
dotnet run Hello World
``` 

<span data-ttu-id="ce7e8-132">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ce7e8-132">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
