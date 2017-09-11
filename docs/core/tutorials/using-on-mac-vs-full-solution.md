---
title: "Visual Studio for Mac を使用した macOS での完全な .NET Core ソリューションの構築"
description: "このトピックでは、再利用可能なライブラリと単体テストを含む .NET Core ソリューションの構築方法を示します。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 6945bedf-5bf3-4955-8588-83fb87511b79
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 60179fb0435803c3235b75ba012e588c6f1b35d3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="1b048-104">Visual Studio for Mac を使用した macOS での完全な .NET Core ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="1b048-104">Building a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="1b048-105">Visual Studio for Mac では、.NET Core アプリケーション開発用の機能をすべて備えた統合開発環境 (IDE) が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-105">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="1b048-106">このトピックでは、再利用可能なライブラリと単体テストを含む .NET Core ソリューションの構築方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1b048-106">This topic walks you through building a .NET Core solution that includes a reusable library and unit testing.</span></span>

<span data-ttu-id="1b048-107">このチュートリアルでは、ユーザーが入力した検索語とテキスト文字列を受け入れ、クラス ライブラリでメソッドを使用した場合に文字列に検索語が表示される回数をカウントし、ユーザーに結果を返すアプリケーションの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1b048-107">This tutorial shows you how to create an application that accepts a search word and a string of text from the user, counts the number of times the search word appears in the string using a method in a class library, and returns the result to the user.</span></span> <span data-ttu-id="1b048-108">ソリューションには、テスト駆動開発 (TDD) の概念の概要としてクラス ライブラリの単体テストも含まれています。</span><span class="sxs-lookup"><span data-stu-id="1b048-108">The solution also includes unit testing for the class library as an introduction to test-driven development (TDD) concepts.</span></span> <span data-ttu-id="1b048-109">完全なサンプルでチュートリアルを続行する場合は、[サンプル ソリューション](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1b048-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample solution](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter).</span></span> <span data-ttu-id="1b048-110">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b048-110">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

> [!NOTE]
> <span data-ttu-id="1b048-111">お客様のフィードバックは非常に貴重です。</span><span class="sxs-lookup"><span data-stu-id="1b048-111">Your feedback is highly valued.</span></span> <span data-ttu-id="1b048-112">次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信できます。</span><span class="sxs-lookup"><span data-stu-id="1b048-112">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="1b048-113">Visual Studio for Mac で、メニューから **[ヘルプ]** > **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="1b048-113">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="1b048-114">お客様のフィードバックは、[開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/41/index.html) ポータルで追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="1b048-114">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> * <span data-ttu-id="1b048-115">提案するには、メニューから **[ヘルプ]** > **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、[Visual Studio for Mac の UserVoice Web ページ](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac)に移動します。</span><span class="sxs-lookup"><span data-stu-id="1b048-115">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1b048-116">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1b048-116">Prerequisites</span></span>

- <span data-ttu-id="1b048-117">OpenSSL (.NET Core 1.1 が実行されている場合): 「[Mac における .NET Core の前提条件](../macos-prerequisites.md)」のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1b048-117">OpenSSL (if running .NET Core 1.1): See the [Prerequisites for .NET Core on Mac](../macos-prerequisites.md) topic.</span></span>
- [<span data-ttu-id="1b048-118">.NET Core SDK 1.1 以降</span><span class="sxs-lookup"><span data-stu-id="1b048-118">.NET Core SDK 1.1 or later</span></span>](https://www.microsoft.com/net/core#macos)
- [<span data-ttu-id="1b048-119">Visual Studio 2017 for Mac</span><span class="sxs-lookup"><span data-stu-id="1b048-119">Visual Studio 2017 for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="1b048-120">必須コンポーネントの詳細については、「[Mac における .NET Core の前提条件](../../core/macos-prerequisites.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b048-120">For more information on prerequisites, see the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md).</span></span> <span data-ttu-id="1b048-121">Visual Studio 2017 for Mac の完全なシステム要件については、「[Visual Studio 2017 for Mac 製品ファミリのシステム要件](https://www.visualstudio.com/productinfo/vs2017-system-requirements-mac)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1b048-121">For the full system requirements of Visual Studio 2017 for Mac, see [Visual Studio 2017 for Mac Product Family System Requirements](https://www.visualstudio.com/productinfo/vs2017-system-requirements-mac).</span></span>

## <a name="building-a-library"></a><span data-ttu-id="1b048-122">ライブラリのビルド</span><span class="sxs-lookup"><span data-stu-id="1b048-122">Building a library</span></span>

1. <span data-ttu-id="1b048-123">ようこそ画面で、**[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-123">On the Welcome screen, select **New Project**.</span></span> <span data-ttu-id="1b048-124">**[新しいプロジェクト]** ダイアログで、**[Multiplatform (マルチプラットフォーム)]** ノードの下にある **[.NET Standard Library (.NET 標準ライブラリ)]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-124">In the **New Project** dialog under the **Multiplatform** node, select the **.NET Standard Library** template.</span></span> <span data-ttu-id="1b048-125">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-125">Select **Next**.</span></span>

   ![[新しいプロジェクト] ダイアログ](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. <span data-ttu-id="1b048-127">プロジェクトには "TextUtils" ("Text Utilities" の短い名前)、ソリューションには "WordCounter" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1b048-127">Name the project "TextUtils" (a short name for "Text Utilities") and the solution "WordCounter".</span></span> <span data-ttu-id="1b048-128">**[ソリューション ディレクトリ内にプロジェクト ディレクトリを作成します]** チェック ボックスはそのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="1b048-128">Leave **Create a project directory within the solution directory** checked.</span></span> <span data-ttu-id="1b048-129">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-129">Select **Create**.</span></span>

   ![[新しいプロジェクト] ダイアログ](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. <span data-ttu-id="1b048-131">**[ソリューション]** サイドバーで、`TextUtils` ノードを展開し、テンプレートで提供される *Class1.cs* というクラス ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="1b048-131">In the **Solution** sidebar, expand the `TextUtils` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="1b048-132">ファイルを右クリックし、コンテキスト メニューから **[名前の変更]** を選択して、ファイル名を *WordCount.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="1b048-132">Right-click the file, select **Rename** from the context menu, and rename the file to *WordCount.cs*.</span></span> <span data-ttu-id="1b048-133">ファイルを開き、内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1b048-133">Open the file and replace the contents with the following code:</span></span>

   <span data-ttu-id="1b048-134">[!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]</span><span class="sxs-lookup"><span data-stu-id="1b048-134">[!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]</span></span>

1. <span data-ttu-id="1b048-135">ファイルを保存します。その場合、3 つの異なる方法 (キーボード ショートカット <kbd>&#8984;</kbd>+<kbd>s</kbd> キーを使用する、メニューから **[ファイル]** > **[保存]** の順に選択する、ファイルのタブを右クリックしてコンテキスト メニューから **[保存]** を選択する) のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b048-135">Save the file by using any of three different methods: use the keyboard shortcut <kbd>&#8984;</kbd>+<kbd>s</kbd>, select **File** > **Save** from the menu, or right-click on the file's tab and select **Save** from the contextual menu.</span></span> <span data-ttu-id="1b048-136">次のイメージは IDE ウィンドウを示しています。</span><span class="sxs-lookup"><span data-stu-id="1b048-136">The following image shows the IDE window:</span></span>

   ![TextUtils クラス ライブラリ、WordCount クラス ファイル、静的クラス WordCount、および GetWordCount メソッドを示す IDE ウィンドウ](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. <span data-ttu-id="1b048-138">IDE ウィンドウの下部の余白にある **[エラー]** を選択して、**[エラー]** パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1b048-138">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="1b048-139">**[ビルド出力]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-139">Select the **Build Output** button.</span></span>

   ![[エラー] ボタンが示された IDE の下余白](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. <span data-ttu-id="1b048-141">メニューから **[ビルド]** > **[すべてビルド]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-141">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="1b048-142">ソリューションがビルドされます。</span><span class="sxs-lookup"><span data-stu-id="1b048-142">The solution builds.</span></span> <span data-ttu-id="1b048-143">ビルド出力パネルに、ビルドが成功したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-143">The build output panel shows that the build is successful.</span></span>

   ![ビルドの成功メッセージが表示された、[エラー] パネルのビルド出力ウィンドウ](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a><span data-ttu-id="1b048-145">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="1b048-145">Creating a test project</span></span>

<span data-ttu-id="1b048-146">単体テストでは、開発および公開時に自動化されたソフトウェア テストが提供されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-146">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="1b048-147">このチュートリアルで使用するテスト フレームワークは [xUnit (バージョン 2.2.0 以降)](https://xunit.github.io/) です。これは、以下の手順で xUnit テスト プロジェクトをソリューションに追加したときに自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1b048-147">The testing framework that you use in this tutorial is [xUnit (version 2.2.0 or later)](https://xunit.github.io/), which is installed automatically when the xUnit test project is added to the solution in the following steps:</span></span>

1. <span data-ttu-id="1b048-148">**[ソリューション]** サイドバーで、`WordCounter` ソリューション名を右クリックし、**[追加]** > **[新しいプロジェクトの追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-148">In the **Solution** sidebar, right-click the `WordCounter` solution and select **Add** > **Add New Project**.</span></span>

1. <span data-ttu-id="1b048-149">**[新しいプロジェクト]** ダイアログで、**[.NET Core]** ノードから **[テスト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-149">In the **New Project** dialog, select **Tests** from the **.NET Core** node.</span></span> <span data-ttu-id="1b048-150">**[xUnit Test Project (xUnit テスト プロジェクト)]** を選択してから **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-150">Select the **xUnit Test Project** followed by **Next**.</span></span>

   ![xUnit テスト プロジェクトを作成する [新しいプロジェクト] ダイアログ](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. <span data-ttu-id="1b048-152">新しいプロジェクトに "TestLibrary" という名前を付けて、**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-152">Name the new project "TestLibrary" and select **Create**.</span></span>

   ![プロジェクト名が示された [新しいプロジェクト] ダイアログ](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. <span data-ttu-id="1b048-154">テスト ライブラリを `WordCount` クラスで使用するには、`TextUtils` プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="1b048-154">In order for the test library to work with the `WordCount` class, add a reference to the `TextUtils` project.</span></span> <span data-ttu-id="1b048-155">**[ソリューション]** サイドバーで、**TestLibrary** の下にある **[依存関係]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="1b048-155">In the **Solution** sidebar, right-click **Dependencies** under **TestLibrary**.</span></span> <span data-ttu-id="1b048-156">コンテキスト メニューから **[参照の編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-156">Select **Edit References** from the context menu.</span></span>

1. <span data-ttu-id="1b048-157">**[参照の編集]** ダイアログで、**[プロジェクト]** タブの **[TextUtils]** プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-157">In the **Edit References** dialog, select the **TextUtils** project on the **Projects** tab.</span></span> <span data-ttu-id="1b048-158">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-158">Select **OK**.</span></span>

   ![[参照の編集] ダイアログ](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. <span data-ttu-id="1b048-160">**[TestLibrary]** プロジェクトで、*UnitTest1.cs* ファイルの名前を *TextUtilsTests.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="1b048-160">In the **TestLibrary** project, rename the *UnitTest1.cs* file to *TextUtilsTests.cs*.</span></span>

1. <span data-ttu-id="1b048-161">ファイルを開き、コードを次のものと置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1b048-161">Open the file and replace the code with the following:</span></span>

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");
   
               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   <span data-ttu-id="1b048-162">次のイメージは、単体テスト コードが配置済みの IDE を示しています。</span><span class="sxs-lookup"><span data-stu-id="1b048-162">The following image shows the IDE with the unit test code in place.</span></span> <span data-ttu-id="1b048-163">`Assert.NotEqual` ステートメントに注目してください。</span><span class="sxs-lookup"><span data-stu-id="1b048-163">Pay attention to the `Assert.NotEqual` statement.</span></span>

   ![IDE のメイン ウィンドウで GetWordCount を確認する最初の単体テスト](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   <span data-ttu-id="1b048-165">TDD を使用して、新しいテストを一度失敗させてテスト ロジックが正しいことを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="1b048-165">Using TDD, it's important to make a new test fail once to confirm its testing logic is correct.</span></span> <span data-ttu-id="1b048-166">メソッドは "Jack" (先頭が大文字) という名前と、"Jack" および "jack" (先頭が大文字のものと小文字のもの) を含む文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="1b048-166">The method passes in the name "Jack" (uppercase) and a string with "Jack" and "jack" (uppercase and lowercase).</span></span> <span data-ttu-id="1b048-167">`GetWordCount` メソッドが正しく機能している場合は、検索語の 2 つのインスタンスのカウントが返されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-167">If the `GetWordCount` method is working properly, it returns a count of two instances of the search word.</span></span> <span data-ttu-id="1b048-168">このテストを意図的に失敗させるには、まず、検索語 "Jack" の 2 つのインスタンスが `GetWordCount` メソッドで返されないことをアサートするテストを実装します。</span><span class="sxs-lookup"><span data-stu-id="1b048-168">In order to fail this test on purpose, you first implement the test asserting that two instances of the search word "Jack" aren't returned by the `GetWordCount` method.</span></span> <span data-ttu-id="1b048-169">次の手順に進んで意図的にテストを失敗させます。</span><span class="sxs-lookup"><span data-stu-id="1b048-169">Continue to the next step to fail the test on purpose.</span></span>

1. <span data-ttu-id="1b048-170">画面の右側の **[単体テスト]** パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1b048-170">Open the **Unit Tests** panel on the right side of the screen.</span></span>

![[単体テスト] パネル](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. <span data-ttu-id="1b048-172">**[ドッキング]** アイコンをクリックして、パネルを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="1b048-172">Click the **Dock** icon to keep the panel open.</span></span>

![[単体テスト] パネルの [ドッキング] アイコン](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. <span data-ttu-id="1b048-174">**[すべて実行]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b048-174">Click the **Run All** button.</span></span>
   
   <span data-ttu-id="1b048-175">テストは失敗します。これが正しい結果です。</span><span class="sxs-lookup"><span data-stu-id="1b048-175">The test fails, which is the correct result.</span></span> <span data-ttu-id="1b048-176">テスト メソッドは、`GetWordCount` メソッドに指定された文字列 "Jack jack" から `inputString` "Jack" の 2 つのインスタンスが返されないことをアサートします。</span><span class="sxs-lookup"><span data-stu-id="1b048-176">The test method asserts that two instances of the `inputString`, "Jack," aren't returned from the string "Jack jack" provided to the `GetWordCount` method.</span></span> <span data-ttu-id="1b048-177">単語の大文字と小文字は `GetWordCount` メソッドでは考慮されないため、2 つのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-177">Since word casing was factored out in the `GetWordCount` method, two instances are returned.</span></span> <span data-ttu-id="1b048-178">2 *is not equal to* 2 というアサーションは失敗します。</span><span class="sxs-lookup"><span data-stu-id="1b048-178">The assertion that 2 *is not equal to* 2 fails.</span></span> <span data-ttu-id="1b048-179">これは正しい結果であり、テストのロジックは適切です。</span><span class="sxs-lookup"><span data-stu-id="1b048-179">This is the correct outcome, and the logic of our test is good.</span></span>

   ![テスト失敗](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. <span data-ttu-id="1b048-181">`Assert.NotEqual` から `Assert.Equal` に変更して `IgnoreCasing` テスト メソッドを変更します。</span><span class="sxs-lookup"><span data-stu-id="1b048-181">Modify the `IgnoreCasing` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="1b048-182">ファイルを保存します。その場合、キーボード ショートカット <kbd>&#8984;</kbd>+<kbd>s</kbd> を使用するか、メニューの **[ファイル]** > **[保存]** の順に選択するか、ファイルのタブを右クリックしてコンテキスト メニューから **[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-182">Save the file by using the keyboard shortcut <kbd>&#8984;</kbd>+<kbd>s</kbd>, **File** > **Save** from the menu, or right-clicking on the file's tab and selecting **Save** from the context menu.</span></span>

   <span data-ttu-id="1b048-183">`searchWord` "Jack" は `GetWordCount` に渡された `inputString` "Jack jack" を含む 2 つのインスタンスを返すことが予想されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-183">You expect that the `searchWord` "Jack" returns two instances with `inputString` "Jack jack" passed into `GetWordCount`.</span></span> <span data-ttu-id="1b048-184">**[単体テスト]** パネルの **[テストの実行]** ボタン、または画面下部の **[テスト結果]** パネルの **[テストの再実行]** ボタンをクリックして、テストを再実行します。</span><span class="sxs-lookup"><span data-stu-id="1b048-184">Run the test again by clicking the **Run Tests** button in the **Unit Tests** panel or the **Rerun Tests** button in the **Test Results** panel at the bottom of the screen.</span></span> <span data-ttu-id="1b048-185">テストに合格します。</span><span class="sxs-lookup"><span data-stu-id="1b048-185">The test passes.</span></span> <span data-ttu-id="1b048-186">文字列 "Jack jack" (大文字と小文字は無視) に "Jack" のインスタンスが 2 つあり、テスト アサーションは `true` です。</span><span class="sxs-lookup"><span data-stu-id="1b048-186">There are two instances of "Jack" in the string "Jack jack" (ignoring casing), and the test assertion is `true`.</span></span>

   ![テスト成功](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. <span data-ttu-id="1b048-188">`Fact` での個々の戻り値のテストは、単体テストで実行できることのほんの一部に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="1b048-188">Testing individual return values with a `Fact` is only the beginning of what you can do with unit testing.</span></span> <span data-ttu-id="1b048-189">別の強力な手法では、`Theory` を使用して一度に複数の値をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="1b048-189">Another powerful technique allows you to test several values at once using a `Theory`.</span></span> <span data-ttu-id="1b048-190">次のメソッドを `TextUtils_GetWordCountShould` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="1b048-190">Add the following method to your `TextUtils_GetWordCountShould` class.</span></span> <span data-ttu-id="1b048-191">このメソッドを追加すると、クラスのメソッドは 2 つになります。</span><span class="sxs-lookup"><span data-stu-id="1b048-191">You have two methods in the class after you add this method:</span></span>

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count, 
                                       string searchWord, 
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   <span data-ttu-id="1b048-192">`CountInstancesCorrectly` は、`GetWordCount` メソッドが正しくカウントすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1b048-192">The `CountInstancesCorrectly` checks that the `GetWordCount` method counts correctly.</span></span> <span data-ttu-id="1b048-193">`InlineData` は確認するカウント、検索語、および入力文字列を示します。</span><span class="sxs-lookup"><span data-stu-id="1b048-193">The `InlineData` provides a count, a search word, and an input string to check.</span></span> <span data-ttu-id="1b048-194">テスト メソッドはデータの行ごとに一度実行されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-194">The test method runs once for each line of data.</span></span> <span data-ttu-id="1b048-195">繰り返しますが、データのカウントが正しく、値が `GetWordCount` メソッドで返されるカウントと一致することがわかっている場合でも、まず、`Assert.NotEqual` を使用して失敗をアサートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b048-195">Note once again that you're asserting a failure first by using `Assert.NotEqual`, even when you know that the counts in the data are correct and that the values match the counts returned by the `GetWordCount` method.</span></span> <span data-ttu-id="1b048-196">意図的にテストを失敗させる手順を実行するのは、最初は時間の無駄と思えるかもしれませんが、まず、テストを失敗させてロジックを確認することはテストのロジックを確認するうえで重要なことです。</span><span class="sxs-lookup"><span data-stu-id="1b048-196">Performing the step of failing the test on purpose might seem like a waste of time at first, but checking the logic of the test by failing it first is an important check on the logic of your tests.</span></span> <span data-ttu-id="1b048-197">失敗させようとしたのに成功するテスト メソッドがある場合、そのテストのロジックにバグがあります。</span><span class="sxs-lookup"><span data-stu-id="1b048-197">When you come across a test method that passes when you expect it to fail, you've found a bug in the logic of the test.</span></span> <span data-ttu-id="1b048-198">テスト メソッドを作成するたびに、この手順を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1b048-198">It's worth the effort to take this step every time you create a test method.</span></span>
   
1. <span data-ttu-id="1b048-199">ファイルを保存し、もう一度テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b048-199">Save the file and run the tests again.</span></span> <span data-ttu-id="1b048-200">大文字と小文字のテストは成功しますが、3 つのカウント テストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="1b048-200">The casing test passes but the three count tests fail.</span></span> <span data-ttu-id="1b048-201">これは予想したとおりの結果です。</span><span class="sxs-lookup"><span data-stu-id="1b048-201">This is exactly what you expect to happen.</span></span>

   ![テスト失敗](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. <span data-ttu-id="1b048-203">`Assert.NotEqual` から `Assert.Equal` に変更して `CountInstancesCorrectly` テスト メソッドを変更します。</span><span class="sxs-lookup"><span data-stu-id="1b048-203">Modify the `CountInstancesCorrectly` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="1b048-204">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="1b048-204">Save the file.</span></span> <span data-ttu-id="1b048-205">テストをもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="1b048-205">Run the tests again.</span></span> <span data-ttu-id="1b048-206">すべてのテストに成功します。</span><span class="sxs-lookup"><span data-stu-id="1b048-206">All tests pass.</span></span>

   ![テスト成功](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a><span data-ttu-id="1b048-208">コンソール アプリの追加</span><span class="sxs-lookup"><span data-stu-id="1b048-208">Adding a console app</span></span>

1. <span data-ttu-id="1b048-209">**[ソリューション]** サイドバーで、`WordCounter` ソリューションを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="1b048-209">In the **Solution** sidebar, right-click the `WordCounter` solution.</span></span> <span data-ttu-id="1b048-210">**[.NET Core]** > **[アプリ]** テンプレートの順に移動してテンプレートを選択し、新しい**コンソール アプリケーション**プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="1b048-210">Add a new **Console Application** project by selecting the template from the **.NET Core** > **App** templates.</span></span> <span data-ttu-id="1b048-211">**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-211">Select **Next**.</span></span> <span data-ttu-id="1b048-212">プロジェクトに **WordCounterApp** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1b048-212">Name the project **WordCounterApp**.</span></span> <span data-ttu-id="1b048-213">**[作成]** を選択し、ソリューションでプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b048-213">Select **Create** to create the project in the solution.</span></span>

1. <span data-ttu-id="1b048-214">**[ソリューション]** サイドバーで、新しい **WordCounterApp** プロジェクトの **[依存関係]** ノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="1b048-214">In the **Solutions** sidebar, right-click the **Dependencies** node of the new **WordCounterApp** project.</span></span> <span data-ttu-id="1b048-215">**[参照の編集]** ダイアログで、**TextUtils** にチェック マークを付けて **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-215">In the **Edit References** dialog, check **TextUtils** and select **OK**.</span></span>

1. <span data-ttu-id="1b048-216">*Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1b048-216">Open the *Program.cs* file.</span></span> <span data-ttu-id="1b048-217">このコードを次のコードを使って置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1b048-217">Replace the code with the following:</span></span>

   <span data-ttu-id="1b048-218">[!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]</span><span class="sxs-lookup"><span data-stu-id="1b048-218">[!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]</span></span>

1. <span data-ttu-id="1b048-219">IDE ではなく、コンソール ウィンドウでアプリを実行するには、`WordCounterApp` プロジェクトを右クリックして **[オプション]** を選択し、**[構成]** の下の **[既定]** ノードを開きます。</span><span class="sxs-lookup"><span data-stu-id="1b048-219">To run the app in a console window instead of the IDE, right-click the `WordCounterApp` project, select **Options**, and open the **Default** node under **Configurations**.</span></span> <span data-ttu-id="1b048-220">**[外部コンソールで実行]** のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1b048-220">Check the box for **Run on external console**.</span></span> <span data-ttu-id="1b048-221">**[コンソール出力を一時停止する]** オプションはオンのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="1b048-221">Leave the **Pause console output** option checked.</span></span> <span data-ttu-id="1b048-222">この設定により、コンソール ウィンドウでアプリが起動し、`Console.ReadLine` ステートメントに入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1b048-222">This setting causes the app to spawn in a console window so that you can type input for the `Console.ReadLine` statements.</span></span> <span data-ttu-id="1b048-223">IDE でそのままアプリを実行すると、`Console.WriteLine` ステートメントの出力が表示されるだけです。</span><span class="sxs-lookup"><span data-stu-id="1b048-223">If you leave the app to run in the IDE, you can only see the output of `Console.WriteLine` statements.</span></span> <span data-ttu-id="1b048-224">`Console.ReadLine` ステートメントは、IDE の **[アプリケーション出力]** パネルでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="1b048-224">`Console.ReadLine` statements do not work in the IDE's **Application Output** panel.</span></span>

   ![[プロジェクト オプション] ウィンドウ](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. <span data-ttu-id="1b048-226">Visual Studio for Mac の現在のバージョンでは、ソリューションの実行時にテストを実行できないため、コンソール アプリを直接実行します。</span><span class="sxs-lookup"><span data-stu-id="1b048-226">Because the current version of Visual Studio for Mac cannot run the tests when the solution is run, you run the console app directly.</span></span> <span data-ttu-id="1b048-227">`WordCounterApp` プロジェクトを右クリックし、コンテキスト メニューから **[Run item (項目の実行)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-227">Right-click on the `WordCounterApp` project and select **Run item** from the context menu.</span></span> <span data-ttu-id="1b048-228">[再生] ボタンでアプリを実行しようとすると、テスト ランナーとアプリの実行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="1b048-228">If you attempt to run the app with the Play button, the test runner and app fail to run.</span></span> <span data-ttu-id="1b048-229">この問題への取り組みの状態について詳しくは、[xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b048-229">For more information on the status of the work on this issue, see [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60).</span></span> <span data-ttu-id="1b048-230">アプリを実行する際に、コンソール ウィンドウで入力を求めるメッセージが表示されたら、検索語と入力文字列の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="1b048-230">When you run the app, provide values for the search word and input string at the prompts in the console window.</span></span> <span data-ttu-id="1b048-231">アプリには、文字列での検索語の表示回数が示されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-231">The app indicates the number of times the search word appears in the string.</span></span>

   !['Iro ate olives by the lake, and the olives were wonderful' という文字列で単語 olives が検索された状態を示すコンソール ウィンドウ。](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. <span data-ttu-id="1b048-234">確認する最後の機能は、Visual Studio for Mac でのデバッグです。</span><span class="sxs-lookup"><span data-stu-id="1b048-234">The last feature to explore is debugging with Visual Studio for Mac.</span></span> <span data-ttu-id="1b048-235">`Console.WriteLine` ステートメントでブレークポイントを設定します。23 行目の左余白を選択すると、コード行の横に赤い丸が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-235">Set a breakpoint on the `Console.WriteLine` statement: Select in the left margin of line 23, and you see a red circle appear next to the line of code.</span></span> <span data-ttu-id="1b048-236">コード行の任意の場所を選択し、メニューから **[実行]** > **[ブレークポイントの設定/解除]** の順に選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b048-236">Alternatively, select anywhere on the line of code and select **Run** > **Toggle Breakpoint** from the menu.</span></span>

   ![23 行目の Console.WriteLine ステートメントにブレークポイントが設定されている状態](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. <span data-ttu-id="1b048-238">`WordCounterApp` プロジェクトを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="1b048-238">Right-click the `WordCounterApp` project.</span></span> <span data-ttu-id="1b048-239">コンテキスト メニューから **[Start Debugging item (項目のデバッグの開始)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b048-239">Select **Start Debugging item** from the context menu.</span></span> <span data-ttu-id="1b048-240">アプリが実行されたら、検索語 "cat" と検索文字列 "The dog chased the cat, but the cat escaped" </span><span class="sxs-lookup"><span data-stu-id="1b048-240">When the app runs, enter the search word "cat" and "The dog chased the cat, but the cat escaped."</span></span> <span data-ttu-id="1b048-241">を入力します。</span><span class="sxs-lookup"><span data-stu-id="1b048-241">for the string to search.</span></span> <span data-ttu-id="1b048-242">`Console.WriteLine` ステートメントに達した時点でプログラムの実行が停止します。その後、ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-242">When the `Console.WriteLine` statement is reached, program execution halts before the statement is executed.</span></span> <span data-ttu-id="1b048-243">**[ローカル]** タブで、`searchWord`、`inputString`、`wordCount`、および `pluralChar` の各値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1b048-243">In the **Locals** tab, you can see the `searchWord`, `inputString`, `wordCount`, and `pluralChar` values.</span></span>

   ![Console.WriteLine ステートメントでプログラムの実行が停止した状態で、Console.WriteLine ステートメントが実行される直前の値を示す [ローカル] ウィンドウ。](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. <span data-ttu-id="1b048-245">**[イミディエイト]** ウィンドウで、「wordCount = 999;」と入力してから Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1b048-245">In the **Immediate** pane, type "wordCount = 999;" and press Enter.</span></span> <span data-ttu-id="1b048-246">これで、`wordCount` 変数に 999 という意味のない値が割り当てられます。これは、デバッグ中に変数値の置き換えが可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="1b048-246">This assigns a nonsense value of 999 to the `wordCount` variable showing that you can replace variable values while debugging.</span></span>

   ![ブレークポイントにヒットした状態。](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. <span data-ttu-id="1b048-249">ツールバーで、*続行*矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b048-249">In the toolbar, click the *continue* arrow.</span></span> <span data-ttu-id="1b048-250">コンソール ウィンドウの出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="1b048-250">Look at the output in the console window.</span></span> <span data-ttu-id="1b048-251">アプリのデバッグ時に設定した 999 という不適切な値が報告されます。</span><span class="sxs-lookup"><span data-stu-id="1b048-251">It reports the incorrect value of 999 that you set when you were debugging the app.</span></span>

   ![ツールバーの続行ボタン](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![検索ワード カウントはアプリで出力された 999 の値に変更されます](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a><span data-ttu-id="1b048-254">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b048-254">See also</span></span>

[<span data-ttu-id="1b048-255">Visual Studio 2017 for Mac リリース ノート</span><span class="sxs-lookup"><span data-stu-id="1b048-255">Visual Studio 2017 for Mac Release Notes</span></span>](https://www.visualstudio.com/news/releasenotes/vs2017-mac-relnotes)

