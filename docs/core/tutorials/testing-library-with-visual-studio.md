---
title: "Visual Studio 2017 の .NET Core を使用したクラス ライブラリのテスト"
description: "Visual Studio 2017 を使用してC# で記述されたクラス ライブラリをテストする方法について説明します"
keywords: ".NET Core, .NET Standard クラス ライブラリ, Visual Studio 2017, 単体テスト"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
ms.translationtype: HT
ms.sourcegitcommit: 3a25c1c3b540bac8ef963a8bbf708b0700c3e9e2
ms.openlocfilehash: 30e46ae97563add2bdf34948349cf2d6214d0de8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---

# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 の .NET Core を使用したクラス ライブラリのテスト

「[Visual Studio 2017 での C# と .NET Core を使用したクラス ライブラリの構築](library-with-visual-studio.md)」または「[Visual Studio 2017 で Visual Basic と .NET Core を使用したクラス ライブラリの構築](vb-library-with-visual-studio.md)」では、<xref:System.String> クラスに拡張メソッドを追加する簡単なクラス ライブラリを作成しました。 ここでは、それが期待どおり動作するかを確認する単体テストを作成しましょう。 この単体テスト プロジェクトは、前のトピックで作成したソリューションに追加します。

## <a name="creating-a-unit-test-project"></a>単体テスト プロジェクトの作成

単体テスト プロジェクトを作成するには、次の操作を行います。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. **ソリューション エクスプローラー**で [**ClassLibraryProjects**] ソリューション ノードのコンテキスト メニューを開き、[**追加**] > [**新しいプロジェクト**] の順に選択します。

1. [**新しいプロジェクトの追加**] ダイアログで、[**Visual C#**] ノードを選択します。 次に、[**.NET Core**] ノードを選び、[**単体テスト プロジェクト (.NET Core)**] プロジェクト テンプレートを選びます。 [**名前**] テキスト ボックスに、プロジェクト名として "StringLibraryTest" と入力します。 [**OK**] を選択し、単体テスト プロジェクトを作成します。

   ![[新しいプロジェクトの追加] ダイアログ](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > 単体テストプロジェクトに加え、Visual Studio を使用して .NET Core 用の xUnit テスト プロジェクトを作成することもできます。

1. Visual Studio でプロジェクトが作成され、コード ウィンドウ内に *UnitTest1.cs* ファイルが開かれます。

   ![既定の単体テスト プロジェクト UnitTest1 クラスおよび TestMethod1 メソッドを示す Visual Studio コード ウィンドウ](./media/testing-library-with-visual-studio/unittestwindow.png)

   単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。

   * 単体テストに使用する型を含む [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) という名前空間がインポートされます。

   * [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が `UnitTest1` クラスに適用されます。 \[TestMethod\] 属性でタグ付けされたテスト クラス内の各テスト メソッドは、単体テスト実行時に自動実行されます。

   * [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性が適用され、単体テスト実行時に自動実行されるテスト メソッドとして `TestMethod1` が定義されます。

1. **ソリューション エクスプローラー**で [**StringLibraryTest**] プロジェクトの [**依存関係**] ノードを右クリックし、コンテキスト メニューの [**参照の追加**] を選択します。

   ![StringLibraryTest の依存関係のコンテキスト メニュー](./media/testing-library-with-visual-studio/addreference.png)

1. [**参照マネージャー**] ダイアログで、[**プロジェクト**] ノードを展開し、[**StringLibrary**] の横のボックスをオンにします。 `StringLibrary` アセンブリへの参照を追加すると、コンパイラで **StringLibrary** メソッドを見つけることができるようになります。 [**OK**] ボタンを選択します。 これによってクラス ライブラリ プロジェクト `StringLibrary` への参照が追加されます。

   ![参照マネージャー](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. **ソリューション エクスプローラー**で [**ClassLibraryProjects**] ソリューション ノードのコンテキスト メニューを開き、[**追加**] > [**新しいプロジェクト**] の順に選択します。

1. [**新しいプロジェクトの追加**] ダイアログで、[**Visual Basic**] ノードを選択します。 次に、[**.NET Core**] ノードを選び、[**単体テスト プロジェクト (.NET Core)**] プロジェクト テンプレートを選びます。 [**名前**] テキスト ボックスに、プロジェクト名として "StringLibraryTest" と入力します。 [**OK**] を選択し、単体テスト プロジェクトを作成します。

   ![[新しいプロジェクトの追加] ダイアログ](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > 単体テストプロジェクトに加え、Visual Studio を使用して .NET Core 用の xUnit テスト プロジェクトを作成することもできます。

1. Visual Studio でプロジェクトが作成され、コード ウィンドウ内に *UnitTest1.vb* ファイルが開かれます。

   ![既定の単体テスト プロジェクト UnitTest1 クラスおよび TestMethod1 メソッドを示す Visual Studio コード ウィンドウ](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。

   * 単体テストに使用する型を含む [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) という名前空間がインポートされます。

   * [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が `UnitTest1` クラスに適用されます。 \[TestMethod\] 属性でタグ付けされたテスト クラス内の各テスト メソッドは、単体テスト実行時に自動実行されます。

   * [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性が適用され、単体テスト実行時に自動実行されるテスト メソッドとして `TestMethod1` が定義されます。

1. **ソリューション エクスプローラー**で [**StringLibraryTest**] プロジェクトの [**依存関係**] ノードを右クリックし、コンテキスト メニューの [**参照の追加**] を選択します。

   ![StringLibraryTest の依存関係のコンテキスト メニュー](./media/testing-library-with-visual-studio/addreference.png)

1. [**参照マネージャー**] ダイアログで、[**プロジェクト**] ノードを展開し、[**StringLibrary**] の横のボックスをオンにします。 `StringLibrary` アセンブリへの参照を追加すると、コンパイラで **StringLibrary** メソッドを見つけることができるようになります。 [**OK**] ボタンを選択します。 これによってクラス ライブラリ プロジェクト `StringLibrary` への参照が追加されます。

   ![参照マネージャー](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>単体テスト メソッドの追加と実行

Visual Studio で単体テストを実行すると、単体テスト クラス ([\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が適用されているクラス) 内の [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性でマークされた各メソッドが実行されます。 1 つのテスト メソッドは、最初のエラーが発生したとき、またはそのメソッドに含まれているすべてのテストが成功したときに終了します。

一般的なテストでは、[アサート](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) クラスのメンバーを呼び出します。 多くのアサート メソッドは最低 2 つのパラメーターを含んでいます。1 つは予期されるテスト結果、もう 1 つは実際のテスト結果です。 頻繁に呼び出されるメソッドには、次の表のようなものがあります。

Assert メソッド | 関数
--- | ---
`Assert.AreEqual` | 2 つの値または 2 つのオブジェクトが等しいことを確認します。 値またはオブジェクトが等しくない場合、アサートは失敗します。
`Assert.AreSame` | 2 つのオブジェクト変数が同じオブジェクトを参照していることを確認します。 変数が別々のオブジェクトを参照している場合、アサートは失敗します。
`Assert.IsFalse` | 条件が `false` であることを確認します。 条件が `true` の場合、アサートは失敗します。
`Assert.IsNotNull` | オブジェクトが `null` でないことを確認します。 オブジェクトが `null` である場合、アサートは失敗します。

テスト メソッドに [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) 属性を適用することもできます。 テスト メソッドがスローすることを期待されている例外の種類を示します。 指定した例外がスローされない場合、テストは失敗します。

`StringLibrary.StartsWithUpper` メソッドのテストでは、大文字で始まる文字列を多く用意します。 これらの場合ではメソッドが `true` を返すと予測されるので、[Assert.IsTrue(Boolean, String)](https://msdn.microsoft.com/library/ms243754.aspx) メソッドを呼び出します。 同様に、大文字以外で始まる文字列を多く用意します。 これらの場合、メソッドは `false` を返すと予測されるので、[Assert.IsFalse(Boolean, String)](https://msdn.microsoft.com/library/ms243805.aspx) メソッドを呼び出します。

ライブラリ メソッドは文字列を処理するので、[空の文字列 (`String.Empty`) ](xref:System.String.Empty) (文字がなく @System.String.Length が 0 である、有効な文字列)、および `null` 文字列 (初期化されていない文字列) を正しく処理するか確認します。 @System.String インスタンスで `StartsWithUpper` が例外メソッドとして呼び出される場合、それに `null` 文字列を渡すことはできません。 しかし、それを静的メソッドとして直接呼び出して、単一の @System.String 引数を渡すこともできます。

メソッドを 3 つ定義します。これらのメソッドでは、文字列配列の各要素について[アサート](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) メソッドが繰り返し呼び出されます。 テスト メソッドは最初のエラーが発生するとすぐに失敗するので、メソッドのオーバー ロードを呼び出して、メソッドの呼び出しで使用される文字列値を示す文字列を渡すようにします。

テスト メソッドを作成するには

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. *UnitTest1.cs* コード ウィンドウで、コードを次のコードに置き換えます。

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   `TestStartsWithUpper` メソッドでの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれており、`TestDoesNotStartWithUpper` メソッドでの小文字のテストにはギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。

1. メニュー バーで、[**ファイル**] > [**名前を付けて UnitTest1.cs を保存**] の順に選択します。 [**名前を付けてファイルを保存**] ダイアログで、[**保存**] ボタンの横にある矢印を選択して、[**エンコード付きで保存**] を選択します。

   ![[名前を付けて保存] ダイアログ](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. *UnitTest1.vb* コード ウィンドウで、コードを次のコードに置き換えます。

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   `TestStartsWithUpper` メソッドでの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれており、`TestDoesNotStartWithUpper` メソッドでの小文字のテストにはギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。

1. メニュー バーで、[**ファイル**] > [**名前を付けて UnitTest1.vb を保存**] の順に選択します。 [**名前を付けてファイルを保存**] ダイアログで、[**保存**] ボタンの横にある矢印を選択して、[**エンコード付きで保存**] を選択します。

   ![[名前を付けて保存] ダイアログ](./media/testing-library-with-visual-studio/savefileas.png)
---

1. [**保存の確認**] ダイアログで [**はい**] ボタンを選択してファイルを保存します。

1. [**保存オプションの詳細設定**] ダイアログの [**エンコード**] ドロップダウン リストから [**Unicode (UTF-8 シグネチャ付き) - コードページ 65001**] を選択し、[**OK**] の順に選択します。

   ![[保存オプションの詳細設定] ダイアログ](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   UTF8 でエンコードされたファイルにソース コードを保存できなかった場合、ASCII ファイルとして保存される場合があります。 その場合は、ランタイムで ASCII 範囲外の UTF8 文字が正確にデコードされず、テスト結果が正確でなくなります。

1. メニュー バーで [**テスト**] > [**実行**] > [**すべてのテスト**] を選択します。 [**テスト エクスプローラー**] ウィンドウが開き、テストが正常に実行されたことを示します。 3 つのテストが [**成功したテスト**] セクションに表示され、[**概要**] セクションにはテストの実行結果が表示されています。

   ![[テスト エクスプローラー] ウィンドウ](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a>テスト エラーの処理

テスト実行にはエラーがなかったので、少し変更を加えてテスト メソッドが 1 つ失敗するようにしてみましょう。

1. `TestDoesNotStartWithUpper` メソッドの `words` 配列を変更し、文字列 "Error" を含めます。 ソリューションをビルドし、テストを実行するときに、Visual Studio では、自動的に開いているファイルが保存されるため、ファイルは保存する必要はありません。

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```
   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```
1. [**テスト**] > [**実行**] > [**すべてのテスト**] をメニュー バーから選択してテストを実行します。 [**テスト エクスプローラー**] ウィンドウに、テストが 2 つ成功し、1 つ失敗したことが示されます。

   ![[テスト エクスプローラー] ウィンドウ](./media/testing-library-with-visual-studio/failedtest.png)

1. [**失敗したテスト**] セクションで、失敗したテスト `TestDoesNotStartWith` を選択します。 [**テスト エクスプローラー**] ウィンドウに、アサートによって生成されたメッセージ "Assert.IsFalse failed. Expected for 'Error': false; actual: True" が表示されます。 エラーのため、配列内の "Error" の後ろのすべての文字列はテストされませんでした。

   ![Is False アサーションの失敗を示す [テスト エクスプローラー] ウィンドウ](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. 追加したコード (`"Error", `) を削除し、テストを再実行します。 テストは成功します。

## <a name="testing-the-release-version-of-the-library"></a>ライブラリのリリース バージョンのテスト

ここまで、ライブラリのデバッグ バージョンをテストしてきました。 すべてのテストが成功し、ライブラリを十分にテストしたので、さらにライブラリのリリース ビルドに対してテストを行います。 コンパイラの最適化などのさまざまな要因により、デバッグ ビルドとリリース ビルドとでは動作が異なる場合があります。

リリース ビルドをテストするには、次の操作を行います。

1. Visual Studio のツールバーで、ビルド構成を **[デバッグ]** から **[リリース]** に変更します。

   ![Visual Studio ツール バー](./media/testing-library-with-visual-studio/toolbar.png)

1. **ソリューション エクスプローラー**で [**StringLibrary**] プロジェクトを右クリックし、コンテキスト メニューの [**ビルド**] を選択し、ライブラリを再コンパイルします。

   ![StringLibrary のコンテキスト メニュー](./media/testing-library-with-visual-studio/buildlibrary.png)

1. [**テスト**] > [**実行**] > [**すべてのテスト**] をメニュー バーから選択して単体テストを実行します。 テストが成功します。

これでライブラリのテストが完了したので、次の手順では呼び出し元が使用できるようにします。 1 つまたは複数のアプリケーションとバンドルするか、NuGet パッケージとして配布することができます。 詳細については、「[Consuming a .NET Standard Class Library ](./consuming-library-with-visual-studio.md)」 (.NET Standard クラス ライブラリを使用する) を参照してください。

