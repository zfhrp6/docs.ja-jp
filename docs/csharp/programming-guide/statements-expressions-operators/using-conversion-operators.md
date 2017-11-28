---
title: "変換演算子の使用 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a43332df795d853c3060a604360adeaea5e3fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="b02d6-102">変換演算子の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b02d6-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="b02d6-103">より使いやすい `implicit` 変換演算子を使用することもできますし、型を変換していることをコードを読むすべての人に明確に示すために `explicit` 変換演算子を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b02d6-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="b02d6-104">このトピックでは、両方の型変換演算子を示します。</span><span class="sxs-lookup"><span data-stu-id="b02d6-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b02d6-105">単純な型変換については、「[方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)」、「[方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)」、「[方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)」、または「<xref:System.Convert>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b02d6-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b02d6-106">例</span><span class="sxs-lookup"><span data-stu-id="b02d6-106">Example</span></span>  
 <span data-ttu-id="b02d6-107">ここでは、明示的な変換演算子の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b02d6-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="b02d6-108">この演算子は、<xref:System.Byte> 型を `Digit` という値型に変換します。</span><span class="sxs-lookup"><span data-stu-id="b02d6-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="b02d6-109">すべての byte 型を Digit 型に変換できるとは限らないため、変換は明示的に行うように指定されています。つまり、`Main` メソッドに示すように、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b02d6-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="b02d6-110">例</span><span class="sxs-lookup"><span data-stu-id="b02d6-110">Example</span></span>  
 <span data-ttu-id="b02d6-111">この例は、上の例で行った処理を元に戻す変換演算子を定義することにより、暗黙の変換演算子を示しています。この例では、`Digit` という値クラスを整数 <xref:System.Byte> 型に変換します。</span><span class="sxs-lookup"><span data-stu-id="b02d6-111">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="b02d6-112">すべての Digit 型を <xref:System.Byte> に変換できるため、変換をユーザーに明示する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b02d6-112">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b02d6-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b02d6-113">See Also</span></span>  
 [<span data-ttu-id="b02d6-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b02d6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b02d6-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b02d6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b02d6-116">変換演算子</span><span class="sxs-lookup"><span data-stu-id="b02d6-116">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [<span data-ttu-id="b02d6-117">is</span><span class="sxs-lookup"><span data-stu-id="b02d6-117">is</span></span>](../../../csharp/language-reference/keywords/is.md)
