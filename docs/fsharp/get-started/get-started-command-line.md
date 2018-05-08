---
title: コマンド ライン ツールを使用して f# の概要します。
description: F# CLI を使用して、.NET Core オペレーティング システム (Windows、macOs または Linux) での単純なマルチ プロジェクト ソリューションをビルドする方法を説明します。
ms.date: 03/26/2018
ms.openlocfilehash: 35ec2313742a0b14c92f3de2662a16aff389b214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>.NET Core CLI を使用して f# の概要します。

この記事では、どのように開始できます f# と .NET Core CLI を使用してオペレーティング システム (Windows、macOS、または Linux) でについて説明します。 コンソール アプリケーションによって呼び出されるクラス ライブラリを複数プロジェクトのソリューションをビルド経由になります。

## <a name="prerequisites"></a>必須コンポーネント

最初に、インストールする必要があります、 [.NET Core SDK 1.0 以降](https://www.microsoft.com/net/download/)です。 サイド バイ サイド インストールがサポートされていること、.NET Core SDK の以前のバージョンをアンインストールする必要はありません。

この記事では、方法を知っているコマンドラインを使用して、任意のテキスト エディターを前提としています。 既にコマンドを使用しない場合[Visual Studio Code](https://code.visualstudio.com) f# のテキスト エディターとして優れたオプションです。 IntelliSense より優れた構文の強調表示、および詳細などの優れた機能を取得するには、ダウンロードすることができます、 [Ionide 拡張子](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)です。

## <a name="build-a-simple-multi-project-solution"></a>単純なマルチ プロジェクト ソリューションをビルドします。

コマンド プロンプト/ターミナルを開いて使用して、 [dotnet 新しい](../../core/tools/dotnet-new.md)と呼ばれる新しいソリューション ファイルを作成するコマンドを`FSNetCore`:

```
dotnet new sln -o FSNetCore
```

前のコマンドを実行した後は、次のディレクトリ構造が生成されます。

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>クラス ライブラリを作成します。

ディレクトリに移動*FSNetCore*です。

使用して、`dotnet new`コマンドで、クラス ライブラリ プロジェクトを作成、 **src**ライブラリをという名前のフォルダーです。

```
dotnet new lib -lang F# -o src/Library
```

前のコマンドを実行した後は、次のディレクトリ構造が生成されます。

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

内容を置き換える`Library.fs`を次のコード。

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Newtonsoft.Json NuGet パッケージをライブラリ プロジェクトに追加します。

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

追加、`Library`プロジェクトを`FSNetCore`ソリューションを使用して、 [dotnet sln 追加](../../core/tools/dotnet-sln.md)コマンド。

```
dotnet sln add src/Library/Library.fsproj
```

使用して NuGet の依存関係を復元、`dotnet restore`コマンド ([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。

### <a name="write-a-console-application-that-consumes-the-class-library"></a>クラス ライブラリを使用するコンソール アプリケーションを書く

使用して、`dotnet new`コマンドで、コンソール アプリケーションを作成、 **src**アプリをという名前のフォルダーです。

```
dotnet new console -lang F# -o src/App
```

前のコマンドを実行した後は、次のディレクトリ構造が生成されます。

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

内容を置き換える、`Program.fs`を次のコード ファイル。

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

参照を追加、`Library`を使用してプロジェクト[dotnet 参照の追加](../../core/tools/dotnet-add-reference.md)です。

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

追加、`App`プロジェクトを`FSNetCore`ソリューションを使用して、`dotnet sln add`コマンド。

```
dotnet sln add src/App/App.fsproj
```

NuGet の依存関係を復元`dotnet restore`([注を参照してください](#dotnet-restore-note)) を実行して`dotnet build`プロジェクトをビルドします。

ディレクトリを変更、`src/App`コンソール プロジェクト プロジェクトと実行を渡す`Hello World`引数として。

```
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