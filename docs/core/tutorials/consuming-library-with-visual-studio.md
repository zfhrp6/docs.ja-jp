---
title: "Visual Studio 2017 の .NET Core を使用したクラス ライブラリの利用"
description: "Visual Studio 2017 でクラス ライブラリのメンバーを呼び出す方法について説明します。"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
dev_langs:
- csharp
- vb
ms.openlocfilehash: 180ed868116967b03c5d4058b5618927242defc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 の .NET Core を使用したクラス ライブラリの利用

「[Visual Studio 2017 での C# と .NET Core を使用したクラス ライブラリの構築](./library-with-visual-studio.md)」または「[Visual Studio 2017 で Visual Basic と .NET Core を使用したクラス ライブラリの構築](vb-library-with-visual-studio.md)」の手順でクラス ライブラリを作成し、「[Visual Studio 2017 の .NET Core を使用したクラス ライブラリのテスト](testing-library-with-visual-studio.md)」でそれをテストし、ライブラリのリリース バージョンをビルドしたら、次の手順は、呼び出し元がそれを利用できるようにすることです。 これは次の 2 つの方法で実行できます。

* ライブラリが 1 つのソリューションで使われる場合 (たとえば、1 つの大規模なアプリケーションのコンポーネントである場合)、1 つのプロジェクトとしてソリューションに含めることができます。

* ライブラリが一般に公開されている場合は、NuGet パッケージとして配布できます。

## <a name="including-a-library-as-a-project-in-a-solution"></a>ソリューション内のプロジェクトとしてライブラリを含める

単体テストをクラス ライブラリと同じソリューションに含めたのと同様に、アプリケーションをソリューションの一部として含めることができます。 たとえば、文字列を入力するようにユーザーに要求して、最初の文字が大文字かどうかを報告するコンソール アプリケーションで、このクラス ライブラリを使うことができます。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. 「[Visual Studio 2017 での C# と .NET Core を使用したクラス ライブラリの構築](./library-with-visual-studio.md)」トピックで作成した `ClassLibraryProjects` ソリューションを開きます。 **ソリューション エクスプローラー**で **ClassLibraryProjects** ソリューションを右クリックし、コンテキスト メニューから **[追加]** > **[新しいプロジェクト]** の順に選びます。

1. **[新しいプロジェクトの追加]** ダイアログで、**[Visual C#]** ノードを展開し、**[.NET Core]** ノードを選択し、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「ShowCase」と入力し、**[OK]** ボタンを選びます。

   ![[新しいプロジェクトの追加] ダイアログ](./media/consuming-library-with-visual-studio/addnewproject.png)

1. **ソリューション エクスプローラー**で、**ShowCase** プロジェクトを右クリックして、コンテキスト メニューで **[スタートアップ プロジェクトに設定]** を選びます。 

   ![ShowCase のコンテキスト メニュー](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. 初期状態では、プロジェクトにはクラス ライブラリへのアクセス権がありません。 プロジェクトでクラス ライブラリのメソッドを呼び出すことができるようにするには、クラス ライブラリへの参照を作成します。 **ソリューション エクスプローラー**で、`ShowCase` プロジェクトの **[依存関係]** ノードを右クリックして、**[参照の追加]** を選びます。

   ![ShowCase の依存関係のコンテキスト メニュー](./media/consuming-library-with-visual-studio/addreference.png)

1. **[参照マネージャー]** ダイアログ ボックスで、クラス ライブラリ プロジェクト **StringLibrary** を選び、**[OK]** ボタンを選びます。

   ![参照マネージャー](./media/consuming-library-with-visual-studio/referencemanager.png)

1. *Program.cs* ファイルのコード ウィンドウで、すべてのコードを次のコードに置き換えます。

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   このコードでは、[Console.WindowHeight](xref:System.Console.WindowHeight) プロパティを使ってコンソール ウィンドウの行数を決定します。 [Console.CursorTop](xref:System.Console.CursorTop) プロパティがコンソール ウィンドウの行数以上であるときは、コードは常にコンソール ウィンドウをクリアして、ユーザーにメッセージを表示します。

   プログラムは、ユーザーに文字列の入力を要求し、 文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに Enter キーを押すと、アプリケーションは終了し、コンソール ウィンドウが閉じます。

1. 必要に応じて、ツールバーを変更して、`ShowCase` プロジェクトの**デバッグ** リリースをコンパイルします。 **ShowCase** の緑色の矢印を選び、プログラムをコンパイルして実行します。

   ![イメージ](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. 「[Visual Studio 2017 で Visual Basic と .NET Core を使用したクラス ライブラリの構築](vb-library-with-visual-studio.md)」トピックで作成した `ClassLibraryProjects` ソリューションを開きます。 **ソリューション エクスプローラー**で **ClassLibraryProjects** ソリューションを右クリックし、コンテキスト メニューから **[追加]** > **[新しいプロジェクト]** の順に選びます。

1. **[新しいプロジェクトの追加]** ダイアログで、**[Visual Basic]** ノードを展開し、**[.NET Core]** ノードを選択し、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「ShowCase」と入力し、**[OK]** ボタンを選びます。

   ![[新しいプロジェクトの追加] ダイアログ](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. **ソリューション エクスプローラー**で、**ShowCase** プロジェクトを右クリックして、コンテキスト メニューで **[スタートアップ プロジェクトに設定]** を選びます。 

   ![ShowCase のコンテキスト メニュー](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. 初期状態では、プロジェクトにはクラス ライブラリへのアクセス権がありません。 プロジェクトでクラス ライブラリのメソッドを呼び出すことができるようにするには、クラス ライブラリへの参照を作成します。 **ソリューション エクスプローラー**で、`ShowCase` プロジェクトの **[依存関係]** ノードを右クリックして、**[参照の追加]** を選びます。

   ![ShowCase の依存関係のコンテキスト メニュー](./media/consuming-library-with-visual-studio/addreference.png)

1. **[参照マネージャー]** ダイアログ ボックスで、クラス ライブラリ プロジェクト **StringLibrary** を選び、**[OK]** ボタンを選びます。

   ![参照マネージャー](./media/consuming-library-with-visual-studio/referencemanager.png)

1. *Program.vb* ファイルのコード ウィンドウで、すべてのコードを次のコードに置き換えます。

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   このコードでは、[Console.WindowHeight](xref:System.Console.WindowHeight) プロパティを使ってコンソール ウィンドウの行数を決定します。 [Console.CursorTop](xref:System.Console.CursorTop) プロパティがコンソール ウィンドウの行数以上であるときは、コードは常にコンソール ウィンドウをクリアして、ユーザーにメッセージを表示します。

   プログラムは、ユーザーに文字列の入力を要求し、 文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに Enter キーを押すと、アプリケーションは終了し、コンソール ウィンドウが閉じます。

1. 必要に応じて、ツールバーを変更して、`ShowCase` プロジェクトの**デバッグ** リリースをコンパイルします。 **ShowCase** の緑色の矢印を選び、プログラムをコンパイルして実行します。

   ![イメージ](./media/consuming-library-with-visual-studio/toolbar.png)
---

「[Visual Studio 2017 で Hello World Application をデバッグする](debugging-with-visual-studio.md)」と「[Visual Studio 2017 を使用した Hello World アプリケーションの発行](publishing-with-visual-studio.md)」の手順に従って、このライブラリを使うアプリケーションをデバッグして発行できます。

## <a name="distributing-the-library-in-a-nuget-package"></a>ライブラリを NuGet パッケージで配布する

NuGet パッケージとして発行すると、クラス ライブラリが広く利用可能になります。 NuGet パッケージの作成は Visual Studio ではサポートされていません。 作成するには、[`dotnet` コマンド ライン ユーティリティ](../../core/tools/dotnet.md)を使います。

1. コンソール ウィンドウが開きます。 たとえば、Windows タスク バーの **[何でも聞いてください]** テキスト ボックスに「`Command Prompt`」 (または省略して「`cmd`」) と入力し、**コマンド プロンプト** デスクトップ アプリを選ぶか、コマンド プロンプトが検索結果で選択されている場合は Enter キーを押して、コンソール ウィンドウを開きます。

1. ライブラリのプロジェクト ディレクトリに移動します。 一般的なファイルの場所を再構成していない限り、*Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* ディレクトリにあります。 このディレクトリには、ソース コードおよびプロジェクト ファイル *StringLibrary.csproj* が含まれています。

1. `dotnet pack --no-build` コマンドを実行します。 `dotnet` ユーティリティにより、*.nupkg* 拡張子を持つパッケージが生成されます。

   > [!TIP]
   > *dotnet.exe* を含むディレクトリが PATH になくても、コンソール ウィンドウで「`where dotnet.exe`」と入力して、場所を検索できます。

NuGet パッケージの作成の詳細については、「[クロスプラットフォーム ツールを使用して NuGet パッケージを作成する方法](../../core/deploying/creating-nuget-packages.md)」を参照してください。
