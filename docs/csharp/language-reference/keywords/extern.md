---
title: extern 修飾子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: aca1a9fa0b57e9b3b0a515a805039ade2fe0c2f1
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027916"
---
# <a name="extern-c-reference"></a><span data-ttu-id="db7f2-102">extern (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="db7f2-102">extern (C# Reference)</span></span>

<span data-ttu-id="db7f2-103">`extern` 修飾子は、外部で実装されるメソッドを宣言するために使用します。</span><span class="sxs-lookup"><span data-stu-id="db7f2-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="db7f2-104">`extern` 修飾子は一般に、相互運用サービスを使用してアンマネージ コードを呼び出すときに、`DllImport` 属性と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="db7f2-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="db7f2-105">この場合、次の例に示すように、メソッドを `static` として宣言する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="db7f2-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="db7f2-106">`extern` キーワードでは、外部アセンブリのエイリアスも定義できます。これにより、単一アセンブリ内から 1 つのコンポーネントの複数バージョンを参照できます。</span><span class="sxs-lookup"><span data-stu-id="db7f2-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="db7f2-107">詳細については、「[extern エイリアス](extern-alias.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db7f2-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="db7f2-108">[abstract](abstract.md) 修飾子および `extern` 修飾子を一緒に使用して同一のメンバーを修飾すると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="db7f2-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="db7f2-109">`extern` 修飾子を使用すると、メソッドが C# コードの外部で実装されていることを意味します。一方、`abstract` 修飾子を使用すると、メソッドの実装がクラスには用意されていないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="db7f2-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="db7f2-110">extern キーワードの C# での用法は、C++ の場合よりも制限されています。</span><span class="sxs-lookup"><span data-stu-id="db7f2-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="db7f2-111">C# のキーワードと C++ のキーワードを比較するには、C++ 言語リファレンスの「extern を使用したリンケージの指定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db7f2-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="db7f2-112">例 1</span><span class="sxs-lookup"><span data-stu-id="db7f2-112">Example 1</span></span>

<span data-ttu-id="db7f2-113">この例では、ユーザーの入力したメッセージをプログラムが受け取って、メッセージ ボックスに表示します。</span><span class="sxs-lookup"><span data-stu-id="db7f2-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="db7f2-114">このプログラムは、User32.dll ライブラリからインポートされた `MessageBox` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="db7f2-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="db7f2-115">例 2</span><span class="sxs-lookup"><span data-stu-id="db7f2-115">Example 2</span></span>

<span data-ttu-id="db7f2-116">この例は、C ライブラリ (ネイティブ DLL) を呼び出す C# プログラムを示しています。</span><span class="sxs-lookup"><span data-stu-id="db7f2-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="db7f2-117">次の C ファイルを作成し、`cmdll.c` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="db7f2-117">Create the following C file and name it `cmdll.c`:</span></span>

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. <span data-ttu-id="db7f2-118">Visual Studio のインストール ディレクトリから Visual Studio x64 (または x32) Native Tools コマンド プロンプト ウィンドウを開き、コマンド プロンプトで「**cl -LD cmdll.c**」と入力して、`cmdll.c` ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="db7f2-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="db7f2-119">同じディレクトリに、次の C# ファイルを作成し、`cm.cs` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="db7f2-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

```csharp
// cm.cs
using System;
using System.Runtime.InteropServices;
public class MainClass
{
    [DllImport("Cmdll.dll")]
      public static extern int SampleMethod(int x);

    static void Main()
    {
        Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
    }
}
```

4. <span data-ttu-id="db7f2-120">Visual Studio のインストール ディレクトリから Visual Studio x64 (または x32) Native Tools コマンド プロンプト ウィンドウを開き、次のように入力して `cm.cs` ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="db7f2-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

> <span data-ttu-id="db7f2-121">**csc cm.cs** (x64 コマンド プロンプトの場合) または **csc -platform:x86 cm.cs** (x32 コマンド プロンプトの場合)</span><span class="sxs-lookup"><span data-stu-id="db7f2-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

<span data-ttu-id="db7f2-122">これで、実行可能ファイル `cm.exe` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="db7f2-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="db7f2-123">`cm.exe` を実行します。</span><span class="sxs-lookup"><span data-stu-id="db7f2-123">Run `cm.exe`.</span></span> <span data-ttu-id="db7f2-124">`SampleMethod` メソッドは、DLL ファイルに値 5 を渡します。DLL は 10 で乗算した値を返します。</span><span class="sxs-lookup"><span data-stu-id="db7f2-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="db7f2-125">このプログラムの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="db7f2-125">The program produces the following output:</span></span>

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a><span data-ttu-id="db7f2-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="db7f2-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="db7f2-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="db7f2-127">See also</span></span>

<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
[<span data-ttu-id="db7f2-128">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="db7f2-128">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="db7f2-129">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="db7f2-129">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="db7f2-130">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="db7f2-130">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="db7f2-131">修飾子</span><span class="sxs-lookup"><span data-stu-id="db7f2-131">Modifiers</span></span>](modifiers.md)  