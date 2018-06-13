---
title: Visual Studio 用開発者コマンド プロンプト
ms.date: 03/30/2017
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3ff897e37e3fa2f7202a54c05c8093ba05282c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402029"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="ab926-102">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="ab926-102">Developer Command Prompt for Visual Studio</span></span>
<span data-ttu-id="ab926-103">Visual Studio の開発者コマンド プロンプトでは、.NET Framework ツールを使いやすくするための環境変数が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ab926-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="ab926-104">開発者コマンド プロンプトは、完全版または Community Edition の Visual Studio でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ab926-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="ab926-105">Express バージョンの Visual Studio ではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="ab926-105">It is not installed with the Express versions of Visual Studio.</span></span>  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="ab926-106">コンピューター上でのコマンド プロンプトの検索</span><span class="sxs-lookup"><span data-stu-id="ab926-106">Searching for the Command Prompt on your machine</span></span>  
 <span data-ttu-id="ab926-107">Visual Studio のバージョンと、インストールした追加の SDK に応じて、複数のコマンド プロンプトが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab926-107">You may see multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="ab926-108">たとえば、Visual Studio の 64 ビット バージョンには、32 ビットと 64 ビットのコマンド プロンプトが用意されています</span><span class="sxs-lookup"><span data-stu-id="ab926-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="ab926-109">(ほとんどのツールでは、32 ビット バージョンと 64 ビット バージョンに違いはありませんが、一部のツールでは、32 ビット環境と 64 ビット環境に固有の変更が加えられています)。次の手順でうまくいかない場合は、「[コンピューター上のファイルを手動で探す](#alternative)」または「[Visual Studio 内からコマンド プロンプトを実行する](#visualstudio)」を試してください。</span><span class="sxs-lookup"><span data-stu-id="ab926-109">(The 32-bit and 64-bit versions of most tools are identical; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the steps below don't work, you can try [Manually locating the files on your machine](#alternative) or [Running command prompt from inside Visual Studio](#visualstudio).</span></span>  
  
 <span data-ttu-id="ab926-110">**Windows 10 の場合**</span><span class="sxs-lookup"><span data-stu-id="ab926-110">**In Windows 10**</span></span>  
  
1.  <span data-ttu-id="ab926-111">キーボードの Windows ロゴ キー ![Windows ロゴ](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") を押すなどして、**[スタート]** メニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="ab926-111">Open the **Start** menu, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="ab926-112">**[スタート]** メニューで、「`dev`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ab926-112">On the **Start** menu, enter `dev`.</span></span> <span data-ttu-id="ab926-113">これにより、検索パターンに一致する、インストールされているアプリの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab926-113">This will bring a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="ab926-114">別のコマンド プロンプトを探す場合は、別の検索語句 (「`prompt`」など) を入力してください。</span><span class="sxs-lookup"><span data-stu-id="ab926-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>  
  
3.  <span data-ttu-id="ab926-115">**[開発者コマンド プロンプト]** (または、使用するコマンド プロンプト) を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab926-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="ab926-116">**Windows 8.1 の場合**</span><span class="sxs-lookup"><span data-stu-id="ab926-116">**In Windows 8.1**</span></span>  
  
1.  <span data-ttu-id="ab926-117">キーボードの Windows ロゴ キー ![Windows ロゴ](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") を押すなどして、**[スタート]** 画面に移動します。</span><span class="sxs-lookup"><span data-stu-id="ab926-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="ab926-118">**[スタート]** 画面で、`CTRL + TAB` キーを押して **[アプリ]** 一覧を開き、「`V`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ab926-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="ab926-119">これにより、インストールされているすべての Visual Studio コマンド プロンプトが含まれた一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab926-119">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
3.  <span data-ttu-id="ab926-120">**[開発者コマンド プロンプト]** (または、使用するコマンド プロンプト) を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab926-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="ab926-121">**Windows 8 の場合**</span><span class="sxs-lookup"><span data-stu-id="ab926-121">**In Windows 8**</span></span>  
  
1.  <span data-ttu-id="ab926-122">キーボードの Windows ロゴ キー ![Windows ロゴ](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") を押すなどして、**[スタート]** 画面に移動します。</span><span class="sxs-lookup"><span data-stu-id="ab926-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="ab926-123">**[スタート]** 画面で、Windows ロゴ キー ![Windows ロゴ](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z` を押します。</span><span class="sxs-lookup"><span data-stu-id="ab926-123">On the **Start** screen, press the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>  
  
3.  <span data-ttu-id="ab926-124">画面下部にある**アプリ ビュー** アイコンを選択し、「`V`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ab926-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="ab926-125">これにより、インストールされているすべての Visual Studio コマンド プロンプトが含まれた一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab926-125">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
4.  <span data-ttu-id="ab926-126">**[開発者コマンド プロンプト]** (または、使用するコマンド プロンプト) を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab926-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="ab926-127">**Windows 7 の場合**</span><span class="sxs-lookup"><span data-stu-id="ab926-127">**In Windows 7**</span></span>  
  
1.  <span data-ttu-id="ab926-128">**[スタート]** を選択し、**[すべてのプログラム]**、**[Microsoft Visual Studio]** の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="ab926-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="ab926-129">インストールされている Visual Studio のバージョンに応じて、**[Visual Studio Tools]**、**[Visual Studio コマンド プロンプト]**、または使用するコマンド プロンプトを選択します。</span><span class="sxs-lookup"><span data-stu-id="ab926-129">Depending on the version of Visual Studio you have installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>  
  
 <span data-ttu-id="ab926-130">[Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) または [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) をインストールしている場合は、ARM、x86、または x64 の各アーキテクチャ用のコマンド プロンプトがさらに表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab926-130">If you have the [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) or [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="ab926-131">各ツールのドキュメントを参照して、どのバージョンのコマンド プロンプトを使用する必要があるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ab926-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="ab926-132">コンピューター上のファイルを手動で探す</span><span class="sxs-lookup"><span data-stu-id="ab926-132">Manually locating the files on your machine</span></span>  
  <span data-ttu-id="ab926-133">インストール済みのコマンド プロンプトのショートカットは、通常 Visual Studio の **[スタート] メニュー**用のフォルダー (C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools 内など) にあります。</span><span class="sxs-lookup"><span data-stu-id="ab926-133">Usually, the shortcuts for the command prompts you have installed will be placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span></span>    <span data-ttu-id="ab926-134">ただし、コマンド プロンプトを探しても、何らかの理由によって期待した結果を得られない場合は、そのショートカットを使用するために、コンピューター上でそのショートカットを手動で探すことができます。</span><span class="sxs-lookup"><span data-stu-id="ab926-134">But if for some reason, searching for the command prompt doesn't yield the expected results, you can try to manually locate the shortcut on your machine in order to use it.</span></span>   <span data-ttu-id="ab926-135">VsDevCmd.bat などのコマンド プロンプトのファイル名を検索するか、または Tools フォルダー (C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools など) に移動します (パスは、Visual Studio のバージョンとインストール先に応じて変わります)。</span><span class="sxs-lookup"><span data-stu-id="ab926-135">Try searching for the name of the command prompt file such as VsDevCmd.bat or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (path will change according to your Visual Studio version and installation location).</span></span>  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="ab926-136">Visual Studio 内からコマンド プロンプトを実行する</span><span class="sxs-lookup"><span data-stu-id="ab926-136">Running command prompt from inside Visual Studio</span></span>  
 <span data-ttu-id="ab926-137">簡単にアクセスできるように、Visual Studio の開発者コマンド プロンプトまたは他のコマンド プロンプトを Visual Studio の [ツール] メニューに追加することができます。このためには、[外部ツール一覧] にそのコマンド プロンプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="ab926-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="ab926-138">この追加を行う方法は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ab926-138">This is how you can accomplish that:</span></span>  
  
1.  <span data-ttu-id="ab926-139">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="ab926-139">Open Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ab926-140">**[ツール]** メニューを選択し、**[外部ツール...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab926-140">Select the **Tools** menu and choose **External Tools...**.</span></span>  
  
3.  <span data-ttu-id="ab926-141">**[外部ツール]** ダイアログ ボックスで、**[追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab926-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="ab926-142">新しいエントリが表示されます</span><span class="sxs-lookup"><span data-stu-id="ab926-142">A new entry appears</span></span>  
  
4.  <span data-ttu-id="ab926-143">新しいメニュー項目の **[タイトル]** を入力します (「`Command Prompt`」など)。</span><span class="sxs-lookup"><span data-stu-id="ab926-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>  
  
5.  <span data-ttu-id="ab926-144">**[コマンド]** フィールドに、起動するファイル (`%comspec%` や `C:\Windows\System32\cmd.exe` など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab926-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe` .</span></span>  
  
6.  <span data-ttu-id="ab926-145">**[引数]** フィールドに、使用する特定のコマンド プロンプトのある場所を指定します (`/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` など (これにより、[!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)] でインストールされた開発者コマンド プロンプトが起動されます))。</span><span class="sxs-lookup"><span data-stu-id="ab926-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (this will launch the Developer Command Prompt installed with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span></span> <span data-ttu-id="ab926-146">この値は、Visual Studio のバージョンとインストール先に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab926-146">This value needs to be changed according to your Visual Studio version and installation location.</span></span>  
  
7.  <span data-ttu-id="ab926-147">**[初期ディレクトリ]** フィールドの値 (**[プロジェクト ディレクトリ]** など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab926-147">Choose a value for the **Initial directory** field such as **Project Directory** .</span></span>  
  
8.  <span data-ttu-id="ab926-148">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ab926-148">Choose the **OK** button.</span></span>  
  
 <span data-ttu-id="ab926-149">この後、新しいメニュー項目が追加され、このコマンド プロンプトに **[ツール]** メニューからアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab926-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab926-150">参照</span><span class="sxs-lookup"><span data-stu-id="ab926-150">See Also</span></span>  
 [<span data-ttu-id="ab926-151">ツール</span><span class="sxs-lookup"><span data-stu-id="ab926-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="ab926-152">Visual Studio の外部ツール</span><span class="sxs-lookup"><span data-stu-id="ab926-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
