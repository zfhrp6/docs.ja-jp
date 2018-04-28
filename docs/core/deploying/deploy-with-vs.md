---
title: Visual Studio で .NET Core アプリを展開する
description: Visual Studio で .NET Core アプリを展開する方法を説明します。
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 238e43149eebb59ecbb25dfc3976f912e0ae8b01
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="deploying-net-core-apps-with-visual-studio"></a><span data-ttu-id="6953f-103">Visual Studio で .NET Core アプリを展開する</span><span class="sxs-lookup"><span data-stu-id="6953f-103">Deploying .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="6953f-104">.NET Core アプリケーションは、アプリケーション バイナリは含むが、対象のシステムに .NET Core があるかどうかに依存する*フレームワークに依存する展開*、またはアプリケーションと .NET Core バイナリの両方を含む*自己完結型の展開*のいずれかで展開できます。</span><span class="sxs-lookup"><span data-stu-id="6953f-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="6953f-105">.NET Core アプリケーションの展開の概要については、「[.NET Core アプリケーションの展開](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6953f-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="6953f-106">次のセクションでは、Microsoft Visual Studio を使用して、次のような展開を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6953f-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="6953f-107">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="6953f-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="6953f-108">サードパーティの依存関係を含む、フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="6953f-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="6953f-109">自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="6953f-109">Self-contained deployment</span></span>
- <span data-ttu-id="6953f-110">サードパーティの依存関係を含む、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="6953f-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="6953f-111">Visual Studio を使用して、.NET Core アプリケーションを開発する方法の詳細については、「[Windows における .NET Core の前提条件](../windows-prerequisites.md#prerequisites-with-visual-studio-2017)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6953f-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="6953f-112">フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="6953f-112">Framework-dependent deployment</span></span>

<span data-ttu-id="6953f-113">サードパーティの依存関係を含まない、フレームワークに依存する展開を展開するプロセスには、アプリのビルド、テスト、および発行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6953f-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="6953f-114">C# で記述された次の単純な例は、このプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="6953f-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="6953f-115">プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-115">Create the project.</span></span>

   <span data-ttu-id="6953f-116">**[ファイル]** > **[新規作成]** > **[プロジェクト]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="6953f-117">**[新しいプロジェクト]** ダイアログの **[インストール済み]** プロジェクトの種類ウィンドウで、**[.NET Core]** を選択し、中央のウィンドウで **[コンソール アプリケーション (.NET Core)]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-117">In the **New Project** dialog, select **.NET Core** in the **Installed** project types pane, and select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="6953f-118">**[名前]** テキスト ボックスに、"FDD" などのプロジェクト名を入力します。</span><span class="sxs-lookup"><span data-stu-id="6953f-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="6953f-119">**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="6953f-120">アプリケーションのソース コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6953f-120">Add the application's source code.</span></span>

   <span data-ttu-id="6953f-121">エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6953f-121">Open the *Program.cs* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="6953f-122">テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="6953f-123">正規表現 `\w+` を使用して、入力テキストの単語を分離します。</span><span class="sxs-lookup"><span data-stu-id="6953f-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="6953f-124">アプリのデバッグ ビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="6953f-125">**[ビルド]** > **[ソリューションのビルド]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="6953f-126">**[デバッグ]** > **[デバッグ開始]** を選択して、アプリケーションのデバッグ ビルドをコンパイルして、実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="6953f-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="6953f-127">アプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="6953f-127">Deploy your app.</span></span>

   <span data-ttu-id="6953f-128">プログラムをデバッグしてテストしたら、アプリと共に配置するファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="6953f-129">Visual Studio から発行するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6953f-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="6953f-130">アプリの (デバッグではなく) リリース バージョンを構築するために、ツールバーでソリューションの構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="6953f-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="6953f-131">**ソリューション エクスプローラー**で (ソリューションではなく) プロジェクトを右クリックし、**[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-131">Right-click on the project (not the solution) in **Solution Explorer**, and select **Publish**.</span></span>

      1. <span data-ttu-id="6953f-132">**[発行]** タブで **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="6953f-133">Visual Studio が、アプリケーションを構成するファイルをローカル ファイル システムに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6953f-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="6953f-134">これで **[発行]** タブには、**[FolderProfile]** という 1 つのプロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="6953f-135">プロファイルの構成設定が、タブの **[概要]** セクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="6953f-136">作成されたファイルは、プロジェクトの *.\bin\release* サブディレクトリのサブディレクトリ内にある、`PublishOutput` という名前のディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-136">The resulting files are placed in a directory named `PublishOutput` that is in a subdirectory of your project's *.\bin\release* subdirectory.</span></span>

<span data-ttu-id="6953f-137">アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="6953f-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="6953f-138">このファイルは、主に例外のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6953f-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="6953f-139">これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。</span><span class="sxs-lookup"><span data-stu-id="6953f-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="6953f-140">ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6953f-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="6953f-141">アプリケーション ファイルの完全なセットは、任意の方法で展開できます。</span><span class="sxs-lookup"><span data-stu-id="6953f-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="6953f-142">たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="6953f-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="6953f-143">インストールしたら、ユーザーはアプリケーションを、`dotnet` コマンドを使用し、`dotnet fdd.dll` などのアプリケーションのファイル名を提供して実行できます。</span><span class="sxs-lookup"><span data-stu-id="6953f-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="6953f-144">また、アプリケーション インストールの一環として、インストーラーはアプリケーション バイナリに加えて、共有フレームワーク インストーラーをバンドルするか、または前提条件として共有フレームワークがあるか確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6953f-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="6953f-145">共有フレームワークのインストールは、コンピューター全体が対象なので、管理者/ルート アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="6953f-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="6953f-146">サードパーティの依存関係を含む、フレームワークに依存する展開</span><span class="sxs-lookup"><span data-stu-id="6953f-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="6953f-147">1 つ以上のサードパーティの依存関係を備えたフレームワークに依存する展開を展開するには、すべての依存関係をプロジェクトに使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6953f-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="6953f-148">アプリをビルドする前に、次の追加手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="6953f-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="6953f-149">**NuGet パッケージ マネージャー**を使用し、プロジェクトに NuGet パッケージへの参照を追加します。このとき、パッケージがシステムにまだない場合はそれをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6953f-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="6953f-150">パッケージ マネージャーを開くには、**[ツール]** > **[NuGet パッケージ マネージャー]** > **[ソリューションの NuGet パッケージの管理]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="6953f-151">`Newtonsoft.Json` がシステムにインストールされていることを確認します。されていない場合はインストールします。</span><span class="sxs-lookup"><span data-stu-id="6953f-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="6953f-152">**[インストール済み]** タブに、システムにインストールされた NuGet パッケージの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="6953f-153">`Newtonsoft.Json` がそこにない場合、**[参照]** タブを選択し、検索ボックスに "Newtonsoft.Json" と入力します。</span><span class="sxs-lookup"><span data-stu-id="6953f-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="6953f-154">`Newtonsoft.Json` を選択し、右側のウィンドウでプロジェクトを選択してから、**[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="6953f-155">`Newtonsoft.Json` が既にシステムにインストールされている場合、**[ソリューション パッケージの管理]** タブの右のウィンドウから選択し、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="6953f-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of hte **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="6953f-156">サードパーティの依存関係を含む、フレームワークに依存する展開は、サードパーティの依存関係と同じ移植性を持つことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6953f-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="6953f-157">たとえば、サードパーティ ライブラリが macOS のみをサポートする場合、そのアプリを Windows システムに移植することはできません。</span><span class="sxs-lookup"><span data-stu-id="6953f-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="6953f-158">この状況は、サードパーティの依存関係自体がネイティブ コードに依存する場合に生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6953f-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="6953f-159">このよい例は、[libuv](https://github.com/libuv/libuv) に対してネイティブの依存関係が必要な [Kestrel サーバー](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)です。</span><span class="sxs-lookup"><span data-stu-id="6953f-159">A good example of this is [Kestrel server](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="6953f-160">このようなサードパーティの依存関係を含むアプリケーションに対して FDD が作成されると、発行された出力には、ネイティブの依存関係がサポートする (そして、その NuGet パッケージ内に存在する) 各[ランタイム識別子 (RID)](../rid-catalog.md) のフォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6953f-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="6953f-161">サードパーティの依存関係を含まない、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="6953f-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="6953f-162">サードパーティの依存関係を含まない自己完結型の展開を展開するプロセスには、プロジェクトの作成、*csproj*ファイルの変更、アプリのビルド、テスト、および発行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6953f-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="6953f-163">C# で記述された次の単純な例は、このプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="6953f-163">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="6953f-164">プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-164">Create the project.</span></span>

   <span data-ttu-id="6953f-165">**[ファイル]** > **[新規作成]** > **[プロジェクト]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-165">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="6953f-166">**[新しいプロジェクトの追加]** ダイアログの **[インストール済み]** プロジェクトの種類ウィンドウで、**[.NET Core]** を選択し、中央のウィンドウで **[コンソール アプリケーション (.NET Core)]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-166">In the **Add New Project** dialog, select **.NET Core** in the **Installed** project types pane, and select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="6953f-167">**[名前]** テキスト ボックスに、"SCD" などのプロジェクト名を入力し、**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-167">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="6953f-168">アプリケーションのソース コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6953f-168">Add the application's source code.</span></span>

   <span data-ttu-id="6953f-169">エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6953f-169">Open the *Program.cs* file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="6953f-170">テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-170">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="6953f-171">正規表現 `\w+` を使用して、入力テキストの単語を分離します。</span><span class="sxs-lookup"><span data-stu-id="6953f-171">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="6953f-172">アプリの対象プラットフォームを定義します。</span><span class="sxs-lookup"><span data-stu-id="6953f-172">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="6953f-173">**ソリューション エクスプローラー**で (ソリューションではなく) プロジェクトを右クリックし、**[編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-173">Right-click on your project (not the solution) In **Solution Explorer**, and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="6953f-174">*csproj* ファイルの `<PropertyGroup>` セクションに、アプリの対象のプラットフォームを定義する `<RuntimeIdentifiers>` タグを作成し、対象とするプラットフォームごとにランタイム識別子 (RID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="6953f-174">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="6953f-175">なお、RID の分離にはセミコロンを追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6953f-175">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="6953f-176">ランタイム識別子の一覧については、「[Runtime IDentifier catalog](../rid-catalog.md)」 (ランタイム識別子のカタログ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6953f-176">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="6953f-177">たとえば、次の例は、アプリが 64 ビット Windows 10 オペレーティング システムおよび 64 ビット OS X バージョン 10.11 オペレーティング システムで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="6953f-177">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```
   <span data-ttu-id="6953f-178">なお、`<RuntimeIdentifiers>` 要素は、*csproj* ファイルの任意の `<PropertyGroup>` に入れることが可能です。</span><span class="sxs-lookup"><span data-stu-id="6953f-178">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="6953f-179">*csproj* ファイルの完全なサンプルは、このセクションの後の部分で示しています。</span><span class="sxs-lookup"><span data-stu-id="6953f-179">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="6953f-180">アプリのデバッグ ビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-180">Create a Debug build of your app.</span></span>

   <span data-ttu-id="6953f-181">**[ビルド]** > **[ソリューションのビルド]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-181">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="6953f-182">**[デバッグ]** > **[デバッグ開始]** を選択して、アプリケーションのデバッグ ビルドをコンパイルして、実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="6953f-182">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="6953f-183">アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="6953f-183">Publish your app.</span></span>

   <span data-ttu-id="6953f-184">プログラムをデバッグしてテストしたら、アプリと共に展開するファイルをアプリの対象のプラットフォームごとに作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-184">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="6953f-185">Visual Studio でアプリを発行するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6953f-185">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="6953f-186">アプリの (デバッグではなく) リリース バージョンを構築するために、ツールバーでソリューションの構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="6953f-186">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="6953f-187">**ソリューション エクスプローラー**で (ソリューションではなく) プロジェクトを右クリックし、**[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-187">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span> 

      1. <span data-ttu-id="6953f-188">**[発行]** タブで **[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-188">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="6953f-189">Visual Studio が、アプリケーションを構成するファイルをローカル ファイル システムに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6953f-189">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="6953f-190">これで **[発行]** タブには、**[FolderProfile]** という 1 つのプロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-190">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="6953f-191">プロファイルの構成設定が、タブの **[概要]** セクションに表示されます。**[Target Runtime]** \(ターゲット ランタイム\) では、発行されたランタイムを識別し、**[対象の場所]** は自己完結型の展開が書き込まれた場所を識別します。</span><span class="sxs-lookup"><span data-stu-id="6953f-191">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="6953f-192">Visual Studio は、発行されたすべてのファイルを、既定で 1 つのディレクトリに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="6953f-192">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="6953f-193">ターゲット ランタイムごとに別のプロファイルを作成し、発行したファイルはプラットフォームごとのディレクトリに配置すると便利なのでお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6953f-193">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="6953f-194">これを行う場合、対象のプラットフォームごとに別の発行プロファイルも作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-194">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="6953f-195">ここでは、次の手順でプラットフォームごとにアプリケーションを再構築します。</span><span class="sxs-lookup"><span data-stu-id="6953f-195">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="6953f-196">**[発行]** ダイアログで、**[新しいプロファイルの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-196">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="6953f-197">**[Pick a publish target]** \(発行する対象の選択)\ ダイアログで **[Choose a folder]** \(フォルダーを選択)\ の場所を *bin\Release\PublishOutput\win10-x64* に変更します。</span><span class="sxs-lookup"><span data-stu-id="6953f-197">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="6953f-198">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-198">Select **OK**.</span></span>

         1. <span data-ttu-id="6953f-199">新しいプロファイル (**FolderProfile1**) をプロファイルの一覧から選択し、**[Target Runtime]** \(ターゲット ランタイム\) が `win10-x64` であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6953f-199">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="6953f-200">違う場合は、**[設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-200">If it isn't, select **Settings**.</span></span> <span data-ttu-id="6953f-201">**[プロファイルの設定]** ダイアログで、**[Target Runtime]** \(ターゲット ランタイム\) を `win10-x64` に変更して、**[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-201">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="6953f-202">それ以外の場合、**[キャンセル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-202">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="6953f-203">64 ビットの Windows 10 プラットフォーム用にアプリを発行するために、**[発行]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-203">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="6953f-204">前の手順を繰り返して、`osx.10.11-x64` プラットフォームのプロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6953f-204">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="6953f-205">**[対象の場所]** が *bin\Release\PublishOutput\osx.10.11-x64* で、**[Target Runtime]** \(ターゲット ランタイム\) は [`osx.10.11-x64`] です。</span><span class="sxs-lookup"><span data-stu-id="6953f-205">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="6953f-206">Visual Studio がこのプロファイルに割り当てる名前は、**FolderProfile2** です。</span><span class="sxs-lookup"><span data-stu-id="6953f-206">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="6953f-207">それぞれの対象の場所には、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6953f-207">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="6953f-208">アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。</span><span class="sxs-lookup"><span data-stu-id="6953f-208">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="6953f-209">このファイルは、主に例外のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6953f-209">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="6953f-210">これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。</span><span class="sxs-lookup"><span data-stu-id="6953f-210">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="6953f-211">ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6953f-211">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="6953f-212">発行したファイルは、任意の方法で展開できます。</span><span class="sxs-lookup"><span data-stu-id="6953f-212">Deploy the published files in any way you like.</span></span> <span data-ttu-id="6953f-213">たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="6953f-213">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="6953f-214">このプロジェクトの完全な *csproj* ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6953f-214">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="6953f-215">サードパーティの依存関係を含む、自己完結型の展開</span><span class="sxs-lookup"><span data-stu-id="6953f-215">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="6953f-216">1 つまたは複数のサードパーティの依存関係を含む自己完結型の展開を展開するプロセスには、依存関係の追加が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6953f-216">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="6953f-217">アプリをビルドする前に、次の追加手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="6953f-217">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="6953f-218">**NuGet パッケージ マネージャー**を使用し、プロジェクトに NuGet パッケージへの参照を追加します。このとき、パッケージがシステムにまだない場合はそれをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6953f-218">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="6953f-219">パッケージ マネージャーを開くには、**[ツール]** > **[NuGet パッケージ マネージャー]** > **[ソリューションの NuGet パッケージの管理]** を順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-219">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="6953f-220">`Newtonsoft.Json` がシステムにインストールされていることを確認します。されていない場合はインストールします。</span><span class="sxs-lookup"><span data-stu-id="6953f-220">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="6953f-221">**[インストール済み]** タブに、システムにインストールされた NuGet パッケージの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6953f-221">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="6953f-222">`Newtonsoft.Json` がそこにない場合、**[参照]** タブを選択し、検索ボックスに "Newtonsoft.Json" と入力します。</span><span class="sxs-lookup"><span data-stu-id="6953f-222">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="6953f-223">`Newtonsoft.Json` を選択し、右側のウィンドウでプロジェクトを選択してから、**[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6953f-223">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="6953f-224">`Newtonsoft.Json` が既にシステムにインストールされている場合、**[ソリューション パッケージの管理]** タブの右のウィンドウからプロジェクトを選択し、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="6953f-224">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="6953f-225">このプロジェクトの完全な *csproj* ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6953f-225">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="6953f-226">アプリケーションを展開すると、アプリで使用されるすべてのサードパーティの依存関係も、アプリケーション ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="6953f-226">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="6953f-227">アプリが実行されているシステムには、サードパーティ ライブラリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="6953f-227">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="6953f-228">サードパーティ ライブラリを含む自己完結型の展開は、そのライブラリでサポートされるプラットフォームにのみ展開できます。</span><span class="sxs-lookup"><span data-stu-id="6953f-228">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="6953f-229">これは、フレームワークに依存する展開にサード パーティの依存関係とネイティブの依存関係があり、ネイティブの依存関係は前にインストールしていた場合を除き、対象のプラットフォームにない場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="6953f-229">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

# <a name="see-also"></a><span data-ttu-id="6953f-230">関連項目</span><span class="sxs-lookup"><span data-stu-id="6953f-230">See also</span></span>
<span data-ttu-id="6953f-231">[.NET Core アプリケーションの展開](index.md) </span><span class="sxs-lookup"><span data-stu-id="6953f-231">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="6953f-232">.NET Core のランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="6953f-232">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   
