---
title: Visual Studio のコードで f# の概要します。
description: Visual Studio Code と Ionide プラグイン suite で f# を使用する方法を説明します。
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728629"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio のコードで f# の概要します。

F# で記述できます[Visual Studio Code](https://code.visualstudio.com)で、 [Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)、IntelliSense および基本的なコードの優れたクロスプラット フォームで軽量な統合開発環境 (IDE) のエクスペリエンスを取得するにはリファクタリングします。 参照してください[Ionide.io](http://ionide.io)をプラグイン スイートに関する詳しい情報を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

必要があります[git がインストールされている](https://git-scm.com/download)するには、パスで使用できると Ionide でプロジェクト テンプレートを使用します。 」と入力して正しくインストールされていることを確認することができます`git --version`キーを押して、コマンド プロンプトで**Enter**です。

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Ionide を使用して[モノラル](http://www.mono-project.com)です。 Macos モノラルをインストールする最も簡単な方法は、Homebrew を介してです。 単に、端末に、次を入力します。

```
brew install mono
```

またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download)です。

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

Ionide Linux では、使用も[モノラル](https://www.mono-project.com)です。 Debian、Ubuntu またはの場合は、次の操作を行うこともできます。

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download)です。

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Windows の場合は、する必要があります[F# でサポートを含む Visual Studio をインストール](get-started-visual-studio.md#installing-f)です。 これにより、書き込み、コンパイル、および f# コードを実行するために必要なすべてのコンポーネントがインストールされます。

またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download/)です。

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>Visual Studio Code と Ionide プラグインのインストール

Visual Studio のコードからをインストールすることができます、 [code.visualstudio.com](https://code.visualstudio.com) web サイトです。

次に、"Ionide"を検索して拡張機能 アイコンをクリックします。

Visual Studio のコードで、f# のサポートに必要なだけプラグイン[Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)です。 ただし、インストールすることも[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)を取得する[偽](https://fsharp.github.io/FAKE/)サポートと[Ionide パケットを作成](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)を取得する[パケットを作成](https://fsprojects.github.io/Paket/)をサポートします。 偽の追加 f# コミュニティ ツールのプロジェクトをビルドし、それぞれの依存関係を管理するのには、パケットを作成します。

## <a name="creating-your-first-project-with-ionide"></a>Ionide を初めてのプロジェクトを作成します。

新しい f# プロジェクトを作成するには、(」と入力して何でも) の新しいフォルダーに Visual Studio のコードを開きます。

次に、コマンド パレットを開きます (**ビュー > コマンド パレット**) と入力します。

```
> F# new project
```

これが電源に、 [FORGE](https://github.com/fsharp-editing/Forge)プロジェクト。

> [!NOTE]
テンプレート オプションが表示されない場合は、コマンド パレットで、次のコマンドを実行してテンプレートを更新してみてください:`>F#: Refresh Project Templates`です。

クリックして"f#::"新しいプロジェクトを選択して**Enter**です。 プロジェクト テンプレートを選択するのには、次の手順を行います。

選択、`classlib`テンプレートとヒット**Enter**です。

次でプロジェクトを作成するディレクトリを選択します。 空のまま、現在のディレクトリが使用されます。

最後に、最後の手順で、プロジェクトの名前を付けます。 F# は[pascal](http://c2.com/cgi/wiki?PascalCase)プロジェクト名にします。 この記事では`ClassLibraryDemo`名として。 プロジェクトの名前を入力するとヒット**Enter**です。

前の手順を実行した場合は、次のように表示される、左側にある Visual Studio コード ワークスペースを取得してください。

1. F# プロジェクト自体には、下に、`ClassLibraryDemo`フォルダーです。
2. 使用してパッケージを追加するための適切なディレクトリ構造[ `Paket`](https://fsprojects.github.io/Paket/)です。
3. クロス プラットフォーム ビルド スクリプトを[ `FAKE`](https://fsharp.github.io/FAKE/)です。
4. `paket.exe`実行可能ファイルをパッケージをフェッチして依存関係が解決することができます。
5. A`.gitignore`ファイルのこのプロジェクトを Git ベースのソース管理に追加する場合。

## <a name="writing-some-code"></a>コードの記述

開く、 *ClassLibraryDemo*フォルダーです。  次のファイルが表示されます。

1. `ClassLibraryDemo.fs`、f# 実装ファイル定義クラスを使用します。
2. `ClassLibraryDemo.fsproj`、、f# のプロジェクト ファイルをこのプロジェクトをビルドするために使用します。
3. `Script.fsx`、、f# スクリプト ファイルをソース ファイルを読み込みます。
4. `paket.references`、プロジェクトの依存関係を指定するパケットを作成ファイル。

開いている`Script.fsx`の末尾に次のコードを追加します。

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

この関数が単語の形式に変換[Pig ラテン](https://en.wikipedia.org/wiki/Pig_Latin)です。 次の手順では、f# 対話型 (FSI) を使用して評価します。

(11 行の長さにする必要があります) 関数全体を強調表示します。 強調表示すると後の保持、 **alt キーを押し**キーを押し、ヒット**Enter**です。 次に、ポップアップ ウィンドウがわかります、次のように表示されるはず。

![Ionide で f# Interactive の出力の例](media/getting-started-vscode/vscode-fsi.png)

これは、3 つのことを行いました。

1. FSI プロセスを開始します。
2. FSI のプロセスが細かく強調表示したコードを送信します。
3. FSI プロセスには、経由で送信されたコードが評価されます。

経由で送信するため、[関数](../language-reference/functions/index.md)FSI をその関数を呼び出すようになりました。 対話型のウィンドウで、次のように入力します。

```fsharp
toPigLatin "banana";;
```

次の結果が表示されます。

```fsharp
val it : string = "ananabay"
```

ここで、最初の文字として母音で試してみましょう。 次のように入力します。

```fsharp
toPigLatin "apple";;
```

次の結果が表示されます。

```fsharp
val it : string = "appleyay"
```

関数は、期待どおりに動作してが表示されます。 以上で、先ほど Visual Studio のコードで、1 つ目の f# 関数を記述し、FSI で評価。

>[!NOTE]
FSI 内の行を終了したように可能性がありますが、`;;`です。 FSI を使用すると、複数行を入力するためです。 `;;`最後に FSI コードが終了したときを知ることができます。

## <a name="explaining-the-code"></a>コードの説明

コードが実際に何かわからない場合、詳細な手順を示します。

ご覧のとおり、`toPigLatin`の入力として単語を受け取り、その単語の Pig ラテン文字表現に変換する関数です。 このルールは次のとおりです。

単語の最初の文字で始まる場合、母音、単語の末尾に「お」を追加します。 母音で始まらない場合、は、単語の末尾にその最初の文字を移動し、「常」を追加しています。

FSI では、次を認識することがあります。

```fsharp
val toPigLatin : word:string -> string
```

示すこの`toPigLatin`で取得する関数は、`string`入力として (と呼ばれる`word`)、し、返します別`string`です。 これと呼ばれますが、[関数の型のシグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)、f# コードを理解するためのキーは、f# の根本的な部分です。 Visual Studio のコード内で、関数ポインターを合わせる場合するも明らかです。

関数の本文には、2 つの異なる部分をわかります。

1. 呼ばれる内部関数は、 `isVowel`、特定の文字を決定する (`c`) を介して提供されたパターンの 1 つと一致する場合にチェックして、母音は、[パターンに一致する](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)セルのかどうか、最初の文字が、母音コンス トラクターの戻り値は、入力文字列から値に基づいて場合は、最初の文字式であるか、母音。

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

フロー`toPigLatin`のため。

かどうか、入力の単語の最初の文字は母音を確認してください。 である場合は、単語の末尾に「お」をアタッチします。 それ以外の場合、単語の末尾までその最初の文字を移動し、「常」を追加します。

1 つの最後にこの方法に注意してください。 その他の多くの言語がとは異なり、関数から返される明示的な指示がないです。 これは f# 式に基づくは、関数の本体の最後の式の戻り値です。 `if..then..else`自体、式の本体では、`then`ブロックまたはの本文、`else`ブロックが入力された値によって返されます。

## <a name="moving-your-script-code-into-the-implementation-file"></a>クラスの実装ファイル、スクリプト コードを移動します。

この記事の前のセクションには、f# コードの記述の一般的な最初の手順が示されている: 初期関数を作成し、FSI して対話的に実行します。 これは、REPL 駆動型開発と呼ばれます場所[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 「読み取り評価印刷ループ」を意味します。 これは何かの操作が得られるまで機能をテストする優れた手段です。

REPL 駆動型開発の次の手順では、f# 実装ファイルの作業中のコードを移動します。 これは、実行可能なアセンブリの f# コンパイラでコンパイルできます。

最初に開く`ClassLibraryDemo.fs`です。  一部のコードが既にされているがわかります。 進めて、クラス定義を削除しがのままにすることを確認、 [ `namespace` ](../language-reference/namespaces.md)上部にある宣言します。

次に、新しい作成[ `module` ](../language-reference/modules.md)と呼ばれる`PigLatin`をコピーし、`toPigLatin`ように、関数。

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

次に、開く、 `Script.fsx` 、ファイルに追加され、全体を削除`toPigLatin`機能しますが、ファイルに次の 2 行を保持することを確認します。

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

FSI を読み込むスクリプトの最初の行が必要な`ClassLibraryDemo.fs`します。 2 番目の行が使いやすい: 省略された場合、オプションですが、入力する必要があります`open ClassLibraryDemo`FSI ウィンドウを表示する場合に、`ToPigLatin`モジュールをスコープにします。

次に、FSI ウィンドウで、関数を使って呼び出し、`PigLatin`前に定義するモジュール。

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

正常に完了 前に、同じ結果を取得することは、f# 実装ファイルから読み込まれるようになりました。 ここでの主な違いは、f# ソース ファイルは FSI 内だけでなく、どこにでも実行できるアセンブリにコンパイルされていることです。

## <a name="summary"></a>まとめ

この記事では次の内容を学習しました。

1. Ionide で Visual Studio のコードを設定する方法です。
2. Ionide で初めての f# プロジェクトを作成する方法。
3. F# スクリプトを使用して、Ionide で、最初の f# 関数を記述し、それを FSI で実行する方法です。
4. スクリプトを移行する方法は、f# ソース コードし、FSI からそのコードを呼び出します。

書き込むはるかに f# を使用してコード Visual Studio のコードと Ionide が組み込まれました。

## <a name="troubleshooting"></a>トラブルシューティング

次に遭遇する特定の問題をトラブルシューティングする方法はいくつかを示します。

1. Ionide の編集機能コードを取得するには、f# ファイルをディスクにしている Visual Studio Code ワークスペースで、開いているフォルダー内に保存する必要があります。
2. 場合は、システムを変更または開いている Visual Studio のコードで Ionide 前提条件をインストールしたら、Visual Studio Code を再起動します。
3. F# コンパイラと f# interactive コマンド ラインから完全修飾パスを使用せずに使用することができることを確認してください。 これを行うように入力して`fsc`f# コンパイラ、コマンドラインでと`fsi`または`fsharpi`Visual f# のツールを Windows と Mac と Linux の Mono それぞれします。
4. プロジェクトのディレクトリで無効な文字があれば、Ionide が動作しない可能性があります。  このような場合、プロジェクト ディレクトリの名前を変更します。
5. Ionide コマンドのいずれも作業している場合、 [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)を誤ってオーバーライドしているかどうかを参照してください。
6. Ionide はコンピューターに分割すると、上記のいずれが問題を修正、削除してください。、`ionide-fsharp`コンピューターにディレクトリおよびプラグインのスイートを再インストールします。

Ionide とは、構築および f# コミュニティのメンバーによって管理されるオープン ソース プロジェクトです。 問題を報告し、自由に投稿にしてください、 [Ionide VSCode: FSharp GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)です。

レポートに問題がある場合は場合に、従ってください[、ログを取得するための使用方法についての問題を報告するときに](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)です。

Ionide 開発者や f# でコミュニティからさらにヘルプを求めることも、 [Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)です。

## <a name="next-steps"></a>次の手順

F# と言語の機能の詳細については、チェック アウト[ツアーの f#](../tour.md)です。
