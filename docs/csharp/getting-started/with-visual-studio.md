---
title: "Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築"
description: "Visual Studio 2017 を使用した、単純な .NET Core コンソール アプリケーションを構築する方法について説明します。"
keywords: ".NET Core、.NET Core コンソール アプリケーション、Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 05/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
ms.translationtype: Human Translation
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b19bf07b2a2bba944bb33ddb1c887f77331ba8d1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="building-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築

このトピックでは、Visual Studio 2017 を使用して、簡単な .NET Core コンソール アプリケーションを構築、デバッグ、発行するステップ バイ ステップの概要を説明します。 Visual Studio 2017 は、.NET Core アプリケーション構築用の機能をすべて備えた開発環境を提供します。 アプリケーションが特定のプラットフォームに依存する場合を除き、.NET Core が対象とする任意のプラットフォームおよび .NET Core がインストールされている任意のシステムで実行可能です。

## <a name="prerequisites"></a>必要条件

[Visual Studio 2017](https://www.visualstudio.com/downloads/) が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。 

詳細については、「[Windows における .NET Core の前提条件](../../core/windows-prerequisites.md)」を参照してください。

## <a name="a-simple-hello-world-application"></a>シンプルな "Hello World" アプリケーション

まず、シンプルな "Hello World" コンソール アプリケーションを作成してみましょう。 この場合は、以下の手順に従ってください。

1. Visual Studio 2017 を起動します。 [**ファイル**] > [**新規作成**] > [**プロジェクト**] をメニュー バーから選択します。 [**新しいプロジェクトの追加**] ダイアログで、[**.NET Core**] ノードを選び、[**コンソール アプリ (.NET Core)**] プロジェクト テンプレートを選びます。 [**名前**] テキスト ボックスに "HelloWorld" と入力します。 [**OK**] ボタンを選択します。

   ![コンソール アプリが選択された状態の [新しいプロジェクト] ダイアログ](./media/with-visual-studio/newproject.png)
   
1. Visual Studio によって開発環境が読み込まれます。 .NET Core の C# コンソール アプリケーション テンプレートで、`Program` というクラスが、<xref:System.String> 配列を引数として必要とする単一のメソッド `Main` とともに自動的に定義されます。 `Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。 アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。

   ![Visual Studio と新しい HelloWorld プロジェクト](./media/with-visual-studio/devenv.png)

   このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。 <xref:System.Console.WriteLine(System.String)?displayProperty=fullName> メソッドを呼び出し、リテラル文字列 "Hello World!" を コンソール ウィンドウに表示します。 ツールバー上の緑色の矢印の付いた **HelloWorld** ボタンを選択すると、プログラムをデバッグ モードで実行できます。 しかしそのとき、コンソール ウィンドウは非常に短い時間だけ表示され、すぐに閉じられます。 これは、`Main` メソッド内の単一のステートメントが実行されるとすぐに `Main` メソッドが終了してアプリケーションが終了するためです。

1. コンソール ウィンドウを閉じる前にアプリケーションに一時停止させるには、<xref:System.Console.WriteLine(System.String)?displayProperty=fullName> メソッドへの呼び出しのすぐ後に次のコードを追加します。

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   このコードは、任意のキーを押すようにユーザーにメッセージを表示し、キーが押されるまでプログラムを一時停止します。

1. メニュー バーで [**ビルド**] > [**ソリューションのビルド**] の順に選択します。 これにより、プログラムが IL (中間言語) にコンパイルされ、それが JIT (just-in-time) コンパイラによってバイナリ コードに変換されます。

1. ツールバー上の緑色の矢印の付いた **HelloWorld** ボタンを選択して、プログラムを実行します。

   ![Hello World Press any key to continue と表示されているコンソール ウィンドウ](./media/with-visual-studio/helloworld1.png)

1. 任意のキーを押して、コンソール ウィンドウを閉じます。

## <a name="enhancing-the-hello-world-application"></a>Hello World アプリケーションの拡張

アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。 以下のように、プログラムを変更してテストします。

1. コード ウィンドウで `public static void Main(string[] args)` 行のすぐ後に、次の C# コードを、先頭に角かっこを付け最後に閉じかっこを付けて入力します。

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   ![Main メソッドが更新された Visual Studio プログラムの C シャープ ファイル](./media/with-visual-studio/codewindow.png)

   このコードは、"What is your name?" と コンソール ウィンドウに表示して、ユーザーが文字列を入力して Enter キーを押すまで待機します。 これは文字列を `name` という変数に格納します。 さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=fullName> プロパティの値を取得して、それを `date` という変数に代入します。 最後に[複合書式指定文字列](../../standard/base-types/composite-format.md)を使用して、これらの値をコンソール ウィンドウに表示します。

1. **[ビルド]** > **[ソリューションのビルド]** と選択して、プログラムをコンパイルします。

1. Visual Studio で、ツールバーの緑色の矢印を選択するか、F5 を押すか、メニューで [**デバッグ**] > [**デバッグの開始**] メニュー アイテムを選択して、プログラムをデバッグ モードで実行します。 プロンプトに対し、名前を入力し、Enter キーを押します。

   ![プログラムの出力が変更されたコンソール ウィンドウ](./media/with-visual-studio/helloworld2.png)

1. 任意のキーを押して、コンソール ウィンドウを閉じます。

アプリケーションが作成され、実行されました。 本格的なアプリケーションを開発するには、さらにいくつか追加の手順を行い、アプリケーションをリリース可能な状態にします。

- アプリケーションのデバッグ方法の詳細については、「[Visual Studio 2017 で C# Hello World アプリケーションをデバッグする](debugging-with-visual-studio.md)」を参照してください。

- アプリケーションの再頒布可能バージョンの開発と発行については、「[Visual Studio 2017 を使用した Hello World アプリケーションの発行](publishing-with-visual-studio.md)」を参照してください。

## <a name="related-topics"></a>関連トピック

.NET Core と Visual Studio 2017 では、コンソール アプリケーションの代わりにクラス ライブラリを構築することもできます。 ステップ バイ ステップの説明については、「[Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築](library-with-visual-studio.md)」を参照してください。

無償ダウンロードできるコード エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用して、Mac、Linux、Windows 上で .NET Core コンソール アプリケーションを開発することもできます。 ステップ バイ ステップのチュートリアルについては、「[Visual Studio Code の概要](with-visual-studio-code.md)」を参照してください。
