---
title: Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築
description: Windows 上の Visual Studio 2017 で完全な .NET Core ソリューションを構築する方法を説明します。
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.openlocfilehash: 52b8781cdc29ac776123402c982353ef437ce74f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="8c762-103">Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="8c762-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="8c762-104">Visual Studio 2017 は、.NET Core アプリケーション開発用の機能をすべて備えた開発環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="8c762-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="8c762-105">このドキュメントでは、再利用可能なライブラリ、サードパーティ製ライブラリのテストと使用を含む、一般的な .NET Core ソリューションをビルドするために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c762-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="8c762-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8c762-106">Prerequisites</span></span>

<span data-ttu-id="8c762-107">[前提条件のページ](../windows-prerequisites.md)の指示に従って、環境を更新します。</span><span class="sxs-lookup"><span data-stu-id="8c762-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="8c762-108">.NET Core プロジェクトのみを使用するソリューション</span><span class="sxs-lookup"><span data-stu-id="8c762-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="8c762-109">ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="8c762-109">Writing the library</span></span>

1. <span data-ttu-id="8c762-110">Visual Studio で、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c762-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="8c762-111">**[新しいプロジェクト]** ダイアログで **[Visual C#]** ノードを展開し、**[.NET Standard]** ノードを選択して **[クラス ライブラリ (.NET Standard)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c762-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="8c762-112">プロジェクトの名前を "Library" に、ソリューションの名前を "Golden" に設定します。</span><span class="sxs-lookup"><span data-stu-id="8c762-112">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="8c762-113">**[ソリューションのディレクトリを作成]** はオンのままにします。</span><span class="sxs-lookup"><span data-stu-id="8c762-113">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="8c762-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c762-114">Click **OK**.</span></span>

3. <span data-ttu-id="8c762-115">ソリューション エクスプローラーで **[依存関係]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c762-115">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="8c762-116">**[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。**Newtonsoft.Json** を参照します。</span><span class="sxs-lookup"><span data-stu-id="8c762-116">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="8c762-117">**[インストール]** をクリックして、使用許諾契約に同意します。</span><span class="sxs-lookup"><span data-stu-id="8c762-117">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="8c762-118">これで、**[依存関係] の [NuGet]** にパッケージが表示され、自動的に復元されるようになります。</span><span class="sxs-lookup"><span data-stu-id="8c762-118">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="8c762-119">ファイルの名前を `Class1.cs` から `Thing.cs` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8c762-119">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="8c762-120">クラス名の変更をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="8c762-120">Accept the rename of the class.</span></span> <span data-ttu-id="8c762-121">メソッドの追加: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="8c762-121">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="8c762-122">**[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c762-122">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="8c762-123">ソリューションがエラーのない状態でビルドされます。</span><span class="sxs-lookup"><span data-stu-id="8c762-123">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="8c762-124">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="8c762-124">Writing the test project</span></span>

1. <span data-ttu-id="8c762-125">ソリューション エクスプローラーで、**[ソリューション]** ノードのコンテキスト メニューを開き、**[追加]**、**[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8c762-125">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="8c762-126">**[新しいプロジェクト]** ダイアログ ボックスにある **[Visual C#] の [.NET Core]** で、**[単体テスト プロジェクト (.NET Core)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c762-126">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="8c762-127">"TestLibrary" という名前を付けて [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c762-127">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="8c762-128">**TestLibrary** プロジェクトで、**[依存関係]** ノードのコンテキスト メニューを開き、**[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c762-128">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="8c762-129">**[プロジェクト]** をクリックし、ライブラリ プロジェクトを確認して [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c762-129">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="8c762-130">これで、テスト プロジェクトからライブラリに参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="8c762-130">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="8c762-131">`UnitTest1.cs` ファイルの名前を `LibraryTests.cs` に変更して、クラスの名前変更を承諾します。</span><span class="sxs-lookup"><span data-stu-id="8c762-131">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="8c762-132">ファイルの先頭に `using Library;` を追加し、`TestMethod1` メソッドを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8c762-132">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="8c762-133">ソリューションをビルドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="8c762-133">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="8c762-134">**[テスト]** メニューで、**[Windows]**、**[テスト エクスプローラー]** の順に選択し、テスト エクスプローラー ウィンドウをワークスペースに取り込みます。</span><span class="sxs-lookup"><span data-stu-id="8c762-134">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="8c762-135">数秒後に、`ThingGetsObjectValFromNumber` テストがテスト エクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c762-135">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="8c762-136">**[すべて実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c762-136">Choose **Run All**.</span></span>
   
   <span data-ttu-id="8c762-137">テストで問題がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c762-137">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="8c762-138">コンソール アプリの作成</span><span class="sxs-lookup"><span data-stu-id="8c762-138">Writing the console app</span></span>

1. <span data-ttu-id="8c762-139">ソリューション エクスプローラーで、ソリューションのコンテキスト メニューを開き、新しい**コンソール アプリケーション (.NET Core)** プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="8c762-139">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="8c762-140">それに "App" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="8c762-140">Name it "App".</span></span>

2. <span data-ttu-id="8c762-141">**App** プロジェクトで、**[依存関係]** ノードのコンテキスト メニューを開き、**[追加]**、**[参照]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8c762-141">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="8c762-142">**[参照マネージャー]** ダイアログ ボックスで、**[プロジェクト]**、**[ソリューション]** ノードの **[ライブラリ]** をオンにして、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c762-142">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="8c762-143">**App** ノードのコンテキスト メニューを開き、**[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c762-143">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="8c762-144">これで、F5 キーまたは Ctrl + F5 キーを押したときにコンソール アプリケーションが起動します。</span><span class="sxs-lookup"><span data-stu-id="8c762-144">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="8c762-145">`Program.cs` ファイルを開き、`using Library;` ディレクティブをファイルの先頭に追加して、`Console.WriteLine($"The answer is {new Thing().Get(42)}.");` を `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="8c762-145">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="8c762-146">追加した行の後にブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="8c762-146">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="8c762-147">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c762-147">Press F5 to run the application..</span></span>

   <span data-ttu-id="8c762-148">アプリケーションがエラーのない状態でビルドされ、ブレークポイントがヒットします。</span><span class="sxs-lookup"><span data-stu-id="8c762-148">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="8c762-149">また、アプリケーションが "The answer is 42." と出力することを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c762-149">You should also be able to check that the application output "The answer is 42.".</span></span>
