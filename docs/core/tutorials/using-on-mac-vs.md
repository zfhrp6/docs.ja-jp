---
title: Visual Studio for Mac を使用した macOS での .NET Core の概要
description: このトピックでは、Visual Studio for Mac と .NET Core を使用して、単純なコンソール アプリケーションをビルドする手順を示します。
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: get-started-article
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 97a9c62280f09f244028c066a04350a59dd0400d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="995c7-103">Visual Studio for Mac を使用した macOS での .NET Core の概要</span><span class="sxs-lookup"><span data-stu-id="995c7-103">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="995c7-104">Visual Studio for Mac では、.NET Core アプリケーション開発用の機能をすべて備えた統合開発環境 (IDE) が提供されます。</span><span class="sxs-lookup"><span data-stu-id="995c7-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="995c7-105">このトピックでは、Visual Studio for Mac と .NET Core を使用して、単純なコンソール アプリケーションをビルドする手順を示します。</span><span class="sxs-lookup"><span data-stu-id="995c7-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="995c7-106">お客様のフィードバックは非常に貴重です。</span><span class="sxs-lookup"><span data-stu-id="995c7-106">Your feedback is highly valued.</span></span> <span data-ttu-id="995c7-107">次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="995c7-107">There are a two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="995c7-108">Visual Studio for Mac で、メニューから **[ヘルプ]** > **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="995c7-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="995c7-109">お客様のフィードバックは、[開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/8/index.html) ポータルで追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="995c7-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="995c7-110">提案するには、メニューから **[ヘルプ]** > **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、[Visual Studio for Mac の UserVoice Web ページ](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac)に移動します。</span><span class="sxs-lookup"><span data-stu-id="995c7-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="995c7-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="995c7-111">Prerequisites</span></span>

<span data-ttu-id="995c7-112">「[Mac における .NET Core の前提条件](../../core/macos-prerequisites.md)」のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="995c7-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="995c7-113">作業の開始</span><span class="sxs-lookup"><span data-stu-id="995c7-113">Getting started</span></span>

<span data-ttu-id="995c7-114">必須コンポーネントと Visual Studio for Mac を既にインストールしている場合は、このセクションをスキップして、「[プロジェクトの作成](#creating-a-project)」に進みます。</span><span class="sxs-lookup"><span data-stu-id="995c7-114">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="995c7-115">以下の手順に従って、必須コンポーネントと Visual Studio for Mac をインストールします。</span><span class="sxs-lookup"><span data-stu-id="995c7-115">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="995c7-116">[Visual Studio for Mac インストーラー](https://www.visualstudio.com/vs/visual-studio-mac/)をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="995c7-116">Download the [Visual Studio for Mac installer](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="995c7-117">インストーラーを実行します。</span><span class="sxs-lookup"><span data-stu-id="995c7-117">Run the installer.</span></span> <span data-ttu-id="995c7-118">使用許諾契約書を読み、同意します。</span><span class="sxs-lookup"><span data-stu-id="995c7-118">Read and accept the license agreement.</span></span> <span data-ttu-id="995c7-119">インストール中に、Xamarin (クロスプラットフォーム モバイル アプリ開発テクノロジ) をインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="995c7-119">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="995c7-120">.NET Core の開発の場合、Xamarin とその関連コンポーネントのインストールは省略できます。</span><span class="sxs-lookup"><span data-stu-id="995c7-120">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="995c7-121">Visual Studio for Mac のインストール プロセスのチュートリアルについては、「[Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/)」 (Visual Studio for Mac の概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="995c7-121">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="995c7-122">インストールが完了したら、Visual Studio for Mac IDE を起動します。</span><span class="sxs-lookup"><span data-stu-id="995c7-122">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="995c7-123">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="995c7-123">Creating a project</span></span>

1. <span data-ttu-id="995c7-124">ようこそ画面で **[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="995c7-124">Select **New Project** on the Welcome screen.</span></span>

   ![Visual Studio for Mac のようこそ画面の [新しいプロジェクト] ボタン](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="995c7-126">**[新しいプロジェクト]** ダイアログで、**[.NET Core]** ノードの下にある **[アプリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="995c7-126">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="995c7-127">**[コンソール アプリケーション]** テンプレートを選択してから **[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="995c7-127">Select the **Console Application** template followed by **Next**.</span></span>

   ![新しいプロジェクト テンプレートのリスト](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="995c7-129">**[プロジェクト名]** には「HelloWorld」と入力します。</span><span class="sxs-lookup"><span data-stu-id="995c7-129">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="995c7-130">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="995c7-130">Select **Create**.</span></span>

   ![[Configure your new Console Application (新しいコンソール アプリケーションの構成)] ダイアログ](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="995c7-132">プロジェクトの依存関係が復元されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="995c7-132">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="995c7-133">プロジェクトには、`Main` メソッドを持つ `Program` クラスを含む *Program.cs* という C# ファイルが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="995c7-133">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="995c7-134">`Console.WriteLine` ステートメントは、アプリの実行時に</span><span class="sxs-lookup"><span data-stu-id="995c7-134">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="995c7-135">コンソールに "Hello World!" と出力します。</span><span class="sxs-lookup"><span data-stu-id="995c7-135">to the console when the app is run.</span></span>

   ![Program.cs ファイルが開かれた状態のメイン ウィンドウ](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="995c7-137">アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="995c7-137">Run the application</span></span>

<span data-ttu-id="995c7-138">アプリは、<kbd>F5</kbd> キーを使用する場合はデバッグ モードで、<kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを使用する場合はリリース モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="995c7-138">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![[アプリケーション出力] ウィンドウに Hello World! が表示された状態](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="995c7-140">次のステップ</span><span class="sxs-lookup"><span data-stu-id="995c7-140">Next step</span></span>

<span data-ttu-id="995c7-141">「[Visual Studio for Mac を使用した macOS での完全な .NET Core ソリューションの構築](using-on-mac-vs-full-solution.md)」トピックでは、再利用可能なライブラリと単体テストを含む完全な .NET Core ソリューションを構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="995c7-141">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
