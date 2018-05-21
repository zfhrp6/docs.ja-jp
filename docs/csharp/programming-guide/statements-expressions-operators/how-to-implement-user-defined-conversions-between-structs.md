---
title: '方法 : 構造体間にユーザー定義の変換を実装する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 178d9e2f92c5c1989253a16d866052a1fc42c10e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="06d27-102">方法 : 構造体間にユーザー定義の変換を実装する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="06d27-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="06d27-103">この例では `RomanNumeral` および `BinaryNumeral` という 2 つの構造体を定義し、それらの間の変換を示します。</span><span class="sxs-lookup"><span data-stu-id="06d27-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06d27-104">例</span><span class="sxs-lookup"><span data-stu-id="06d27-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="06d27-105">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="06d27-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="06d27-106">前述の例では、次のようなステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="06d27-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="06d27-107">このステートメントでは `RomanNumeral` から `BinaryNumeral` への変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="06d27-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="06d27-108">`RomanNumeral` から `BinaryNumeral` への直接変換はないため、`RomanNumeral` から `int` へ変換するためのキャストと、`int` から `BinaryNumeral` へ変換するためのキャストが使用されています。</span><span class="sxs-lookup"><span data-stu-id="06d27-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="06d27-109">次のようなステートメントもあります。</span><span class="sxs-lookup"><span data-stu-id="06d27-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="06d27-110">このステートメントでは `BinaryNumeral` から `RomanNumeral` への変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="06d27-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="06d27-111">`RomanNumeral` は `BinaryNumeral` からの暗黙の型変換を定義しているため、キャストは不要です。</span><span class="sxs-lookup"><span data-stu-id="06d27-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d27-112">参照</span><span class="sxs-lookup"><span data-stu-id="06d27-112">See Also</span></span>  
 [<span data-ttu-id="06d27-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="06d27-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="06d27-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="06d27-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="06d27-115">変換演算子</span><span class="sxs-lookup"><span data-stu-id="06d27-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
