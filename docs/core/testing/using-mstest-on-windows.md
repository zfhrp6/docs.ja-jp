---
title: "Windows で MSTest と .NET Core を使用する"
description: "Visual Studio 2015 を使用して、Windows で MSTest と .NET Core を使用する方法"
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
translationtype: Human Translation
ms.sourcegitcommit: 6795f1ace77e6f4d1b2fe07e6281f4acb6d21271
ms.openlocfilehash: 11faa46347b18240e9ddf1c27f27a814103e2565

---

# <a name="unit-testing-with-mstest-and-net-core-on-windows-using-visual-studio-2015"></a>Visual Studio 2015 を使用して、Windows で MSTest と .NET Core を使用して単体テストを行う

複数のプラットフォームを対象とする場合は XUnit の方が適していますが、Windows の .NET Core でも MSTest を使用できます。

## <a name="prerequisites"></a>必須コンポーネント

「[Getting started with .NET Core on Windows](../tutorials/using-on-windows.md)」 (Windows で .NET Core を使用する) の指示に従って、ライブラリ オブジェクトを作成します。

### <a name="writing-the-test-project-using-mstest"></a>MSTest を使用するテスト プロジェクトの作成

1. ソリューション エクスプローラーで、**[ソリューション]** ノードのコンテキスト メニューを開き、**[追加]**、**[新しいソリューション フォルダー]** の順に選択します。 フォルダーの名前を "test" にします。 
   これはソリューション フォルダーであり、物理フォルダーではありません。

2. **test** フォルダーのコンテキスト メニューを開き、**[追加]** の **[新しいプロジェクト]** を選択します。 **[新しいプロジェクト]** ダイアログ ボックスで、**[コンソール アプリケーション (.NET Core)]** を選択します。 "TestLibrary" という名前を付けて、`Golden\test` パスの下に置きます。 

   > [!IMPORTANT]
   > クラス ライブラリではなくコンソール アプリケーションのプロジェクトを作成する必要があります。

3. **TestLibrary** プロジェクトで、**[参照]** ノードのコンテキスト メニューを開き、**[参照の追加]** を選択します。 

4. **[参照マネージャー]** ダイアログ ボックスで、**[プロジェクト]**、**[ソリューション]** ノードの **[ライブラリ]** をオンにして、**[OK]** をクリックします。 

5. **TestLibrary** プロジェクトで `project.json` ファイルを開き、`"Library": "1.0.0-*"` を `"Library": {"target": "project"}` に置き換えます。 

   これは、`Library` プロジェクトが同じ名前の NuGet パッケージに解決されるのを防ぐためです。 target を "project" に明示的に設定することで、ツールはパッケージではなくその名前のプロジェクトを最初に検索します。 

6. **[参照]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。

7. **[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。 **[プレリリースを含める]** チェック ボックスをオンにし、**MSTest.TestFramework** のバージョン 1.0.1-preview 以降を参照して、**[インストール]** をクリックします。 

8. **dotnet-test-mstest** バージョン 1.1.1-preview 以降を参照して、**[インストール]** をクリックします。

9. `project.json` を編集し、`"version"` セクションの後に `"testRunner": "mstest",` を追加します。

10. `LibraryTests.cs` クラス ファイルを **TestLibrary** プロジェクトに追加し、`using` ディレクティブの `Microsoft.VisualStudio.TestTools.UnitTesting;` と `using Library;` をファイルの先頭に追加して、次のコードをクラスに追加します。
    ```csharp
    [TestClass]
    public class LibraryTests
    {
        [TestMethod]
        public void ThingGetsObjectValFromNumber()
        {
            Assert.AreEqual(42, new Thing().Get(42));
        }
    }
    ```
    * 必要に応じて、`Program.cs` ファイルを **TestLibrary** プロジェクトから削除し、`"buildOptions": {"emitEntryPoint": true},` を `project.json` から削除します。

   ソリューションをビルドできるようになります。 
   
11. **[テスト]** メニューで **[Windows]**、**[テスト エクスプローラー]** の順に選択し、テスト エクスプローラーで **[すべて実行]** を選択します。
   
   テストで問題がないことを確認します。



<!--HONumber=Nov16_HO3-->


