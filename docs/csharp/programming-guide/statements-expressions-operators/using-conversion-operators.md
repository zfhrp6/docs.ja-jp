---
title: 変換演算子の使用 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: e03fb12200bc15de9c1686edd40921201598621f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-conversion-operators-c-programming-guide"></a>変換演算子の使用 (C# プログラミング ガイド)
より使いやすい `implicit` 変換演算子を使用することもできますし、型を変換していることをコードを読むすべての人に明確に示すために `explicit` 変換演算子を使用することもできます。 このトピックでは、両方の型変換演算子を示します。  
  
> [!NOTE]
>  単純な型変換については、「[方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)」、「[方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)」、「[方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)」、または「<xref:System.Convert>」を参照してください。  
  
## <a name="example"></a>例  
 ここでは、明示的な変換演算子の例を示します。 この演算子は、<xref:System.Byte> 型を `Digit` という値型に変換します。 すべての byte 型を Digit 型に変換できるとは限らないため、変換は明示的に行うように指定されています。つまり、`Main` メソッドに示すように、キャストを使用する必要があります。  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a>例  
 この例は、上の例で行った処理を元に戻す変換演算子を定義することにより、暗黙の変換演算子を示しています。この例では、`Digit` という値クラスを整数 <xref:System.Byte> 型に変換します。 すべての Digit 型を <xref:System.Byte> に変換できるため、変換をユーザーに明示する必要はありません。  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [is](../../../csharp/language-reference/keywords/is.md)
