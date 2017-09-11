---
title: "Visual Studio 2017 での .NET Core および C# を使用した Hello World アプリケーションの構築"
description: "Visual Studio 2017 で C# を使用した、単純な .NET Core コンソール アプリケーションを構築する方法について説明します。"
keywords: ".NET Core、.NET Core コンソール アプリケーション、Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
ms.translationtype: HT
ms.sourcegitcommit: 9b3a2f38b981dd5e7c3535c8212125a147aab122
ms.openlocfilehash: 37b81a6d4cf53dcf17158ccc4df6aca488f9a26b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/29/2017

---

# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="6ac6c-104">Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="6ac6c-104">Build a C# Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="6ac6c-105">このトピックでは、Visual Studio 2017 で C# を使用して、簡単な .NET Core コンソール アプリケーションを構築、デバッグ、発行するステップ バイ ステップの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-105">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="6ac6c-106">Visual Studio 2017 は、.NET Core アプリケーション構築用の機能をすべて備えた開発環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-106">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="6ac6c-107">アプリケーションが特定のプラットフォームに依存する場合を除き、.NET Core が対象とする任意のプラットフォームおよび .NET Core がインストールされている任意のシステムで実行可能です。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-107">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ac6c-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="6ac6c-108">Prerequisites</span></span>

<span data-ttu-id="6ac6c-109">[Visual Studio 2017](https://www.visualstudio.com/downloads/) が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-109">[Visual Studio 2017](https://www.visualstudio.com/downloads/) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="6ac6c-110">.NET Core 1.1 または .NET Core 2.0 のいずれかを使用して、アプリを開発することができます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-110">You can develop your app with either .NET Core 1.1 or .NET Core 2.0.</span></span>

<span data-ttu-id="6ac6c-111">詳細については、「[Windows における .NET Core の前提条件](../../core/windows-prerequisites.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-111">For more information, see the [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md) topic.</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="6ac6c-112">シンプルな "Hello World" アプリケーション</span><span class="sxs-lookup"><span data-stu-id="6ac6c-112">A simple Hello World application</span></span>

<span data-ttu-id="6ac6c-113">まず、シンプルな "Hello World" コンソール アプリケーションを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-113">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="6ac6c-114">この場合は、以下の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-114">Follow these steps:</span></span>

1. <span data-ttu-id="6ac6c-115">Visual Studio 2017 を起動します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-115">Launch Visual Studio 2017.</span></span> <span data-ttu-id="6ac6c-116">[**ファイル**] > [**新規作成**] > [**プロジェクト**] をメニュー バーから選択します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-116">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="6ac6c-117">[*新しいプロジェクト**] ダイアログで、[**Visual C#**] ノードを選択し、[**.NET Core**] ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-117">In the *New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="6ac6c-118">次に、[**コンソール アプリ (.NET Core)**] プロジェクト テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-118">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="6ac6c-119">[**名前**] テキスト ボックスに "HelloWorld" と入力します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-119">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="6ac6c-120">[**OK**] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-120">Select the **OK** button.</span></span>

   ![コンソール アプリが選択された状態の [新しいプロジェクト] ダイアログ](./media/with-visual-studio/newproject.png)
   
1. <span data-ttu-id="6ac6c-122">Visual Studio は、テンプレートを使用してプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-122">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="6ac6c-123">.NET Core の C# コンソール アプリケーション テンプレートで、`Program` というクラスが、<xref:System.String> 配列を引数として必要とする単一のメソッド `Main` とともに自動的に定義されます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-123">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="6ac6c-124">`Main` はアプリケーションのエントリ ポイントで、アプリケーションを起動するときに、ランタイムによって自動的に呼び出されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="6ac6c-125">アプリケーションが起動されるときに提供されるコマンドライン引数はすべて *args* 配列にあります。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio と新しい HelloWorld プロジェクト](./media/with-visual-studio/devenv.png)

   <span data-ttu-id="6ac6c-127">このテンプレートでは、シンプルな "Hello World" アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="6ac6c-128"><xref:System.Console.WriteLine(System.String)?displayProperty=fullName> メソッドを呼び出し、リテラル文字列 "Hello World!" を</span><span class="sxs-lookup"><span data-stu-id="6ac6c-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=fullName> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="6ac6c-129">コンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-129">in the console window.</span></span> <span data-ttu-id="6ac6c-130">ツールバー上の緑色の矢印の付いた **HelloWorld** ボタンを選択すると、プログラムをデバッグ モードで実行できます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-130">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="6ac6c-131">しかしそのとき、コンソール ウィンドウは非常に短い時間だけ表示され、すぐに閉じられます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-131">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="6ac6c-132">これは、`Main` メソッド内の単一のステートメントが実行されるとすぐに `Main` メソッドが終了してアプリケーションが終了するためです。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-132">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="6ac6c-133">コンソール ウィンドウを閉じる前にアプリケーションに一時停止させるには、<xref:System.Console.WriteLine(System.String)?displayProperty=fullName> メソッドへの呼び出しのすぐ後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-133">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=fullName> method:</span></span>

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   <span data-ttu-id="6ac6c-134">このコードは、任意のキーを押すようにユーザーにメッセージを表示し、キーが押されるまでプログラムを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-134">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="6ac6c-135">メニュー バーで [**ビルド**] > [**ソリューションのビルド**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="6ac6c-136">これにより、プログラムが IL (中間言語) にコンパイルされ、それが JIT (just-in-time) コンパイラによってバイナリ コードに変換されます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-136">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="6ac6c-137">ツールバー上の緑色の矢印の付いた **HelloWorld** ボタンを選択して、プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-137">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Hello World Press any key to continue と表示されているコンソール ウィンドウ](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="6ac6c-139">任意のキーを押して、コンソール ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-139">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="6ac6c-140">Hello World アプリケーションの拡張</span><span class="sxs-lookup"><span data-stu-id="6ac6c-140">Enhancing the Hello World application</span></span>

<span data-ttu-id="6ac6c-141">アプリケーションを拡張し、ユーザーに名前の入力を求め、日付と時刻と共にそれを表示するようにします。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-141">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="6ac6c-142">以下のように、プログラムを変更してテストします。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-142">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="6ac6c-143">コード ウィンドウで `public static void Main(string[] args)` 行のすぐ後に、次の C# コードを、先頭に角かっこを付け最後に閉じかっこを付けて入力します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-143">Enter the following C# code in the code window immediately after the opening bracket that follows the `public static void Main(string[] args)` line and before the first closing bracket:</span></span>

   <span data-ttu-id="6ac6c-144">[!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="6ac6c-144">[!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]</span></span>

   <span data-ttu-id="6ac6c-145">このコードでは、既存の <xref:System.Console.WriteLine%2A?displayProperty=fullName>、<xref:System.Console.Write%2A?displayProperty=fullName>、および <xref:System.Console.ReadKey%2A?displayProperty=fullName> ステートメントを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-145">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=fullName>, <xref:System.Console.Write%2A?displayProperty=fullName>, and <xref:System.Console.ReadKey%2A?displayProperty=fullName> statements.</span></span>

   ![Main メソッドが更新された Visual Studio プログラムの C シャープ ファイル](./media/with-visual-studio/codewindow.png)

   <span data-ttu-id="6ac6c-147">このコードは、"What is your name?" と</span><span class="sxs-lookup"><span data-stu-id="6ac6c-147">This code displays "What is your name?"</span></span> <span data-ttu-id="6ac6c-148">コンソール ウィンドウに表示して、ユーザーが文字列を入力して Enter キーを押すまで待機します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-148">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="6ac6c-149">これは文字列を `name` という変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-149">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="6ac6c-150">さらに現在の現地時刻を含む <xref:System.DateTime.Now?displayProperty=fullName> プロパティの値を取得して、それを `date` という変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-150">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=fullName> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="6ac6c-151">最後に[挿入文字列](../../csharp/language-reference/keywords/interpolated-strings.md)を使用して、これらの値をコンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-151">Finally, it uses an [interpolated string](../../csharp/language-reference/keywords/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="6ac6c-152">**[ビルド]** > **[ソリューションのビルド]** と選択して、プログラムをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-152">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="6ac6c-153">Visual Studio で、ツールバーの緑色の矢印を選択するか、F5 を押すか、メニューで [**デバッグ**] > [**デバッグの開始**] メニュー アイテムを選択して、プログラムをデバッグ モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-153">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="6ac6c-154">プロンプトに対し、名前を入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-154">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![プログラムの出力が変更されたコンソール ウィンドウ](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="6ac6c-156">任意のキーを押して、コンソール ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-156">Press any key to close the console window.</span></span>

<span data-ttu-id="6ac6c-157">アプリケーションが作成され、実行されました。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-157">You've created and run your application.</span></span> <span data-ttu-id="6ac6c-158">本格的なアプリケーションを開発するには、さらにいくつか追加の手順を行い、アプリケーションをリリース可能な状態にします。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-158">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="6ac6c-159">アプリケーションのデバッグ方法の詳細については、「[Visual Studio 2017 で C# Hello World アプリケーションをデバッグする](debugging-with-visual-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-159">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="6ac6c-160">アプリケーションの再頒布可能バージョンの開発と発行については、「[Visual Studio 2017 を使用した C# Hello World アプリケーションの発行](publishing-with-visual-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-160">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="6ac6c-161">関連トピック</span><span class="sxs-lookup"><span data-stu-id="6ac6c-161">Related topics</span></span>

<span data-ttu-id="6ac6c-162">.NET Core と Visual Studio 2017 では、コンソール アプリケーションの代わりにクラス ライブラリを構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-162">Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017.</span></span> <span data-ttu-id="6ac6c-163">ステップ バイ ステップの説明については、「[Visual Studio 2017 の C# および .NET Core を使用したクラス ライブラリの構築](library-with-visual-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-163">For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).</span></span>

<span data-ttu-id="6ac6c-164">無償ダウンロードできるコード エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用して、Mac、Linux、Windows 上で .NET Core コンソール アプリケーションを開発することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-164">You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor.</span></span> <span data-ttu-id="6ac6c-165">ステップ バイ ステップのチュートリアルについては、「[Visual Studio Code の概要](with-visual-studio-code.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ac6c-165">For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md).</span></span>

