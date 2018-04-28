---
title: Visual Studio 2017 の .NET Core を使用したクラス ライブラリのテスト
description: Visual Studio 2017 を使用してC# で記述されたクラス ライブラリをテストする方法について説明します
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: devlang-csharp
ms.devlang: csharp
dev_langs:
- csharp
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: 0356ea286238f4b722a42795c9456f7532766f7d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="60f8d-103">Visual Studio 2017 の .NET Core を使用したクラス ライブラリのテスト</span><span class="sxs-lookup"><span data-stu-id="60f8d-103">Testing a class library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="60f8d-104">「[Visual Studio 2017 での C# と .NET Core を使用したクラス ライブラリの構築](library-with-visual-studio.md)」または「[Visual Studio 2017 で Visual Basic と .NET Core を使用したクラス ライブラリの構築](vb-library-with-visual-studio.md)」では、<xref:System.String> クラスに拡張メソッドを追加する簡単なクラス ライブラリを作成しました。</span><span class="sxs-lookup"><span data-stu-id="60f8d-104">In [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md) or [Building a class library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="60f8d-105">ここでは、それが期待どおり動作するかを確認する単体テストを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="60f8d-105">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="60f8d-106">この単体テスト プロジェクトは、前のトピックで作成したソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-106">You'll add your unit test project to the solution you created in the previous topic.</span></span>

## <a name="creating-a-unit-test-project"></a><span data-ttu-id="60f8d-107">単体テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="60f8d-107">Creating a unit test project</span></span>

<span data-ttu-id="60f8d-108">単体テスト プロジェクトを作成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="60f8d-108">To create the unit test project, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="60f8d-109">C#</span><span class="sxs-lookup"><span data-stu-id="60f8d-109">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="60f8d-110">**ソリューション エクスプローラー**で **[ClassLibraryProjects]** ソリューション ノードのコンテキスト メニューを開き、**[追加]** > **[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-110">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="60f8d-111">**[新しいプロジェクトの追加]** ダイアログで、**[Visual C#]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-111">In the **Add New Project** dialog, select the **Visual C#** node.</span></span> <span data-ttu-id="60f8d-112">次に、**[.NET Core]** ノードを選び、**[単体テスト プロジェクト (.NET Core)]** プロジェクト テンプレートを選びます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-112">Then select the **.NET Core** node followed by the **Unit Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="60f8d-113">**[名前]** テキスト ボックスに、プロジェクト名として "StringLibraryTest" と入力します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-113">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="60f8d-114">**[OK]** を選択し、単体テスト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-114">Select **OK** to create the unit test project.</span></span>

   ![[新しいプロジェクトの追加] ダイアログ](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > <span data-ttu-id="60f8d-116">単体テストプロジェクトに加え、Visual Studio を使用して .NET Core 用の xUnit テスト プロジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-116">In addition to a Unit Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="60f8d-117">Visual Studio でプロジェクトが作成され、コード ウィンドウ内に *UnitTest1.cs* ファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-117">Visual Studio creates the project and opens the *UnitTest1.cs* file in the code window.</span></span>

   ![既定の単体テスト プロジェクト UnitTest1 クラスおよび TestMethod1 メソッドを示す Visual Studio コード ウィンドウ](./media/testing-library-with-visual-studio/unittestwindow.png)

   <span data-ttu-id="60f8d-119">単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-119">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="60f8d-120">単体テストに使用する型を含む [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) という名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-120">It imports the [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="60f8d-121">[\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が `UnitTest1` クラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-121">It applies the [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="60f8d-122">\[TestMethod\] 属性でタグ付けされたテスト クラス内の各テスト メソッドは、単体テスト実行時に自動実行されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-122">Each test method in a test class tagged with the \[TestMethod\] attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="60f8d-123">[\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性が適用され、単体テスト実行時に自動実行されるテスト メソッドとして `TestMethod1` が定義されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-123">It applies the [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="60f8d-124">**ソリューション エクスプローラー**で **[StringLibraryTest]** プロジェクトの **[依存関係]** ノードを右クリックし、コンテキスト メニューの **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-124">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest の依存関係のコンテキスト メニュー](./media/testing-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="60f8d-126">**[参照マネージャー]** ダイアログで、**[プロジェクト]** ノードを展開し、**[StringLibrary]** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="60f8d-126">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="60f8d-127">`StringLibrary` アセンブリへの参照を追加すると、コンパイラで **StringLibrary** メソッドを見つけることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="60f8d-127">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="60f8d-128">**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-128">Select the **OK** button.</span></span> <span data-ttu-id="60f8d-129">これによってクラス ライブラリ プロジェクト `StringLibrary` への参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-129">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![参照マネージャー](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="60f8d-131">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60f8d-131">Visual Basic</span></span>](#tab/visual-basic) 
1. <span data-ttu-id="60f8d-132">**ソリューション エクスプローラー**で **[ClassLibraryProjects]** ソリューション ノードのコンテキスト メニューを開き、**[追加]** > **[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-132">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="60f8d-133">**[新しいプロジェクトの追加]** ダイアログで、**[Visual Basic]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-133">In the **Add New Project** dialog, select the **Visual Basic** node.</span></span> <span data-ttu-id="60f8d-134">次に、**[.NET Core]** ノードを選び、**[単体テスト プロジェクト (.NET Core)]** プロジェクト テンプレートを選びます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-134">Then select the **.NET Core** node followed by the **Unit Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="60f8d-135">**[名前]** テキスト ボックスに、プロジェクト名として "StringLibraryTest" と入力します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-135">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="60f8d-136">**[OK]** を選択し、単体テスト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-136">Select **OK** to create the unit test project.</span></span>

   ![[新しいプロジェクトの追加] ダイアログ](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > <span data-ttu-id="60f8d-138">単体テストプロジェクトに加え、Visual Studio を使用して .NET Core 用の xUnit テスト プロジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-138">In addition to a Unit Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="60f8d-139">Visual Studio でプロジェクトが作成され、コード ウィンドウ内に *UnitTest1.vb* ファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-139">Visual Studio creates the project and opens the *UnitTest1.vb* file in the code window.</span></span>

   ![既定の単体テスト プロジェクト UnitTest1 クラスおよび TestMethod1 メソッドを示す Visual Studio コード ウィンドウ](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   <span data-ttu-id="60f8d-141">単体テストのテンプレートで作成されたソース コードにより、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-141">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="60f8d-142">単体テストに使用する型を含む [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) という名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-142">It imports the [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="60f8d-143">[\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が `UnitTest1` クラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-143">It applies the [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="60f8d-144">\[TestMethod\] 属性でタグ付けされたテスト クラス内の各テスト メソッドは、単体テスト実行時に自動実行されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-144">Each test method in a test class tagged with the \[TestMethod\] attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="60f8d-145">[\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性が適用され、単体テスト実行時に自動実行されるテスト メソッドとして `TestMethod1` が定義されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-145">It applies the [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="60f8d-146">**ソリューション エクスプローラー**で **[StringLibraryTest]** プロジェクトの **[依存関係]** ノードを右クリックし、コンテキスト メニューの **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-146">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest の依存関係のコンテキスト メニュー](./media/testing-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="60f8d-148">**[参照マネージャー]** ダイアログで、**[プロジェクト]** ノードを展開し、**[StringLibrary]** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="60f8d-148">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="60f8d-149">`StringLibrary` アセンブリへの参照を追加すると、コンパイラで **StringLibrary** メソッドを見つけることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="60f8d-149">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="60f8d-150">**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-150">Select the **OK** button.</span></span> <span data-ttu-id="60f8d-151">これによってクラス ライブラリ プロジェクト `StringLibrary` への参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-151">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![参照マネージャー](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a><span data-ttu-id="60f8d-153">単体テスト メソッドの追加と実行</span><span class="sxs-lookup"><span data-stu-id="60f8d-153">Adding and running unit test methods</span></span>

<span data-ttu-id="60f8d-154">Visual Studio で単体テストを実行すると、単体テスト クラス ([\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 属性が適用されているクラス) 内の [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 属性でマークされた各メソッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-154">When Visual Studio runs a unit test, it executes each method marked with the [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) attribute in a unit test class, the class to which the  [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) attribute is applied.</span></span> <span data-ttu-id="60f8d-155">1 つのテスト メソッドは、最初のエラーが発生したとき、またはそのメソッドに含まれているすべてのテストが成功したときに終了します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-155">A test method ends when the first failure is encountered or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="60f8d-156">一般的なテストでは、[アサート](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) クラスのメンバーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-156">The most common tests call members of the [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) class.</span></span> <span data-ttu-id="60f8d-157">多くのアサート メソッドは最低 2 つのパラメーターを含んでいます。1 つは予期されるテスト結果、もう 1 つは実際のテスト結果です。</span><span class="sxs-lookup"><span data-stu-id="60f8d-157">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="60f8d-158">頻繁に呼び出されるメソッドには、次の表のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="60f8d-158">Some of its most frequently called methods are shown in the table below.</span></span>

<span data-ttu-id="60f8d-159">Assert メソッド</span><span class="sxs-lookup"><span data-stu-id="60f8d-159">Assert methods</span></span> | <span data-ttu-id="60f8d-160">関数</span><span class="sxs-lookup"><span data-stu-id="60f8d-160">Function</span></span>
--- | ---
`Assert.AreEqual` | <span data-ttu-id="60f8d-161">2 つの値または 2 つのオブジェクトが等しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-161">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="60f8d-162">値またはオブジェクトが等しくない場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-162">The assert fails if the values or objects are not equal.</span></span>
`Assert.AreSame` | <span data-ttu-id="60f8d-163">2 つのオブジェクト変数が同じオブジェクトを参照していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-163">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="60f8d-164">変数が別々のオブジェクトを参照している場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-164">The assert fails if the variables refer to different objects.</span></span>
`Assert.IsFalse` | <span data-ttu-id="60f8d-165">条件が `false` であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-165">Verifies that a condition is `false`.</span></span> <span data-ttu-id="60f8d-166">条件が `true` の場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-166">The assert fails if the condition is `true`.</span></span>
`Assert.IsNotNull` | <span data-ttu-id="60f8d-167">オブジェクトが `null` でないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-167">Verifies that an object is not `null`.</span></span> <span data-ttu-id="60f8d-168">オブジェクトが `null` である場合、アサートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-168">The assert fails if the object is `null`.</span></span>

<span data-ttu-id="60f8d-169">テスト メソッドに [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) 属性を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-169">You can also apply the [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) attribute to a test method.</span></span> <span data-ttu-id="60f8d-170">テスト メソッドがスローすることを期待されている例外の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-170">It indicates the type of exception a test method is expected to throw.</span></span> <span data-ttu-id="60f8d-171">指定した例外がスローされない場合、テストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-171">The test fails if the specified exception is not thrown.</span></span>

<span data-ttu-id="60f8d-172">`StringLibrary.StartsWithUpper` メソッドのテストでは、大文字で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-172">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="60f8d-173">これらの場合ではメソッドが `true` を返すと予測されるので、[Assert.IsTrue(Boolean, String)](https://msdn.microsoft.com/library/ms243754.aspx) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-173">You expect the method to return `true` in these cases, so you can call the [Assert.IsTrue(Boolean, String)](https://msdn.microsoft.com/library/ms243754.aspx) method.</span></span> <span data-ttu-id="60f8d-174">同様に、大文字以外で始まる文字列を多く用意します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-174">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="60f8d-175">これらの場合、メソッドは `false` を返すと予測されるので、[Assert.IsFalse(Boolean, String)](https://msdn.microsoft.com/library/ms243805.aspx) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-175">You expect the method to return `false` in these cases, so you can call the [Assert.IsFalse(Boolean, String)](https://msdn.microsoft.com/library/ms243805.aspx) method.</span></span>

<span data-ttu-id="60f8d-176">ライブラリ メソッドは文字列を処理するので、[空の文字列 (`String.Empty`) ](xref:System.String.Empty) (文字がなく <xref:System.String.Length> が 0 である、有効な文字列)、および `null` 文字列 (初期化されていない文字列) を正しく処理するか確認します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-176">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that has not been initialized.</span></span> <span data-ttu-id="60f8d-177"><xref:System.String> インスタンスで `StartsWithUpper` が例外メソッドとして呼び出される場合、それに `null` 文字列を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="60f8d-177">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it cannot be passed a `null` string.</span></span> <span data-ttu-id="60f8d-178">しかし、それを静的メソッドとして直接呼び出して、単一の <xref:System.String> 引数を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-178">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="60f8d-179">メソッドを 3 つ定義します。これらのメソッドでは、文字列配列の各要素について[アサート](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) メソッドが繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-179">You'll define three methods, each of which calls its [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) method repeatedly for each element in a string array.</span></span> <span data-ttu-id="60f8d-180">テスト メソッドは最初のエラーが発生するとすぐに失敗するので、メソッドのオーバー ロードを呼び出して、メソッドの呼び出しで使用される文字列値を示す文字列を渡すようにします。</span><span class="sxs-lookup"><span data-stu-id="60f8d-180">Because the test method fails as soon as it encounters the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="60f8d-181">テスト メソッドを作成するには</span><span class="sxs-lookup"><span data-stu-id="60f8d-181">To create the test methods:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="60f8d-182">C#</span><span class="sxs-lookup"><span data-stu-id="60f8d-182">C#</span></span>](#tab/csharp) 
1. <span data-ttu-id="60f8d-183">*UnitTest1.cs* コード ウィンドウで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-183">In the *UnitTest1.cs* code window, replace the code with the following code:</span></span>

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   <span data-ttu-id="60f8d-184">`TestStartsWithUpper` メソッドでの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれており、`TestDoesNotStartWithUpper` メソッドでの小文字のテストにはギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="60f8d-184">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="60f8d-185">メニュー バーで、**[ファイル]** > **[名前を付けて UnitTest1.cs を保存]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-185">On the menu bar, select **File** > **Save UnitTest1.cs As**.</span></span> <span data-ttu-id="60f8d-186">**[名前を付けてファイルを保存]** ダイアログで、**[保存]** ボタンの横にある矢印を選択して、**[エンコード付きで保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-186">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![[名前を付けて保存] ダイアログ](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="60f8d-188">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60f8d-188">Visual Basic</span></span>](#tab/visual-basic) 
1. <span data-ttu-id="60f8d-189">*UnitTest1.vb* コード ウィンドウで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-189">In the *UnitTest1.vb* code window, replace the code with the following code:</span></span>

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="60f8d-190">`TestStartsWithUpper` メソッドでの大文字のテストには、ギリシャ語の大文字のアルファ (U+0391) とキリル文字の大文字 EM (U+041C) が含まれており、`TestDoesNotStartWithUpper` メソッドでの小文字のテストにはギリシャ語の小文字のアルファ (U+03B1) とキリル文字の小文字 Ghe (U+0433) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="60f8d-190">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="60f8d-191">メニュー バーで、**[ファイル]** > **[名前を付けて UnitTest1.vb を保存]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-191">On the menu bar, select **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="60f8d-192">**[名前を付けてファイルを保存]** ダイアログで、**[保存]** ボタンの横にある矢印を選択して、**[エンコード付きで保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-192">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![[名前を付けて保存] ダイアログ](./media/testing-library-with-visual-studio/savefileas.png)
---

1. <span data-ttu-id="60f8d-194">**[保存の確認]** ダイアログで **[はい]** ボタンを選択してファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-194">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="60f8d-195">**[保存オプションの詳細設定]** ダイアログの **[エンコード]** ドロップダウン リストから **[Unicode (UTF-8 シグネチャ付き) - コードページ 65001]** を選択し、**[OK]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-195">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   ![[保存オプションの詳細設定] ダイアログ](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   <span data-ttu-id="60f8d-197">UTF8 でエンコードされたファイルにソース コードを保存できなかった場合、ASCII ファイルとして保存される場合があります。</span><span class="sxs-lookup"><span data-stu-id="60f8d-197">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="60f8d-198">その場合は、ランタイムで ASCII 範囲外の UTF8 文字が正確にデコードされず、テスト結果が正確でなくなります。</span><span class="sxs-lookup"><span data-stu-id="60f8d-198">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be accurate.</span></span>

1. <span data-ttu-id="60f8d-199">メニュー バーで **[テスト]** > **[実行]** > **[すべてのテスト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-199">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="60f8d-200">**[テスト エクスプローラー]** ウィンドウが開き、テストが正常に実行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-200">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="60f8d-201">3 つのテストが **[成功したテスト]** セクションに表示され、**[概要]** セクションにはテストの実行結果が表示されています。</span><span class="sxs-lookup"><span data-stu-id="60f8d-201">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   ![[テスト エクスプローラー] ウィンドウ](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a><span data-ttu-id="60f8d-203">テスト エラーの処理</span><span class="sxs-lookup"><span data-stu-id="60f8d-203">Handling test failures</span></span>

<span data-ttu-id="60f8d-204">テスト実行にはエラーがなかったので、少し変更を加えてテスト メソッドが 1 つ失敗するようにしてみましょう。</span><span class="sxs-lookup"><span data-stu-id="60f8d-204">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="60f8d-205">`TestDoesNotStartWithUpper` メソッドの `words` 配列を変更し、文字列 "Error" を含めます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-205">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="60f8d-206">ソリューションをビルドし、テストを実行するときに、Visual Studio では、自動的に開いているファイルが保存されるため、ファイルは保存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="60f8d-206">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```
   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```
1. <span data-ttu-id="60f8d-207">**[テスト]** > **[実行]** > **[すべてのテスト]** をメニュー バーから選択してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-207">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="60f8d-208">**[テスト エクスプローラー]** ウィンドウに、テストが 2 つ成功し、1 つ失敗したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-208">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   ![[テスト エクスプローラー] ウィンドウ](./media/testing-library-with-visual-studio/failedtest.png)

1. <span data-ttu-id="60f8d-210">**[失敗したテスト]** セクションで、失敗したテスト `TestDoesNotStartWith` を選択します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-210">In the **Failed Tests** section, select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="60f8d-211">**[テスト エクスプローラー]** ウィンドウに、アサートによって生成されたメッセージ "Assert.IsFalse failed.</span><span class="sxs-lookup"><span data-stu-id="60f8d-211">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="60f8d-212">Expected for 'Error': false; actual: True" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-212">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="60f8d-213">エラーのため、配列内の "Error" の後ろのすべての文字列はテストされませんでした。</span><span class="sxs-lookup"><span data-stu-id="60f8d-213">Because of the failure, all strings in the array after "Error" were not tested.</span></span>

   ![Is False アサーションの失敗を示す [テスト エクスプローラー] ウィンドウ](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. <span data-ttu-id="60f8d-215">追加したコード (`"Error", `) を削除し、テストを再実行します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-215">Remove the code that you added (`"Error", `) and rerun the test.</span></span> <span data-ttu-id="60f8d-216">テストは成功します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-216">The tests will pass.</span></span>

## <a name="testing-the-release-version-of-the-library"></a><span data-ttu-id="60f8d-217">ライブラリのリリース バージョンのテスト</span><span class="sxs-lookup"><span data-stu-id="60f8d-217">Testing the Release version of the library</span></span>

<span data-ttu-id="60f8d-218">ここまで、ライブラリのデバッグ バージョンをテストしてきました。</span><span class="sxs-lookup"><span data-stu-id="60f8d-218">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="60f8d-219">すべてのテストが成功し、ライブラリを十分にテストしたので、さらにライブラリのリリース ビルドに対してテストを行います。</span><span class="sxs-lookup"><span data-stu-id="60f8d-219">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="60f8d-220">コンパイラの最適化などのさまざまな要因により、デバッグ ビルドとリリース ビルドとでは動作が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="60f8d-220">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="60f8d-221">リリース ビルドをテストするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="60f8d-221">To test the Release build:</span></span>

1. <span data-ttu-id="60f8d-222">Visual Studio のツールバーで、ビルド構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-222">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   ![Visual Studio ツール バー](./media/testing-library-with-visual-studio/toolbar.png)

1. <span data-ttu-id="60f8d-224">**ソリューション エクスプローラー**で **[StringLibrary]** プロジェクトを右クリックし、コンテキスト メニューの **[ビルド]** を選択し、ライブラリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="60f8d-224">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   ![StringLibrary のコンテキスト メニュー](./media/testing-library-with-visual-studio/buildlibrary.png)

1. <span data-ttu-id="60f8d-226">**[テスト]** > **[実行]** > **[すべてのテスト]** をメニュー バーから選択して単体テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-226">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="60f8d-227">テストが成功します。</span><span class="sxs-lookup"><span data-stu-id="60f8d-227">The tests pass.</span></span>

<span data-ttu-id="60f8d-228">これでライブラリのテストが完了したので、次の手順では呼び出し元が使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="60f8d-228">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="60f8d-229">1 つまたは複数のアプリケーションとバンドルするか、NuGet パッケージとして配布することができます。</span><span class="sxs-lookup"><span data-stu-id="60f8d-229">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="60f8d-230">詳細については、「[Consuming a .NET Standard Class Library ](./consuming-library-with-visual-studio.md)」 (.NET Standard クラス ライブラリを使用する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f8d-230">For more information, see [Consuming a .NET Standard Class Library](./consuming-library-with-visual-studio.md).</span></span>
