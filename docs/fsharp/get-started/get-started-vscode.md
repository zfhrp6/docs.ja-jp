---
title: Visual Studio のコードで f# の概要します。
description: Visual Studio Code と Ionide プラグイン suite で f# を使用する方法を説明します。
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728629"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="5d54b-103">Visual Studio のコードで f# の概要します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="5d54b-104">F# で記述できます[Visual Studio Code](https://code.visualstudio.com)で、 [Ionide プラグイン](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)、IntelliSense および基本的なコードの優れたクロスプラット フォームで軽量な統合開発環境 (IDE) のエクスペリエンスを取得するにはリファクタリングします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="5d54b-105">参照してください[Ionide.io](http://ionide.io)をプラグイン スイートに関する詳しい情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d54b-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d54b-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5d54b-106">Prerequisites</span></span>

<span data-ttu-id="5d54b-107">必要があります[git がインストールされている](https://git-scm.com/download)するには、パスで使用できると Ionide でプロジェクト テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-107">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="5d54b-108">」と入力して正しくインストールされていることを確認することができます`git --version`キーを押して、コマンド プロンプトで**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-108">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="5d54b-109">macOS</span><span class="sxs-lookup"><span data-stu-id="5d54b-109">macOS</span></span>](#tab/macos)

<span data-ttu-id="5d54b-110">Ionide を使用して[モノラル](http://www.mono-project.com)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-110">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="5d54b-111">Macos モノラルをインストールする最も簡単な方法は、Homebrew を介してです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-111">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="5d54b-112">単に、端末に、次を入力します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-112">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="5d54b-113">またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-113">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="5d54b-114">Linux</span><span class="sxs-lookup"><span data-stu-id="5d54b-114">Linux</span></span>](#tab/linux)

<span data-ttu-id="5d54b-115">Ionide Linux では、使用も[モノラル](https://www.mono-project.com)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-115">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="5d54b-116">Debian、Ubuntu またはの場合は、次の操作を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-116">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="5d54b-117">またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-117">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="5d54b-118">Windows</span><span class="sxs-lookup"><span data-stu-id="5d54b-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="5d54b-119">Windows の場合は、する必要があります[F# でサポートを含む Visual Studio をインストール](get-started-visual-studio.md#installing-f)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-119">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="5d54b-120">これにより、書き込み、コンパイル、および f# コードを実行するために必要なすべてのコンポーネントがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-120">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="5d54b-121">またをインストールする必要があります、 [.NET Core SDK](https://www.microsoft.com/net/download/)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-121">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="5d54b-122">Visual Studio Code と Ionide プラグインのインストール</span><span class="sxs-lookup"><span data-stu-id="5d54b-122">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="5d54b-123">Visual Studio のコードからをインストールすることができます、 [code.visualstudio.com](https://code.visualstudio.com) web サイトです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-123">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>

<span data-ttu-id="5d54b-124">次に、"Ionide"を検索して拡張機能 アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-124">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="5d54b-125">Visual Studio のコードで、f# のサポートに必要なだけプラグイン[Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-125">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="5d54b-126">ただし、インストールすることも[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)を取得する[偽](https://fsharp.github.io/FAKE/)サポートと[Ionide パケットを作成](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)を取得する[パケットを作成](https://fsprojects.github.io/Paket/)をサポートします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-126">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="5d54b-127">偽の追加 f# コミュニティ ツールのプロジェクトをビルドし、それぞれの依存関係を管理するのには、パケットを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-127">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="5d54b-128">Ionide を初めてのプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-128">Creating your first project with Ionide</span></span>

<span data-ttu-id="5d54b-129">新しい f# プロジェクトを作成するには、(」と入力して何でも) の新しいフォルダーに Visual Studio のコードを開きます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-129">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="5d54b-130">次に、コマンド パレットを開きます (**ビュー > コマンド パレット**) と入力します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-130">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="5d54b-131">これが電源に、 [FORGE](https://github.com/fsharp-editing/Forge)プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="5d54b-131">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="5d54b-132">テンプレート オプションが表示されない場合は、コマンド パレットで、次のコマンドを実行してテンプレートを更新してみてください:`>F#: Refresh Project Templates`です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-132">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="5d54b-133">クリックして"f#::"新しいプロジェクトを選択して**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-133">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="5d54b-134">プロジェクト テンプレートを選択するのには、次の手順を行います。</span><span class="sxs-lookup"><span data-stu-id="5d54b-134">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="5d54b-135">選択、`classlib`テンプレートとヒット**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-135">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="5d54b-136">次でプロジェクトを作成するディレクトリを選択します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-136">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="5d54b-137">空のまま、現在のディレクトリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-137">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="5d54b-138">最後に、最後の手順で、プロジェクトの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-138">Finally, name your project in the final step.</span></span> <span data-ttu-id="5d54b-139">F# は[pascal](http://c2.com/cgi/wiki?PascalCase)プロジェクト名にします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-139">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="5d54b-140">この記事では`ClassLibraryDemo`名として。</span><span class="sxs-lookup"><span data-stu-id="5d54b-140">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="5d54b-141">プロジェクトの名前を入力するとヒット**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-141">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="5d54b-142">前の手順を実行した場合は、次のように表示される、左側にある Visual Studio コード ワークスペースを取得してください。</span><span class="sxs-lookup"><span data-stu-id="5d54b-142">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="5d54b-143">F# プロジェクト自体には、下に、`ClassLibraryDemo`フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-143">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="5d54b-144">使用してパッケージを追加するための適切なディレクトリ構造[ `Paket`](https://fsprojects.github.io/Paket/)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-144">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="5d54b-145">クロス プラットフォーム ビルド スクリプトを[ `FAKE`](https://fsharp.github.io/FAKE/)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-145">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="5d54b-146">`paket.exe`実行可能ファイルをパッケージをフェッチして依存関係が解決することができます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-146">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="5d54b-147">A`.gitignore`ファイルのこのプロジェクトを Git ベースのソース管理に追加する場合。</span><span class="sxs-lookup"><span data-stu-id="5d54b-147">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="5d54b-148">コードの記述</span><span class="sxs-lookup"><span data-stu-id="5d54b-148">Writing some code</span></span>

<span data-ttu-id="5d54b-149">開く、 *ClassLibraryDemo*フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-149">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="5d54b-150">次のファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-150">You should see the following files:</span></span>

1. <span data-ttu-id="5d54b-151">`ClassLibraryDemo.fs`、f# 実装ファイル定義クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-151">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="5d54b-152">`ClassLibraryDemo.fsproj`、、f# のプロジェクト ファイルをこのプロジェクトをビルドするために使用します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-152">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="5d54b-153">`Script.fsx`、、f# スクリプト ファイルをソース ファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-153">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="5d54b-154">`paket.references`、プロジェクトの依存関係を指定するパケットを作成ファイル。</span><span class="sxs-lookup"><span data-stu-id="5d54b-154">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="5d54b-155">開いている`Script.fsx`の末尾に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-155">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="5d54b-156">この関数が単語の形式に変換[Pig ラテン](https://en.wikipedia.org/wiki/Pig_Latin)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-156">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="5d54b-157">次の手順では、f# 対話型 (FSI) を使用して評価します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-157">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="5d54b-158">(11 行の長さにする必要があります) 関数全体を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-158">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="5d54b-159">強調表示すると後の保持、 **alt キーを押し**キーを押し、ヒット**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-159">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="5d54b-160">次に、ポップアップ ウィンドウがわかります、次のように表示されるはず。</span><span class="sxs-lookup"><span data-stu-id="5d54b-160">You'll notice a window pop up below, and it should show something like this:</span></span>

![Ionide で f# Interactive の出力の例](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="5d54b-162">これは、3 つのことを行いました。</span><span class="sxs-lookup"><span data-stu-id="5d54b-162">This did three things:</span></span>

1. <span data-ttu-id="5d54b-163">FSI プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-163">It started the FSI process.</span></span>
2. <span data-ttu-id="5d54b-164">FSI のプロセスが細かく強調表示したコードを送信します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-164">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="5d54b-165">FSI プロセスには、経由で送信されたコードが評価されます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-165">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="5d54b-166">経由で送信するため、[関数](../language-reference/functions/index.md)FSI をその関数を呼び出すようになりました。</span><span class="sxs-lookup"><span data-stu-id="5d54b-166">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="5d54b-167">対話型のウィンドウで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-167">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="5d54b-168">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-168">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="5d54b-169">ここで、最初の文字として母音で試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5d54b-169">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="5d54b-170">次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-170">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="5d54b-171">次の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-171">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="5d54b-172">関数は、期待どおりに動作してが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-172">The function appears to be working as expected.</span></span> <span data-ttu-id="5d54b-173">以上で、先ほど Visual Studio のコードで、1 つ目の f# 関数を記述し、FSI で評価。</span><span class="sxs-lookup"><span data-stu-id="5d54b-173">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="5d54b-174">FSI 内の行を終了したように可能性がありますが、`;;`です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-174">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="5d54b-175">FSI を使用すると、複数行を入力するためです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-175">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="5d54b-176">`;;`最後に FSI コードが終了したときを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-176">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="5d54b-177">コードの説明</span><span class="sxs-lookup"><span data-stu-id="5d54b-177">Explaining the code</span></span>

<span data-ttu-id="5d54b-178">コードが実際に何かわからない場合、詳細な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-178">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="5d54b-179">ご覧のとおり、`toPigLatin`の入力として単語を受け取り、その単語の Pig ラテン文字表現に変換する関数です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-179">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="5d54b-180">このルールは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-180">The rules for this are as follows:</span></span>

<span data-ttu-id="5d54b-181">単語の最初の文字で始まる場合、母音、単語の末尾に「お」を追加します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-181">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="5d54b-182">母音で始まらない場合、は、単語の末尾にその最初の文字を移動し、「常」を追加しています。</span><span class="sxs-lookup"><span data-stu-id="5d54b-182">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="5d54b-183">FSI では、次を認識することがあります。</span><span class="sxs-lookup"><span data-stu-id="5d54b-183">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="5d54b-184">示すこの`toPigLatin`で取得する関数は、`string`入力として (と呼ばれる`word`)、し、返します別`string`です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-184">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="5d54b-185">これと呼ばれますが、[関数の型のシグネチャ](https://fsharpforfunandprofit.com/posts/function-signatures/)、f# コードを理解するためのキーは、f# の根本的な部分です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-185">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="5d54b-186">Visual Studio のコード内で、関数ポインターを合わせる場合するも明らかです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-186">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="5d54b-187">関数の本文には、2 つの異なる部分をわかります。</span><span class="sxs-lookup"><span data-stu-id="5d54b-187">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="5d54b-188">呼ばれる内部関数は、 `isVowel`、特定の文字を決定する (`c`) を介して提供されたパターンの 1 つと一致する場合にチェックして、母音は、[パターンに一致する](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="5d54b-188">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="5d54b-189">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)セルのかどうか、最初の文字が、母音コンス トラクターの戻り値は、入力文字列から値に基づいて場合は、最初の文字式であるか、母音。</span><span class="sxs-lookup"><span data-stu-id="5d54b-189">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="5d54b-190">フロー`toPigLatin`のため。</span><span class="sxs-lookup"><span data-stu-id="5d54b-190">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="5d54b-191">かどうか、入力の単語の最初の文字は母音を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5d54b-191">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="5d54b-192">である場合は、単語の末尾に「お」をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-192">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="5d54b-193">それ以外の場合、単語の末尾までその最初の文字を移動し、「常」を追加します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-193">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="5d54b-194">1 つの最後にこの方法に注意してください。 その他の多くの言語がとは異なり、関数から返される明示的な指示がないです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-194">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="5d54b-195">これは f# 式に基づくは、関数の本体の最後の式の戻り値です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-195">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="5d54b-196">`if..then..else`自体、式の本体では、`then`ブロックまたはの本文、`else`ブロックが入力された値によって返されます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-196">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="5d54b-197">クラスの実装ファイル、スクリプト コードを移動します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-197">Moving your script code into the implementation file</span></span>

<span data-ttu-id="5d54b-198">この記事の前のセクションには、f# コードの記述の一般的な最初の手順が示されている: 初期関数を作成し、FSI して対話的に実行します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-198">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="5d54b-199">これは、REPL 駆動型開発と呼ばれます場所[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 「読み取り評価印刷ループ」を意味します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-199">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="5d54b-200">これは何かの操作が得られるまで機能をテストする優れた手段です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-200">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="5d54b-201">REPL 駆動型開発の次の手順では、f# 実装ファイルの作業中のコードを移動します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-201">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="5d54b-202">これは、実行可能なアセンブリの f# コンパイラでコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="5d54b-202">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="5d54b-203">最初に開く`ClassLibraryDemo.fs`です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-203">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="5d54b-204">一部のコードが既にされているがわかります。</span><span class="sxs-lookup"><span data-stu-id="5d54b-204">You'll notice that some code is already in there.</span></span> <span data-ttu-id="5d54b-205">進めて、クラス定義を削除しがのままにすることを確認、 [ `namespace` ](../language-reference/namespaces.md)上部にある宣言します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-205">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="5d54b-206">次に、新しい作成[ `module` ](../language-reference/modules.md)と呼ばれる`PigLatin`をコピーし、`toPigLatin`ように、関数。</span><span class="sxs-lookup"><span data-stu-id="5d54b-206">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="5d54b-207">次に、開く、 `Script.fsx` 、ファイルに追加され、全体を削除`toPigLatin`機能しますが、ファイルに次の 2 行を保持することを確認します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-207">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="5d54b-208">FSI を読み込むスクリプトの最初の行が必要な`ClassLibraryDemo.fs`します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-208">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="5d54b-209">2 番目の行が使いやすい: 省略された場合、オプションですが、入力する必要があります`open ClassLibraryDemo`FSI ウィンドウを表示する場合に、`ToPigLatin`モジュールをスコープにします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-209">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="5d54b-210">次に、FSI ウィンドウで、関数を使って呼び出し、`PigLatin`前に定義するモジュール。</span><span class="sxs-lookup"><span data-stu-id="5d54b-210">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="5d54b-211">正常に完了</span><span class="sxs-lookup"><span data-stu-id="5d54b-211">Success!</span></span> <span data-ttu-id="5d54b-212">前に、同じ結果を取得することは、f# 実装ファイルから読み込まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5d54b-212">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="5d54b-213">ここでの主な違いは、f# ソース ファイルは FSI 内だけでなく、どこにでも実行できるアセンブリにコンパイルされていることです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-213">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="5d54b-214">まとめ</span><span class="sxs-lookup"><span data-stu-id="5d54b-214">Summary</span></span>

<span data-ttu-id="5d54b-215">この記事では次の内容を学習しました。</span><span class="sxs-lookup"><span data-stu-id="5d54b-215">In this article, you've learned:</span></span>

1. <span data-ttu-id="5d54b-216">Ionide で Visual Studio のコードを設定する方法です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-216">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="5d54b-217">Ionide で初めての f# プロジェクトを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="5d54b-217">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="5d54b-218">F# スクリプトを使用して、Ionide で、最初の f# 関数を記述し、それを FSI で実行する方法です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-218">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="5d54b-219">スクリプトを移行する方法は、f# ソース コードし、FSI からそのコードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-219">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="5d54b-220">書き込むはるかに f# を使用してコード Visual Studio のコードと Ionide が組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="5d54b-220">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="5d54b-221">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5d54b-221">Troubleshooting</span></span>

<span data-ttu-id="5d54b-222">次に遭遇する特定の問題をトラブルシューティングする方法はいくつかを示します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-222">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="5d54b-223">Ionide の編集機能コードを取得するには、f# ファイルをディスクにしている Visual Studio Code ワークスペースで、開いているフォルダー内に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d54b-223">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="5d54b-224">場合は、システムを変更または開いている Visual Studio のコードで Ionide 前提条件をインストールしたら、Visual Studio Code を再起動します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-224">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="5d54b-225">F# コンパイラと f# interactive コマンド ラインから完全修飾パスを使用せずに使用することができることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5d54b-225">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="5d54b-226">これを行うように入力して`fsc`f# コンパイラ、コマンドラインでと`fsi`または`fsharpi`Visual f# のツールを Windows と Mac と Linux の Mono それぞれします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-226">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="5d54b-227">プロジェクトのディレクトリで無効な文字があれば、Ionide が動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5d54b-227">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="5d54b-228">このような場合、プロジェクト ディレクトリの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="5d54b-228">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="5d54b-229">Ionide コマンドのいずれも作業している場合、 [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)を誤ってオーバーライドしているかどうかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d54b-229">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="5d54b-230">Ionide はコンピューターに分割すると、上記のいずれが問題を修正、削除してください。、`ionide-fsharp`コンピューターにディレクトリおよびプラグインのスイートを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="5d54b-230">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="5d54b-231">Ionide とは、構築および f# コミュニティのメンバーによって管理されるオープン ソース プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="5d54b-231">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="5d54b-232">問題を報告し、自由に投稿にしてください、 [Ionide VSCode: FSharp GitHub リポジトリ](https://github.com/ionide/ionide-vscode-fsharp)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-232">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="5d54b-233">レポートに問題がある場合は場合に、従ってください[、ログを取得するための使用方法についての問題を報告するときに](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-233">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="5d54b-234">Ionide 開発者や f# でコミュニティからさらにヘルプを求めることも、 [Ionide Gitter チャネル](https://gitter.im/ionide/ionide-project)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-234">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5d54b-235">次の手順</span><span class="sxs-lookup"><span data-stu-id="5d54b-235">Next steps</span></span>

<span data-ttu-id="5d54b-236">F# と言語の機能の詳細については、チェック アウト[ツアーの f#](../tour.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d54b-236">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
