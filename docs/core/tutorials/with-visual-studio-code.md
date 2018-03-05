---
title: "C# および Visual Studio Code の使用を開始する - C# ガイド"
description: "Visual Studio Code を使用した、C# で初めての .NET Core アプリケーションを作成してデバッグする方法について説明します。"
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: 0c37040220bb7f38cdd75176bb9ed2a2199b7096
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2018
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="74098-103">C# および Visual Studio Code の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="74098-103">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="74098-104">.NET Core は、Windows、Linux および macOS で実行されるアプリケーションを作成するための、高速でモジュール型のプラットフォームを提供します。</span><span class="sxs-lookup"><span data-stu-id="74098-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="74098-105">Visual Studio Code を C# 拡張機能とともに使用して、C# IntelliSense の完全サポート (スマート コード補完) とデバッグによる強力な編集機能をご活用ください。</span><span class="sxs-lookup"><span data-stu-id="74098-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74098-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="74098-106">Prerequisites</span></span>

1. <span data-ttu-id="74098-107">[Visual Studio Code](https://code.visualstudio.com/) のインストール。</span><span class="sxs-lookup"><span data-stu-id="74098-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="74098-108">[.NET Core SDK](https://www.microsoft.com/net/download/core) のインストール。</span><span class="sxs-lookup"><span data-stu-id="74098-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="74098-109">Visual Studio Code の [C# 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)のインストール。</span><span class="sxs-lookup"><span data-stu-id="74098-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="74098-110">Visual Studio Code に拡張機能をインストールする方法については、[VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74098-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="74098-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="74098-111">Hello World</span></span>

<span data-ttu-id="74098-112">.NET Core でシンプルな "Hello World" プログラムを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="74098-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="74098-113">プロジェクトを開く</span><span class="sxs-lookup"><span data-stu-id="74098-113">Open a project:</span></span>

    * <span data-ttu-id="74098-114">Visual Studio Code を開きます。</span><span class="sxs-lookup"><span data-stu-id="74098-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="74098-115">左側のメニューで [エクスプローラー] アイコンをクリックし、**[フォルダーを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74098-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="74098-116">メイン メニューから **[ファイル]**、**[フォルダーを開く]** の順に選択し、C# プロジェクトを保存するフォルダーを開き、**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="74098-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="74098-117">ここで、*Hello World* という名前のプロジェクトのフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="74098-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="74098-119">C# プロジェクトを初期化する</span><span class="sxs-lookup"><span data-stu-id="74098-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="74098-120">Visual Studio Code から統合ターミナルを開きます。メイン メニューで **[表示]**、**[統合端末]** の順に選択してください。</span><span class="sxs-lookup"><span data-stu-id="74098-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="74098-121">ターミナル ウィンドウで、`dotnet new console` と入力します。</span><span class="sxs-lookup"><span data-stu-id="74098-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="74098-122">このコマンドで、フォルダーに `HelloWorld.csproj` という名前の C# プロジェクト ファイルとともに、単純な "Hello World" プログラムが既に書き込まれた `Program.cs` ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="74098-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![dotnet new コマンド](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="74098-124">ビルド資産を解決する</span><span class="sxs-lookup"><span data-stu-id="74098-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="74098-125">**.NET Core 1.x** の場合、「`dotnet restore`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="74098-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="74098-126">`dotnet restore` を実行すると、プロジェクトのビルドに必要な .NET Core パッケージにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="74098-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![dotnet restore コマンド](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="74098-128">"Hello World" プログラムを実行する</span><span class="sxs-lookup"><span data-stu-id="74098-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="74098-129">「`dotnet run`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="74098-129">Type `dotnet run`.</span></span> 

      ![dotnet run コマンド](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="74098-131">[Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)、または [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) での詳細設定については、簡単なビデオ チュートリアルを見ることができます。</span><span class="sxs-lookup"><span data-stu-id="74098-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="74098-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="74098-132">Debug</span></span>

1. <span data-ttu-id="74098-133">*Program.cs* をクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="74098-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="74098-134">Visual Studio Code で初めて C# ファイルを開くと、[OmniSharp](http://www.omnisharp.net/) がエディターに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="74098-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Program.cs ファイルを開く](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="74098-136">Visual Studio Code で、アプリのビルドとデバッグに必要なアセットの追加を求められます。</span><span class="sxs-lookup"><span data-stu-id="74098-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="74098-137">**[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="74098-137">Select **Yes**.</span></span> 

    ![足りない資産の入力を求める](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="74098-139">デバッグ ビューを開くには、左側のメニューにある [デバッグ] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="74098-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![[デバッグ] タブを開く](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="74098-141">ウィンドウの上部で緑色の矢印を探します。</span><span class="sxs-lookup"><span data-stu-id="74098-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="74098-142">その横にあるドロップダウン リストで `.NET Core Launch (console)` が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="74098-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![.NET Core を選択する](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="74098-144">9 行目の横にある**エディター余白** (エディター内の行番号の左側の領域) をクリックして、プロジェクトにブレークポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="74098-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9.</span></span>

    ![ブレークポイントの設定](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="74098-146">デバッグを開始するには、<kbd>F5 キー</kbd>または緑色の矢印を選択します。</span><span class="sxs-lookup"><span data-stu-id="74098-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="74098-147">デバッガーは、前述の手順で設定したブレークポイントに達すると、プログラムの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="74098-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="74098-148">デバッグ中は左上のペインにローカル変数が表示され、デバッグ コンソールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="74098-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![実行およびデバッグ](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="74098-150">上部にある緑色の矢印を選択してデバッグを継続するか、上部にある赤色の四角形を選択して停止します。</span><span class="sxs-lookup"><span data-stu-id="74098-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="74098-151">Visual Studio Code で OmniSharp を使用した .NET Core のデバッグの詳細とトラブルシューティングのヒントについては、「[Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)」 (.NET Core デバッガーの設定に関する指示) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74098-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74098-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="74098-152">See also</span></span>
<span data-ttu-id="74098-153">[Visual Studio Code の設定](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="74098-153">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="74098-154">Visual Studio Code でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="74098-154">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
