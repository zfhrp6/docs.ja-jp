---
title: "CLI を使用する .NET Core に関する概要 | Microsoft Docs"
description: "Windows、Linux、または macOS の .NET Core での、.NET Core コマンド ライン インターフェイス (CLI) の使用方法を段階的に説明するチュートリアル。"
keywords: .NET Core, CLI
author: cartermp
ms.author: mairaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 240061d2515c14ba7ab733f4cc9e7e38fb2a5c7c
ms.lasthandoff: 03/07/2017

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要

このトピックでは、.NET Core CLI ツールを利用し、自分のコンピューターでプラットフォームに依存しないアプリを開発する方法について説明します。

.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../tools/index.md)」(.NET Core SDK の概要) を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- [.NET Core SDK 1.0.0](https://www.microsoft.com/net/download/core)。
- ユーザーが選んだテキスト エディターまたはコード エディター。

## <a name="hello-console-app"></a>Hello コンソール アプリ

最初に、適切な名前のフォルダーに移動するか、新しく作成します。 サンプル コードでは *Hello* という名前を使用しています ([こちら](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild)を参照)。

コマンド プロンプトを開いて次のように入力します。

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

簡単に説明します。

1. `$ dotnet new console`

[`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の `Hello.csproj` プロジェクト ファイルを作成します。  また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。
   
`Hello.csproj`:

[!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。

   * `OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。
   * `TargetFramework` タグは、対象の .NET ランタイムを指定します。 高度なシナリオでは、複数の対象フレームワークを指定し、1 回の操作でそれらすべてにビルドすることができます。 このチュートリアルでは、.NET Core 1.0 の場合のビルドについてのみ説明します。

   `Program.cs`:

[!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   プログラムは `using System` で始まります。これは、"`System` 名前空間のすべてがこのファイルのスコープになる" こと意味します。 `System` 名前空間には、`string` などの基本的な構造、または数値型が含まれます。

   次に、`Hello` という名前空間を定義します。 これを必要なものに変更できます。 `Program` という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。 この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。 実際は、この配列は使用されません。プログラムはコンソールに "Hello World!" と 記述するだけです。 後に、この引数を利用するようにコードを変更します。

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) は、[NuGet](http://nuget.org) (.NET パッケージ マネージャー) を参照して依存関係のツリーを復元します。 NuGet は、*Hello.csproj* ファイルを分析し、ファイルに記載されている依存関係をダウンロードして (またはコンピューターのキャッシュから取得して)、*obj/project.assets.json* ファイルを書き込みます。  *project.assets.json* ファイルをコンパイルして実行できる必要があります。
   
   *project.assets.json* ファイルは、NuGet の依存関係およびアプリについて記述するその他の情報のグラフの永続的で完全なセットです。  このファイルは、[`dotnet build`](../tools/dotnet-build.md) や [`dotnet run`](../tools/dotnet-run.md) などの他のツールによって読み取られ、これらのツールが NuGet の依存関係とバインド解決の正しいセットでソース コードを処理できるようにします。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) は、[`dotnet build`](../tools/dotnet-build.md) を呼び出してビルド ターゲットがビルドされていることを確認した後、`dotnet <assembly.dll>` を呼び出してターゲット アプリケーションを実行します。
   
    ```
    $ dotnet run
    Hello World!
    ```

    [`dotnet build`](../tools/dotnet-build.md) を実行し、ビルド コンソール アプリケーションを実行しないでコードをコンパイルすることもできます。 これで、Windows で `dotnet bin\Debug\netcoreapp1.0\Hello.dll` を使用して (Windows 以外のシステムの場合は `/` を使用して) 実行できる DLL ファイルとしてアプリケーションがコンパイルされます。 アプリケーションには引数を指定することもできます。それについてはこのトピックの後半で説明します。

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    高度なシナリオでは、展開可能なプラットフォーム固有のファイルの自己完結型セットとしてアプリケーションをビルドし、.NET Core が必ずしもインストールされているとは限らないコンピューターに対して実行することができます。 詳細については、「[.NET Core アプリケーション展開](../deploying/index.md)」を参照してください。

### <a name="augmenting-the-program"></a>プログラムの拡張

プログラムを少し変更してみましょう。 フィボナッチ数は面白いです。アプリを実行した人に挨拶をする引数を使用するためにフィボナッチ数も追加しましょう。

1. *Program.cs* ファイルの内容を次のコードで置き換えます。

[!code-csharp[フィボナッチ](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. [`dotnet build`](../tools/dotnet-build.md) を実行し、変更内容をコンパイルします。

3. アプリにパラメーターを渡すプログラムを実行します。

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

以上です。  自由に `Program.cs` を拡張できます。

## <a name="working-with-multiple-files"></a>複数のファイルの操作

単純な&1; 回だけのプログラムには&1; つのファイルで十分ですが、より複雑なアプリを開発する場合、プロジェクトに複数のソース ファイルを用意する必要があるでしょう。先のフィボナッチのサンプルから作成してみましょう。いくつかのフィボナッチ値をキャッシュしてから、再帰機能を追加します。 

1. 次のコードを利用し、*FibonacciGenerator.cs* という名前の *Hello* ディレクトリ内に新しいファイルを追加します。

[!code-csharp[フィボナッチ ジェネレーター](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. *Program.cs* ファイルの `Main` メソッドを変更し、次の例のように新しいクラスをインスタンス化し、そのメソッドを呼び出します。

[!code-csharp[新しい Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. [`dotnet build`](../tools/dotnet-build.md) を実行し、変更内容をコンパイルします。

4. [`dotnet run`](../tools/dotnet-run.md) を実行し、アプリを実行します。 プログラムの出力は次のようになります。

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

以上です。 これで、ここで学習した基本的な概念を利用し、自分だけのプログラムを作成できます。

このチュートリアルで紹介した、アプリケーションを実行するコマンドと手順は、開発時にのみ利用されます。 アプリの展開に進むときは、.NET Core アプリの別の[展開方法](../deploying/index.md)や [`dotnet publish`](../tools/dotnet-publish.md) コマンドを利用した方が効果的な場合もあります。

## <a name="see-also"></a>関連項目

[.NET Core CLI ツールを使用したプロジェクトの整理およびテスト](testing-with-cli.md)
