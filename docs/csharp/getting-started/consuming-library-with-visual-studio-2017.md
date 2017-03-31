---
title: "Visual Studio 2017 の .NET Core を使用したクラス ライブラリの利用"
description: "Visual Studio 2017 を使用してクラス ライブラリでメンバーを呼び出す方法について説明します"
keywords: ".NET Core, .NET Core クラス ライブラリ, .NET Standard, .NET Standard クラス ライブラリの配布"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: d7b94076-1108-4174-94e7-a18f00072bb7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0b42eeb0149feec09ddacba98383da3abd53bb5e
ms.lasthandoff: 03/13/2017

---

# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 の .NET Core を使用したクラス ライブラリの利用 #

「[Building a C# class library with .NET Core in Visual Studio 2017 (Visual Studio 2017 の .NET Core を使用して C# クラス ライブラリをビルドする)](./library-with-visual-studio-2017.md)」、および「[Testing a class library with .NET Core in Visual Studio 2017 (Visual Studio 2017 の .NET Core を使用してクラス ライブラリをテストする)](testing-library-with-visual-studio.md)」の手順に従って、クラス ライブラリをビルドおよびテストし、ライブラリのリリース バージョンをビルドしたら、次の手順では呼び出し元がリリース バージョンを利用できるようにします。 これは次の 2 つの方法で実行できます。

- ライブラリが 1 つのソリューションで使用される場合 (たとえば、1 つの大規模なアプリケーションのコンポーネントである場合)、単に 1 つのプロジェクトとしてソリューションに含めることができます。

- ライブラリが一般に公開されている場合は、NuGet パッケージとして配布できます。

## <a name="including-a-library-as-a-project-in-a-solution"></a>ソリューション内のプロジェクトとしてライブラリを含める ##

単体テストをクラス ライブラリと同じソリューションに含めたのと同様に、アプリケーションをソリューションの一部として含めることができます。 例として、クラス ライブラリをコンソール アプリケーションで使用し、文字列を入力するようにユーザーに要求して、最初の文字が大文字かどうかを報告することにします。

1. 「[Building a C# class library with .NET Core in Visual Studio 2017 (Visual Studio 2017 の .NET Core を使用して C# クラス ライブラリをビルドする)](./library-with-visual-studio-2017.md)」のトピックで作成した `ClassLibraryProjects` ソリューションを開きます。ソリューション エクスプローラーで、**[ClassLibraryProjects]** ノードのコンテキスト メニューを開き、**[追加]****[新しいプロジェクト]** の順に選択します。

1. 次の図のとおり、**[新しいプロジェクトの追加]** ダイアログで、**[Visual C#]** ノードと **[.NET Core]** ノードを展開して、**[Console App (.NET Core)]** プロジェクト テンプレートを選択します。

   ![イメージ](./media/use-library.jpg)

1. **[名前]** ボックスに「`ShowCase`」と入力して、**[OK]** を選択します。

1. ソリューション エクスプローラーで、**ShowCase** プロジェクト ノードのコンテキスト メニューを開き、**[スタートアップ プロジェクトに設定]** を選択します。

1. 最初の設定では、このプロジェクトにはクラス ライブラリへのアクセス権がありません。 クラス ライブラリのメソッドを呼び出せるようにするには、**[ソリューション エクスプローラー]** で、**[ショーケース]** プロジェクトの **[依存関係]** ノードのコンテキスト メニューを開いて、**[参照の追加]** を選択します。

1. **[参照マネージャー]** ダイアログで、次の図のとおり、ライブラリ プロジェクトである **[StringLibrary]** を選択して、**[OK]** を選択します。

   ![イメージ](./media/add-lib-ref.jpg)

1. 'program.cs' ファイルのコード ウィンドウで、すべてのコードを次のコードに置き換えます。

 [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs#1)]

   このコードでは [Console.WindowHeight](xref:System.Console.WindowHeight) プロパティを使用して、コンソール ウィンドウの行の数を決定します。 [Console.CursorTop](xref:System.Console.CursorTop) プロパティがコンソール ウィンドウの行の総数以上であるときは、コードは常にコンソール ウィンドウをクリアして、ユーザーにメッセージを再表示します。

   プログラム自体がユーザーに要求するのは、文字列の入力のみです。 次に、文字列が大文字で始まるかどうかを示します。 ユーザーが文字列を入力せずに **Enter** キーを押すと、コンソール ウィンドウが閉じ、アプリケーションが終了します。

1. 必要に応じて、次の図のようにツールバーを変更して、`ShowCase` プロジェクトの **[デバッグ]** リリースをコンパイルします。

   ![イメージ](./media/showcase-toolbar.jpg)

1. **[ショーケース]** の緑色の矢印をクリックして、プログラムをコンパイルして実行します。

次いで、「[Visual Studio 2017 で C# Hello World Application をデバッグする](debugging-with-visual-studio-2017.md)」と「[Publishing your Hello World Application with Visual Studio 2017 (Visual Studio 2017 で Hello World Application を発行する)](publishing-with-visual-studio-2017.md)」の手順に従って、このライブラリで使用されているアプリケーションをデバッグし、最終的に発行することができます。

## <a name="distributing-the-library-in-a-nuget-package"></a>ライブラリを NuGet パッケージで配布する ##

NuGet パッケージとして発行すると、クラス ライブラリがより広く利用可能になります。 NuGet パッケージの作成は Visual Studio ではサポートされていません。 作成するには、次のように [`dotnet.exe` コマンド ライン ユーティリティ](../../core/tools/dotnet.md)を使用します。

1. コンソール ウィンドウが開きます。 たとえば、Windows タスクバーの **[何でも聞いてください]** ボックスに、「`Command Prompt`」と入力し、**[コマンド プロンプト]** デスクトップ アプリを選択してコンソール ウィンドウを開きます。

1. ライブラリのプロジェクト ディレクトリに移動します。 ファイルの場所を再構成していなければ、通常は `Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary` ディレクトリにあります。 このディレクトリには、ソース コードおよびプロジェクト ファイル `StringLibrary.csproj` が含まれています。

1. `dotnet.exe pack --no-build` コマンドを実行します。 `dotnet.exe` ユーティリティにより、.nupkg 拡張子を持つパッケージが生成されます。

   > [!TIP]
   > `dotnet.exe` を含むディレクトリがパスになくても、コンソール ウィンドウに「`where dotnet.exe`」と入力して、場所を検索できます。

NuGet パッケージの作成の詳細については、「[クロスプラットフォーム ツールを使用して NuGet パッケージを作成する方法](../../core/deploying/creating-nuget-packages.md)」を参照してください。
