---
title: "Visual Studio 2017 での C# Hello World アプリケーションのデバッグ"
description: "Visual Studio 2017 を使用して C# で記述された Hello World アプリをデバッグする方法を説明します。"
keywords: ".NET Core, .NET Core コンソール アプリケーション, .NET Core デバッグ"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
ms.openlocfilehash: 6fbebf69b2772b4159841d13068e7b95a39bea92
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="0f633-104">Visual Studio 2017 での Hello World アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="0f633-104">Debug your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="0f633-105">ここまでは、[「Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築」](.\with-visual-studio.md) または[「Visual Studio 2017 での .NET Core を使用した Visual Basic Hello World アプリケーションの構築」](vb-with-visual-studio.md)の手順に従って、簡単なコンソール アプリケーションを作成して実行しました。</span><span class="sxs-lookup"><span data-stu-id="0f633-105">So far, you've followed the steps in [Build a C# Hello World Application with .NET Core in Visual Studio 2017](.\with-visual-studio.md) or [Build a Visual Basic Hello World Application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md) to create and run a simple console application.</span></span> <span data-ttu-id="0f633-106">アプリケーションを記述してコンパイルしたら、テストを開始できます。</span><span class="sxs-lookup"><span data-stu-id="0f633-106">Once you've written and compiled your application, you can begin testing it.</span></span> <span data-ttu-id="0f633-107">Visual Studio には、アプリケーションのテストおよびトラブルシューティングの際に使用できるデバッグ ツールの包括的なセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0f633-107">Visual Studio includes a comprehensive set of debugging tools that you can use when testing and troubleshooting your application.</span></span>

## <a name="debugging-in-debug-mode"></a><span data-ttu-id="0f633-108">デバッグ モードでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="0f633-108">Debugging in Debug mode</span></span>

<span data-ttu-id="0f633-109">"*デバッグ*" と "*リリース*" は、 Visual Studio に 2 つある既定のビルド構成です。</span><span class="sxs-lookup"><span data-stu-id="0f633-109">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="0f633-110">現時点のビルド構成はツールバーに表示されています。</span><span class="sxs-lookup"><span data-stu-id="0f633-110">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="0f633-111">次のツール バーの画像では、**デバッグ** モードでアプリケーションをコンパイルするように Visual Studio が構成されています。</span><span class="sxs-lookup"><span data-stu-id="0f633-111">The following toolbar image shows that Visual Studio is configured to compile your application in **Debug** mode.</span></span>

   ![Visual Studio ツール バー](./media/debugging-with-visual-studio/toolbar1.png)

<span data-ttu-id="0f633-113">最初は常にデバッグ モードでプログラムをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f633-113">You should always begin by testing your program in Debug mode.</span></span> <span data-ttu-id="0f633-114">デバッグ モードでは、コンパイラのほとんどの最適化がオフになり、ビルド プロセスの間に豊富な情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-114">Debug mode turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="setting-a-breakpoint"></a><span data-ttu-id="0f633-115">ブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="0f633-115">Setting a breakpoint</span></span>

<span data-ttu-id="0f633-116">プログラムをデバッグ モードで実行して、デバッグ機能をいくつか試してみます。</span><span class="sxs-lookup"><span data-stu-id="0f633-116">Run your program in Debug mode and try a few debugging features:</span></span>

1. <span data-ttu-id="0f633-117">"*ブレークポイント*" が設定された行が実行される "*前*" に、アプリケーションの実行が一時的に中断されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-117">A *breakpoint* temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="0f633-118">C#</span><span class="sxs-lookup"><span data-stu-id="0f633-118">C#</span></span>](#tab/csharp)
   <span data-ttu-id="0f633-119">`Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` という行にブレークポイントを設定します。そのためには、コード ウィンドウでこの行の左端の余白をクリックするか、またはこの行を選択してメニューから **[デバッグ]** > **[ブレークポイントの設定/解除]** の順に選びます。</span><span class="sxs-lookup"><span data-stu-id="0f633-119">Set a breakpoint on the line that reads `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="0f633-120">次の図のとおり、Visual Studio ではブレークポイントを強調表示し、左端の余白に赤い円を表示することで、ブレークポイントがある行を示しています。</span><span class="sxs-lookup"><span data-stu-id="0f633-120">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   ![ブレークポイントが設定された Visual Studio のプログラム ウィンドウ](./media/debugging-with-visual-studio/setbreakpoint.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="0f633-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f633-122">Visual Basic</span></span>](#tab/visual-basic)
   <span data-ttu-id="0f633-123">`Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` という行にブレークポイントを設定します。そのためには、コード ウィンドウでこの行の左端の余白をクリックするか、またはこの行を選択してメニューから **[デバッグ]** > **[ブレークポイントの設定/解除]** の順に選びます。</span><span class="sxs-lookup"><span data-stu-id="0f633-123">Set a breakpoint on the line that reads `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` by clicking in the left margin of the code window on that line or by choosing the **Debug** > **Toggle Breakpoint** menu item with the line selected.</span></span> <span data-ttu-id="0f633-124">次の図のとおり、Visual Studio ではブレークポイントを強調表示し、左端の余白に赤い円を表示することで、ブレークポイントがある行を示しています。</span><span class="sxs-lookup"><span data-stu-id="0f633-124">As the following figure shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red circle in its left margin.</span></span>

   <a name="visual-studio-program-window-with-breakpoint-setmediadebugging-with-visual-studiovb-setbreakpointpng"></a>![ブレークポイントが設定された Visual Studio のプログラム ウィンドウ](./media/debugging-with-visual-studio/vb-setbreakpoint.png)
---

1. <span data-ttu-id="0f633-126">ツール バーで緑色の矢印が付いた **HelloWorld** ボタンを選ぶか、F5 キーを押すか、**[デバッグ]** > **[デバッグの開始]** の順に選ぶことにより、プログラムをデバッグ モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="0f633-126">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar, pressing F5, or choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="0f633-127">プログラムが名前の入力を求めたら、コンソール ウィンドウに文字列を入力して、Enter を押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-127">Enter a string in the console window when the program prompts for a name and press Enter.</span></span>

1. <span data-ttu-id="0f633-128">プログラムがブレークポイントに到達すると、プログラム実行は停止します。`Console.WriteLine` メソッドが実行される前にも停止します。</span><span class="sxs-lookup"><span data-stu-id="0f633-128">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="0f633-129">**[自動変数]** ウィンドウには、現在の行の付近で使用されている変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-129">The **Autos** window displays the values of variables that are used around the current line.</span></span> <span data-ttu-id="0f633-130">**[ローカル]** ウィンドウ (**[ローカル]** タブをクリックすることで表示できる) には、現在実行しているメソッドで定義されている変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-130">The **Locals** window (which you can view by clicking the **Locals** tab) displays the values of variables that are defined in the currently executing method.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="0f633-131">C#</span><span class="sxs-lookup"><span data-stu-id="0f633-131">C#</span></span>](#tab/csharp)
   ![Visual Studio のアプリケーション ウィンドウ](./media/debugging-with-visual-studio/break.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="0f633-133">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f633-133">Visual Basic</span></span>](#tab/visual-basic)
   <a name="visual-studio-application-windowmediadebugging-with-visual-studiovb-breakpng"></a>![Visual Studio のアプリケーション ウィンドウ](./media/debugging-with-visual-studio/vb-break.png)
---

1. <span data-ttu-id="0f633-135">変数の値を変更して、プログラムにどのような影響があるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="0f633-135">You can change the value of the variables to see how it affects your program.</span></span> <span data-ttu-id="0f633-136">**[イミディエイト ウィンドウ]** が表示されない場合は、**[デバッグ]** > **[Windows]** > **[イミディエイト]** メニュー項目の順に選びます。</span><span class="sxs-lookup"><span data-stu-id="0f633-136">If the **Immediate Window** is not visible, display it by choosing the **Debug** > **Windows** > **Immediate** menu item.</span></span> <span data-ttu-id="0f633-137">**[イミディエイト ウィンドウ]** では、デバッグ中のアプリケーションと対話できます。</span><span class="sxs-lookup"><span data-stu-id="0f633-137">The **Immediate Window** lets you interact with the application you're debugging.</span></span>

1. <span data-ttu-id="0f633-138">変数の値をインタラクティブに変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f633-138">You can interactively change the values of variables.</span></span> <span data-ttu-id="0f633-139">**[イミディエイト ウィンドウ]** に「`name = "Gracie"`」と入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-139">Enter `name = "Gracie"` in the **Immediate Window** and press the Enter key.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="0f633-140">C#</span><span class="sxs-lookup"><span data-stu-id="0f633-140">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="0f633-141">**[イミディエイト ウィンドウ]** に「`date = new DateTime(2016,11,01,11,59,00)`」と入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-141">Enter `date = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

   <span data-ttu-id="0f633-142">**[イミディエイト ウィンドウ]** に、文字列変数の値と、<xref:System.DateTime> 値のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-142">The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="0f633-143">さらに、変数の値は **[自動変数]** ウィンドウおよび **[ローカル]** ウィンドウで更新されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-143">In addition, the value of the variables is updated in the **Autos** and **Locals** windows.</span></span>

   ![[自動変数] ウィンドウと [イミディエイト ウィンドウ]](./media/debugging-with-visual-studio/autosimmediate.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="0f633-145">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f633-145">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="0f633-146">**[イミディエイト ウィンドウ]** に「`currentDate = new DateTime(2016,11,01,11,59,00)`」と入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-146">Enter `currentDate = new DateTime(2016,11,01,11,59,00)` in the **Immediate Window** and press the Enter key.</span></span>

<!-- The **Immediate Window** displays the value of the string variable and the properties of the <xref:System.DateTime> value. In addition, the value of the variables is updated in the **Autos** and **Locals** windows.

   ![Autos window and Immediate Window](./media/debugging-with-visual-studio/vb-autosimmediate.png)
-->
---

1. <span data-ttu-id="0f633-147">ツール バーの **[続行]** ボタンを選ぶか、**[デバッグ]** > **[続行]** メニュー項目を選んで、プログラムの実行を続けます。</span><span class="sxs-lookup"><span data-stu-id="0f633-147">Continue program execution by selecting the **Continue** button in the toolbar or by selecting the **Debug** > **Continue** menu item.</span></span> <span data-ttu-id="0f633-148">コンソール ウィンドウに表示される値は、**[イミディエイト ウィンドウ]** で行った変更に対応しています。</span><span class="sxs-lookup"><span data-stu-id="0f633-148">The values displayed in the console window correspond to the changes you made in the **Immediate Window**.</span></span>

   !["What is your name?" というプロンプトに対して入力した値 "Jack" と、"Hello Gracie on 11/1/2016 at 11:59am" が表示されたコンソール ウィンドウ](./media/debugging-with-visual-studio/changed.png)

1. <span data-ttu-id="0f633-150">任意のキーを押してアプリケーションを終了して、デバッグ モードを終了します。</span><span class="sxs-lookup"><span data-stu-id="0f633-150">Press any key to exit the application and end Debug mode.</span></span>

## <a name="setting-a-conditional-breakpoint"></a><span data-ttu-id="0f633-151">条件付きブレークポイントの設定</span><span class="sxs-lookup"><span data-stu-id="0f633-151">Setting a conditional breakpoint</span></span>

<span data-ttu-id="0f633-152">プログラムは、ユーザーが入力した文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f633-152">Your program displays the string that the user enters.</span></span> <span data-ttu-id="0f633-153">ユーザーが何も入力しないとどうなるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="0f633-153">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="0f633-154">これは、便利なデバッグ機能 "*条件付きブレークポイント*" を使ってテストできます。この機能は、1 つまたは複数の条件が満たされたときにプログラムの実行をブレークします。</span><span class="sxs-lookup"><span data-stu-id="0f633-154">You can test this with a useful debugging feature, the *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="0f633-155">条件付きブレークポイントを設定して、ユーザーが文字列の入力に失敗したときに何が起こるかをテストするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0f633-155">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="0f633-156">C#</span><span class="sxs-lookup"><span data-stu-id="0f633-156">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="0f633-157">ブレークポイントを表す赤丸を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0f633-157">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="0f633-158">コンテキスト メニューの **[条件]** を選んで、**[ブレークポイント設定]** ダイアログを開きます。</span><span class="sxs-lookup"><span data-stu-id="0f633-158">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="0f633-159">**[条件]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0f633-159">Check the box for **Conditions**.</span></span>

   ![[ブレークポイント設定] パネル](./media/debugging-with-visual-studio/breakpointsettings.png)

1. <span data-ttu-id="0f633-161">**[条件式]** で、[例 x == 5] を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0f633-161">For the **Conditional Expression** replace "e.g. x == 5" with the following:</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="0f633-162">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f633-162">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="0f633-163">ブレークポイントを表す赤丸を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0f633-163">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="0f633-164">コンテキスト メニューの **[条件]** を選んで、**[ブレークポイント設定]** ダイアログを開きます。</span><span class="sxs-lookup"><span data-stu-id="0f633-164">On the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="0f633-165">**[条件]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0f633-165">Check the box for **Conditions**.</span></span>

   ![[ブレークポイント設定] パネル](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. <span data-ttu-id="0f633-167">**[条件式]** で、[例 x == 5] を次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0f633-167">For the **Conditional Expression** replace "e.g. x = 5" with the following:</span></span>

   ```vb
   String.IsNullOrEmpty(name)
   ```
---

   <span data-ttu-id="0f633-168">*name* に値が割り当てられていないため、またはその値が空の文字列 ("") であるために `String.IsNullOrEmpty(name)` メソッドは `true` になるという、コード条件を検証します。</span><span class="sxs-lookup"><span data-stu-id="0f633-168">You're testing for a code condition, that the `String.IsNullOrEmpty(name)` method call is `true` either because *name* has not been assigned a value or because its value is an empty string ("").</span></span> <span data-ttu-id="0f633-169">"*ヒット カウント*" または "*フィルター条件*" を指定することもできます。ヒット カウントは、ステートメントが指定した回数だけ実行される前にプログラム実行に割り込み、フィルター条件はスレッド識別子、プロセス名、スレッド名などの属性に基づいてプログラム実行に割り込みます。</span><span class="sxs-lookup"><span data-stu-id="0f633-169">You can also specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="0f633-170">**[閉じる]** を選んでダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0f633-170">Select the **Close** button to close the dialog.</span></span>

1. <span data-ttu-id="0f633-171">プログラムをデバッグ モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="0f633-171">Run the program in Debug mode.</span></span>

1. <span data-ttu-id="0f633-172">コンソール ウィンドウで、名前の入力を求められたら、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-172">In the console window, press the Enter key when prompted to enter your name.</span></span>

1. <span data-ttu-id="0f633-173">`name` が `null` または <xref:System.String.Empty?displayProperty=nameWithType> のどちらかであるという指定した条件が満たされたため、ブレークポイントに到達すると、`Console.WriteLine` メソッドが実行される前に、プログラムの実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="0f633-173">Because the condition we specified, `name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>, has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="0f633-174">**[ローカル]** ウィンドウを選ぶと、現在実行しているメソッドのローカル変数の値が表示されます。この場合は、プログラムの `Main` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0f633-174">Select the **Locals** window, which shows the values of variables that are local to the currently executing method, which is the `Main` method in your program.</span></span> <span data-ttu-id="0f633-175">`name` 変数の値が `""` または <xref:System.String.Empty?displayProperty=nameWithType> であることを調べます。</span><span class="sxs-lookup"><span data-stu-id="0f633-175">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="0f633-176">C#</span><span class="sxs-lookup"><span data-stu-id="0f633-176">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="0f633-177">**[イミディエイト ウィンドウ]** に次のステートメントを入力して、値が空の文字列であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0f633-177">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="0f633-178">結果は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="0f633-178">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ![ステートメントが実行された後で値 true を返す [イミディエイト ウィンドウ]](./media/debugging-with-visual-studio/emptystring.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="0f633-180">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f633-180">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="0f633-181">**[イミディエイト ウィンドウ]** に次のステートメントを入力して、値が空の文字列であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0f633-181">Confirm the value is an empty string by entering the following statement in the **Immediate Window**.</span></span> <span data-ttu-id="0f633-182">結果は `true` になります。</span><span class="sxs-lookup"><span data-stu-id="0f633-182">The result is `true`.</span></span>

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![ステートメントが実行された後で値 true を返す [イミディエイト ウィンドウ]](./media/debugging-with-visual-studio/vb-emptystring.png)
---

1. <span data-ttu-id="0f633-184">ツール バーの **[続行]** を選んで、プログラムの実行を続けます。</span><span class="sxs-lookup"><span data-stu-id="0f633-184">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="0f633-185">任意のキーを押してコンソール ウィンドウを閉じ、デバッグ モードを終了します。</span><span class="sxs-lookup"><span data-stu-id="0f633-185">Press any key to close the console window and exit Debug mode.</span></span>

1. <span data-ttu-id="0f633-186">コード ウィンドウの左端の余白のドットをクリックするか、行を選択して **[デバッグ] > [ブレークポイントの設定/解除]** メニュー項目を選んで、ブレークポイントをクリアします。</span><span class="sxs-lookup"><span data-stu-id="0f633-186">Clear the breakpoint by clicking on the dot in the left margin of the code window or by choosing the **Debug > Toggle Breakpoint** menu item with the row selected.</span></span>

---
## <a name="stepping-through-a-program"></a><span data-ttu-id="0f633-187">プログラムのステップ実行</span><span class="sxs-lookup"><span data-stu-id="0f633-187">Stepping through a program</span></span>

<span data-ttu-id="0f633-188">Visual Studio では、1 行ずつプログラムをステップ実行して、実行を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f633-188">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="0f633-189">通常は、ブレークポイントを設定してこの機能を使用し、プログラム コードのごく一部を通じてプログラム フローに従います。</span><span class="sxs-lookup"><span data-stu-id="0f633-189">Ordinarily, you'd set a breakpoint and use this feature to follow program flow though a small part of your program code.</span></span> <span data-ttu-id="0f633-190">プログラムが小さいため、次の手順に従ってプログラム全体をステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="0f633-190">Since your program is small, you can step through the entire program by doing the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="0f633-191">C#</span><span class="sxs-lookup"><span data-stu-id="0f633-191">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="0f633-192">メニュー バーで **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-192">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-193">次に実行される行が強調表示されて、横に矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-193">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/stepinto1.png)

   <span data-ttu-id="0f633-195">この時点で **[自動変数]** ウィンドウには、このプログラムで変数が 1 つ (`args`) しか定義されていないことが示されています。</span><span class="sxs-lookup"><span data-stu-id="0f633-195">At this point, the **Autos** window shows that your program has defined only one variable, `args`.</span></span> <span data-ttu-id="0f633-196">プログラムにコマンド ライン引数を 1 つも渡していないので、値は空の文字列配列になっています。</span><span class="sxs-lookup"><span data-stu-id="0f633-196">Because you haven't passed any command-line arguments to the program, its value is an empty string array.</span></span> <span data-ttu-id="0f633-197">さらに、空のコンソール ウィンドウが開かれています。</span><span class="sxs-lookup"><span data-stu-id="0f633-197">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="0f633-198">**[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-198">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-199">次に実行される行が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-199">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="0f633-200">図に示すように、直前のステートメントとこのステートメントの間のコードを実行するのにかかった時間は 1 ミリ秒未満です。</span><span class="sxs-lookup"><span data-stu-id="0f633-200">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="0f633-201">宣言された変数はまだ `args` しかなく、コンソール ウィンドウも空のままです。</span><span class="sxs-lookup"><span data-stu-id="0f633-201">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/stepinto2.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="0f633-203">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f633-203">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="0f633-204">メニュー バーで **[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-204">On the menu bar, choose **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-205">次に実行される行が強調表示されて、横に矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-205">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/vb-stepinto1.png)

   <span data-ttu-id="0f633-207">この時点で、プログラムにコマンドライン引数をまだ渡していないので、**[自動変数]**ウィンドウには、`args` 変数の値が空の文字列配列である旨が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-207">At this point, because you haven't passed any command-line arguments to the program, the **Autos** window shows that the value of the `args` variable is an empty string array.</span></span> <span data-ttu-id="0f633-208">さらに、空のコンソール ウィンドウが開かれています。</span><span class="sxs-lookup"><span data-stu-id="0f633-208">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="0f633-209">**[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-209">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-210">次に実行される行が強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-210">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="0f633-211">図に示すように、直前のステートメントとこのステートメントの間のコードを実行するのにかかった時間は 1 ミリ秒未満です。</span><span class="sxs-lookup"><span data-stu-id="0f633-211">As the figure shows, it has taken less than one millisecond to execute the code between the last statement and this one.</span></span> <span data-ttu-id="0f633-212">宣言された変数はまだ `args` しかなく、コンソール ウィンドウも空のままです。</span><span class="sxs-lookup"><span data-stu-id="0f633-212">`args` remains the only declared variable, and the console window remains blank.</span></span>

   ![Visual Studio ウィンドウ](./media/debugging-with-visual-studio/vb-stepinto2.png)
---

1. <span data-ttu-id="0f633-214">**[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-214">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-215">`name` の変数代入を含むステートメントが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-215">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="0f633-216">**[自動変数]** ウィンドウに `name` が `null` (C# の場合) または `Nothing` (Visual Basic の場合) であると表示され、コンソール ウィンドウに "What is your name?" という文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-216">The **Autos** window shows that `name` is `null` (in C#) or `Nothing` (in Visual Basic), and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="0f633-217">このプロンプトが表示されたら、コンソール ウィンドウに文字列を入力して Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-217">Respond to the prompt by entering a string in the console window and pressing Enter.</span></span> <span data-ttu-id="0f633-218">コンソールは応答しなくなり、入力した文字列はコンソール ウィンドウに表示されませんが、それでも <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドにより入力はキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="0f633-218">The console is unresponsive, and the string you enter isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="0f633-219">**[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-219">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-220">`date` (C#) または `currentDate` (Visual Basic) の変数代入を含むステートメントが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-220">Visual Studio highlights the statement that includes the `date` (in C#) or `currentDate` (in Visual Basic) variable assignment.</span></span> <span data-ttu-id="0f633-221">**[自動変数]** ウィンドウには、<xref:System.DateTime.Now?displayProperty=nameWithType> プロパティの値および <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> メソッドの呼び出しによって返された値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-221">The **Autos** window shows the <xref:System.DateTime.Now?displayProperty=nameWithType> property value and the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0f633-222">コンソール ウィンドウには、コンソールにより求められて入力した文字列も表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-222">The console window also displays the string entered when the console prompted for input.</span></span>

1. <span data-ttu-id="0f633-223">**[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-223">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-224">**[自動変数]** ウィンドウには、<xref:System.DateTime.Now?displayProperty=nameWithType> プロパティから代入された後の `date` 変数の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-224">The **Autos** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0f633-225">コンソール ウィンドウに変更はありません。</span><span class="sxs-lookup"><span data-stu-id="0f633-225">The console window is unchanged.</span></span>

1. <span data-ttu-id="0f633-226">**[デバッグ]** > **[ステップ イン]** を選ぶか、F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-226">Select **Debug** > **Step Into** or press the F11 key.</span></span> <span data-ttu-id="0f633-227">Visual Studio は、<xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0f633-227">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0f633-228">`date` の値 (または `currentDate`) と `name` の値が **[自動変数]** ウィンドウに表示され、コンソール ウィンドウに書式付き文字列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f633-228">The values of the `date` (or `currentDate`) and `name` variables appear in the **Autos** window, and the console window displays the formatted string.</span></span>

1. <span data-ttu-id="0f633-229">**[デバッグ]** > **[ステップ アウト]** の順に選ぶか、Shift + F11 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f633-229">Select **Debug** > **Step Out** or press Shift and the F11 key.</span></span> <span data-ttu-id="0f633-230">これによりステップ バイ ステップの実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="0f633-230">This stops step-by-step execution.</span></span> <span data-ttu-id="0f633-231">コンソール ウィンドウにメッセージが表示され、任意のキーを押すよう求められます。</span><span class="sxs-lookup"><span data-stu-id="0f633-231">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="0f633-232">任意のキーを押してコンソール ウィンドウを閉じ、デバッグ モードを終了します。</span><span class="sxs-lookup"><span data-stu-id="0f633-232">Press any key to close the console window and exit Debug mode.</span></span>

## <a name="building-a-release-version"></a><span data-ttu-id="0f633-233">リリース バージョンのビルド</span><span class="sxs-lookup"><span data-stu-id="0f633-233">Building a Release version</span></span>

<span data-ttu-id="0f633-234">アプリケーションのデバッグ ビルドのテストが終了したら、リリース バージョンもコンパイルしてテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f633-234">Once you've tested the Debug build of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="0f633-235">リリース バージョンには、アプリケーションの動作に悪影響を与える可能性があるコンパイラの最適化が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="0f633-235">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="0f633-236">たとえば、パフォーマンスを向上させるように設計されたコンパイラの最適化では、非同期アプリケーションまたはマルチスレッド アプリケーションで競合状態が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f633-236">For example, compiler optimizations that are designed to improve performance can create race conditions in asynchronous or multithreaded applications.</span></span>

<span data-ttu-id="0f633-237">コンソール アプリケーションのリリース バージョンをビルドしてテストするには、ツール バーのビルド構成を **[デバッグ]** から **[リリース]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="0f633-237">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![イメージ](./media/debugging-with-visual-studio/toolbar2.png)

<span data-ttu-id="0f633-239">F5 キーを押すか、**[ビルド]** メニューの **[ソリューションのビルド]** を選ぶ、コンソール アプリケーションのリリース バージョンがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="0f633-239">When you press F5 or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of your console application.</span></span> <span data-ttu-id="0f633-240">アプリケーションのデバッグ バージョンと同様に、テストできます。</span><span class="sxs-lookup"><span data-stu-id="0f633-240">You can test it as you did the Debug version of the application.</span></span>

<span data-ttu-id="0f633-241">アプリケーションのデバッグが終了したら、次の手順ではアプリケーションを配置可能なバージョンにして発行します。</span><span class="sxs-lookup"><span data-stu-id="0f633-241">Once you've finished debugging your application, the next step is to publish a deployable version of your application.</span></span> <span data-ttu-id="0f633-242">この方法については、「[Visual Studio 2017 を使用した Hello World アプリケーションの発行](./publishing-with-visual-studio.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0f633-242">For information on how to do this, see [Publish the Hello World application with Visual Studio 2017](./publishing-with-visual-studio.md).</span></span>
