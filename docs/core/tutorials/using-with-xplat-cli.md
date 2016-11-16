---
title: "Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要"
description: "Windows、Linux、または macOS の .NET Core での、.NET Core コマンド ライン インターフェイス (CLI) の使用に関する概要"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: be988f09-7349-43b0-97fb-3a703d4587ce
translationtype: Human Translation
ms.sourcegitcommit: aeb199a9aeb1584570ad2a2942e2f22c75a59616
ms.openlocfilehash: aafa0c110dc3a2820f7e050d70b9450af1db35d8

---

# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要

このガイドでは、.NET Core CLI ツールを使用してクロスプラットフォーム コンソール アプリを作成する方法を説明します。  最も基本的なコンソール アプリから始めて、最終的にテストを含む複数プロジェクトまで拡張します。 既に作成してあるものを基にして、これらの機能を追加していきます。

.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../sdk.md)」(.NET Core SDK の概要) を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

始める前に、[最新の .NET Core CLI ツール](https://www.microsoft.com/net/core)があることを確認します。  テキスト エディターも必要です。

## <a name="hello-console-app"></a>Hello コンソール アプリ

最初に、適切な名前のフォルダーに移動するか、新しく作成します。  サンプル コードでは "Hello" という名前を使用しています ([こちら](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Hello)を参照)。

コマンド プロンプトを開いて次のように入力します。

```
$ dotnet new
$ dotnet restore
$ dotnet run
```

簡単に説明します。

1. `$ dotnet new`

   [`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な NuGet 依存関係を含む最新の `project.json` ファイルを作成します。  また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。
   
   `project.json`:
   ```json
   {
        "version": "1.0.0-*",
        "buildOptions": {
            "emitEntryPoint": true
        },
        "dependencies": {
            "Microsoft.NETCore.App": {
                "type": "platform",
                "version": "1.0.0"
            }
        },   
       "frameworks": {
            "netcoreapp1.0": {
                "imports": "dnxcore50"
            }
        }
   }
   ```
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

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) は、NuGet を参照して依存関係のツリーを復元します。 NuGet は、`project.json` ファイルを分析し、ファイルに記載されている依存関係をダウンロードして (またはコンピューターのキャッシュから取得して)、`project.lock.json` ファイルを書き込みます。  `project.lock.json` ファイルをコンパイルして実行できる必要があります。
   
   `project.lock.json` ファイルは、NuGet の依存関係およびアプリについて記述するその他の情報のグラフの永続的で完全なセットです。  このファイルは、`dotnet build` や `dotnet run` などの他のツールによって読み取られ、これらのツールが NuGet の依存関係とバインド解決の正しいセットでソース コードを処理できるようにします。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) は、`dotnet build` を呼び出してビルド ターゲットがビルドされていることを確認した後、`dotnet <assembly.dll>` を呼び出してターゲット アプリケーションを実行します。
   
```
$ dotnet run
Hello, World!
```

[`dotnet build`](../tools/dotnet-build.md) を実行し、ビルド コンソール アプリケーションを実行しないでコードをコンパイルすることもできます。

### <a name="building-a-selfcontained-application"></a>自己完結型アプリケーションのビルド

ポータブル アプリケーションではなく自己完結型アプリケーションをコンパイルします。 異なる種類のアプリケーションとその展開方法については、[.NET Core での移植性の種類についての記事](../deploying/index.md)を参照してください。

自己完結型アプリケーションを構築するようツールに指示するには、`project.json` ファイルを変更する必要があります。 これについては、サンプル ディレクトリの [HelloNative](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloNative) プロジェクトを参照してください。

最初の変更として、すべての依存関係から `"type": "platform"` 要素を削除します。 今のところ、このプロジェクトの依存関係は `"Microsoft.NETCore.App"` だけです。 `dependencies` セクションは次のようになります。

```json
"dependencies": {
    "Microsoft.NETCore.App": {
        "version": "1.0.0"
    }
},
```

次に、`runtimes` ノードを追加してすべてのターゲット実行環境を指定する必要があります。 たとえば、次の `runtimes` ノードは、64 ビット版 Windows 10 および 64 ビット版 Mac OS X バージョン 10.11 用の実行可能ファイルを作成するようビルド システムに指示します。
ビルド システムは、現在の環境のネイティブ実行可能ファイルを生成します。 Windows コンピューターでこの手順に従うと、Windows の実行可能ファイルがビルドされます。 Mac でこの手順に従うと、OS X の実行可能ファイルがビルドされます。

```json 
"runtimes": {
  "win10-x64": {},
  "osx.10.11-x64": {}
}
```

サポートされているランタイムの完全な一覧は、[RID カタログ](../rid-catalog.md)を参照してください。 
 
これら 2 つの変更を行った後、`dotnet restore` を実行し、次に `dotnet build` を実行してネイティブな実行可能ファイルを作成します。 その後、生成されたネイティブ実行可能ファイルを実行できます。 

次の例では Windows の場合のコマンドを示します。 この例では、ネイティブ実行可能ファイルが生成される場所が示されており、プロジェクト ディレクトリの名前は HelloNative です。

```
$ dotnet restore 
$ dotnet build 
$ .\bin\Debug\netcoreapp1.0\win10-x64\HelloNative.exe
Hello World!
```

ネイティブ アプリケーションは、ビルドに要する時間は少し長くなりますが、実行は若干速くなります。 この現象は、アプリケーションが大きくなるほど顕著になります。

`project.json` がネイティブ ビルドを作成するときは、ビルド プロセスで生成されるファイルが増えます。 これらのファイルは `bin\Debug\netcoreapp1.0\<platform>` に作成されます。`<platform>` は選択された RID です。 プロジェクトの `HelloNative.dll` に加えて、ランタイムを読み込んでアプリケーションを開始する `HelloNative.exe` があります。
プロジェクト ディレクトリの名前を変更したので、生成されるアプリケーションの名前が変わっていることに注意してください。  

このアプリケーションをパッケージ化し、.NET ランタイムが含まれないコンピューターで実行することができます。
そのためには、`dotnet publish` コマンドを使用します。 `dotnet publish` コマンドは、`./bin/Debug/netcoreapp1.0/<platform>` ディレクトリの下に `publish` という名前の新しいサブディレクトリを作成します。 実行可能ファイル、依存するすべての DLL、およびフレームワークが、このサブディレクトリにコピーされます。 そのディレクトリを別のコンピューター (またはコンテナー) にパッケージ化し、そこでアプリケーションを実行できます。 

そのアプリケーションを、最初の Hello World サンプルでの `dotnet publish` の動作と比較してみます。 そのアプリケーションは "*ポータブル アプリケーション*" であり、これは .NET Core 用アプリケーションの既定の種類です。 ポータブル アプリケーションを実行するには、ターゲット コンピューターに .NET Core がインストールされている必要があります。 ポータブル アプリケーションは、ビルドしたコンピューターとは別のコンピューターで実行できます。 ネイティブ アプリケーションは、ターゲット マシンごとに個別に作成する必要があります。 `dotnet publish`が作成するディレクトリには、アプリケーションの DLL と、プラットフォームのインストールに含まれないすべての依存 DLL が格納されます。

### <a name="augmenting-the-program"></a>プログラムの拡張

ファイルを少し変更してみます。  フィボナッチ数列を作ります (ネイティブのバージョンを使用します)。

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
$ .\bin\Debug\netcoreapp1.0\win10-x64\Fibonacci.exe
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
using static System.Console;
using NumberFun;
```

最後にビルドします。

`$ dotnet build`

新しいファイルの機能を作成します。

### <a name="example-a-fibonacci-sequence-generator"></a>例: フィボナッチ シーケンス ジェネレーター

前の[フィボナッチの例](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/Fibonacci)を利用し、フィボナッチ数をいくつかキャッシュして再帰的な処理を加えます。  [改良版フィボナッチの例](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/FibonacciBetter)のコードは次のようになります。

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

`Dictionary<int, int>` および `IEnumerable<int>` を使用して `System.Collections` 名前空間を組み込んでいることに注意してください。
`Microsoft.NetCore.App` パッケージは "*メタパッケージ*" であり、.NET Framework の多くのコア アセンブリを含みます。 このメタパッケージを含めることで、プロジェクトに `System.Collections.dll` アセンブリが組み込まれます。 このことを確認するには、`dotnet publish` を実行し、インストールされたパッケージに含まれるファイルを調べます。 `System.Collections.dll` が一覧に含まれることがわかります。 

```json
{ 
  "version": "1.0.0-*", 
  "buildOptions": { 
    "debugType": "portable", 
    "emitEntryPoint": true 
  }, 
  "dependencies": {}, 
  "frameworks": { 
    "netcoreapp1.0": { 
      "dependencies": { 
        "Microsoft.NETCore.App": { 
          "version": "1.0.0" 
        } 
      }, 
      "imports": "dnxcore50" 
    } 
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.11-x64": {}
  }
}
```

次に、以下に示すように、`Program.cs`  ファイルの `Main()` メソッドを変更します。 この例では、`Program.cs` に `using System;` ステートメントがあるものと想定しています。 `using static System.Console;` ステートメントがある場合は、`Console.` を `Console.WriteLine` から削除します。  

```csharp
public static void Main(string[] args)
{
    var generator = new FibonacciGenerator();
    foreach (var digit in generator.Generate(15))
    {
        WriteLine(digit);
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

## <a name="using-folders-to-organize-code"></a>フォルダーを使用してコードを整理する

新しい種類の作業を導入したいものとします。  そのためには、ファイルを追加し、`Program.cs` ファイルに含めることができる名前空間を割り当てます。

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__project.json
```

プロジェクトのサイズが比較的小さい場合に適しています。  しかし、多くの異なる種類のデータを含み、複数レイヤーになる可能性のある大規模なアプリケーションでは、論理的な整理が必要になります。  その場合はフォルダーを使用します。  このガイドで説明する [NewTypes サンプル プロジェクト](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes)に従うことも、独自のファイルとフォルダーを作成することもできます。

最初に、プロジェクトのルートの下に新しいフォルダーを作成します。  `/Model`がここでは選択されています。

```
/NewTypes
|__/Model
|__Program.cs
|__project.json
```

フォルダーに新しい種類をいくつか追加します。

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__project.json
```

同じディレクトリ内のファイルであった場合と同じように、すべてを同じ名前空間にするので、`Program.cs` に含めることができます。

### <a name="example-pet-types"></a>例: ペットの種類

この例では、2 つの新しい種類 `Dog` と `Cat` を作成し、インターフェイス `IPet` を実装します。

フォルダーの構造:

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__project.json
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`project.json`:
```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "emitEntryPoint": true
  },
  "dependencies": {
    "Microsoft.NETCore.App": {
      "type": "platform",
      "version": "1.0.0"
    }
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": "dnxcore50"
    }
  }
}
```

これを実行すると次のようになります。

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

新しいペットの種類 (`Bird` など) を追加して、このプロジェクトを拡張できます。

## <a name="testing-your-console-app"></a>コンソール アプリのテスト

どこかの時点でプロジェクトをテストする必要があります。  次に適切な方法を示します。

1. 既存プロジェクトのすべてのソースを、新しい `src` フォルダーに移動します。

   ```
   /Project
   |__/src
   ```

2. `/test` ディレクトリを作成します。

   ```
   /Project
   |__/src
   |__/test
   ```

3. 新しい `global.json` ファイルを作成します。

   ```
   /Project
   |__/src
   |__/test
   |__global.json
   ```

   `global.json`:
   ```json
   {
      "projects": [
         "src", "test"
      ]
   }
   ```

   このファイルは、これがマルチプロジェクト システムであることをビルド システムに伝えます。これにより、ビルド システムは現在実行しているフォルダー以外でも依存関係を検索します。  これは、テスト プロジェクトのテスト対象コードに依存関係を配置できるので重要です。
   
### <a name="example-extending-the-newtypes-project"></a>例: NewTypes プロジェクトの拡張

プロジェクト システムを設定したので、テスト プロジェクトを作成し、テストの作成を始めることができます。  これ以降このガイドでは、[サンプルの Types プロジェクト](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypes)を使用して拡張します。  さらに、[Xunit](https://xunit.github.io/) テスト フレームワークを使用します。  この手順に従っても、独自のマルチプロジェクト システムを作成してもかまいません。


プロジェクト全体の構造は、次のようになります。

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__project.json
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__project.json
|__global.json
```

テスト プロジェクトに必要な 2 つの新しい要素があります。

1. 以下のものを含む正しい `project.json`:

   * 次のものへの参照:`xunit`
   * 次のものへの参照:`dotnet-test-xunit`
   * テスト対象コードに対応する名前空間への参照

2. Xunit テスト クラス。

`NewTypesTests/project.json`:
```json
{
  "version": "1.0.0-*",
  "testRunner": "xunit",

  "dependencies": {
    "Microsoft.NETCore.App": {
      "type":"platform",
      "version": "1.0.0"
    },
    "xunit":"2.2.0-beta2-build3300",
    "dotnet-test-xunit": "2.2.0-preview2-build1029",
    "NewTypes": "1.0.0"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "portable-net45+win8" 
      ]
    }
  }
}
```

`PetTests.cs`: 
```csharp
using System;
using Xunit;
using Pets;
public class PetTests
{
    [Fact]
    public void DogTalkToOwnerTest()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerTest()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.Equal(expected, actual);
    }
}
```
   
これでテストを実行することができます。  [`dotnet test`](../tools/dotnet-test.md) コマンドは、プロジェクトで指定したテスト ランナーを実行します。 最上位レベルのディレクトリで開始します。
 
```
$ dotnet restore
$ cd test/NewTypesTests
$ dotnet test
```
 
出力は次のようになります。
 
```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```
 
## <a name="conclusion"></a>まとめ
 
このガイドでは、.NET Core コンソール アプリの作成方法について、基礎からマルチプロジェクト システムと単体テストまで説明しました。  次は、あなた自身が優れたコンソール アプリを作る番です。
 
さらに高度なコンソール アプリの例に興味がある場合は、「[Writing .NET Core console apps using the CLI tools: An advanced step-by-step guide](cli-console-app-tutorial-advanced.md)」(CLI ツールを用いた .NET Core コンソール アプリの作成: 高度なステップ バイ ステップ ガイド) をご覧ください。



<!--HONumber=Nov16_HO1-->


