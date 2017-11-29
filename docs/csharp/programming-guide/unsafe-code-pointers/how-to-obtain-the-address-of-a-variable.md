---
title: "方法: 変数のアドレスを取得する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="87966-102">方法: 変数のアドレスを取得する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="87966-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="87966-103">固定変数に評価される単項式のアドレスを取得するには、address-of 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="87966-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="87966-104">address-of 演算子は、変数にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="87966-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="87966-105">変数が移動可能な変数である場合、[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)を使用して変数のアドレスを取得する前に、一時的に変数を固定できます。</span><span class="sxs-lookup"><span data-stu-id="87966-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="87966-106">ユーザーは変数が初期化されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87966-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="87966-107">変数が初期化されていない場合、コンパイラはエラー メッセージを発行しません。</span><span class="sxs-lookup"><span data-stu-id="87966-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="87966-108">定数または値のアドレスを取得できません。</span><span class="sxs-lookup"><span data-stu-id="87966-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87966-109">例</span><span class="sxs-lookup"><span data-stu-id="87966-109">Example</span></span>  
 <span data-ttu-id="87966-110">この例では、`int`、`p` へのポインターを宣言し、整数変数 `number` のアドレスを代入します。</span><span class="sxs-lookup"><span data-stu-id="87966-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="87966-111">変数 `number` は *p への代入の結果として初期化されます。</span><span class="sxs-lookup"><span data-stu-id="87966-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="87966-112">この代入ステートメントをコメントにする場合は、変数 `number` の初期化が削除されますが、コンパイル時のエラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="87966-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="87966-113">ポインターに格納されているアドレスを取得して表示するために、[メンバー アクセス](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)演算子 `->` が使用されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="87966-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="87966-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="87966-114">See Also</span></span>  
 [<span data-ttu-id="87966-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="87966-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="87966-116">ポインター式</span><span class="sxs-lookup"><span data-stu-id="87966-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="87966-117">ポインター型</span><span class="sxs-lookup"><span data-stu-id="87966-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="87966-118">型</span><span class="sxs-lookup"><span data-stu-id="87966-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="87966-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="87966-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="87966-120">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="87966-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="87966-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="87966-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
