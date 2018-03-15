---
title: "Visual Studio のコードで f# の概要します。"
description: "Visual Studio Code と Ionide プラグイン suite で f# を使用する方法を説明します。"
keywords: "visual f#、f#、関数型プログラミングでは、.NET、Visual Studio のコードでの vscode Ionide"
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: c452e791b27bc3f32e137a515011d953005344c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="3fad4-104">Visual Studio のコードで f# の概要します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-104">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="3fad4-105">F# で記述できます[Visual Studio Code](https://code.visualstudio.com)で、 [Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)、IntelliSense および基本的なコードの優れたクロスプラット フォームで軽量な IDE (Integrade 開発環境) のエクスペリエンスを取得するにはリファクタリングします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-105">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE (Integrade Development Enivronment) experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="3fad4-106">参照してください[Ionide.io](http://ionide.io)をプラグイン スイートに関する詳しい情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fad4-106">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3fad4-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3fad4-107">Prerequisites</span></span>

<span data-ttu-id="3fad4-108">必要があります[git がインストールされている](https://git-scm.com/download)するには、パスで使用できると Ionide でプロジェクト テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-108">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="3fad4-109">」と入力して正しくインストールされていることを確認することができます`git --version`キーを押して、コマンド プロンプトで**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-109">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="3fad4-110">macOS</span><span class="sxs-lookup"><span data-stu-id="3fad4-110">macOS</span></span>](#tab/macos)

<span data-ttu-id="3fad4-111">Ionide を使用して[モノラル](http://www.mono-project.com)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-111">Ionide uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="3fad4-112">Macos モノラルをインストールする最も簡単な方法は、Homebrew を介してです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-112">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="3fad4-113">単に、端末に、次を入力します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-113">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="3fad4-114">またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-114">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="3fad4-115">Linux</span><span class="sxs-lookup"><span data-stu-id="3fad4-115">Linux</span></span>](#tab/linux)

<span data-ttu-id="3fad4-116">Ionide Linux では、使用も[モノラル](https://www.mono-project.com)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-116">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="3fad4-117">Debian、Ubuntu またはの場合は、次の操作を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-117">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="3fad4-118">またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-118">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="3fad4-119">Windows</span><span class="sxs-lookup"><span data-stu-id="3fad4-119">Windows</span></span>](#tab/windows)

<span data-ttu-id="3fad4-120">Windows の場合は、する必要があります[F# でサポートを含む Visual Studio をインストール](get-started-visual-studio.md#installing-f)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-120">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="3fad4-121">これにより、書き込み、コンパイル、および f# コードを実行するために必要なすべてのコンポーネントがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-121">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="3fad4-122">またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download/)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-122">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="3fad4-123">Visual Studio Code と Ionide プラグインのインストール</span><span class="sxs-lookup"><span data-stu-id="3fad4-123">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="3fad4-124">Visual Studio のコードからをインストールすることができます、 [code.visualstudio.com](https://code.visualstudio.com) web サイトです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-124">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span> <span data-ttu-id="3fad4-125">その後は、Ionide プラグインを検索する 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="3fad4-125">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="3fad4-126">コマンド パレット (Ctrl + Shift + P Windows では、⌘ + Shift + P macos、Ctrl + Shift + P Linux 上) を使用し、次に入力します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-126">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="3fad4-127">"Ionide"を検索して拡張機能 アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-127">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="3fad4-128">Visual Studio のコードで、f# のサポートに必要なだけプラグイン[Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-128">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="3fad4-129">ただし、インストールすることも[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)を取得し、[偽](https://fsharp.github.io/FAKE/)サポートと[Ionide パケットを作成](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)を取得する[パケットを作成](https://fsprojects.github.io/Paket/)をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-129">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="3fad4-130">偽のプロジェクトをビルドして、それぞれの依存関係を管理するその他 f# コミュニティ ツールは、パケットを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-130">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="3fad4-131">Ionide を初めてのプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-131">Creating your first project with Ionide</span></span>

<span data-ttu-id="3fad4-132">新しい f# プロジェクトを作成するには、(」と入力して何でも) の新しいフォルダーに Visual Studio のコードを開きます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-132">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="3fad4-133">次に、コマンド パレット (Ctrl + Shift + P Windows では、⌘ + Shift + P macos、Linux で Ctrl + Shift + P) を開き、次を入力します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-133">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="3fad4-134">これが電源に、 [FORGE](https://github.com/fsharp-editing/Forge)プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="3fad4-134">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="3fad4-135">次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-135">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="3fad4-136">上記が表示されない場合、は、コマンド パレットで、次のコマンドを実行してテンプレートを更新してみてください:`>F#: Refresh Project Templates`です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-136">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="3fad4-137">クリックして"f#::"新しいプロジェクトを選択して**Enter**をクリックすると、この手順。</span><span class="sxs-lookup"><span data-stu-id="3fad4-137">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="3fad4-138">これにより、特定の種類のプロジェクト テンプレートが選択されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-138">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="3fad4-139">ここでは、非常に多くのオプションなどが、 [FsLab](https://fslab.org)データ サイエンス用のテンプレートまたは[Suave](https://suave.io) Web プログラミング用のテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-139">There are quite a few options here, such as an [FsLab](https://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="3fad4-140">この記事では、`classlib`テンプレートのため強調表示して、ヒット**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-140">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="3fad4-141">次の手順が到達してしまいます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-141">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="3fad4-142">これにより、必要に応じて別のディレクトリにプロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-142">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="3fad4-143">空白のままに今のところです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-143">Leave it blank for now.</span></span>  <span data-ttu-id="3fad4-144">現在のディレクトリにプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-144">It will create the project in the current directory.</span></span>  <span data-ttu-id="3fad4-145">キーを押すと**Enter**、次の手順が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-145">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="3fad4-146">これにより、プロジェクトにできます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-146">This lets you name your project.</span></span>  <span data-ttu-id="3fad4-147">F# は[pascal](http://c2.com/cgi/wiki?PascalCase)プロジェクト名にします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-147">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="3fad4-148">この記事では`ClassLibraryDemo`名として。</span><span class="sxs-lookup"><span data-stu-id="3fad4-148">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="3fad4-149">プロジェクトの名前を入力するとヒット**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-149">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="3fad4-150">前の手順の手順を実行した場合は、次のように、左側にある Visual Studio コード ワークスペースを取得してください。</span><span class="sxs-lookup"><span data-stu-id="3fad4-150">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="3fad4-151">このテンプレートには、便利ですが見つかったら、いくつかの点が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-151">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="3fad4-152">F# プロジェクト自体には、下に、`ClassLibraryDemo`フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-152">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="3fad4-153">使用してパッケージを追加するための適切なディレクトリ構造[ `Paket`](https://fsprojects.github.io/Paket/)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-153">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="3fad4-154">クロス プラットフォーム ビルド スクリプトを[ `FAKE`](https://fsharp.github.io/FAKE/)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-154">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="3fad4-155">`paket.exe`実行可能ファイルのパッケージをフェッチして依存関係が解決することができます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-155">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="3fad4-156">A`.gitignore`ファイルのこのプロジェクトを Git ベースのソース管理に追加する場合。</span><span class="sxs-lookup"><span data-stu-id="3fad4-156">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="3fad4-157">コードの記述</span><span class="sxs-lookup"><span data-stu-id="3fad4-157">Writing some code</span></span>

<span data-ttu-id="3fad4-158">開く、 *ClassLibraryDemo*フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-158">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="3fad4-159">次のファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-159">You should see the following files:</span></span>

1. <span data-ttu-id="3fad4-160">`ClassLibraryDemo.fs`、f# 実装ファイル定義クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-160">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="3fad4-161">`CassLibraryDemo.fsproj`、、f# のプロジェクト ファイルをこのプロジェクトをビルドするために使用します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-161">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="3fad4-162">`Script.fsx`、f# スクリプト ファイルに、ソース ファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-162">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="3fad4-163">`paket.references`、パケットを作成ファイルをプロジェクトの依存関係を指定します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-163">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="3fad4-164">開いている`Script.fsx`の末尾に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-164">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="3fad4-165">この関数が単語の形式に変換[Pig ラテン](https://en.wikipedia.org/wiki/Pig_Latin)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-165">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="3fad4-166">次の手順では、f# 対話型 (FSI) を使用して評価します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-166">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="3fad4-167">(11 行の長さにする必要があります) 関数全体を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-167">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="3fad4-168">強調表示すると後の保持、 **alt キーを押し**キーを押し、ヒット**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-168">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="3fad4-169">次に、ポップアップ ウィンドウがわかります、次のように表示されるはず。</span><span class="sxs-lookup"><span data-stu-id="3fad4-169">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="3fad4-170">これは、3 つのことを行いました。</span><span class="sxs-lookup"><span data-stu-id="3fad4-170">This did three things:</span></span>

1. <span data-ttu-id="3fad4-171">FSI プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-171">It started the FSI process.</span></span>
2. <span data-ttu-id="3fad4-172">FSI のプロセスが細かく強調表示したコードを送信します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-172">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="3fad4-173">FSI プロセスには、経由で送信されたコードが評価されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-173">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="3fad4-174">経由で送信するため、[関数](../language-reference/functions/index.md)FSI をその関数を呼び出すようになりました。</span><span class="sxs-lookup"><span data-stu-id="3fad4-174">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="3fad4-175">対話型のウィンドウで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-175">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="3fad4-176">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-176">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="3fad4-177">ここで、最初の文字として母音で試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="3fad4-177">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="3fad4-178">次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-178">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="3fad4-179">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-179">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="3fad4-180">関数は、期待どおりに動作してが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-180">The function appears to be working as expected.</span></span>  <span data-ttu-id="3fad4-181">以上で、先ほど Visual Studio のコードで、1 つ目の f# 関数を記述し、FSI で評価。</span><span class="sxs-lookup"><span data-stu-id="3fad4-181">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="3fad4-182">FSI 内の行を終了したように可能性がありますが、`;;`です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-182">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="3fad4-183">FSI を使用すると、複数行を入力するためです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-183">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="3fad4-184">`;;`最後に FSI コードが終了したときを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-184">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="3fad4-185">コードの説明</span><span class="sxs-lookup"><span data-stu-id="3fad4-185">Explaining the code</span></span>

<span data-ttu-id="3fad4-186">コードが実際に何かわからない場合、詳細な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-186">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="3fad4-187">ご覧のとおり、`toPigLatin`の入力として単語を受け取り、その単語の Pig ラテン文字表現に変換する関数です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-187">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="3fad4-188">このルールは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-188">The rules for this are as follows:</span></span>

<span data-ttu-id="3fad4-189">単語の最初の文字で始まる場合、母音、単語の末尾に「お」を追加します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-189">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="3fad4-190">母音で始まらない場合、は、単語の末尾にその最初の文字を移動し、「常」を追加しています。</span><span class="sxs-lookup"><span data-stu-id="3fad4-190">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="3fad4-191">FSI では、次を認識することがあります。</span><span class="sxs-lookup"><span data-stu-id="3fad4-191">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="3fad4-192">示すこの`toPigLatin`取得関数は、`string`入力として (と呼ばれる`word`)、し、返します別`string`です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-192">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="3fad4-193">これと呼ばれますが、[関数の型のシグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)、f# コードを理解するためのキーは、f# の根本的な部分です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-193">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="3fad4-194">Visual Studio のコード内で、関数ポインターを合わせる場合するも明らかです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-194">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="3fad4-195">関数の本文には、2 つの異なる部分をわかります。</span><span class="sxs-lookup"><span data-stu-id="3fad4-195">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="3fad4-196">呼ばれる内部関数は、 `isVowel`、特定の文字を決定 (`c`) を介して提供されたパターンの 1 つと一致する場合にチェックして、母音は、[パターンに一致する](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="3fad4-196">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="3fad4-197">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)場合は、最初の文字は、入力文字列からの戻り値を構築、母音、どのチェックに基づいて場合は、最初の文字式であるか、母音。</span><span class="sxs-lookup"><span data-stu-id="3fad4-197">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="3fad4-198">フロー`toPigLatin`のため。</span><span class="sxs-lookup"><span data-stu-id="3fad4-198">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="3fad4-199">かどうか、入力の単語の最初の文字は母音を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3fad4-199">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="3fad4-200">である場合は、単語の末尾に「お」をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-200">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="3fad4-201">それ以外の場合、単語の末尾までその最初の文字を移動し、「常」を追加します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-201">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="3fad4-202">1 つの最後にこの方法に注意してください。 その他の多くの言語がとは異なり、関数から返される明示的な指示がないです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-202">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="3fad4-203">これは f# 式に基づくは、関数の本体の最後の式の戻り値です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-203">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="3fad4-204">`if..then..else`自体、式の本体では、`then`ブロックまたはの本文、`else`ブロックが入力された値によって返されます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-204">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="3fad4-205">クラスの実装ファイル、スクリプト コードを移動します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-205">Moving your script code into the implementation file</span></span>

<span data-ttu-id="3fad4-206">この記事の前のセクションには、f# コードの記述の一般的な最初の手順が示されている: 初期関数を作成し、FSI して対話的に実行します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-206">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="3fad4-207">これは、REPL が「読み取り評価印刷ループ」を意味、REPL 駆動型開発と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-207">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="3fad4-208">これは何かの操作が得られるまで機能をテストする優れた手段です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-208">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="3fad4-209">REPL 駆動型開発の次の手順では、f# 実装ファイルの作業中のコードを移動します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-209">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="3fad4-210">これで実行できるアセンブリの f# コンパイラでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-210">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="3fad4-211">最初に開く`ClassLibraryDemo.fs`です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-211">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="3fad4-212">一部のコードが既にされているがわかります。</span><span class="sxs-lookup"><span data-stu-id="3fad4-212">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="3fad4-213">進めて、クラス定義を削除しがのままにすることを確認、 [ `namespace` ](../language-reference/namespaces.md)上部にある宣言します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-213">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="3fad4-214">次に、新しい作成[ `module` ](../language-reference/modules.md)と呼ばれる`PigLatin`をコピーし、`toPigLatin`ように、関数。</span><span class="sxs-lookup"><span data-stu-id="3fad4-214">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="3fad4-215">これは、多くの方法の場合も、コードを c# または Visual Basic プロジェクトから呼び出す関数は f# コードで、一般的な方法を整理することができます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-215">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="3fad4-216">次に、開く、 `Script.fsx` 、ファイルに追加され、全体を削除`toPigLatin`機能しますが、ファイルに次の 2 行を保持することを確認します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-216">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="3fad4-217">FSI を読み込むスクリプトの最初の行が必要な`ClassLibraryDemo.fs`します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-217">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="3fad4-218">2 番目の行が使いやすい: 省略された場合、オプションですが、入力する必要があります`open ClassLibraryDemo`FSI ウィンドウを表示する場合に、`ToPigLatin`モジュールをスコープにします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-218">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="3fad4-219">次に、FSI ウィンドウで、関数を使って呼び出し、`PigLatin`前に定義するモジュール。</span><span class="sxs-lookup"><span data-stu-id="3fad4-219">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="3fad4-220">正常に完了</span><span class="sxs-lookup"><span data-stu-id="3fad4-220">Success!</span></span>  <span data-ttu-id="3fad4-221">前に、同じ結果を取得することは、f# 実装ファイルから読み込まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3fad4-221">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="3fad4-222">ここでの主な違いは、f# ソース ファイルが FSI 内だけでなく、どこにでも実行できるアセンブリにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="3fad4-222">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="3fad4-223">まとめ</span><span class="sxs-lookup"><span data-stu-id="3fad4-223">Summary</span></span>

<span data-ttu-id="3fad4-224">この記事では次の内容を学習しました。</span><span class="sxs-lookup"><span data-stu-id="3fad4-224">In this article, you've learned:</span></span>

1. <span data-ttu-id="3fad4-225">Ionide で Visual Studio のコードを設定する方法です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-225">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="3fad4-226">Ionide で初めての f# プロジェクトを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="3fad4-226">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="3fad4-227">F# スクリプトを使用して、Ionide で、最初の f# 関数を記述し、それを FSI で実行する方法です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-227">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="3fad4-228">スクリプトを移行する方法は、f# ソース コードし、FSI からそのコードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-228">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="3fad4-229">書き込むはるかに f# を使用してコード Visual Studio のコードと Ionide が組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="3fad4-229">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="3fad4-230">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3fad4-230">Troubleshooting</span></span>

<span data-ttu-id="3fad4-231">次に遭遇する特定の問題をトラブルシューティングする方法はいくつかを示します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-231">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="3fad4-232">Ionide の編集機能コードを取得するには、f# ファイルをディスクにしている Visual Studio Code ワークスペースで、開いているフォルダー内に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fad4-232">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="3fad4-233">場合は、システムを変更または開いている Visual Studio のコードで Ionide 前提条件をインストールしたら、Visual Studio Code を再起動します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-233">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="3fad4-234">F# コンパイラと f# interactive コマンド ラインから完全修飾パスを使用せずに使用することができることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3fad4-234">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="3fad4-235">これを行うように入力して`fsc`f# コンパイラ、コマンドラインでと`fsi`または`fsharpi`Visual f# のツールを Windows と Mac と Linux の Mono それぞれします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-235">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="3fad4-236">プロジェクトのディレクトリで無効な文字があれば、Ionide が動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3fad4-236">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="3fad4-237">このような場合、プロジェクト ディレクトリの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="3fad4-237">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="3fad4-238">Ionide コマンドのいずれも作業している場合、 [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)を誤ってオーバーライドしているかどうかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fad4-238">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="3fad4-239">Ionide はコンピューターに分割すると、上記のいずれが問題を修正、削除してください。、`ionide-fsharp`コンピューターにディレクトリおよびプラグインのスイートを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="3fad4-239">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="3fad4-240">Ionide とは、構築および f# コミュニティのメンバーによって管理されるオープン ソース プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="3fad4-240">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="3fad4-241">問題を報告し、自由に投稿にしてください、 [Ionide VSCode: FSharp GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-241">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="3fad4-242">レポートに問題がある場合は場合に、従ってください[、ログを取得するための使用方法についての問題を報告するときに](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-242">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="3fad4-243">Ionide 開発者や f# でコミュニティからさらにヘルプを求めることも、 [Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-243">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3fad4-244">次の手順</span><span class="sxs-lookup"><span data-stu-id="3fad4-244">Next steps</span></span>

<span data-ttu-id="3fad4-245">F# と言語の機能の詳細については、チェック アウト[ツアーの f#](../tour.md)です。</span><span class="sxs-lookup"><span data-stu-id="3fad4-245">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3fad4-246">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fad4-246">See also</span></span>

[<span data-ttu-id="3fad4-247">F# のツアー</span><span class="sxs-lookup"><span data-stu-id="3fad4-247">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="3fad4-248">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="3fad4-248">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="3fad4-249">関数</span><span class="sxs-lookup"><span data-stu-id="3fad4-249">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="3fad4-250">モジュール</span><span class="sxs-lookup"><span data-stu-id="3fad4-250">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="3fad4-251">名前空間</span><span class="sxs-lookup"><span data-stu-id="3fad4-251">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="3fad4-252">Ionide VSCode: FSharp</span><span class="sxs-lookup"><span data-stu-id="3fad4-252">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)
