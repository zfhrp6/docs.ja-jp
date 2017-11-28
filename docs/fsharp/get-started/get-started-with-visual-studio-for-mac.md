---
title: "Mac 用 Visual Studio での f# の概要します。"
description: "使用する方法をについて f# で Visual Studio for mac"
keywords: "visual f#, f#, 関数型プログラミング"
author: mizzle-mo
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: beee874e3a549531b520d4ac2150bc10dcab7725
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Mac 用 Visual Studio での f# の概要します。

F# および Visual f# ツールは、Mac の IDE の Visual Studio でサポートされます。  作業を開始するには[Mac 用の Visual Studio のダウンロード](https://www.visualstudio.com/downloads/download-visual-studio-vs)まだ行っていない場合は、します。  この記事 for Mac を Visual Studio コミュニティ 2017 を使用しますが、任意のバージョンの F# で使用することができます。

## <a name="installing-f"></a>F# をインストールします。 #

Visual Studio for Mac をダウンロード後にインストールするを選択するように求められます。  この記事の目的でおはままになっている、既定値です。  Windows 用 Visual Studio とは対照的を具体的には f# のサポートをインストールする必要はありません。  続行するには、「インストール」キーを押します。

インストールが完了した後は、"Visual Studio を起動する"を選択します。  起動することも、Finder から macos です。

## <a name="creating-a-console-application"></a>コンソール アプリケーションを作成します。

Mac 用の Visual Studio での最も基本的なプロジェクトの 1 つは、コンソール アプリケーションです。  これを行う方法を次に示します。  Visual Studio for Mac が開くです。

1. **ファイル** メニューのをポイント**新しいソリューション**です。

2.  新しいプロジェクト ダイアログでは、コンソール アプリケーションの 2 つの異なるテンプレートがあります。  もう 1 つである .NET、.NET Framework を対象にする]-> [です。  .NET Core では他のテンプレートは、.NET Core を対象とするアプリ]-> [です。  この記事の目的でテンプレートのいずれかで動作します。

3. コンソール アプリの場合は、c# f# を必要に応じて変更します。  選択、**次**前方に移動するボタンです。  

4. プロジェクトの名前を指定し、アプリの必要なオプションを選択します。  プレビュー ウィンドウに作成されるディレクトリ構造を表示する画面の端に通知することは、選択したオプションに基づいています。  

5. 
              **[作成]**をクリックします。  ソリューション エクスプ ローラーで f# プロジェクトが表示されます。

## <a name="writing-your-code"></a>コードの記述

最初にいくつかのコードを記述して開始しましょう。  確認して、`Program.fs`ファイルが開いている場合と、その内容を次に置き換えます。

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

前のコード例の関数で`square`が定義されているという名前の入力を取り`x`単独で乗算します。  F# で使用されるため[型の推論](../language-reference/type-inference.md)の型`x`を指定する必要はありません。  F# コンパイラは乗算が有効で型を認識し、型に割り当てられます`x`方法に基づいて`square`と呼びます。  ポインターを合わせる場合`square`次を参照する必要があります。

```
val square: x:int -> int
```

これは、関数の型のシグネチャと呼ばれるものです。  次のように読み取ることができます:"正方形をという名前の整数を受け取る関数は、x と整数が生成されます"です。  コンパイラから受け取った注`square`、`int`型ここでは、これは、ジェネリックであるため乗算いない間は*すべて*型しますが、ではなくがジェネリック型の closed set 間でします。  選択、f# コンパイラ`int`このポイントが調整されます型シグネチャを呼び出す場合`square`と、別の入力など、型、`float`です。

別の関数、 `main`、定義されるで装飾されている、 `EntryPoint` f# コンパイラにそのプログラムの実行を指示する属性を開始する必要がありますがあります。  その他のと同じ規則に従う[C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)コマンドライン引数は、この関数に渡すことが、整数コードが返されます (通常`0`)。

このために呼び出される関数では、`square`関数の引数を持つ`12`します。  F# コンパイラの型が割り当てられます`square`する`int -> int`(を受け取る関数は、`int`を生成し、 `int`)。  呼び出し`printfn`を C スタイルのプログラミング言語、書式指定文字列で指定された値に対応するパラメーターに類似した形式の文字列を使用して書式設定された印刷機能であり、結果と新しい行に出力します。

## <a name="running-your-code"></a>コードの実行

コードを実行し をクリックして結果を表示することができます**実行**トップ レベル メニューからし**デバッグなしで開始**です。  これは、デバッグを行わず、プログラムを実行し、結果を確認することができます。

Visual Studio for Mac のポップをコンソール ウィンドウに出力され、次が表示されます。

```
12 squared is 144!
```

おめでとうございます!   Mac 用 Visual Studio で初めての f# プロジェクトを作成、f# の関数は、その関数の呼び出しの結果を印刷書き込まれ、いくつかの結果を表示するプロジェクトを実行しました。

## <a name="using-f-interactive"></a>F# Interactive を使用します。

最適な機能の Visual f# Mac のためのツールを Visual Studio での 1 つは、f# Interactive ウィンドウです。  そのコードを呼び出すし、その結果を対話的に確認できますプロセスでコードを送信することができます。

使用を開始するには、強調表示、`square`コードで定義された関数。  次に、をクリックして**編集**トップ レベル メニューからです。  次に選択**選択範囲を f# Interactive に送信**です。  これは、f# 対話型ウィンドウで、コードを実行します。  選択範囲を右クリックしを選択する代わりに、**選択範囲を f# Interactive に送信**です。  F# 対話型ウィンドウ内に次の表示が表示されます。

```
>

val square : x:int -> int

>
```

同じ関数のシグネチャを示します、`square`関数で、先ほど見た関数に置かれているとします。  `square`はこれで、f# Interactive のプロセスで定義されている、異なる値で呼び出すことができます。

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

これは、関数を実行、結果を新しい名前に束縛`it`の型および値を表示および`it`です。  各行を終了する必要がありますに注意してください`;;`です。  これは、どのように f# Interactive を知っている、関数呼び出しが完了するとします。  F# Interactive で新しい関数を定義することもできます。

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

上記の定義を新しい関数の場合、 `isOdd`、受け取り、`int`と奇数かどうかをチェック。  異なる入力で返される内容を表示するには、この関数を呼び出すことができます。  関数呼び出し内で関数を呼び出すことができます。

```
> isOdd (square 15);;
val it : bool = true
```

使用することも、[前方パイプ演算子](../language-reference/symbol-and-operator-reference/index.md)2 つの関数に値をパイプライン処理します。

```
> 15 |> square |> isOdd;;
val it : bool = true
```

後のチュートリアルでは、前方パイプ演算子などについて説明します。

これは、f# Interactive で行うことができますに glimpse のみです。  詳細については、チェック アウト[f# による対話型プログラミング](../tutorials/fsharp-interactive/index.md)です。

## <a name="next-steps"></a>次のステップ

まだの場合はチェック アウト、[ツアーの f#](../tour.md)、f# 言語のコア機能の一部をカバーします。  一部の f# では、機能の概要を知るされ for Mac を Visual Studio にコピーし、実行できる十分なコード サンプルを入力します。  使用できますが、いくつかの優れた外部リソースからの[f# ガイド](../index.md)です。

## <a name="see-also"></a>関連項目
 [Visual F#](../index.md)  
 [F# のツアー](../tour.md)  
 [F# 言語リファレンス](../language-reference/index.md)  
 [型の推論](../language-reference/type-inference.md)  
 [シンボルと演算子のリファレンス](../language-reference/symbol-and-operator-reference/index.md)  
