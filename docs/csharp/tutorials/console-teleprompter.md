---
title: "コンソール アプリケーション"
description: "このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 41e8976e7b133380687a65265fd5ebe9a810a4ff
ms.lasthandoff: 03/13/2017

---

# <a name="console-application"></a>コンソール アプリケーション

## <a name="introduction"></a>はじめに
このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。 内容は以下の通りです。
*    .NET Core コマンド ライン インターフェイス (CLI) の基本
*    C# コンソール アプリケーションの構造
*    コンソール入出力
*    .NET Core でのファイル入出力 API の基本
*    .NET Core でのタスク非同期プログラミング モデルの基本

テキスト ファイルを読み取って、そのテキスト ファイルの内容をコンソールにエコーするアプリケーションをビルドします。 コンソールへの出力を、内容を読み上げる速度に合わせるようにします。 ‘<’ または ‘>’ キーを押して、速度を速めたり遅めたりできます。

このチュートリアルには、多くの機能が含まれています。 それらを 1 つずつビルドしてみましょう。 
## <a name="prerequisites"></a>必須コンポーネント
お使いのコンピューターを、.NET Core が実行するように設定する必要があります。 インストールの指示については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。 このアプリケーションは、Windows、Linux、macOS または Docker コンテナーで実行できます。 お好みのコード エディターをインストールしてください。 
## <a name="create-the-application"></a>アプリケーションを作成する
まず最初に新しいアプリケーションを作成します。 コマンド プロンプトを開き、アプリケーション用の新しいディレクトリを作成します。 それを、現在のディレクトリとしてください。 コマンド プロンプトで `dotnet new console` のコマンドを入力します。 これで、基本的な "Hello World" アプリケーションのスターター ファイルが作成されます。

変更を加える前に、このシンプルな Hello World アプリケーションを実行する手順を見ていきましょう。 アプリケーション作成後、コマンド プロンプトで `dotnet restore` と入力します。 このコマンドにより、NuGet パッケージの復元処理が実行されます。 NuGet は .NET パッケージ マネージャーです。 このコマンドにより、プロジェクトの依存関係のうち欠落しているものがすべてダウンロードされます。 これは新しいプロジェクトなので、依存関係は何もなく、最初の実行で .NET Core フレームワークがダウンロードされます。 最初のこの手順の後は、新しい依存パッケージを追加するときに `dotnet restore` を実行するか、依存関係のいずれかのバージョンを更新する必要しかありません。 このプロセスでは、プロジェクト ディレクトリ内にプロジェクト ロック ファイル (project.lock.json) も作成されます。 このファイルは、プロジェクトの依存関係を管理するのに役立ちます。 ファイルには、プロジェクトの依存関係すべてのローカルの場所が含まれています。 このファイルはソース コントロールに配置する必要はありません。`dotnet restore` を実行するときに生成されるためです。 

パッケージを復元したら、`dotnet build` を実行します。 これにより、ビルド エンジンが実行され、アプリケーション実行可能ファイルが作成されます。 最後に、`dotnet run` を実行してアプリケーションを実行します。  

シンプルな Hello World アプリケーションのコードはすべて Program.cs に含まれています。 使い慣れたテキスト エディターでそのファイルを開きます。 最初の変更を加えてみましょう。
ファイルの上部に、using ステートメントがあります。

```csharp
using System;
```

このステートメントは、`System` 名前空間からのいずれの型もスコープ内にあることをコンパイラに伝えています。 お使いになったことのある他のオブジェクト指向の言語と同じく、C# では名前空間を使用して型を整理します。 この Hello World プログラムも同様です。 プログラムが `ConsoleApplication` 名前空間に含まれていることがわかります。 名前があまりわかりやすくないので、`TeleprompterConsole` に変更します。

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>ファイルの読み取りとエコー
最初に追加する機能は、テキスト ファイルを読み取り、そのテキストすべてをコンソールに表示するものです。 まず、テキスト ファイルを追加しましょう。 この[サンプル](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter)の GitHub リポジトリから、[sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) ファイルをプロジェクト ディレクトリにコピーします。 これがアプリケーションのスクリプトとして機能します。

次に、以下のメソッドを Program クラス (`Main` メソッドの右下) に追加します。

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

このメソッドは、2 つの新しい名前空間の型を使用します。 これをコンパイルするには、ファイルの先頭に次の 2 行を追加する必要があります。

```csharp
using System.Collections.Generic;
using System.IO;
```

`IEnumerable<T>` インターフェイスは `System.Collections.Generic` 名前空間で定義されます。 @System.IO.File クラスは `System.IO` 名前空間で定義されます。

このメソッドは*列挙子メソッド*と呼ばれる特殊な種類の C# メソッドです。 列挙子メソッドは、遅延評価されるシーケンスを返します。 つまり、シーケンスを使用するコードによって要求されると、そのシーケンス内の各項目が生成されことになります。 列挙子メソッドは、1 つまたは複数の `yield return` ステートメントを含むメソッドです。 `ReadFrom` メソッドによって返されるオブジェクトには、シーケンス内の各項目を生成するコードが含まれています。 この例では、ソース ファイルからテキストの次の行を読み取り、その文字列を返す処理が含まれます。 呼び出し元のコードがシーケンスから次の項目を要求するたびに、コードはファイルからテキストの次の行を読み取り、それを返します。 ファイルが完全に読み取られたら、シーケンスは、これ以上項目がないことを示します。

新機能としてさらに、C# 構文要素が 2 つあります。 このメソッド内の `using` ステートメントは、リソースのクリーンアップを管理するものです。 `using` ステートメント内で初期化された変数 (この例では `reader`) は、`IDisposable` インターフェイスを実装する必要があります。 @System.IDisposable インターフェイスは、リソースの解放が必要なときに呼び出す必要がある 1 つのメソッド `Dispose` を定義します。 実行が `using` ステートメントの右中かっこに達したときに、コンパイラがその呼び出しを生成します。 コンパイラによって生成されたコードでは、using ステートメントによって定義されたブロック内のコードから例外がスローされた場合でも、確実にリソースを解放させます。

`reader` 変数は `var` キーワードを使用して定義されます。 `var` は*暗黙的に型指定されたローカル変数*を定義します。 つまり、変数の型は、変数に割り当てられているオブジェクトのコンパイル時の型によって決まるということです。 ここでは、@System.IO.File.OpenText からの戻り値のことで、これは @System.IO.StreamReader オブジェクトです。
 
ここで、`Main` メソッドにファイルを読み取るコードを入力してみましょう。 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

プログラムを実行します (`dotnet run` を使用して、コンソールに出力されるすべての行を確認できるようにします)。  

## <a name="adding-delays-and-formatting-output"></a>遅延の追加と出力の書式設定
コードは今の状態だと、表示が早すぎて読み上げることができません。 出力に遅延を追加する必要があります。 非同期処理を可能にするコア コードを作成していくことになります。 しかしここでの手順では、アンチパターンをいくつか使います。 このアンチパターンは、コードを追加しながらコメントで指摘され、コードは後の手順で更新されます。

このセクションでは 2 つの手順があります。 最初に、行全体ではなく単一の語を返すように反復子メソッドを更新します。 そのために、次の変更をします。 `yield return line;` ステートメントを、次のコードに置き換えます。

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

次に、ファイルの行を使用する方法を変更し、各語を書き込んだ後に遅延を追加する必要があります。 `Main` メソッドの `Console.WriteLine(line)` ステートメントを、次のブロックに置き換えます。

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

`Task` クラスは `System.Threading.Tasks` 名前空間にあるので、`using` ステートメントをファイルの先頭に追加する必要があります。

```csharp
using System.Threading.Tasks;
```

このサンプルを実行し、出力を確認します。 これで、各語が出力されるたびに 200 ミリ秒の遅延が発生するようになりました。 しかし、表示される出力には問題があります。ソース テキスト ファイルには、改行なしで 80 文字を超える行が複数あるからです。 スクロール中にそれを読み取るのは困難です。 これは簡単に修正できます。 各行の長さを追跡して、行の長さが特定のしきい値に達したら新しい行を生成するだけです。 行の長さを保持する `words` の宣言の後に、ローカル変数を宣言します。

```csharp
var lineLength = 0;
```
 
そして、次のコードを `yield return word + " ";` ステートメントの後 (右中かっこの前) に追加します。

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```
 
サンプルを実行すると、事前に設定されていたペースで読み上げることができます。

## <a name="async-tasks"></a>非同期タスク
この最後の手順では、1 つのタスク内で非同期的に出力を記述し、あわせて別のタスクを実行してテキスト表示の速度を上げ下げするユーザーからの命令を読み取る、というコードを追加します。 これは少しの手順だけで済み、これで必要な変更はすべて完了となります。
最初に、ここまでで作成したファイルを読み取り表示するコードを表す、非同期の @System.Threading.Tasks.Task を返すメソッドを作成します。

このメソッドを `Program` クラス (`Main` メソッドの本体から取得したもの) に追加します。

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

2 点、変更されます。 1 点目は、メソッドの本体で、@System.Threading.Tasks.Task.Wait を呼び出してタスクが終了するのを同期的に待つかわりに、このバージョンでは `await` キーワードを使用することです。 そのためには、`async` 修飾子をメソッド シグネチャに追加する必要があります。 このメソッドは `Task` を返します。 `Task` オブジェクトを返す return ステートメントがないことに注意してください。 かわりに、その `Task` オブジェクトは `await` 演算子を使用した時にコンパイラが生成したコードによって作成されます。 このメソッドは `await` に達するときに戻ることが想像できます。 `Task` が返されたということは、作業が完了していないことを表しています。
このメソッドは、待機中のタスクが完了したときに再開します。 それが完了すると `Task` が返され、タスクが完了したことがわかります。
コード呼び出しでは、その返された `Task` を監視して、いつ完了したのか判断します。

この新しいメソッドは `Main` メソッドで呼び出すことができます。

```csharp
ShowTeleprompter().Wait();
```

ここで、`Main` では、コードは同期的に待機します。 可能なときは同期的に待機しないで、`await` 演算子を使用します。 しかし、コンソール アプリケーションの `Main` メソッドでは、`await` 演算子を使うことはできません。 それでは、すべてのタスクが完了する前にアプリケーションが終了することになります。

次に、2 つ目の非同期メソッドを記述して、コンソールを読み取り、‘<’ キーおよび ‘>’ キーを監視する必要があります。 そのタスクに追加するメソッドは次の通りです。

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

ここでは、ラムダ式を作成して、コンソールからキーを読み取り、ユーザーが ‘<’ または ‘>’ キーを押したときの遅延を表すローカル変数を変更する @System.Action デリゲートを表します。 このメソッドは @System.Console.ReadKey を使用してブロックし、ユーザーがキーを押すまで待機します。

この機能を完成させるには、これら両方のタスク (`GetInput` と `ShowTeleprompter`) を開始し、これら 2 つのタスク間で共有データを管理する、`async Task` を返す新しいメソッドを作成する必要があります。
 
これら 2 つのタスク間で共有データを処理するクラスを作成しましょう。 このクラスには、2 つのパブリック プロパティが含まれます。遅延、そして、ファイルが完全に読み取られたことを示すフラグです。

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
    }
}
```

そのクラスを新しいファイルに配置し、上記のように、`TeleprompterConsole` 名前空間にそのクラスを囲います。 さらに `using static` ステートメントを追加して、囲むクラスや名前空間の名前なしで `Min` および `Max` メソッドを参照できるようにする必要があります。 `using static` ステートメントは 1 つのクラスからメソッドをインポートします。 これは、この時点までで使用した、名前空間からすべてのクラスをインポートした `using` ステートメントとは対照的です。

```csharp
using static System.Math;
```

もう 1 つの新しい言語機能は `lock` ステートメントです。 このステートメントは、特定の時点で単一のスレッドのみがそのコードに含まれることを保証します。 1 つのスレッドがロックされているセクションにある場合は、その他のスレッドは、最初のスレッドがそのセクションを終了するのを待つ必要があります。 `lock` ステートメントは、ロック セクションを保護するオブジェクトを使用します。 このクラスは、標準的な表現形式に従ってクラスのプライベート オブジェクトをロックします。

次に、`ShowTeleprompter` メソッドと `GetInput` メソッドを更新して、新しい `config` オブジェクトを使用する必要があります。 最後の `Task` を返す `async` メソッドを書いて、両方のタスクを開始し、最初のタスクが終了するときに終了させます。

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

ここでの 1 つの新しいメソッドが、@System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[]) の呼び出しです。 これによって、その引数リスト内の任意のタスクが完了したらすぐに終了する `Task` が作成されます。

次に、遅延の `config` オブジェクトを使用するように、`ShowTeleprompter` メソッドと `GetInput` メソッドの両方を更新する必要があります。

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

この新しいバージョンの `ShowTeleprompter` は、`TeleprompterConfig` クラスの新しいメソッドを呼び出します。 ここで、`Main` を更新して `ShowTeleprompter` の代わりに `RunTeleprompter` を呼び出す必要があります。

```csharp
RunTeleprompter().Wait();
```

終了するには、`SetDone` メソッドを追加し、`Done` プロパティを `TelePrompterConfig` クラスに追加する必要があります。

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a>まとめ
このチュートリアルでは、コンソール アプリケーションでの作業に関連する、C# 言語と .NET Core ライブラリについての多くの機能を説明しました。
ここでの知識を基にすれば、この言語やここで紹介したクラスについてさらに理解していけるでしょう。 ファイルとコンソール入出力の基本、タスク ベースの非同期プログラミング モデルのブロック使用と非ブロック使用、C# 言語のツアーと C# プログラムの構成方法、および .NET Core のコマンド ライン インターフェイスとツールについて説明しました。
 

