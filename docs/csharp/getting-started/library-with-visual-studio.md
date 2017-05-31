---
title: "Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築"
description: "Visual Studio 2017 を使用してC# で記述されたクラス ライブラリを構築する方法について"
keywords: ".NET Core、.NET Standard クラス ライブラリ、Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: 1ecccb03bc28da51a580b790b5ba8dd594bb7f18
ms.contentlocale: ja-jp
ms.lasthandoff: 05/03/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築

"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。 .NET Core を使用して開発されたクラス ライブラリは .NET Standard Library をサポートしており、お使いのライブラリを、そのバージョンの .NET Standard Library をサポートする任意の .NET プラットフォームによって呼び出すことができます。 クラス ライブラリを完了させたら、サードパーティ製のコンポーネントとして配布するかどうか、あるいは 1 つまたは複数のアプリケーションにバンドルされたコンポーネントとして含めるかどうかを決定できます。

> [!NOTE]
> .NET Standard のバージョンとサポート対象のプラットフォームの一覧は、[.NET Standard Library](../../standard/library.md) を参照してください。

このトピックでは、1 つの文字列処理メソッドを含む簡単なユーティリティ ライブラリを作成します。 それを[拡張メソッド](../../csharp/programming-guide/classes-and-structs/extension-methods.md)として実装し、@System.String クラスのメンバーと同じように呼び出すことができるようにします。

## <a name="creating-a-class-library-solution"></a>クラス ライブラリのソリューションを作成する

最初に、クラス ライブラリ プロジェクトとその関連プロジェクトのソリューションを作成します。 1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。 このソリューションは次のように作成します。

1. Visual Studio のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選びます。

1. **[新しいプロジェクト]** ダイアログの **[その他のプロジェクトの種類]** ノードを展開し、**[Visual Studio ソリューション]** を選びます。 ソリューションの名前を "ClassLibraryProjects" にして、**[OK]** ボタンを選びます。

   ![[新しいプロジェクト] ダイアログ](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>クラス ライブラリ プロジェクトの作成

クラス ライブラリ プロジェクトを作成します。

1. **ソリューション エクスプローラー**で **ClassLibraryProjects** ソリューション ファイルを右クリックし、コンテキスト メニューから **[追加]** > **[新しいプロジェクト]** の順に選びます。

1. **[新しいプロジェクトの追加]** ダイアログ ボックスで、**[.NET Core]** ノードを選び、**[クラス ライブラリ (.NET Core)]** プロジェクト テンプレートを選びます。 **[名前]** テキスト ボックスに、プロジェクト名として「StringLibrary」と入力します。 **[OK]** を選んでクラス ライブラリ プロジェクトを作成します。

   ![[新しいプロジェクトの追加] ダイアログ](./media/library-with-visual-studio/libproject.png)

   ![既定のクラス ライブラリ テンプレート コードが表示された Visual Studio アプリケーション ウィンドウ](./media/library-with-visual-studio/stringlibrary.png)

1. コード ウィンドウ内のコードを次のコードに置き換えて、ファイルを保存します。

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   クラス ライブラリ `UtilityLibraries.StringLibrary` には `StartsWithUpper` という名前のメソッドが含まれており、これによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す @System.Boolean 値が返されます。 Unicode 規格では、大文字と小文字が区別されます。 .NET Core では、[`Char.IsUpper`](xref:System.Char.IsUpper(System.Char)) メソッドは文字が大文字の場合に `true` を返します。

1. メニュー バーで [**ビルド**] > [**ソリューションのビルド**] の順に選択します。 プロジェクトはエラーなしでコンパイルされます。

   ![ビルドが成功したことを示す出力ペイン](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a>次のステップ

ライブラリを正常に作成できました。 そのメソッドの呼び出しをまだ行っていないので、期待どおりに動作するかわかりません。 ライブラリ開発の次のステップでは、[C# 単体テスト プロジェクト](testing-library-with-visual-studio.md)を使ってライブラリをテストします。

