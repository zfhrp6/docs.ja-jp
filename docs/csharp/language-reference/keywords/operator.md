---
title: "operator (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
dev_langs:
- CSharp
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
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
ms.openlocfilehash: 76d403493861e9c587672412cd2989c419b8717a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="operator-c-reference"></a><span data-ttu-id="c257f-102">operator (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c257f-102">operator (C# Reference)</span></span>
<span data-ttu-id="c257f-103">`operator` キーワードを使用して、組み込みの演算子をオーバーロードしたり、クラスまたは構造体宣言内でユーザー定義の変換を行ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c257f-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c257f-104">例</span><span class="sxs-lookup"><span data-stu-id="c257f-104">Example</span></span>  
 <span data-ttu-id="c257f-105">小数を処理する非常に簡単なクラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c257f-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="c257f-106">このクラスは、小数の加算および乗算を実行するために + 演算子および * 演算子をオーバーロードします。また、小数型を倍精度浮動小数点型に変換する変換演算子も提供します。</span><span class="sxs-lookup"><span data-stu-id="c257f-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 <span data-ttu-id="c257f-107">[!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c257f-107">[!code-cs[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c257f-108">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c257f-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c257f-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c257f-109">See Also</span></span>  
 <span data-ttu-id="c257f-110">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c257f-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c257f-111">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c257f-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c257f-112">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c257f-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c257f-113">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="c257f-113">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="c257f-114">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="c257f-114">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 [<span data-ttu-id="c257f-115">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="c257f-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

