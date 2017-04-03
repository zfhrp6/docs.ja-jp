---
title: "Visual Studio 2017 の .NET Core を使用したクラス ライブラリのテスト"
description: "Visual Studio 2017 を使用してC# で記述されたクラス ライブラリをテストする方法について説明します"
keywords: ".NET Core, .NET Standard クラス ライブラリ, Visual Studio 2017, 単体テスト"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ee21799706b971f0ec13285b0771b32b4367f570
ms.lasthandoff: 03/13/2017

---

# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 の .NET Core を使用したクラス ライブラリのテスト #

「[Building a class library with C# and .NET Core in Visual Studio 2017 (Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築)](library-with-visual-studio-2017.md)」では、@System.String クラスに拡張メソッドを追加するシン簡単なクラス ライブラリを作成しました。 ここでは、それが期待どおり動作するかを確認する単体テストを作成しましょう。 この単体テスト プロジェクトは、前のトピックで作成したソリューションに追加します。

## <a name="creating-a-unit-test-project"></a>単体テスト プロジェクトの作成 ##

単体テスト プロジェクトを作成するには、次の操作を行います。

1. ソリューション エクスプローラーで、**[ClassLibraryProjects]** ソリューション ノードのコンテキスト メニューを開き、**[追加]** > **[新しいプロジェクト]** の順に選択します。

   <!-- Need a VS 2017 version  [!NOTE] In addition to a Unit Test project, you can also use Visual Studio to create an XUnit test project for .NET Core. For a walkthrough that includes an XUnit test project, see [Getting started with .NET Core on Windows, using Visual Studio 2015](../../core/tutorials/using-on-windows.md). --> 

1. 次の図に示すように、**[新しいプロジェクトの追加]** ダイアログ ボックスで、**[Visual C#]** ノードおよび **[.NET Core]** ノードを展開し、**[単体テスト プロジェクト (.NET Core)]** プロジェクト テンプレートを選択して「`StringLibraryTest`」と名前を付けます。

   ![イメージ](./media/testproject.jpg)

1. **[OK]** ボタンを選択すると、プロジェクトが作成されます。 次の図のように、Visual Studio でプロジェクトが作成され、コード ウィンドウ内に `UnitTest1.cs` ファイルが開かれます。

   ![イメージ](./media/unit_test_code_window.jpg)

   単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。

   - 単体テストに使用する型を含む [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) という名前空間がインポートされます。

   - [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が `UnitTest1` クラスに適用されます。 \[TestMethod\] 属性でタグ付けされたテスト クラス内の各テスト メソッドは、単体テスト実行時に自動実行されます。

   - [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性が適用され、単体テスト実行時に自動実行されるテスト メソッドとして `TestMethod1` が定義されます。

1. ソリューション エクスプローラーで **[StringLibraryTest]** プロジェクトの **[依存関係]** ノードのコンテキスト メニューを開き、**[参照の追加]** を選択します。 これによってクラス ライブラリ プロジェクト `StringLibrary` への参照が追加されます。 

1. 次の図のように、**[参照マネージャー]** ダイアログ ボックスで **[プロジェクト]** ノードを展開して、**[ソリューション]** を選択し、**[StringLibrary]** の横にあるチェックボックスをオンにします。 `StringLibrary` アセンブリへの参照を追加すると、コンパイラで **StringLibrary** メソッドへの呼び出しを解決できるようになります。

   ![イメージ](./media/add_reference.jpg)

1. **[OK]** ボタンをクリックして **[参照マネージャー]** ダイアログ ボックスを閉じます。

## <a name="adding-and-running-unit-test-methods"></a>単体テスト メソッドの追加と実行 ##

Visual Studio で単体テストを実行すると、単体テスト クラス ([\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が適用されているクラス) 内の [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性でマークされた各メソッドが実行されます。 1 つのテスト メソッドは、最初のエラーが発生したとき、またはそのメソッドに含まれているすべてのテストが成功したときに終了します。

一般的なテストでは、[アサート](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) クラスのメンバーを呼び出します。 多くのアサート メソッドは最低 2 つのパラメーターを含んでいます。1 つは予期されるテスト結果、もう 1 つは実際のテスト結果です。 頻繁に呼び出されるメソッドには、次のようなものがあります。

- `Assert.AreEqual`。2 つの値または 2 つのオブジェクトが等しいことを確認します。 値またはオブジェクトが等しくない場合、アサートは失敗します。

- `Assert.AreSame`。2 つのオブジェクト変数が同じオブジェクトを参照していることを確認します。 変数が別々のオブジェクトを参照している場合、アサートは失敗します。

- `Assert.IsFalse`。条件が False であることを確認します。 条件が True の場合、アサートは失敗します。

- `Assert.IsNotNull`。オブジェクトが `null` でないことを確認します。 オブジェクトが `null` である場合、アサートは失敗します。

さらに、[ \[ExpectedException\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) 属性を使用して、テスト メソッドがスローすると予測される例外の型を示すことができます。 これは、例外の発生につながる条件をテストするのに使用します。 指定した例外がスローされない場合、テストは失敗します。

`StringLibrary.StartsWithUpper` メソッドのテストでは、大文字で始まる文字列を多く用意します。 これらの場合ではメソッドが `True` を返すと予測されるので、[Assert.IsTrue(Boolean, String)](https://msdn.microsoft.com/library/ms243754.aspx) メソッドを呼び出します。 同様に、大文字以外で始まる文字列を多く用意します。 これらの場合メソッドは False を返すと予測されるので、[Assert.IsFalse(Boolean, String)](https://msdn.microsoft.com/library/ms243805.aspx) メソッドを呼び出します。

ライブラリ メソッドは文字列を処理するので、[空の文字列](xref:System.String.Empty) (文字がなく @System.String.Length が 0 である、有効な文字列)、および `null` 文字列 (初期化されていない文字列) を正しく処理するか確認します。 @System.String インスタンスで `StartsWithUpper` が例外メソッドとして呼び出される場合、それに `null` 文字列を渡すことはできません。 しかし、それを静的メソッドとして直接呼び出して、単一の @System.String 引数を渡すことができます。

メソッドを 3 つ定義します。これらのメソッドでは、文字列配列の各要素について[アサート](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) メソッドが繰り返し呼び出されます。 テスト メソッドは最初のエラーが発生するとすぐに失敗するので、メソッドのオーバー ロードを呼び出して、メソッドの呼び出しで使用される文字列値を示す文字列を渡すようにします。

テスト メソッドの作成は以下のように行います。

1. コード ウィンドウ内のコードを、次のコードに置き換えます。

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs#1)]

   `TestStartsWithUpper` メソッドでの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれており、`TestDoesNotStartWithUpper` メソッドでの小文字のテストにはギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。

1. メニュー バーで、**[ファイル]** > **[名前を付けて UnitTest1.cs を保存]** の順に選択します。 **[名前を付けてファイルを保存]** ダイアログ ボックスで、**[保存]** の横にある矢印を選択して、**[エンコード付きで保存...]** を選択します。*

1. [名前を付けて保存の確認] ダイアログ ボックスで **[はい]** をクリックしてファイルを保存します。

1. **[保存オプションの詳細設定]** ダイアログ ボックスの **[エンコード]** ドロップダウン リストから **[Unicode (UTF-8 シグネチャ付き) - コードページ 65001]** > **[OK]** の順に選択します。

   UTF8 でエンコードされたファイルにソース コードを保存できなかった場合、ASCII ファイルとして保存される場合があります。 その場合は、ランタイムで ASCII 範囲外の文字が正確にデコードされず、テスト結果が正確でなくなります。

1. メニュー バーで、**[テスト]** > **[実行]** > **[すべてのテスト]** の順に選択します。 次の図のように、**テスト エクスプローラー** ウィンドウが開き、両方のテストが正常に実行されたことが示されます。 3 つのテストが **[成功したテスト]** セクションに表示され、**[概要]** セクションにはテストの実行結果が表示されています。

   ![イメージ](./media/first_test.jpg)

## <a name="handling-test-failures"></a>テスト エラーの処理 ##

上記のテスト実行はエラーがなかったので、少し変更を加えてテスト メソッドが 1 つ失敗するようにしてみましょう。

1. `TestDoesNotStartWithUpper` メソッドの `words` 配列を、文字列 "Error" を含めるように変更して、次のようなステートメントにします。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. **[テスト]** > **[実行]** > **[すべてのテスト]** の順に選択して、テストを実行します。 次の図のように、**テスト エクスプローラー** ウィンドウで 2 つのテストが成功し 1 つが失敗したと表示されます。

   ![イメージ](./media/failed_test.jpg)

1. **[失敗したテスト]** セクションで、失敗したテスト `TestDoesNotStartWith` を選択します。 **テスト エクスプローラー** の下のウィンドウに、アサートによって生成されたメッセージ "Assert.IsFalse failed. Expected for 'Error': false; actual: True" が下記の**テスト エクスプローラー**の図のように表示されます。 エラーのため、配列内の "Error" の後ろのすべての文字列はテストされませんでした。

   ![イメージ](./media/failed_test2.jpg)

1. 追加されたコード (`"Error", `) を削除し、テストを再実行します。 これでテストは成功するはずです。

## <a name="testing-the-release-version-of-the-library"></a>ライブラリのリリース バージョンのテスト ##

ここまで、ライブラリのデバッグ バージョンをテストしてきました。 すべてのテストが成功し、ライブラリを十分にテストしたので、さらにライブラリのリリース ビルドに対してテストを行います。 コンパイラの最適化などのさまざまな要因により、デバッグ ビルドとリリース ビルドとでは動作が異なる場合があります。

リリース ビルドをテストするには、次の操作を行います。

1. Visual Studio のツールバーで、ビルド構成を **[デバッグ]** から **[リリース]** に変更します。 次の図は、ツールバーの一部を示しています。

   ![イメージ](./media/lib_release.jpg)

1. **ソリューション エクスプ ローラー**で、**[StringLibrary]** プロジェクト ノードのコンテキスト メニューを開き、**[ビルド]** を選択してライブラリを再コンパイルします。

1. Visual Studio メニューから **[テスト]** > **[実行]** > **[すべてのテスト]** を選択し、単体テストを再実行します。 テストはすべて成功するはずです。

これでライブラリのテストが完了したので、次の手順では呼び出し元が使用できるようにします。 1 つまたは複数のアプリケーションとバンドルするか、NuGet パッケージとして配布することができます。 これを行う方法については、「[Consuming a .NET Standard Class Library (.NET Standard クラス ライブラリを使用する)](./consuming-library-with-visual-studio-2017.md)」を参照してください。

