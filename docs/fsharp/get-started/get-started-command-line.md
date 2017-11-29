---
title: "コマンド ライン ツールを使用して f# の概要します。"
description: "クロス プラットフォームの .NET Core CLI で f# を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング, .NET, .NET Core"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: a23d4861ce599f20f37ecd0564a0187e7b9b739f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>.NET Core CLI を使用して f# の概要します。

この記事では、どのように開始できます f# .NET Core での使用をについて説明します。 これを通過コンソール アプリケーションによって呼び出されるクラス ライブラリとマルチ プロジェクト ソリューションを構築します。

## <a name="prerequisites"></a>必須コンポーネント

最初に、インストールする必要があります、 [.NET Core SDK 1.0 以降](https://dot.net/core)です。 サイド バイ サイド インストールがサポートされていること、.NET Core SDK の以前のバージョンをアンインストールする必要はありません。

この記事では、方法を知っているコマンドラインを使用して、任意のテキスト エディターを前提としています。 既にコマンドを使用しない場合[Visual Studio Code](https://code.visualstudio.com) f# のテキスト エディターとして優れたオプションです。 IntelliSense より優れた構文の強調表示、および詳細などの優れた機能を取得するには、ダウンロードすることができます、 [Ionide 拡張子](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)です。

## <a name="building-a-simple-multi-project-solution"></a>単純なマルチ プロジェクト ソリューションを構築します。

コマンド プロンプト/ターミナルを開いて使用して、`dotnet new`と呼ばれる新しいソリューション ファイルを作成するコマンドを`FSNetCore`:

```
dotnet new sln -o FSNetCore
```

次のディレクトリ構造は、コマンドの完了の結果として生成されます。

```
FSNetCore
    ├── FSNetCore.sln
```

ディレクトリに移動*FSNetCore*およびソリューション フォルダーをプロジェクトの追加を開始します。
 
### <a name="writing-a-class-library"></a>クラス ライブラリを作成

使用して、`dotnet new`コマンドで、クラス ライブラリ プロジェクトを作成、 **src**ライブラリをという名前のフォルダーです。 

```bash
dotnet new lib -lang F# -o src/Library 
```

次のディレクトリ構造は、コマンドの完了の結果として生成されます。

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

内容を置き換える`Library.fs`次。

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

Newtonsoft.Json NuGet パッケージをライブラリ プロジェクトに追加します。

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

追加、`Library`プロジェクトを`FSNetCore`ソリューションを使用して、`dotnet sln add`コマンド。

```bash
dotnet sln add src/Library/Library.fsproj
```

NuGet の依存関係を復元`dotnet restore`([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。

### <a name="writing-a-console-application-which-consumes-the-class-library"></a>クラス ライブラリを使用するコンソール アプリケーションの作成

使用して、`dotnet new`コマンドで、コンソール アプリケーションを作成、 **src**アプリをという名前のフォルダーです。 

```bash
dotnet new console -lang F# -o src/App 
```

次のディレクトリ構造は、コマンドの完了の結果として生成されます。

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

変更`Program.fs`に。

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

参照を追加、`Library`を使用してプロジェクト`dotnet add reference`です。

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

追加、`App`プロジェクトを`FSNetCore`ソリューションを使用して、`dotnet sln add`コマンド。

```bash
dotnet sln add src/App/App.fsproj
```

NuGet の依存関係を復元`dotnet restore`([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。

ディレクトリを変更、`src/App`コンソール プロジェクト プロジェクトと実行を渡す`Hello World`引数として。

```bash
cd src/App
dotnet run Hello World
``` 

次の結果が表示されます。

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]