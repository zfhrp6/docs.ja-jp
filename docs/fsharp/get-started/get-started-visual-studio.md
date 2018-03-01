---
title: "F# では、Visual Studio での概要します。"
description: "Visual Studio で f# を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 818bf50507a88e1d765da8d0505ed8da4790b71f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="91b63-104">F# では、Visual Studio での概要します。</span><span class="sxs-lookup"><span data-stu-id="91b63-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="91b63-105">Visual Studio IDE では、f# および Visual f# ツールがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="91b63-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="91b63-106">作業を開始するには[Visual Studio のダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)まだ行っていない場合は、します。</span><span class="sxs-lookup"><span data-stu-id="91b63-106">To begin, you should [download Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="91b63-107">この記事の内容が Visual Studio 2017 Community Edition を使用しますが、任意のバージョンの F# で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="91b63-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="91b63-108">F# をインストールします。</span><span class="sxs-lookup"><span data-stu-id="91b63-108">Installing F#</span></span> #

<span data-ttu-id="91b63-109">最初に Visual Studio をダウンロードしている場合、Visual Studio インストーラーが最初にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="91b63-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="91b63-110">インストーラーから Visual Studio 2017 の任意のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="91b63-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="91b63-111">既にインストールされていることをクリックして**変更**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="91b63-112">次に、ワークロードの一覧を表示されます。</span><span class="sxs-lookup"><span data-stu-id="91b63-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="91b63-113">F# では、次のワークロードのを通じてにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="91b63-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="91b63-114">ワークロード</span><span class="sxs-lookup"><span data-stu-id="91b63-114">Workload</span></span>|<span data-ttu-id="91b63-115">アクション</span><span class="sxs-lookup"><span data-stu-id="91b63-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="91b63-116">.NET Core クロスプラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="91b63-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="91b63-117">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="91b63-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="91b63-118">ASP.NET と Web 開発</span><span class="sxs-lookup"><span data-stu-id="91b63-118">ASP.NET and web development</span></span> | <span data-ttu-id="91b63-119">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="91b63-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="91b63-120">Azure の開発</span><span class="sxs-lookup"><span data-stu-id="91b63-120">Azure development</span></span> | <span data-ttu-id="91b63-121">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="91b63-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="91b63-122">.NET によるモバイル開発</span><span class="sxs-lookup"><span data-stu-id="91b63-122">Mobile development with .NET</span></span> | <span data-ttu-id="91b63-123">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="91b63-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="91b63-124">データ サイエンスと分析のアプリケーション</span><span class="sxs-lookup"><span data-stu-id="91b63-124">Data science and analytical applications</span></span> | <span data-ttu-id="91b63-125">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="91b63-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="91b63-126">.NET デスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="91b63-126">.NET desktop development</span></span> | <span data-ttu-id="91b63-127">選択**f# デスクトップの言語サポート**右側から</span><span class="sxs-lookup"><span data-stu-id="91b63-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="91b63-128">データ ストレージとデータ処理</span><span class="sxs-lookup"><span data-stu-id="91b63-128">Data storage and processing</span></span> | <span data-ttu-id="91b63-129">選択**f# デスクトップの言語サポート**右側から</span><span class="sxs-lookup"><span data-stu-id="91b63-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="91b63-130">次に、をクリックして**変更**右下にします。</span><span class="sxs-lookup"><span data-stu-id="91b63-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="91b63-131">選択したすべてのものがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="91b63-131">This will install everything you have selected.</span></span>  <span data-ttu-id="91b63-132">クリックして、f# 言語のサポートを備えた Visual Studio 2017 を開くことができますし、**起動**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="91b63-133">コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="91b63-133">Creating a console application</span></span>

<span data-ttu-id="91b63-134">Visual Studio での最も基本的なプロジェクトの 1 つは、コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="91b63-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="91b63-135">これを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="91b63-135">Here's how to do it.</span></span>  <span data-ttu-id="91b63-136">Visual Studio が起動したら。</span><span class="sxs-lookup"><span data-stu-id="91b63-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="91b63-137">**ファイル** メニューのをポイント**新規**を選択し**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="91b63-138">新規のプロジェクトのダイアログ ボックスで、**テンプレート**、表示されるはず**Visual f#**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="91b63-139">F# のテンプレートを表示する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="91b63-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="91b63-140">いずれかを選択**.NET Core コンソール アプリ**または**コンソール アプリ**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="91b63-141">選択、**わかりました**f# プロジェクトを作成するボタンです。</span><span class="sxs-lookup"><span data-stu-id="91b63-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="91b63-142">ソリューション エクスプ ローラーで f# プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="91b63-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="91b63-143">コードの記述</span><span class="sxs-lookup"><span data-stu-id="91b63-143">Writing your code</span></span>

<span data-ttu-id="91b63-144">最初にいくつかのコードを記述して開始しましょう。</span><span class="sxs-lookup"><span data-stu-id="91b63-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="91b63-145">確認して、`Program.fs`ファイルが開いている場合と、その内容を次に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="91b63-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="91b63-146">前のコード例の関数で`square`が定義されているという名前の入力を取り`x`単独で乗算します。</span><span class="sxs-lookup"><span data-stu-id="91b63-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="91b63-147">F# で使用されるため[型の推論](../language-reference/type-inference.md)の型`x`を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="91b63-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="91b63-148">F# コンパイラは乗算が有効で型を認識し、型に割り当てられます`x`方法に基づいて`square`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="91b63-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="91b63-149">ポインターを合わせる場合`square`次を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91b63-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="91b63-150">これは、関数の型のシグネチャと呼ばれるものです。</span><span class="sxs-lookup"><span data-stu-id="91b63-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="91b63-151">次のように読み取ることができます:"正方形をという名前の整数を受け取る関数は、x と整数が生成されます"です。</span><span class="sxs-lookup"><span data-stu-id="91b63-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="91b63-152">コンパイラから受け取った注`square`、`int`型ここでは、これは、ジェネリックであるため乗算いない間は*すべて*型しますが、ではなくがジェネリック型の closed set 間でします。</span><span class="sxs-lookup"><span data-stu-id="91b63-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="91b63-153">選択、f# コンパイラ`int`このポイントが調整されます型シグネチャを呼び出す場合`square`と、別の入力など、型、`float`です。</span><span class="sxs-lookup"><span data-stu-id="91b63-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="91b63-154">別の関数、 `main`、定義されるで装飾されている、 `EntryPoint` f# コンパイラにそのプログラムの実行を指示する属性を開始する必要がありますがあります。</span><span class="sxs-lookup"><span data-stu-id="91b63-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="91b63-155">その他のと同じ規則に従う[C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)コマンドライン引数は、この関数に渡すことが、整数コードが返されます (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="91b63-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="91b63-156">このために呼び出される関数では、`square`関数の引数を持つ`12`します。</span><span class="sxs-lookup"><span data-stu-id="91b63-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="91b63-157">F# コンパイラの型が割り当てられます`square`する`int -> int`(を受け取る関数は、`int`を生成し、 `int`)。</span><span class="sxs-lookup"><span data-stu-id="91b63-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="91b63-158">呼び出し`printfn`を C スタイルのプログラミング言語、書式指定文字列で指定された値に対応するパラメーターに類似した形式の文字列を使用して書式設定された印刷機能であり、結果と新しい行に出力します。</span><span class="sxs-lookup"><span data-stu-id="91b63-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="91b63-159">コードの実行</span><span class="sxs-lookup"><span data-stu-id="91b63-159">Running your code</span></span>

<span data-ttu-id="91b63-160">コードを実行し、キーを押して結果を表示することができます**ctrl + f5**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="91b63-161">これは、デバッグを行わず、プログラムを実行し、結果を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="91b63-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="91b63-162">または、選択することができます、**デバッグ**トップレベル メニューは、Visual Studio 内の項目し、選択**デバッグなしで開始**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="91b63-163">Visual Studio のポップをコンソール ウィンドウに出力され、次が表示されます。</span><span class="sxs-lookup"><span data-stu-id="91b63-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="91b63-164">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="91b63-164">Congratulations!</span></span>  <span data-ttu-id="91b63-165">Visual Studio で初めての f# プロジェクトを作成、f# の関数は、その関数の呼び出しの結果を印刷書き込まれ、いくつかの結果を表示するプロジェクトを実行しました。</span><span class="sxs-lookup"><span data-stu-id="91b63-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="91b63-166">F# Interactive を使用します。</span><span class="sxs-lookup"><span data-stu-id="91b63-166">Using F# Interactive</span></span>

<span data-ttu-id="91b63-167">最適な機能では、Visual f# のツールを Visual Studio での 1 つは、f# Interactive ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="91b63-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="91b63-168">そのコードを呼び出すし、その結果を対話的に確認できますプロセスでコードを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="91b63-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="91b63-169">使用を開始するには、強調表示、`square`コードで定義された関数。</span><span class="sxs-lookup"><span data-stu-id="91b63-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="91b63-170">次に、保持、 **Alt**キーを押して**Enter**です。</span><span class="sxs-lookup"><span data-stu-id="91b63-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="91b63-171">これは、f# 対話型ウィンドウで、コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="91b63-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="91b63-172">F# 対話型ウィンドウ内に次の表示が表示されます。</span><span class="sxs-lookup"><span data-stu-id="91b63-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="91b63-173">同じ関数のシグネチャを示します、`square`関数で、先ほど見た関数に置かれているとします。</span><span class="sxs-lookup"><span data-stu-id="91b63-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="91b63-174">`square`はこれで、f# Interactive のプロセスで定義されている、異なる値で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="91b63-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="91b63-175">これは、関数を実行、結果を新しい名前に束縛`it`の型および値を表示および`it`です。</span><span class="sxs-lookup"><span data-stu-id="91b63-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="91b63-176">各行を終了する必要がありますに注意してください`;;`です。</span><span class="sxs-lookup"><span data-stu-id="91b63-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="91b63-177">これは、どのように f# Interactive を知っている、関数呼び出しが完了するとします。</span><span class="sxs-lookup"><span data-stu-id="91b63-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="91b63-178">F# Interactive で新しい関数を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="91b63-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="91b63-179">上記の定義を新しい関数の場合、 `isOdd`、受け取り、`int`と奇数かどうかをチェック。</span><span class="sxs-lookup"><span data-stu-id="91b63-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="91b63-180">異なる入力で返される内容を表示するには、この関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="91b63-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="91b63-181">関数呼び出し内で関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="91b63-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="91b63-182">使用することも、[前方パイプ演算子](../language-reference/symbol-and-operator-reference/index.md)2 つの関数に値をパイプライン処理します。</span><span class="sxs-lookup"><span data-stu-id="91b63-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="91b63-183">後のチュートリアルでは、前方パイプ演算子などについて説明します。</span><span class="sxs-lookup"><span data-stu-id="91b63-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="91b63-184">これは、f# Interactive で行うことができますに glimpse のみです。</span><span class="sxs-lookup"><span data-stu-id="91b63-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="91b63-185">詳細については、チェック アウト[f# による対話型プログラミング](../tutorials/fsharp-interactive/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="91b63-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="91b63-186">次の手順</span><span class="sxs-lookup"><span data-stu-id="91b63-186">Next steps</span></span>

<span data-ttu-id="91b63-187">まだの場合はチェック アウト、[ツアーの f#](../tour.md)、f# 言語のコア機能の一部をカバーします。</span><span class="sxs-lookup"><span data-stu-id="91b63-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="91b63-188">一部の f# では、機能の概要を知るされ Visual Studio にコピーし、実行できる十分なコード サンプルを入力します。</span><span class="sxs-lookup"><span data-stu-id="91b63-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="91b63-189">使用できますが、いくつかの優れた外部リソースからの[f# ガイド](../index.md)です。</span><span class="sxs-lookup"><span data-stu-id="91b63-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91b63-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="91b63-190">See also</span></span>
 [<span data-ttu-id="91b63-191">Visual F#</span><span class="sxs-lookup"><span data-stu-id="91b63-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="91b63-192">F# のツアー</span><span class="sxs-lookup"><span data-stu-id="91b63-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="91b63-193">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="91b63-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="91b63-194">型の推論</span><span class="sxs-lookup"><span data-stu-id="91b63-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="91b63-195">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="91b63-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
