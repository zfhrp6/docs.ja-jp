---
title: "Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築"
description: "Windows 上の Visual Studio 2017 で完全な .NET Core ソリューションを構築する方法を説明します。"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ba7e082c-a7c8-431e-a342-f67734b660f6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6b164198f5fbbae5ebc6164fc281dd7de8172b70
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="ef4af-104">Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="ef4af-104">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="ef4af-105">Visual Studio 2017 は、.NET Core アプリケーション開発用の機能をすべて備えた開発環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-105">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="ef4af-106">このドキュメントでは、再利用可能なライブラリ、サードパーティ製ライブラリのテストと使用を含む、一般的な .NET Core ソリューションをビルドするために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-106">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="ef4af-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="ef4af-107">Prerequisites</span></span>

<span data-ttu-id="ef4af-108">[前提条件のページ](../windows-prerequisites.md)の指示に従って、環境を更新します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-108">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="ef4af-109">.NET Core プロジェクトのみを使用するソリューション</span><span class="sxs-lookup"><span data-stu-id="ef4af-109">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="ef4af-110">ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="ef4af-110">Writing the library</span></span>

1. <span data-ttu-id="ef4af-111">Visual Studio で、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-111">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="ef4af-112">**[新しいプロジェクト]** ダイアログで **[Visual C#]** ノードを展開し、**[.NET Core]** ノードを選択して **[クラス ライブラリ (.NET Standard)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-112">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Core** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="ef4af-113">プロジェクトの名前を "Library" に、ソリューションの名前を "Golden" に設定します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="ef4af-114">**[ソリューションのディレクトリを作成]** はオンのままにします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="ef4af-115">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-115">Click **OK**.</span></span>

3. <span data-ttu-id="ef4af-116">ソリューション エクスプローラーで **[依存関係]** ノードのコンテキスト メニューを開き、**[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="ef4af-117">**[パッケージ ソース]** として "nuget.org" を選択し、**[参照]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab.</span></span> <span data-ttu-id="ef4af-118">**Newtonsoft.Json** を参照します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-118">Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="ef4af-119">**[インストール]** をクリックして、使用許諾契約に同意します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-119">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="ef4af-120">これで、**[依存関係] の [NuGet]** にパッケージが表示され、自動的に復元されるようになります。</span><span class="sxs-lookup"><span data-stu-id="ef4af-120">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="ef4af-121">ファイルの名前を `Class1.cs` から `Thing.cs` に変更します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-121">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="ef4af-122">クラス名の変更をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-122">Accept the rename of the class.</span></span> <span data-ttu-id="ef4af-123">メソッドの追加: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="ef4af-123">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="ef4af-124">**[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-124">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="ef4af-125">ソリューションがエラーのない状態でビルドされます。</span><span class="sxs-lookup"><span data-stu-id="ef4af-125">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="ef4af-126">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="ef4af-126">Writing the test project</span></span>

1. <span data-ttu-id="ef4af-127">ソリューション エクスプローラーで、**[ソリューション]** ノードのコンテキスト メニューを開き、**[追加]**、**[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-127">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="ef4af-128">**[新しいプロジェクト]** ダイアログ ボックスにある **[Visual C#] の [.NET Core]** で、**[単体テスト プロジェクト (.NET Core)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-128">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="ef4af-129">"TestLibrary" という名前を付けて [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-129">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="ef4af-130">**TestLibrary** プロジェクトで、**[依存関係]** ノードのコンテキスト メニューを開き、**[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-130">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="ef4af-131">**[プロジェクト]** をクリックし、ライブラリ プロジェクトを確認して [OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-131">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="ef4af-132">これで、テスト プロジェクトからライブラリに参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ef4af-132">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="ef4af-133">`UnitTest1.cs` ファイルの名前を `LibraryTests.cs` に変更して、クラスの名前変更を承諾します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-133">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="ef4af-134">ファイルの先頭に `using Library;` を追加し、`TestMethod1` メソッドを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ef4af-134">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="ef4af-135">ソリューションをビルドできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ef4af-135">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="ef4af-136">**[テスト]** メニューで、**[Windows]**、**[テスト エクスプローラー]** の順に選択し、テスト エクスプローラー ウィンドウをワークスペースに取り込みます。</span><span class="sxs-lookup"><span data-stu-id="ef4af-136">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="ef4af-137">数秒後に、`ThingGetsObjectValFromNumber` テストがテスト エクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ef4af-137">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="ef4af-138">**[すべて実行]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-138">Choose **Run All**.</span></span>
   
   <span data-ttu-id="ef4af-139">テストで問題がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-139">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="ef4af-140">コンソール アプリの作成</span><span class="sxs-lookup"><span data-stu-id="ef4af-140">Writing the console app</span></span>

1. <span data-ttu-id="ef4af-141">ソリューション エクスプローラーで、ソリューションのコンテキスト メニューを開き、新しい**コンソール アプリケーション (.NET Core)** プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-141">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="ef4af-142">それに "App" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="ef4af-142">Name it "App".</span></span>

2. <span data-ttu-id="ef4af-143">**App** プロジェクトで、**[依存関係]** ノードのコンテキスト メニューを開き、**[追加]**、**[参照]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-143">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="ef4af-144">**[参照マネージャー]** ダイアログ ボックスで、**[プロジェクト]**、**[ソリューション]** ノードの **[ライブラリ]** をオンにして、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-144">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="ef4af-145">**App** ノードのコンテキスト メニューを開き、**[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-145">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="ef4af-146">これで、F5 キーまたは Ctrl + F5 キーを押したときにコンソール アプリケーションが起動します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-146">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="ef4af-147">`Program.cs` ファイルを開き、`using Library;` ディレクティブをファイルの先頭に追加して、`Console.WriteLine($"The answer is {new Thing().Get(42)}.");` を `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-147">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="ef4af-148">追加した行の後にブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-148">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="ef4af-149">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-149">Press F5 to run the application..</span></span>

   <span data-ttu-id="ef4af-150">アプリケーションがエラーのない状態でビルドされ、ブレークポイントがヒットします。</span><span class="sxs-lookup"><span data-stu-id="ef4af-150">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="ef4af-151">また、アプリケーションが "The answer is 42." と出力することを確認します。</span><span class="sxs-lookup"><span data-stu-id="ef4af-151">You should also be able to check that the application output "The answer is 42.".</span></span>

