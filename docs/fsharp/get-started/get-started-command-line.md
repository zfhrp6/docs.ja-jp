---
title: コマンド ライン ツールを使用して f# の概要します。
description: F# CLI を使用して、.NET Core オペレーティング システム (Windows、macOs または Linux) での単純なマルチ プロジェクト ソリューションをビルドする方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 767385be605d863644db563a2e86a41ca80527c4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="b569c-103">.NET Core CLI を使用して f# の概要します。</span><span class="sxs-lookup"><span data-stu-id="b569c-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="b569c-104">この記事では、どのように開始できます f# と .NET Core CLI を使用してオペレーティング システム (Windows、macOS、または Linux) でについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b569c-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="b569c-105">コンソール アプリケーションによって呼び出されるクラス ライブラリを複数プロジェクトのソリューションをビルド経由になります。</span><span class="sxs-lookup"><span data-stu-id="b569c-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b569c-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b569c-106">Prerequisites</span></span>

<span data-ttu-id="b569c-107">最初に、インストールする必要があります、 [.NET Core SDK 1.0 以降](https://www.microsoft.com/net/download/)です。</span><span class="sxs-lookup"><span data-stu-id="b569c-107">To begin, you must install the [.NET Core SDK 1.0 or later](https://www.microsoft.com/net/download/).</span></span> <span data-ttu-id="b569c-108">サイド バイ サイド インストールがサポートされていること、.NET Core SDK の以前のバージョンをアンインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b569c-108">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="b569c-109">この記事では、方法を知っているコマンドラインを使用して、任意のテキスト エディターを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b569c-109">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="b569c-110">既にコマンドを使用しない場合[Visual Studio Code](https://code.visualstudio.com) f# のテキスト エディターとして優れたオプションです。</span><span class="sxs-lookup"><span data-stu-id="b569c-110">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="b569c-111">IntelliSense より優れた構文の強調表示、および詳細などの優れた機能を取得するには、ダウンロードすることができます、 [Ionide 拡張子](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)です。</span><span class="sxs-lookup"><span data-stu-id="b569c-111">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="b569c-112">単純なマルチ プロジェクト ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b569c-112">Build a simple multi-project solution</span></span>

<span data-ttu-id="b569c-113">コマンド プロンプト/ターミナルを開いて使用して、 [dotnet 新しい](../../core/tools/dotnet-new.md)と呼ばれる新しいソリューション ファイルを作成するコマンドを`FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="b569c-113">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="b569c-114">前のコマンドを実行した後は、次のディレクトリ構造が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b569c-114">The following directory structure is produced after running the previous command:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="b569c-115">クラス ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b569c-115">Write a class library</span></span>

<span data-ttu-id="b569c-116">ディレクトリに移動*FSNetCore*です。</span><span class="sxs-lookup"><span data-stu-id="b569c-116">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="b569c-117">使用して、`dotnet new`コマンドで、クラス ライブラリ プロジェクトを作成、 **src**ライブラリをという名前のフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="b569c-117">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```
dotnet new lib -lang F# -o src/Library
```

<span data-ttu-id="b569c-118">前のコマンドを実行した後は、次のディレクトリ構造が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b569c-118">The following directory structure is produced after running the previous command:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="b569c-119">内容を置き換える`Library.fs`を次のコード。</span><span class="sxs-lookup"><span data-stu-id="b569c-119">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="b569c-120">Newtonsoft.Json NuGet パッケージをライブラリ プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="b569c-120">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="b569c-121">追加、`Library`プロジェクトを`FSNetCore`ソリューションを使用して、 [dotnet sln 追加](../../core/tools/dotnet-sln.md)コマンド。</span><span class="sxs-lookup"><span data-stu-id="b569c-121">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="b569c-122">使用して NuGet の依存関係を復元、`dotnet restore`コマンド ([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b569c-122">Restore the NuGet dependencies using the `dotnet restore` command ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="b569c-123">クラス ライブラリを使用するコンソール アプリケーションを書く</span><span class="sxs-lookup"><span data-stu-id="b569c-123">Write a console application that consumes the class library</span></span>

<span data-ttu-id="b569c-124">使用して、`dotnet new`コマンドで、コンソール アプリケーションを作成、 **src**アプリをという名前のフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="b569c-124">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="b569c-125">前のコマンドを実行した後は、次のディレクトリ構造が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b569c-125">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="b569c-126">内容を置き換える、`Program.fs`を次のコード ファイル。</span><span class="sxs-lookup"><span data-stu-id="b569c-126">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="b569c-127">参照を追加、`Library`を使用してプロジェクト[dotnet 参照の追加](../../core/tools/dotnet-add-reference.md)です。</span><span class="sxs-lookup"><span data-stu-id="b569c-127">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="b569c-128">追加、`App`プロジェクトを`FSNetCore`ソリューションを使用して、`dotnet sln add`コマンド。</span><span class="sxs-lookup"><span data-stu-id="b569c-128">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="b569c-129">NuGet の依存関係を復元`dotnet restore`([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b569c-129">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="b569c-130">ディレクトリを変更、`src/App`コンソール プロジェクト プロジェクトと実行を渡す`Hello World`引数として。</span><span class="sxs-lookup"><span data-stu-id="b569c-130">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```
cd src/App
dotnet run Hello World
```

<span data-ttu-id="b569c-131">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b569c-131">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]