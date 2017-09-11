---
title: "return (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
dev_langs:
- CSharp
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
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
ms.openlocfilehash: 596375a1cba8f5ecbad636a6829c1a0599f8c0f4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="return-c-reference"></a><span data-ttu-id="f5cec-102">return (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f5cec-102">return (C# Reference)</span></span>
<span data-ttu-id="f5cec-103">`return` ステートメントは、メソッドの実行を終了し、呼び出し側のメソッドに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="f5cec-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="f5cec-104">省略可能な値を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="f5cec-104">It can also return an optional value.</span></span> <span data-ttu-id="f5cec-105">メソッドが `void` 型の場合、`return` ステートメントは省略できます。</span><span class="sxs-lookup"><span data-stu-id="f5cec-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="f5cec-106">return ステートメントが `try` ブロック内にある場合は、制御が呼び出し側のメソッドに返される前に、`finally` ブロック (存在する場合) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="f5cec-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cec-107">例</span><span class="sxs-lookup"><span data-stu-id="f5cec-107">Example</span></span>  
 <span data-ttu-id="f5cec-108">次の例では、メソッド `A()` が変数 `Area` を [double](../../../csharp/language-reference/keywords/double.md) 値として返します。</span><span class="sxs-lookup"><span data-stu-id="f5cec-108">In the following example, the method `A()` returns the variable `Area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 <span data-ttu-id="f5cec-109">[!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5cec-109">[!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f5cec-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f5cec-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5cec-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5cec-111">See Also</span></span>  
 <span data-ttu-id="f5cec-112">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5cec-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f5cec-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5cec-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f5cec-114">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5cec-114">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f5cec-115">[return ステートメント](/cpp/cpp/return-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="f5cec-115">[return Statement](/cpp/cpp/return-statement-cpp) </span></span>  
 [<span data-ttu-id="f5cec-116">ジャンプ ステートメント</span><span class="sxs-lookup"><span data-stu-id="f5cec-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)

