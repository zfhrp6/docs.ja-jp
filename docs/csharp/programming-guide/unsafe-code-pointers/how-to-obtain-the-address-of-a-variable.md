---
title: '方法: 変数のアドレスを取得する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bb52aee3341194697b40b30ec14afced61a200be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340126"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="5b59b-102">方法: 変数のアドレスを取得する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5b59b-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="5b59b-103">固定変数に評価される単項式のアドレスを取得するには、address-of 演算子 `&` を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b59b-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="5b59b-104">address-of 演算子は、変数にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="5b59b-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="5b59b-105">変数が移動可能な変数である場合、[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)を使用して変数のアドレスを取得する前に、一時的に変数を固定できます。</span><span class="sxs-lookup"><span data-stu-id="5b59b-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="5b59b-106">ユーザーは変数が初期化されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b59b-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="5b59b-107">変数が初期化されていない場合、コンパイラはエラー メッセージを発行しません。</span><span class="sxs-lookup"><span data-stu-id="5b59b-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="5b59b-108">定数または値のアドレスを取得できません。</span><span class="sxs-lookup"><span data-stu-id="5b59b-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b59b-109">例</span><span class="sxs-lookup"><span data-stu-id="5b59b-109">Example</span></span>  
 <span data-ttu-id="5b59b-110">この例では、`int`、`p` へのポインターを宣言し、整数変数 `number` のアドレスを代入します。</span><span class="sxs-lookup"><span data-stu-id="5b59b-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="5b59b-111">変数 `number` は `*p` への代入の結果として初期化されます。</span><span class="sxs-lookup"><span data-stu-id="5b59b-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="5b59b-112">この代入ステートメントをコメント アウトする場合は、変数 `number` の初期化が削除されますが、コンパイル時のエラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="5b59b-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="5b59b-113">[`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを指定してこの例をコンパイルしてください。</span><span class="sxs-lookup"><span data-stu-id="5b59b-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="5b59b-114">参照</span><span class="sxs-lookup"><span data-stu-id="5b59b-114">See Also</span></span>  
 [<span data-ttu-id="5b59b-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5b59b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5b59b-116">ポインター式</span><span class="sxs-lookup"><span data-stu-id="5b59b-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="5b59b-117">ポインター型</span><span class="sxs-lookup"><span data-stu-id="5b59b-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="5b59b-118">型</span><span class="sxs-lookup"><span data-stu-id="5b59b-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="5b59b-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="5b59b-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="5b59b-120">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="5b59b-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="5b59b-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5b59b-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
