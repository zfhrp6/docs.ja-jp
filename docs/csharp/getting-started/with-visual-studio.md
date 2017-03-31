---
title: "Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築"
description: "Visual Studio 2017 を使用した、単純な .NET Core コンソール アプリケーションを構築する方法について説明します。"
keywords: ".NET Core、.NET Core コンソール アプリケーション、Visual Studio 2017"
author: stevehoag
ms.author: shoag
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f1a20f399b4ab34986d700622ff3bf3859b001bd
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築 #

このトピックでは、Visual Studio 2017 を使用して、簡単な .NET Core コンソール アプリケーションを構築、デバッグ、発行するステップ バイ ステップの概要を説明します。 Visual Studio 2017 は、.NET Core アプリケーション構築用の機能をすべて備えた開発環境を提供します。 このアプリケーションは固有のプラットフォームに依存しない限り、.NET Core がターゲットとする任意のプラットフォームおよび .NET Core がインストールされている任意のシステムで実行可能です。

## <a name="prerequisites"></a>必須コンポーネント ##

- [Visual Studio 2017](https://www.visualstudio.com/downloads/) が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。 

詳細については、Windows 前提条件のトピックの [Visual Studio 2017](../../core/windows-prerequisites.md) のセクションを参照してください。

## <a name="a-simple-hello-world-application"></a>シンプルな "Hello World" アプリケーション ##

まず、シンプルな "Hello World" コンソール アプリケーションを作成してみましょう。 次に手順を示します。

1. Visual Studio を起動し、**[ファイル]** メニューで **[新規作成]**、 > **[プロジェクト]** の順に選択します。 **[新しいプロジェクト]** ダイアログで、左側のペインで **[Visual C#]** ノードを展開し、**[.NET Core]** ノードを選択します。

2. 右側のペインで、**[Console App (.NET Core)]** を選択します。 下図のように、プロジェクトの名前として `HelloWorld` を入力し、**[ソリューションのディレクトリを作成]** チェックボックスがオンになっていることを確認します。

   ![コンソール アプリを選択した状態の [新しいプロジェクト] ダイアログのスクリーンショット](./media/with-visual-studio/vs_newproject.jpg)
   
3. **[OK]** を選択します。 下図のように、Visual Studio はコード ウィンドウとともに開発環境を表示します。 .NET Core の C# コンソール アプリケーション テンプレートで、`Program` というクラスが、@System.String 配列を引数として必要とする単一のメソッド `Main` とともに自動的に定義されます。 `Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。 アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。

   ![Visual Studio と新しい HelloWorld プロジェクト](./media/with-visual-studio/vs_devenv.jpg)

   このテンプレートは非常にシンプルな "Hello World"アプリケーションを作成します。@System.Console.WriteLine(System.String) メソッドを呼び出してコンソール ウィンドウにリテラル文字列 "Hello World!"  を表示するものです。 ツールバー上の緑色の矢印の付いた "HelloWorld" ボタンを選択すると、プログラムをデバッグ モードで実行できます。 しかしそのとき、コンソール ウィンドウは非常に短いあいだだけ表示され、すぐに閉じられます。 これは、`Main` メソッド内の単一のステートメントが実行されるとすぐに `Main` が終了してアプリケーションが終了するためです。

4. コンソール ウィンドウを閉じる前に、アプリケーションが一時停止するようにしましょう。 @System.Console.WriteLine(System.String) メソッドへの呼び出しのすぐ後に、次のコードを追加します。

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   このコードは、任意のキーを押すようにユーザーにメッセージを表示し、キーが押されるまでプログラムを一時停止します。

5. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。 これにより、プログラムが IL (中間言語) にコンパイルされ、それが JIT (just-in-time) コンパイラによってバイナリ コードに変換されます。

6. ツールバー上の緑色の矢印の付いた "HelloWorld" ボタンを選択して、プログラムを実行します。 結果を次の例に示します。

   ![イメージ](./media/with-visual-studio/simple_hello.jpg)

7. 任意のキーを押して、ウィンドウを閉じます。

## <a name="enhancing-the-hello-world-application"></a>"Hello World" アプリケーションの拡張 ##

アプリケーションを拡張しましょう。ユーザーに名前を入力させ、コンソール ウィンドウにその名前を日時と一緒に表示します。 以下のように、プログラムを変更してテストします。

1. コード ウィンドウで `public static void Main(string[] args)` 行の後に、次の C# コードを、先頭に角かっこを付け最後に閉じかっこを付けて入力します。

   [!CODE [GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   結果としてコード ウィンドウは次のように表示されます。

   ![変更したプログラムが実行されている](./media/with-visual-studio/codewindow.jpg)

   このコードはコンソールに "What is your name?" と表示して、 ユーザーが文字列を入力して Enter キー押すまで待機します。 入力された文字列を `name` という変数に格納します。 さらに現在の現地時刻を含む @System.DateTime.Now プロパティの値を取得して、それを `date` という変数に代入します。 次に[複合書式指定文字列](../../standard/base-types/composite-format.md)を使用して、これらの値をコンソールに表示します。

2. **[ビルド]** > **[ソリューションのビルド]** と選択して、プログラムをコンパイルします。 これにより、プログラムが IL (中間言語) にコンパイルされ、それが JIT (just-in-time) コンパイラによってバイナリ コードに変換されます。

3. Visual Studio で、ツールバーの緑色の矢印を選択するか、F5 を押すか、メニューで **[デバッグ]** > **[デバッグの開始]** と選択して、プログラムをデバッグ モードで実行します。 プロンプトに対して名前を入力して Enter キーを押すと、コンソール ウィンドウは以下のような状態になります。

   ![変更したプログラムが実行されている](./media/with-visual-studio/console.jpg)

4. 任意のキーを押して、コンソール ウィンドウを閉じます。 これでデバッグ モードは終了します。

以上で、シンプルなアプリケーションの作成と実行が完了しました。 本格的なアプリケーションを開発するには、さらにいくつか追加の手順を行い、アプリケーションをリリース可能な状態にする必要があります。

- アプリケーションのデバッグ方法の詳細については、[Hello World アプリケーションのデバッグ](debugging-with-visual-studio-2017.md)に関するページを参照してください。

- アプリケーションの再頒布可能バージョンの開発と発行については、[Hello World アプリケーションの発行](publishing-with-visual-studio-2017.md)に関するページを参照してください。

## <a name="related-topics"></a>関連トピック ##

.NET Core と Visual Studio 2017 では、コンソール アプリケーションの代わりにクラス ライブラリを構築することもできます。 ステップ バイ ステップの説明については、「[Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築](library-with-visual-studio-2017.md)」を参照してください。

無償ダウンロードできるコード エディタである Visual Studio Code を使用して、Mac、Linux、Windows 上で .NET Core コンソール アプリケーションを開発できます。 ステップ バイ ステップのチュートリアルについては、「[Visual Studio Code の概要](with-visual-studio-code.md)」を参照してください。

