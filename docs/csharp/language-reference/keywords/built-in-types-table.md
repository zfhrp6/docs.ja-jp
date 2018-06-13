---
title: 組み込み型の一覧表 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 120347e5bff7f0d6c7120af0cb250936ca39ea16
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172267"
---
# <a name="built-in-types-table-c-reference"></a>組み込み型の一覧表 (C# リファレンス)
次の表は、C# の組み込み型のキーワードを示しています。これは、<xref:System> 名前空間の定義済み型の別名です。  
  
|C# 型|.NET Framework 型|  
|--------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>コメント  
 表内の、`object` と `string` を除くすべての型が、単純型と呼ばれます。  
  
 C# 型のキーワードと別名は相互に交換できます。 たとえば、整数の変数を宣言するには、次のいずれかの宣言を使用します。  
  
```csharp  
int x = 123;  
System.Int32 x = 123;  
```  
  
 C# 型の実際の型を表示するには、`GetType()` システム メソッドを使用します。 たとえば、次のステートメントは、`myVariable` の型を表すシステムの別名を表示します。  
  
```csharp  
Console.WriteLine(myVariable.GetType());  
```  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) 演算子も使用できます。  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [値型](../../../csharp/language-reference/keywords/value-types.md)  
 [既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)  
 [数値結果テーブルの書式設定](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [型のリファレンス表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
