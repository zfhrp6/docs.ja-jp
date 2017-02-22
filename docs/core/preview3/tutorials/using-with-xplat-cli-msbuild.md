---
title: "Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要 (.NET Core Tools RC4) | Microsoft Docs"
description: "Windows、Linux、または macOS の .NET Core での、.NET Core コマンド ライン インターフェイス (CLI) の使用に関する概要"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 4c17da61f492e17edf4d69d79be430ead3dd0cc6

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line-net-core-tools-rc4"></a>Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要 (.NET Core Tools RC4)

> [!WARNING]
> このトピックは .NET Core Tools RC4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要](../../tutorials/using-with-xplat-cli.md)」トピックを参照してください。

このガイドでは、.NET Core CLI ツールを使用してクロスプラットフォーム コンソール アプリを作成する方法を説明します。  最も基本的なコンソール アプリから始めて、最終的にテストを含む複数プロジェクトまで拡張します。 既に作成してあるものを基にして、これらの機能を追加していきます。

.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../tools/dotnet.md)」(.NET Core SDK の概要) を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

始める前に、[.NET Core CLI ツール RC4 以降](https://github.com/dotnet/core/blob/master/release-notes/preview3-download.md)があることを確認します。  テキスト エディターも必要です。

## <a name="hello-console-app"></a>Hello コンソール アプリ

最初に、適切な名前のフォルダーに移動するか、新しく作成します。  サンプル コードでは "Hello" という名前を使用しています ([こちら](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild)を参照)。

コマンド プロンプトを開いて次のように入力します。

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

簡単に説明します。

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の `Hello.csproj` プロジェクト ファイルを作成します。  また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。
   
   `Hello.csproj`:
   ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
        <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
        
        <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>netcoreapp1.0</TargetFramework>
        </PropertyGroup>

        <ItemGroup>
            <Compile Include="**\*.cs" />
            <EmbeddedResource Include="**\*.resx" />
        </ItemGroup>

        <ItemGroup>
            <PackageReference Include="Microsoft.NETCore.App">
                <Version>1.0.1</Version>
            </PackageReference>
            <PackageReference Include="Microsoft.NET.Sdk">
                <Version>1.0.0-alpha-20161104-2</Version>
                <PrivateAssets>All</PrivateAssets>
            </PackageReference>
        </ItemGroup>
        
        <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
   ```

   プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。

   * `Import` タグは、すべての .NET Core プロジェクトに共通の一部のプロパティを示します。
   * `OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。
   * `TargetFramework` タグは、対象の .NET ランタイムを指定します。 高度なシナリオでは、複数の対象フレームワークを指定し、1 回の操作でそれらすべてにビルドすることができます。 このチュートリアルでは、.NET Core 1.0 の場合のビルドについてのみ説明します。
   * `Compile` タグは、コンパイラに現在のディレクトリとすべてのサブディレクトリにある、`.cs` ファイル拡張子を持つすべてのファイル (つまり、プロジェクト内のすべての C# ファイル) をビルドするように指示します。 高度なシナリオでは、ファイルを除外できますが、このチュートリアルのほとんどの簡単なシナリオでは、この行はそのままにしておいてもかまいません。
   * `EmbeddedResource` タグは、ビルド システムに、拡張子 `.resx` を持つローカリゼーション ファイルをコンパイル済みの実行可能ファイルに埋め込むように指示します。 このチュートリアルではこの機能は使用しません。
   * `PackageReference` タグは、アプリケーションのビルド時に復元および組み込む必要がある依存関係パッケージを指定します。 各パッケージ参照は、`Include` 属性でパッケージの名前と、バージョン番号を指定します。 最も高度なシナリオでは、パッケージ参照をさらに追加します。 ディスク上の他のプロジェクトを参照することもできます。

   `Program.cs`:
   ```csharp
   using System;

   namespace ConsoleApplication
   {
       public class Program
       {
           public static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   プログラムは `using System` で始まります。これは、"`System` 名前空間のすべてがこのファイルのスコープになる" こと意味します。 `System` 名前空間には、`string` などの基本的な構造、または数値型が含まれます。

   次に、"ConsoleApplication" という名前空間を定義します。 これを必要なものに変更できます。 "Program" という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。 この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。 実際は、この配列は使用されません。プログラムはコンソールに "Hello World!" と 記述するだけです。 `Console.WriteLine` を以下のコードに変更して、もう少し面白い内容にすることができます。

   ```csharp
   if (args.Length > 0)
   {
       Console.WriteLine($"Hello {args[0]}!");
   }
   else
   {
       Console.WriteLine("Hello World!");
   }
   ```

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) は、[NuGet](http://nuget.org) (.NET のパッケージ マネージャー) を参照して依存関係のツリーを復元します。 NuGet は、`Hello.csproj` ファイルを分析し、ファイルに記載されている依存関係をダウンロードして (またはコンピューターのキャッシュから取得して)、`obj/project.assets.json` ファイルを書き込みます。  `project.assets.json` ファイルをコンパイルして実行できる必要があります。
   
   `project.assets.json` ファイルは、NuGet の依存関係およびアプリについて記述するその他の情報のグラフの永続的で完全なセットです。  このファイルは、`dotnet build` や `dotnet run` などの他のツールによって読み取られ、これらのツールが NuGet の依存関係とバインド解決の正しいセットでソース コードを処理できるようにします。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) は、`dotnet build` を呼び出してビルド ターゲットがビルドされていることを確認した後、`dotnet <assembly.dll>` を呼び出してターゲット アプリケーションを実行します。
   
    ```
    $ dotnet run
    Hello World!
    ```

    [`dotnet build`](../tools/dotnet-build.md) を実行し、ビルド コンソール アプリケーションを実行しないでコードをコンパイルすることもできます。 これで、`bin/Debug/netcoreapp1.0/Hello.dll` コンパイル済みアプリケーションを Windows では `dotnet bin\Debug\netcoreapp1.0\Hello.dll` を使用して、他のシステムでは `dotnet bin/Debug/netcoreapp1.0/Hello.dll` を使用して実行することができます。 コマンドラインで次のようにして追加のパラメーターを指定することができます (ここでは Windows を想定)。

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll .NET
    Hello .NET!
    ```

    高度なシナリオでは、展開可能なプラットフォーム固有のファイルの自己完結型セットとしてアプリケーションをビルドし、.NET Core が必ずしもインストールされているとは限らないコンピューターに対して実行することができます。 詳細については、「[.NET Core アプリケーション展開](../deploying/index.md)」を参照してください。

### <a name="augmenting-the-program"></a>プログラムの拡張

ファイルを少し変更してみます。  フィボナッチ数列を作ってみましょう。

`Program.cs`:

```csharp
using static System.Console;

namespace ConsoleApplication
{
    public class Program
    {
        public static int FibonacciNumber(int n)
        {
            int a = 0;
            int b = 1;
            int tmp;
            
            for (int i = 0; i < n; i++)
            {
                tmp = a;
                a = b;
                b += tmp;
            }
            
            return a;   
        }
        
        public static void Main(string[] args)
        {
            WriteLine("Hello World!");
            WriteLine("Fibonacci Numbers 1-15:");
            
            for (int i = 0; i < 15; i++)
            {
                WriteLine($"{i+1}: {FibonacciNumber(i)}");
            }
        }
    }
}
```

プログラムを実行します (Windows を使用し、プロジェクト ディレクトリの名前を Fibonacci に変更してあるものとします)。

```
$ dotnet build
$ dotnet bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
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

## <a name="adding-some-new-files"></a>新しいファイルの追加

1 個限りの簡単なプログラムの場合は単一のファイルが便利ですが、複数のコンポーネントがあるものを作成する場合は複数のファイルに分割することが必要になる可能性があります。  複数のファイルはそのための方法です。

新しいファイルを作成し、固有の名前空間を設定します。

```csharp
using System;

namespace NumberFun
{
    // code can go here
} 
```

次に、それを `Program.cs` ファイルに含めます。

```csharp
using NumberFun;
```

最後にビルドします。

`$ dotnet build`

新しいファイルの機能を作成します。

### <a name="example-a-fibonacci-sequence-generator"></a>例: フィボナッチ シーケンス ジェネレーター

前のフィボナッチの例を利用し、フィボナッチの値をいくつかキャッシュして再帰的な処理を加えます。  [より高度なフィボナッチ例](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetterMsBuild)のコードでは、以下のコードで新しい `FibonacciGenerator.cs` ファイルを使用できます。

```csharp
using System;
using System.Collections.Generic;

namespace NumberFun
{
    public class FibonacciGenerator
    {
        private Dictionary<int, int> _cache = new Dictionary<int, int>();
        
        private int Fib(int n) => n < 2 ? n : FibValue(n - 1) + FibValue(n - 2);
        
        private int FibValue(int n)
        {
            if (!_cache.ContainsKey(n))
            {
                _cache.Add(n, Fib(n));
            }
            
            return _cache[n];
        }
        
        public IEnumerable<int> Generate(int n)
        {
            for (int i = 0; i < n; i++)
            {
                yield return FibValue(i);
            }
        }
    }
}
```

次に、以下に示すように、`Program.cs` ファイルの `Main()` メソッドを変更します。

```csharp
using System;
using NumberFun;

class Program
{
    static void Main(string[] args)
    {
        var generator = new FibonacciGenerator();
        foreach (var digit in generator.Generate(15))
        {
            Console.WriteLine(digit);
        }
    }
}
```

最後に実行します。

```
$ dotnet run
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

以上です。

## <a name="conclusion"></a>まとめ
 
このガイドでは、.NET Core コンソール アプリの作成方法について、基礎からマルチプロジェクト システムと単体テストまで説明しました。  次は、あなた自身が優れたコンソール アプリを作る番です。
 
コンソール アプリのより高度な例については、「[.NET Core コマンド ラインを使用したプロジェクトの整理およびテスト (.NET Core Tools RC4)](using-with-xplat-cli-msbuild-folders.md)」というチュートリアルを参照してください。



<!--HONumber=Feb17_HO2-->


