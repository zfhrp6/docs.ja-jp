---
title: "Main() とコマンドライン引数 (C# プログラミング ガイド)"
ms.date: 2017-08-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
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
ms.openlocfilehash: 51408654abd0dcd2f7159438b507c44bd579bfd9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="0cfa7-102">Main() とコマンドライン引数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="0cfa7-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="0cfa7-103">`Main` メソッドは、C# アプリケーションのエントリ ポイントです</span><span class="sxs-lookup"><span data-stu-id="0cfa7-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="0cfa7-104">(ライブラリおよびサービスでは、エントリ ポイントとしての `Main` メソッドは必要ありません)。アプリケーションを起動すると、最初に `Main` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="0cfa7-105">C# プログラムのエントリ ポイントは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="0cfa7-106">`Main` メソッドを持つクラスが 2 つ以上ある場合、プログラムをコンパイルする際に **/main** コンパイラ オプションを使用して、どの `Main` メソッドをエントリ ポイントとして使用するかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="0cfa7-107">詳細については、「[/main (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 <span data-ttu-id="0cfa7-108">[!code-cs[csProgGuideMain 17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0cfa7-108">[!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]</span></span>

## <a name="overview"></a><span data-ttu-id="0cfa7-109">概要</span><span class="sxs-lookup"><span data-stu-id="0cfa7-109">Overview</span></span>

- <span data-ttu-id="0cfa7-110">`Main` メソッドは実行可能プログラムのエントリ ポイントであり、ここでプログラムの制御を開始および終了します。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-110">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="0cfa7-111">`Main` は、クラスまたは構造体の内部で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-111">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="0cfa7-112">`Main` は [static](../../../csharp/language-reference/keywords/static.md) である必要がありますが、[public](../../../csharp/language-reference/keywords/public.md) である必要はありません</span><span class="sxs-lookup"><span data-stu-id="0cfa7-112">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="0cfa7-113">(先ほどの例では、既定の [private](../../../csharp/language-reference/keywords/private.md) のアクセスを受け取ります)。外側のクラスまたは構造体は、static である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-113">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="0cfa7-114">`Main` の戻り値の型は、`void` または `int` のいずれかになります。C# 7.1 以降では `Task` または `Task<int>` になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-114">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="0cfa7-115">`Main` で `Task` または `Task<int>` が返される場合に限り、`Main` の宣言に [`async`](../../language-reference/keywords/async.md) 修飾子を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-115">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="0cfa7-116">この条件により、`async void Main` メソッドが明確に除外されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-116">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="0cfa7-117">`Main` メソッドを宣言する際、コマンドライン引数を含む `string[]` パラメーターは指定してもしなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-117">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="0cfa7-118">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] を使用して Windows アプリケーションを作成する場合、このパラメーターを手動で追加するか <xref:System.Environment> クラスを使用して、コマンドライン引数を取得できます。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-118">When using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="0cfa7-119">パラメーターは、インデックス 0 のコマンドライン引数として読み取られます。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-119">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="0cfa7-120">C や C++ とは異なり、プログラムの名前が最初のコマンドライン引数として扱われることはありません。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-120">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="0cfa7-121">コンソール アプリケーションの `Main` で `await` を使用して非同期操作を開始する必要がある場合、戻り値の型 `async`、`Task`、`Task<int>` を追加することでプログラム コードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="0cfa7-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0cfa7-122">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0cfa7-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0cfa7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cfa7-123">See also</span></span>
<span data-ttu-id="0cfa7-124">[csc.exe を使用したコマンドラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)
[インサイド C# プログラム](../../../csharp/programming-guide/inside-a-program/index.md)</span><span class="sxs-lookup"><span data-stu-id="0cfa7-124">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[C# Programming Guide](../../../csharp/programming-guide/index.md)
[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md)
[Inside a C# Program](../../../csharp/programming-guide/inside-a-program/index.md)</span></span>

