---
title: "Main() の戻り値 (C# プログラミング ガイド)"
ms.date: 2017-08-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: d019d1c5757a961c03439d756e808ae13fd8a67b
ms.openlocfilehash: 50943bdd0b7726145797faf82719537a388dad89
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---

# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="5fc16-102">Main() の戻り値 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5fc16-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="5fc16-103">`Main` メソッドは `void` を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-103">The `Main` method can return `void`:</span></span>

<span data-ttu-id="5fc16-104">[!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5fc16-104">[!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]</span></span>

<span data-ttu-id="5fc16-105">`int` を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-105">It can also return an `int`:</span></span>

<span data-ttu-id="5fc16-106">[!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5fc16-106">[!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]</span></span>

<span data-ttu-id="5fc16-107">`Main` からの戻り値を使用しない場合は、`void` を返すと少し簡単なコードにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-107">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="5fc16-108">ただし、整数値を返すことによって、プログラムが状態の情報を、実行可能ファイルを呼び出す他のプログラムまたはスクリプトに伝達することができます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-108">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="5fc16-109">`Main` からの戻り値は、プロセスの終了コードとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-109">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="5fc16-110">次の例では、`Main` からの戻り値にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-110">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="5fc16-111">例</span><span class="sxs-lookup"><span data-stu-id="5fc16-111">Example</span></span>

<span data-ttu-id="5fc16-112">この例では、[.NET Core](../../../core/index.md) コマンド ライン ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-112">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="5fc16-113">.NET Core コマンド ライン ツールをよく理解していない場合は、この[概要のトピック](../../../core/tutorials/using-with-xplat-cli.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fc16-113">If you are unfamilar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="5fc16-114">*program.cs* の `Main` メソッドを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-114">Modify the `Main` method in *program.cs* as follows:</span></span>

<span data-ttu-id="5fc16-115">[!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="5fc16-115">[!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]</span></span>

<span data-ttu-id="5fc16-116">プログラムを Windows で実行する場合、`Main` 関数からの戻り値はすべて 1 つの環境変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-116">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="5fc16-117">この環境変数を取得するには、バッチ ファイルから `ERRORLEVEL` を使用するか、PowerShell から `$LastExitCode` を使用します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-117">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="5fc16-118">[dotnet CLI](../../../core/tools/dotnet.md) の `dotnet build` コマンドを使用してアプリケーションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-118">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="5fc16-119">次に、PowerShell スクリプトを使用してアプリケーションを実行し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-119">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="5fc16-120">次のコードをテキスト ファイルに貼り付け、プロジェクトが保存されているフォルダーに `test.ps1` として保存します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-120">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="5fc16-121">PowerShell プロンプトに「`test.ps1`」と入力して PowerShell スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-121">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="5fc16-122">コードがゼロを返すため、バッチ ファイルで成功が報告されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-122">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="5fc16-123">ただし、MainReturnValTest.cs が 0 以外の値を返すように変更して、プログラムを再コンパイルする場合、PowerShell スクリプトの後続の実行では失敗が報告されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-123">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="5fc16-124">出力例</span><span class="sxs-lookup"><span data-stu-id="5fc16-124">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="5fc16-125">非同期 Main の戻り値</span><span class="sxs-lookup"><span data-stu-id="5fc16-125">Async Main return values</span></span>

<span data-ttu-id="5fc16-126">非同期 Main の戻り値によって、`Main` 内の非同期メソッドを呼び出すために必要な定型コードを、コンパイラで生成されるコードに移動します。</span><span class="sxs-lookup"><span data-stu-id="5fc16-126">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="5fc16-127">以前のバージョンでは、このコンストラクトを出力して非同期コードを呼び出し、非同期操作が完了するまでプログラムが実行されるようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="5fc16-127">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="5fc16-128">現在のバージョンでは、以下のように書き換えられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5fc16-128">Now, this can be replaced by:</span></span>

<span data-ttu-id="5fc16-129">[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]</span><span class="sxs-lookup"><span data-stu-id="5fc16-129">[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]</span></span>

<span data-ttu-id="5fc16-130">新しい構文を使用すると、コンパイラから常に正しいコードが生成されるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="5fc16-130">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="5fc16-131">コンパイラから生成されるコード</span><span class="sxs-lookup"><span data-stu-id="5fc16-131">Compiler generated code</span></span>

<span data-ttu-id="5fc16-132">アプリケーションのエントリ ポイントから `Task` または `Task<int>` が返されると、コンパイラによって、アプリケーション コードで宣言されたエントリ ポイント メソッドを呼び出す新しいエントリ ポイントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-132">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="5fc16-133">このエントリ ポイント名が `$GeneratedMain` だとすると、これらのエントリ ポイントについて次のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-133">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="5fc16-134">`static Task Main()` の結果、`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-134">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="5fc16-135">`static Task Main(string[])` の結果、`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-135">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="5fc16-136">`static Task<int> Main()` の結果、`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-136">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="5fc16-137">`static Task<int> Main(string[])` の結果、`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-137">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="5fc16-138">この例の `Main` メソッドで `async` 修飾子を使用した場合、同じコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5fc16-138">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fc16-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fc16-139">See also</span></span>
<span data-ttu-id="5fc16-140">[C# プログラミング ガイド](../../programming-guide/index.md)
[C# リファレンス](../index.md)
[Main() とコマンド ライン引数](index.md)
[方法: コマンド ライン引数を表示する](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[方法: foreach を使用してコマンド ライン引数にアクセスする](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span><span class="sxs-lookup"><span data-stu-id="5fc16-140">[C# Programming Guide](../../programming-guide/index.md)
[C# Reference](../index.md)
[Main() and Command-Line Arguments](index.md)
[How to: Display Command Line Arguments](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[How to: Access Command-Line Arguments Using foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span></span>

