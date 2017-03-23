---
title: "macOS での .NET Core の概要"
description: "Visual Studio Code を使用した macOS での .NET Core の概要"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: c4d1b7690ca87f2a1a9ced4d82e47aee2f7ecc9f
ms.lasthandoff: 03/07/2017

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-code"></a>Visual Studio Code を使用した macOS での .NET Core の概要

このドキュメントでは、[Visual Studio Code](http://code.visualstudio.com) を使用して .NET Core ソリューションを作成する手順とワークフローを説明します。
プロジェクトを作成し、単体テストを作成し、デバッグ ツールを使用し、[NuGet](http://nuget.org) からサードパーティ製ライブラリを組み込む方法について説明します。

この記事では、Mac OS で Visual Studio Code を使用します。 Windows プラットフォームと違う場合は指摘します。

## <a name="prerequisites"></a>必須コンポーネント

始める前に、[.NET Core SDK](https://www.microsoft.com/net/core) をインストールする必要があります。 .NET Core SDK には、.NET Core のフレームワークとランタイムの最新リリースが含まれています。

[Visual Studio Code](http://code.visualstudio.com) のインストールも必要です。
この記事の中では、.NET Core の開発エクスペリエンスが向上する拡張機能もインストールします。

## <a name="getting-started"></a>作業の開始

このチュートリアルのソースは、[GitHub](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) で提供されています。

Visual Studio Code を開始します。 Ctrl + \` (逆引用符) キーを押して、VS Code で埋め込みターミナルを開きます (または、その方がよければ別のターミナル ウィンドウを使うこともできます)。

このガイドでは&3; つのプロジェクトを作成します。ライブラリ プロジェクト、そのライブラリ プロジェクトのテスト、ライブラリを使用するコンソール アプリケーションです。 

最初にこれらのフォルダーを作成します。 ターミナルで、"golden" ディレクトリを作成します。 VS Code で、*golden* ディレクトリを開きます。 このディレクトリはソリューションのルートです。 [`dotnet new`](../tools/dotnet-new.md) コマンドを実行して新しいソリューションを作成する:

```
dotnet new sln
```

このコマンドにより、ソリューション全体の *golden.sln* ファイルが作成されます。

次にライブラリを作成します。 ターミナル ウィンドウ (VS Code の埋め込みターミナルまたは別のターミナル) で、ディレクトリを *golden/* に移動し、コマンドを入力します。

```
dotnet new classlib -o library
```

これでライブラリ プロジェクトと&2; つのファイル (*library.csproj* と *Class1.cs*) が *library* ディレクトリに作成されます。 そのライブラリ プロジェクトをソリューションに追加します。 [`dotnet sln`](../tools/dotnet-sln.md) コマンドを実行し、新しく作成された *library.csproj* プロジェクトをソリューションに追加します。

```
dotnet sln add library/library.csproj
```

作成したプロジェクトを確認しましょう。 *library.csproj* ファイルには、次の情報が含まれています。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

このライブラリ プロジェクトはオブジェクトの JSON 表現を使用するので、`Newtonsoft.Json` NuGet パッケージへの参照を追加します。 `dotnet add` コマンドにより、新しい項目がプロジェクトに追加されます。 NuGet パッケージに参照を追加するには、`package` コマンドを使用し、パッケージの名前を指定します。 

```
dotnet add library package Newtonsoft.Json
```

これにより `Newtonsoft.Json` とその依存関係がライブラリ プロジェクトに追加されます。 あるいは、*library.csproj* ファイルを手動で編集し、次のノードを追加できます。

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1</Version>
  </PackageReference>
</ItemGroup>
```

これらの依存関係の追加が完了した後、ワークスペースにこれらのパッケージをインストールする必要があります。 `dotnet restore` コマンドを実行してすべての依存関係を更新し、*obj/project.assets.json* ファイルをプロジェクト ディレクトリに書き込みます。 このファイルには、プロジェクト内のすべての依存関係の完全な依存関係ツリーが含まれています。 このファイルを読む必要はありません。.NET Core SDK のツールによって使用されます。

次に、C# のコードを更新します。 パブリック メソッドを&1; つ含む `Thing` クラスを作成します。 このメソッドは&2; つの数値の合計を返しますが、そのためには、値を JSON 文字列に変換した後、それを逆シリアル化します。 ファイル *Class1.cs* の名前を *Thing.cs* に変更します。 次に、既存のコード (テンプレートによって生成された Class1) を次のように置き換えます。

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

このコードでは、静的な using、式本体のメンバー、補間文字列など、C# の最新の機能を利用しています。これらについては、[C# の詳細](../../csharp/index.md)に関するセクションを参照してください。

コードを更新したので、`dotnet build` を使用してライブラリをビルドできます。

これで *golden/library/bin/Debug/netstandard1.4* に *library.dll* ファイルがビルドされました。

### <a name="writing-the-test-project"></a>テスト プロジェクトの作成

ビルドしたライブラリのテスト プロジェクトを作成します。 *golden* ディレクトリに移動します。 `dotnet new xunit -o test-library` を実行して新しいテスト プロジェクトを作成します。 `dotnet sln add test-library/test-library.csproj` を実行し、このプロジェクトをソリューションに追加することもできます。

前の手順で作成したライブラリの依存関係ノードを追加する必要があります。 `dotnet add reference` コマンドで次が実行されます。

```
dotnet add test-library/test-library.csproj reference library/library.csproj
```

あるいは、*test-library.csproj* ファイルを手動で編集し、次のノードを追加できます。

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

`library` ノードでは、この依存関係を現在のワークスペースのプロジェクトに解決する必要があることが指定されています。 これを明示的に指定しないと、同じ名前の NuGet パッケージに対してテスト プロジェクトがビルドされる可能性があります。

依存関係を正しく構成したので、ライブラリのテストを作成します。 *UnitTest1.cs* を開き、内容を次のコードに置き換えます。

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.Equal(42, new Thing().Get(19, 23));
        }
    }
}
```

次に、`dotnet restore` と `dotnet build` を実行します。 これらのコマンドにより、依存関係を復元し、ビルドするためのすべてのプロジェクトが再帰的に検索されます。
最後に、`dotnet test test-library/test-library.csproj` を実行し、テストを実行します。
XUnit コンソールのテスト ランナーは、1 つのテストを実行して合格したことをレポートします。 

### <a name="writing-the-console-app"></a>コンソール アプリの作成

端末で `dotnet new console -o app` を実行して新しいコンソール アプリケーションを作成します。 このプロジェクトはソリューションの一部でもあります。そのため、`dotnet sln add app/app.csproj` を実行し、プロジェクトをソリューションに追加します。

コンソール アプリケーションは、前の手順でビルドしてテストしたライブラリに依存します。 `dotnet add reference` をもう一度実行し、それを示す必要があります。

```
dotnet add app/app.csproj reference library/library.csproj
```

`dotnet restore` を実行してすべての依存関係を復元します。 *program.cs* を開き、`Main` メソッドの内容を次の行に置き換えます。

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

2 つの `using` ディレクティブをファイルの先頭に追加する必要があります。

```csharp
using static System.Console;
using Library;
```

その後、`dotnet build` を実行します。 アセンブリが作成されるので、「`dotnet run -p app/app.csproj`」と入力して実行可能ファイルを実行できます。
`dotnet run` の `-p` 引数は、メイン アプリケーションのプロジェクトを指定します。

### <a name="debugging-your-application"></a>アプリケーションのデバッグ

C# の拡張機能を使用して VS Code でコードをデバッグできます。
この拡張機能をインストールするには、`F1` キーを押して VS Code パレットを開きます。 「`ext install`」と入力して、拡張機能の一覧を表示します。 C# 拡張機能を選択します。 詳細については、[Visual Studio Code C# 拡張機能のドキュメント](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)を参照してください。

拡張機能をインストールした後、VS Code でアプリケーションを再起動して新しい拡張機能を読み込むように求められます。 拡張機能のインストールが済むと、デバッガー タブを開くことができます (図を参照)。

![VS Code のデバッガー](./media/using-on-macos/vscodedebugger.png)

`Main` の `WriteLine` ステートメントにブレークポイントを設定します。 そのためには、`F9` キーを押すか、ブレークポイントを設定する行の左側の余白をクリックします。 VS Code 画面左側のデバッグ アイコンをクリックしてデバッガーを開きます (図を参照)。 その後、[再生] ボタンをクリックしてデバッガーでアプリケーションを開始します。

ブレークポイントがヒットします。 `Get` メソッドにステップ インし、正しい引数を渡したことを確認します。 答えが実際に 42 であることを確認してください。

