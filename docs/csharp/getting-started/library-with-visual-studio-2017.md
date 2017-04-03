---
title: "Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築"
description: "Visual Studio 2017 を使用してC# で記述されたクラス ライブラリを構築する方法について"
keywords: ".NET Core、.NET Standard クラス ライブラリ、Visual Studio 2017"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 28fa60cdcf8e0056314af271208759eadd8503a5
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築 #

クラス ライブラリは、任意のアプリケーションから呼び出すことができる型とメソッドを定義します。 .NET Core を使用して開発されたクラス ライブラリは .NET Standard Library をサポートしており、お使いのライブラリを、そのバージョンの .NET Standard Library をサポートする任意の .NET プラットフォームによって呼び出すことができます。 クラス ライブラリを完了させたら、サードパーティ製のコンポーネントとして配布するかどうか、あるいは 1 つまたは複数のアプリケーションにバンドルされるコンポーネントとして含めるかどうかを決定できます。

> [!NOTE]
> .NET Standard のバージョンとサポート対象のプラットフォームの一覧は、[.NET Standard Library](../../standard/library.md) を参照してください。

このトピックでは、1 つの文字列処理メソッドを含む簡単なユーティリティ ライブラリを作成します。 それを[拡張メソッド](../../csharp/programming-guide/classes-and-structs/extension-methods.md)として実装して、@System.String クラスのメンバーと同じように呼び出すことができるようにします。

## <a name="creating-a-class-library-solution"></a>クラス ライブラリのソリューションを作成する ##

クラス ライブラリ プロジェクトとその関連プロジェクトのソリューションを作成してみましょう。 1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。 このソリューションは次のように作成します。

1. Visual Studio メニュー バーで、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順に選択します。

1. 次の図のように、**[新しいプロジェクト]** ダイアログ ボックスで、**[その他のプロジェクトの種類]** ノードを展開し **[Visual Studio ソリューション]** を選択します。

   ![イメージ](./media/solution.jpg)

1. ソリューションの名前を "ClassLibraryProjects" とし、**[OK]** ボタンをクリックします。 次の図に、結果を示します。

   ![イメージ](./media/vs_with_solution.jpg)

## <a name="creating-the-class-library-project"></a>クラス ライブラリ プロジェクトの作成 ##

次にクラス ライブラリ プロジェクトを作成します。

1. **ソリューション エクスプローラー**で、**[ClassLibraryProjects]** ノードのコンテキスト メニューを開き、**[追加]**、**[新しいプロジェクト]** の順に選択します。

1. **[新しいプロジェクトの追加]** ダイアログで **[.NET Core]** ノードを選択し、**[Class Library (.NET Standard)]** テンプレートを選択します。

1. 次の図に示すように、**[名前]** テキスト ボックスでプロジェクト名として "StringLibrary" を入力します。

   ![イメージ](./media/lib_project.jpg)

1. **[OK]** をクリックしてクラス ライブラリ オブジェクトを作成します。 次の図に、結果を示します。

   ![イメージ](./media/class_library.jpg)

1. コード ウィンドウ内のコードを、次のコードと置き換えます。

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   クラス ライブラリ `UtilityLibraries.StringLibrary` には `StartsWithUpper` という名前のメソッドが含まれており、これによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す @System.Boolean 値が返されます。 どの文字が大文字かは、Unicode 規格によって定義されています。 .NET Core では、[Char.IsUpper](xref:System.Char.IsUpper(System.Char)) メソッドは文字が大文字の場合に `true` を返します。

1. メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。 プロジェクトはエラーなしでコンパイルされます。

## <a name="the-next-step"></a>次のステップ ##

ここまでで、ライブラリを正常に作成しました。 しかしそのメソッドの呼び出しをまだ行っていないので、期待どおりに動作するかわかりません。 ライブラリ開発の次のステップとして、[C# ユニット テスト プロジェクト](testing-library-with-visual-studio.md)の内容を使用して、テストをしてみましょう。



