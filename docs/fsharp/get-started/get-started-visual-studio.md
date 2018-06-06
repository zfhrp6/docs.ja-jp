---
title: F# では、Visual Studio での概要します。
description: Visual Studio で f# を使用する方法を説明します。
ms.date: 02/13/2017
ms.openlocfilehash: 22fbe8086ec133605e1d9b4b28e524fe2ed8ac28
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728535"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="a30a6-103">F# では、Visual Studio での概要します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="a30a6-104">Visual Studio IDE では、f# および Visual f# ツールがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="a30a6-105">作業を開始するには[Visual Studio のダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)まだ行っていない場合は、します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-105">To begin, you should [download Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="a30a6-106">この記事の内容が Visual Studio 2017 Community Edition を使用しますが、任意のバージョンの F# で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-106">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="a30a6-107">F# をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a30a6-107">Installing F#</span></span> #

<span data-ttu-id="a30a6-108">最初に Visual Studio をダウンロードしている場合、Visual Studio インストーラーが最初にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-108">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="a30a6-109">インストーラーから Visual Studio 2017 の任意のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a30a6-109">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="a30a6-110">既にインストールされていることをクリックして**変更**です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-110">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="a30a6-111">次に、ワークロードの一覧を表示されます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-111">You'll next see a list of Workloads.</span></span> <span data-ttu-id="a30a6-112">F# では、次のワークロードのを通じてにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-112">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="a30a6-113">ワークロード</span><span class="sxs-lookup"><span data-stu-id="a30a6-113">Workload</span></span>|<span data-ttu-id="a30a6-114">アクション</span><span class="sxs-lookup"><span data-stu-id="a30a6-114">Action</span></span>|
|--------|------|
| <span data-ttu-id="a30a6-115">.NET Core クロスプラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="a30a6-115">.NET Core cross-platform development</span></span> | <span data-ttu-id="a30a6-116">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="a30a6-116">No action - F# is installed by default</span></span> |
| <span data-ttu-id="a30a6-117">ASP.NET と Web 開発</span><span class="sxs-lookup"><span data-stu-id="a30a6-117">ASP.NET and web development</span></span> | <span data-ttu-id="a30a6-118">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="a30a6-118">No action - F# is installed by default</span></span> |
| <span data-ttu-id="a30a6-119">Azure の開発</span><span class="sxs-lookup"><span data-stu-id="a30a6-119">Azure development</span></span> | <span data-ttu-id="a30a6-120">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="a30a6-120">No action - F# is installed by default</span></span> |
| <span data-ttu-id="a30a6-121">.NET によるモバイル開発</span><span class="sxs-lookup"><span data-stu-id="a30a6-121">Mobile development with .NET</span></span> | <span data-ttu-id="a30a6-122">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="a30a6-122">No action - F# is installed by default</span></span> |
| <span data-ttu-id="a30a6-123">データ サイエンスと分析のアプリケーション</span><span class="sxs-lookup"><span data-stu-id="a30a6-123">Data science and analytical applications</span></span> | <span data-ttu-id="a30a6-124">既定では、f# のアクションがインストールされていません</span><span class="sxs-lookup"><span data-stu-id="a30a6-124">No action - F# is installed by default</span></span> |
| <span data-ttu-id="a30a6-125">.NET デスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="a30a6-125">.NET desktop development</span></span> | <span data-ttu-id="a30a6-126">選択**f# デスクトップの言語サポート**右側から</span><span class="sxs-lookup"><span data-stu-id="a30a6-126">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="a30a6-127">データ ストレージとデータ処理</span><span class="sxs-lookup"><span data-stu-id="a30a6-127">Data storage and processing</span></span> | <span data-ttu-id="a30a6-128">選択**f# デスクトップの言語サポート**右側から</span><span class="sxs-lookup"><span data-stu-id="a30a6-128">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="a30a6-129">次に、をクリックして**変更**右下にします。</span><span class="sxs-lookup"><span data-stu-id="a30a6-129">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="a30a6-130">選択したすべてのものがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-130">This will install everything you have selected.</span></span>  <span data-ttu-id="a30a6-131">クリックして、f# 言語のサポートを備えた Visual Studio 2017 を開くことができますし、**起動**です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-131">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="a30a6-132">コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-132">Creating a console application</span></span>

<span data-ttu-id="a30a6-133">Visual Studio での最も基本的なプロジェクトの 1 つは、コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="a30a6-133">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="a30a6-134">これを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-134">Here's how to do it.</span></span>  <span data-ttu-id="a30a6-135">Visual Studio が起動したら。</span><span class="sxs-lookup"><span data-stu-id="a30a6-135">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="a30a6-136">**ファイル** メニューのをポイント**新規**を選択し**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-136">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="a30a6-137">新規のプロジェクトのダイアログ ボックスで、**テンプレート**、表示されるはず**Visual f#** です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-137">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="a30a6-138">F# のテンプレートを表示する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-138">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="a30a6-139">いずれかを選択 **.NET Core コンソール アプリ**または**コンソール アプリ**です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-139">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="a30a6-140">選択、**わかりました**f# プロジェクトを作成するボタンです。</span><span class="sxs-lookup"><span data-stu-id="a30a6-140">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="a30a6-141">ソリューション エクスプ ローラーで f# プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-141">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="a30a6-142">コードの記述</span><span class="sxs-lookup"><span data-stu-id="a30a6-142">Writing your code</span></span>

<span data-ttu-id="a30a6-143">最初にいくつかのコードを記述して開始しましょう。</span><span class="sxs-lookup"><span data-stu-id="a30a6-143">Let's get started by writing some code first.</span></span>  <span data-ttu-id="a30a6-144">確認して、`Program.fs`ファイルが開いている場合と、その内容を次に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-144">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="a30a6-145">前のコード例の関数で`square`が定義されているという名前の入力を取り`x`単独で乗算します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-145">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="a30a6-146">F# で使用されるため[型の推論](../language-reference/type-inference.md)の型`x`を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a30a6-146">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="a30a6-147">F# コンパイラは乗算が有効で型を認識し、型に割り当てられます`x`方法に基づいて`square`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-147">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="a30a6-148">ポインターを合わせる場合`square`次を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a30a6-148">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="a30a6-149">これは、関数の型のシグネチャと呼ばれるものです。</span><span class="sxs-lookup"><span data-stu-id="a30a6-149">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="a30a6-150">次のように読み取ることができます:"正方形をという名前の整数を受け取る関数は、x と整数が生成されます"です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-150">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="a30a6-151">コンパイラから受け取った注`square`、`int`型ここでは、これは、ジェネリックであるため乗算いない間は*すべて*型しますが、ではなくがジェネリック型の closed set 間でします。</span><span class="sxs-lookup"><span data-stu-id="a30a6-151">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="a30a6-152">選択、f# コンパイラ`int`このポイントが調整されます型シグネチャを呼び出す場合`square`と、別の入力など、型、`float`です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-152">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="a30a6-153">別の関数、 `main`、定義されるで装飾されている、 `EntryPoint` f# コンパイラにそのプログラムの実行を指示する属性を開始する必要がありますがあります。</span><span class="sxs-lookup"><span data-stu-id="a30a6-153">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="a30a6-154">その他のと同じ規則に従う[C スタイルのプログラミング言語](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)コマンドライン引数は、この関数に渡すことが、整数コードが返されます (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="a30a6-154">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="a30a6-155">このために呼び出される関数では、`square`関数の引数を持つ`12`します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-155">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="a30a6-156">F# コンパイラの型が割り当てられます`square`する`int -> int`(を受け取る関数は、`int`を生成し、 `int`)。</span><span class="sxs-lookup"><span data-stu-id="a30a6-156">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="a30a6-157">呼び出し`printfn`を C スタイルのプログラミング言語、書式指定文字列で指定された値に対応するパラメーターに類似した形式の文字列を使用して書式設定された印刷機能であり、結果と新しい行に出力します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-157">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="a30a6-158">コードの実行</span><span class="sxs-lookup"><span data-stu-id="a30a6-158">Running your code</span></span>

<span data-ttu-id="a30a6-159">コードを実行し、キーを押して結果を表示することができます**ctrl + f5**です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-159">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="a30a6-160">これは、デバッグを行わず、プログラムを実行し、結果を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-160">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="a30a6-161">または、選択することができます、**デバッグ**トップレベル メニューは、Visual Studio 内の項目し、選択**デバッグなしで開始**です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-161">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="a30a6-162">Visual Studio のポップをコンソール ウィンドウに出力され、次が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a30a6-162">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="a30a6-163">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="a30a6-163">Congratulations!</span></span>  <span data-ttu-id="a30a6-164">Visual Studio で初めての f# プロジェクトを作成、f# の関数は、その関数の呼び出しの結果を印刷書き込まれ、いくつかの結果を表示するプロジェクトを実行しました。</span><span class="sxs-lookup"><span data-stu-id="a30a6-164">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a30a6-165">次の手順</span><span class="sxs-lookup"><span data-stu-id="a30a6-165">Next steps</span></span>

<span data-ttu-id="a30a6-166">まだの場合はチェック アウト、[ツアーの f#](../tour.md)、f# 言語のコア機能の一部をカバーします。</span><span class="sxs-lookup"><span data-stu-id="a30a6-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="a30a6-167">一部の f# では、機能の概要を知るされ Visual Studio にコピーし、実行できる十分なコード サンプルを入力します。</span><span class="sxs-lookup"><span data-stu-id="a30a6-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="a30a6-168">使用できますが、いくつかの優れた外部リソースからの[f# ガイド](../index.md)です。</span><span class="sxs-lookup"><span data-stu-id="a30a6-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a30a6-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="a30a6-169">See also</span></span>
 [<span data-ttu-id="a30a6-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="a30a6-170">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="a30a6-171">F# のツアー</span><span class="sxs-lookup"><span data-stu-id="a30a6-171">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="a30a6-172">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="a30a6-172">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="a30a6-173">型の推論</span><span class="sxs-lookup"><span data-stu-id="a30a6-173">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="a30a6-174">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="a30a6-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
