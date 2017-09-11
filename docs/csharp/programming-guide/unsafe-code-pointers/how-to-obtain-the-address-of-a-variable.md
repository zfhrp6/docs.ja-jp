---
title: "方法: 変数のアドレスを取得する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 169f68cc80b7a27427a9987942e66e0ba9ed1a02
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="e972a-102">方法: 変数のアドレスを取得する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e972a-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="e972a-103">固定変数に評価される単項式のアドレスを取得するには、address-of 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="e972a-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="e972a-104">address-of 演算子は、変数にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="e972a-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="e972a-105">変数が移動可能な変数である場合、[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)を使用して変数のアドレスを取得する前に、一時的に変数を固定できます。</span><span class="sxs-lookup"><span data-stu-id="e972a-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="e972a-106">ユーザーは変数が初期化されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e972a-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="e972a-107">変数が初期化されていない場合、コンパイラはエラー メッセージを発行しません。</span><span class="sxs-lookup"><span data-stu-id="e972a-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="e972a-108">定数または値のアドレスを取得できません。</span><span class="sxs-lookup"><span data-stu-id="e972a-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e972a-109">例</span><span class="sxs-lookup"><span data-stu-id="e972a-109">Example</span></span>  
 <span data-ttu-id="e972a-110">この例では、`int`、`p` へのポインターを宣言し、整数変数 `number` のアドレスを代入します。</span><span class="sxs-lookup"><span data-stu-id="e972a-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="e972a-111">変数 `number` は *p への代入の結果として初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e972a-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="e972a-112">この代入ステートメントをコメントにする場合は、変数 `number` の初期化が削除されますが、コンパイル時のエラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="e972a-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="e972a-113">ポインターに格納されているアドレスを取得して表示するために、[メンバー アクセス](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)演算子 `->` が使用されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="e972a-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 <span data-ttu-id="e972a-114">[!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e972a-114">[!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]</span></span>  
  
 <span data-ttu-id="e972a-115">[!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e972a-115">[!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e972a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e972a-116">See Also</span></span>  
 <span data-ttu-id="e972a-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e972a-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e972a-118">[ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="e972a-118">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="e972a-119">[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="e972a-119">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="e972a-120">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="e972a-120">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="e972a-121">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="e972a-121">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="e972a-122">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e972a-122">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="e972a-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e972a-123">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

