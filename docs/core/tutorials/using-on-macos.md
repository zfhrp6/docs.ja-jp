---
title: "macOS での .NET Core の概要"
description: "Visual Studio Code を使用した macOS での .NET Core の概要"
keywords: .NET, .NET Core
author: bleroy
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
translationtype: Human Translation
ms.sourcegitcommit: 2339be6aef7e2ff942f1f1999a12f48ee4a77ee8
ms.openlocfilehash: b9d53f32347572614a67e1cc432089f8e18d7cdf

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-code"></a>Visual Studio Code を使用した macOS での .NET Core の概要

著者: [Bertrand Le Roy](https://github.com/bleroy)、[Phillip Carter](https://github.com/cartermp)、[Bill Wagner](https://github.com/billwagner)

協力: [Toni Solarin-Sodara](https://github.com/tsolarin)

このドキュメントでは、[Visual Studio Code](http://code.visualstudio.com) を使用して .NET Core ソリューションを作成する手順とワークフローを説明します。
プロジェクトを作成し、単体テストを作成し、デバッグ ツールを使用し、[NuGet](http://nuget.org) からサードパーティ製ライブラリを組み込む方法について説明します。

この記事では、Mac OS で Visual Studio Code を使用します。 Windows プラットフォームと違う場合は指摘します。

## <a name="prerequisites"></a>必須コンポーネント

始める前に、現在はプレビュー リリースである [.NET Core SDK](https://www.microsoft.com/net/core) をインストールする必要があります。 .NET Core SDK には、.NET Core のフレームワークとランタイムの最新リリースが含まれています。

[Visual Studio Code](http://code.visualstudio.com) のインストールも必要です。
この記事の中では、.NET Core の開発エクスペリエンスが向上する拡張機能もインストールします。

これらへのリンクはすべて、[.NET のホーム ページ](http://dot.net)にあります。

## <a name="getting-started"></a>作業の開始

このチュートリアルのソースは、[GitHub](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) で提供されています。

Visual Studio Code を開始します。 Ctrl + \` (逆引用符) キーを押して、VS Code で埋め込みターミナルを開きます (または、その方がよければ別のターミナル ウィンドウを使うこともできます)。

このガイドでは 3 つのプロジェクトを作成します。ライブラリ プロジェクト、そのライブラリ プロジェクトのテスト、ライブラリを使用するコンソール アプリケーションです。 これら 3 つのプロジェクトには標準的なフォルダー構造を使用します。 この標準フォルダー構造に従うことで、.NET Core SDK のツールは、運用コード プロジェクトとテスト コード プロジェクトの間の関係を理解できます。 これにより、開発環境の生産性が向上します。

最初にこれらのフォルダーを作成します。 ターミナルで、"golden" ディレクトリを作成します。 そのディレクトリの下に、`src` ディレクトリと `test` ディレクトリを作成します。 `src` の下に、`app` ディレクトリと `library` ディレクトリを作成します。 `test` に、`test-library` ディレクトリを作成します。 これは、VS Code のターミナルを使用して、または VS Code で親フォルダーをクリックして [新しいフォルダー] アイコンをクリックすることにより、行うことができます。

VS Code で、"golden" ディレクトリを開きます。 このディレクトリはソリューションのルートです。

次に、ソリューションのルート ディレクトリに `global.json` ファイルを作成します。
`global.json` の内容は次のとおりです。

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

この時点で、ディレクトリ ツリーは次のようになります。


```
/golden
|__global.json
|__/src
   |__/app
   |__/library
|__/test
   |__/test-library
```

### <a name="writing-the-library"></a>ライブラリの作成

次にライブラリを作成します。 ターミナル ウィンドウ (VS Code の埋め込みターミナルまたは別のターミナル) で、ディレクトリを `golden/src/library` に移動し、`dotnet new -t lib` コマンドを入力します。
2 つのファイル `project.json` と `Library.cs` を含むライブラリ プロジェクトが作成されます。

`project.json`には次の情報が含まれます。

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {},
  "frameworks": {
    "netstandard1.6": {
      "dependencies": {
        "NETStandard.Library": "1.6.0"
      }
    }
  }
}
```


このライブラリ プロジェクトはオブジェクトの JSON 表現を使用するので、`Newtonsoft.Json` NuGet パッケージへの参照を追加します。 `project.json` に、パッケージの最新プレリリース バージョンを依存関係として追加します。

```json
"dependencies": {
    "Newtonsoft.Json": "9.0.1-beta1"
},
```

これらの依存関係の追加が完了した後、ワークスペースにこれらのパッケージをインストールする必要があります。 `dotnet restore` コマンドを実行してすべての依存関係を更新し、`project.lock.json` ファイルをプロジェクト ディレクトリに書き込みます。 このファイルには、プロジェクト内のすべての依存関係の完全な依存関係ツリーが含まれています。 このファイルを読む必要はありません。.NET Core SDK のツールによって使用されます。

次に、C# のコードを更新します。 パブリック メソッドを 1 つ含む `Thing` クラスを作成します。 このメソッドは 2 つの数値の合計を返しますが、そのためには、値を JSON 文字列に変換した後、それを逆シリアル化します。 ファイルの名前を `Library.cs` から `Thing.cs` に変更します。 次に、既存のコード (テンプレートによって生成された Class1) を次のように置き換えます。

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

このコードでは、静的 using、式本体のメンバー、補間文字列など、C# の最新の機能を利用しています。これらについては、「[Learn C#](../../csharp/index.md)」(C# ガイド) を参照してください。

コードを更新したので、`dotnet build` を使用してライブラリをビルドできます。

ビルドされた `library.dll` ファイルは `golden/src/library/bin/Debug/netstandard1.6` にあります。

### <a name="writing-the-test-project"></a>テスト プロジェクトの作成

ビルドしたライブラリのテスト プロジェクトを作成します。 `test/test-library` ディレクトリに移動します。 `dotnet new -t xunittest` を実行して新しいテスト プロジェクトを作成します。 

前の手順で作成したライブラリの依存関係ノードを追加する必要があります。 `project.json` を開き、dependencies セクションを次のように更新します (最後の `library` ノードも含みます)。

```json
"dependencies": {
  "System.Runtime.Serialization.Primitives": "4.1.1",
  "xunit": "2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "library": {
    "target": "project"
  }
}
```

`library` ノードでは、この依存関係を現在のワークスペースのプロジェクトに解決する必要があることが指定されています。 これを明示的に指定しないと、同じ名前の NuGet パッケージに対してテスト プロジェクトがビルドされる可能性があります。

依存関係を正しく構成したので、ライブラリのテストを作成します。 `Tests.cs` を開き、内容を次のコードに置き換えます。

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

次に、`dotnet restore`、`dotnet build`、`dotnet test` を実行します。
XUnit コンソールのテスト ランナーは、1 つのテストを実行して合格したことをレポートします。 

### <a name="writing-the-console-app"></a>コンソール アプリの作成

ターミナルで、`golden/src/app` ディレクトリに移動します。 `dotnet new` を実行して新しいコンソール アプリケーションを作成します。

コンソール アプリケーションは、前の手順でビルドしてテストしたライブラリに依存します。 `project.json` を編集してこの依存関係を追加することにより、そのことを示す必要があります。  `dependencies` ノードで、次のように `library` ノードを追加します。

```json
"dependencies": {
  "library": {
    "target": "project"
  }
}
```

テスト ライブラリのときと同じように、ここでも `project` ノードが重要です。 これが現在のソリューションのプロジェクトであり、NuGet パッケージのプロジェクトではないことを示します。

`dotnet restore` を実行してすべての依存関係を復元します。 `program.cs` を開き、`Main` メソッドの内容を次の行に置き換えます。

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

2 つの `using` ディレクティブをファイルの先頭に追加する必要があります。

```csharp
using static System.Console;
using Library;
```

その後、`dotnet build` を実行します。 アセンブリが作成されるので、「`dotnet run`」と入力して実行可能ファイルを実行できます。

### <a name="debugging-your-application"></a>アプリケーションのデバッグ

C# の拡張機能を使用して VS Code でコードをデバッグできます。
この拡張機能をインストールするには、`F1` キーを押して VS Code パレットを開きます。 「`ext install`」と入力して、拡張機能の一覧を表示します。 C# 拡張機能を選択します。 詳細については、[Visual Studio Code C# 拡張機能のドキュメント](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)を参照してください。

拡張機能をインストールした後、VS Code でアプリケーションを再起動して新しい拡張機能を読み込むように求められます。 拡張機能のインストールが済むと、デバッガー タブを開くことができます (図を参照)。

![VS Code のデバッガー](./media/using-on-macos/vscodedebugger.png)


デバッガーを起動すると、デバッガーを構成するように指示されます。 構成を行うと、`.vscode` ディレクトリと 2 つのファイル `tasks.json` および `launch.json` が作成されます。 これら 2 つのファイルはデバッガーの構成を制御します。 ほとんどのプロジェクトでは、このディレクトリはソース管理に含まれません。
このチュートリアルに関連付けられているサンプルに含まれるので、必要な編集を確認できます。

ソリューションには複数のプロジェクトが含まれているので、正しいコマンドを実行するには各ファイルを変更する必要があります。 最初に、`tasks.json` を開きます。 既定のビルド タスクは、ワークスペースのソース ディレクトリの `dotnet build` を実行します。 代わりに、`src/app` ディレクトリのものを実行する必要があります。 `options` ノードを追加し、現在の作業ディレクトリをそれに設定します。

```json
"options": {
    "cwd": "${workspaceRoot}/src/app"
}
```

次に、`launch.json` を開き、プログラムのパスを更新します。 "configurations" の下にプログラムを記述しているノードがあります。 次のように表示されます。

```json
"program": "${workspaceRoot}/bin/Debug/<target-framework>/<project-name.dll>",
```

これを次のように変更します。

```json
"program": "${workspaceRoot}/src/app/bin/Debug/netcoreapp1.0/app.dll",
```

Windows で実行している場合は、アプリケーションの `project.json` (`src/app` ディレクトリにあります) を更新し、ポータブル PDB ファイルを生成する必要があります (Mac OSX と Linux では既定でこのようになります)。
`buildOptions` に `debugType` ノードを追加します。 `src/app` フォルダーと `src/library` フォルダー両方の `project.json` に `debugType` ノードを追加します。

```json
  "buildOptions": {
    "debugType": "portable"
  },
```

`Main` の `WriteLine` ステートメントにブレークポイントを設定します。 そのためには、`F9` キーを押すか、ブレークポイントを設定する行の左側の余白をクリックします。 VS Code 画面左側のデバッグ アイコンをクリックしてデバッガーを開きます (図を参照)。 その後、[再生] ボタンをクリックしてデバッガーでアプリケーションを開始します。

ブレークポイントがヒットします。 `Get` メソッドにステップ インし、正しい引数を渡したことを確認します。 答えが実際に 42 であることを確認してください。



<!--HONumber=Nov16_HO3-->


