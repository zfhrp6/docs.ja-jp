---
title: operator (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: d633a46e21f913aa8c05289dccfb63e71efd697e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="operator-c-reference"></a><span data-ttu-id="275c8-102">operator (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="275c8-102">operator (C# Reference)</span></span>
<span data-ttu-id="275c8-103">`operator` キーワードを使用して、組み込みの演算子をオーバーロードしたり、クラスまたは構造体宣言内でユーザー定義の変換を行ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="275c8-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="275c8-104">例</span><span class="sxs-lookup"><span data-stu-id="275c8-104">Example</span></span>  
 <span data-ttu-id="275c8-105">小数を処理する非常に簡単なクラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="275c8-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="275c8-106">このクラスは、小数の加算および乗算を実行するために `+` 演算子および `*` 演算子をオーバーロードします。また、`Fraction` 型を `double` 型に変換する変換演算子も提供します。</span><span class="sxs-lookup"><span data-stu-id="275c8-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="275c8-107">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="275c8-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="275c8-108">参照</span><span class="sxs-lookup"><span data-stu-id="275c8-108">See Also</span></span>  
 [<span data-ttu-id="275c8-109">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="275c8-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="275c8-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="275c8-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="275c8-111">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="275c8-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="275c8-112">implicit</span><span class="sxs-lookup"><span data-stu-id="275c8-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="275c8-113">explicit</span><span class="sxs-lookup"><span data-stu-id="275c8-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="275c8-114">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="275c8-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
