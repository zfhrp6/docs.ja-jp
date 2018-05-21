---
title: 匿名関数 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 51a3c2e8399fdaae19ebe33f0d9ecc4bfd598799
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="11e4c-102">匿名関数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="11e4c-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="11e4c-103">匿名関数は、デリゲート型が必要とされる任意の場所で使用できる "インライン" のステートメントまたは式です。</span><span class="sxs-lookup"><span data-stu-id="11e4c-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="11e4c-104">名前付きデリゲートを初期化するときや、メソッドのパラメーターとして名前付きデリゲート型の代わりに渡したりするときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="11e4c-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="11e4c-105">ここでは、2 種類ある匿名関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="11e4c-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="11e4c-106">[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="11e4c-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="11e4c-107">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="11e4c-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="11e4c-108">ラムダ式は、式ツリーとデリゲートにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="11e4c-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="11e4c-109">C# のデリゲートの進化</span><span class="sxs-lookup"><span data-stu-id="11e4c-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="11e4c-110">C# 1.0 では、コードのどこかで定義したメソッドを使用して明示的に初期化することで、デリゲートのインスタンスを作成していました。</span><span class="sxs-lookup"><span data-stu-id="11e4c-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="11e4c-111">C# 2.0 では、デリゲートの呼び出しで実行できる名前なしのインライン ステートメント ブロックを記述する方法として、匿名メソッドの概念が導入されました。</span><span class="sxs-lookup"><span data-stu-id="11e4c-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="11e4c-112">C# 3.0 では、ラムダ式が導入されました。ラムダ式は、概念的には匿名メソッドと似ていますが、より表現力が豊かで簡潔です。</span><span class="sxs-lookup"><span data-stu-id="11e4c-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="11e4c-113">これら 2 つの機能は総称として*匿名関数*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="11e4c-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="11e4c-114">一般的に、バージョン 3.5 以降の [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] をターゲットとするアプリケーションであれば、ラムダ式を使用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="11e4c-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="11e4c-115">次の例は、C# 1.0 から C# 3.0 のデリゲート作成の進化を示しています。</span><span class="sxs-lookup"><span data-stu-id="11e4c-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="11e4c-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="11e4c-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="11e4c-117">参照</span><span class="sxs-lookup"><span data-stu-id="11e4c-117">See Also</span></span>  
 [<span data-ttu-id="11e4c-118">ステートメント、式、および演算子</span><span class="sxs-lookup"><span data-stu-id="11e4c-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [<span data-ttu-id="11e4c-119">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="11e4c-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="11e4c-120">デリゲート</span><span class="sxs-lookup"><span data-stu-id="11e4c-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="11e4c-121">式ツリー</span><span class="sxs-lookup"><span data-stu-id="11e4c-121">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
