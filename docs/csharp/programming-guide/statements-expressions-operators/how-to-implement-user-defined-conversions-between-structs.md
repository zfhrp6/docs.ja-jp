---
title: "方法 : 構造体間にユーザー定義の変換を実装する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: 11
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
ms.openlocfilehash: cc8856bb3bf8943c1b6648f7d81447a3e59b9489
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="25727-102">方法 : 構造体間にユーザー定義の変換を実装する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="25727-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="25727-103">この例では `RomanNumeral` および `BinaryNumeral` という 2 つの構造体を定義し、それらの間の変換を示します。</span><span class="sxs-lookup"><span data-stu-id="25727-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25727-104">例</span><span class="sxs-lookup"><span data-stu-id="25727-104">Example</span></span>  
 <span data-ttu-id="25727-105">[!code-cs[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="25727-105">[!code-cs[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="25727-106">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="25727-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="25727-107">前述の例では、次のようなステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="25727-107">In the previous example, the statement:</span></span>  
  
     <span data-ttu-id="25727-108">[!code-cs[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="25727-108">[!code-cs[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]</span></span>  
  
     <span data-ttu-id="25727-109">このステートメントでは `RomanNumeral` から `BinaryNumeral` への変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="25727-109">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="25727-110">`RomanNumeral` から `BinaryNumeral` への直接変換はないため、`RomanNumeral` から `int` へ変換するためのキャストと、`int` から `BinaryNumeral` へ変換するためのキャストが使用されています。</span><span class="sxs-lookup"><span data-stu-id="25727-110">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="25727-111">次のようなステートメントもあります。</span><span class="sxs-lookup"><span data-stu-id="25727-111">Also the statement</span></span>  
  
     <span data-ttu-id="25727-112">[!code-cs[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="25727-112">[!code-cs[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]</span></span>  
  
     <span data-ttu-id="25727-113">このステートメントでは `BinaryNumeral` から `RomanNumeral` への変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="25727-113">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="25727-114">`RomanNumeral` は `BinaryNumeral` からの暗黙の型変換を定義しているため、キャストは不要です。</span><span class="sxs-lookup"><span data-stu-id="25727-114">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25727-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="25727-115">See Also</span></span>  
 <span data-ttu-id="25727-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="25727-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="25727-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="25727-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="25727-118">変換演算子</span><span class="sxs-lookup"><span data-stu-id="25727-118">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)

