---
title: "Visual Studio 2017 での Hello World アプリケーションの発行"
description: "発行では、アプリケーションを実行するために必要なファイルのセットを作成します。"
keywords: ".NET, .NET Core, コンソール アプリケーション, 発行, 配置"
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.workload: dotnetcore
ms.openlocfilehash: 40479d85f9b31fcc80e3d12537126941878a09a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="7898e-104">Visual Studio 2017 での Hello World アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="7898e-104">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="7898e-105">「[Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築](with-visual-studio.md)」または「[Visual Studio 2017 での .NET Core を使用した Visual Basic Hello World アプリケーションの構築](vb-with-visual-studio.md)」では、Hello World コンソール アプリケーションを構築しました。</span><span class="sxs-lookup"><span data-stu-id="7898e-105">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="7898e-106">「[Visual Studio 2017 での C# Hello World アプリケーションのデバッグ](debugging-with-visual-studio.md)」では、Visual Studio デバッガーを使ってアプリケーションをテストしました。</span><span class="sxs-lookup"><span data-stu-id="7898e-106">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="7898e-107">正しく動作することが確認できたので、他のユーザーが使用できるように発行することができます。</span><span class="sxs-lookup"><span data-stu-id="7898e-107">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="7898e-108">発行では、アプリケーションを実行するために必要なファイルのセットが作成されます。これらのファイルは、対象コンピューターにコピーすることで配置できます。</span><span class="sxs-lookup"><span data-stu-id="7898e-108">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="7898e-109">アプリケーションを発行および実行するには</span><span class="sxs-lookup"><span data-stu-id="7898e-109">To publish and run your application:</span></span> 

1. <span data-ttu-id="7898e-110">Visual Studio がアプリケーションのリリース バージョンをビルドしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7898e-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="7898e-111">必要に応じて、ツール バーのビルド構成の設定を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="7898e-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio ツール バー](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="7898e-113">**HelloWorld** プロジェクト (HelloWorld ソリューションではなく) を右クリックし、メニューから **[発行]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="7898e-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="7898e-114">Visual Studio のメイン メニューの **[ビルド]** から **[HelloWorld を発行]** を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="7898e-114">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio ツール バー](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio ツール バー](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="7898e-117">コンソール ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="7898e-117">Open a console window.</span></span> <span data-ttu-id="7898e-118">たとえば、Windows タスク バーの **[検索するテキストをここに入力]** テキスト ボックスに「`Command Prompt`」 (または省略して「`cmd`」) と入力し、**コマンド プロンプト** デスクトップ アプリを選ぶか、コマンド プロンプトが検索結果で選択されている場合は Enter キーを押して、コンソール ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="7898e-118">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="7898e-119">アプリケーションのプロジェクト ディレクトリの `bin\release\PublishOutput` サブディレクトリで、発行されたアプリケーションに移動します。</span><span class="sxs-lookup"><span data-stu-id="7898e-119">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="7898e-120">次の図に示すように、発行された出力には次の 4 つのファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7898e-120">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="7898e-121">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="7898e-121">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="7898e-122">アプリケーションのランタイム依存関係ファイル。</span><span class="sxs-lookup"><span data-stu-id="7898e-122">The application's runtime dependencies file.</span></span> <span data-ttu-id="7898e-123">アプリケーションの実行に必要な .NET Core コンポーネントとライブラリ (アプリケーションが含まれる動的リンク ライブラリを含む) を定義します。</span><span class="sxs-lookup"><span data-stu-id="7898e-123">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="7898e-124">詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7898e-124">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="7898e-125">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="7898e-125">*HelloWorld.dll*</span></span>

         <span data-ttu-id="7898e-126">アプリケーションが含まれるファイル。</span><span class="sxs-lookup"><span data-stu-id="7898e-126">The file that contains your application.</span></span> <span data-ttu-id="7898e-127">動的リンク ライブラリであり、コンソール ウィンドウに `dotnet HelloWorld.dll` コマンドを入力することで実行できます。</span><span class="sxs-lookup"><span data-stu-id="7898e-127">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="7898e-128">*HelloWorld.pdb* (配置は省略可能)</span><span class="sxs-lookup"><span data-stu-id="7898e-128">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="7898e-129">デバッグ シンボルが含まれるファイル。</span><span class="sxs-lookup"><span data-stu-id="7898e-129">A file that contains debug symbols.</span></span> <span data-ttu-id="7898e-130">このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7898e-130">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="7898e-131">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="7898e-131">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="7898e-132">アプリケーションのランタイム構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="7898e-132">The application's runtime configuration file.</span></span> <span data-ttu-id="7898e-133">ビルドされたアプリケーションが実行時に基盤とする .NET Core のバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="7898e-133">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="7898e-134">詳細については、「[ランタイム構成ファイル](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7898e-134">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![発行されたファイルが表示されているコンソール ウィンドウ](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="7898e-136">発行プロセスでは、フレームワークに依存する配置が作成されます。これは、.NET Core がシステムにインストールされていれば、.NET Core によってサポートされる任意のプラットフォームで発行されたアプリケーションが動作する配置の種類です。</span><span class="sxs-lookup"><span data-stu-id="7898e-136">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="7898e-137">ユーザーはコンソール ウィンドウから `dotnet HelloWorld.dll` コマンドを発行することによって、アプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7898e-137">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="7898e-138">.NET Core アプリケーションの発行と展開の詳細については、「[.NET Core アプリケーション展開](../../core/deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7898e-138">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
