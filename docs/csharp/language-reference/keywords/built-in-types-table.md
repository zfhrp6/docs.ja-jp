---
title: "組み込み型の一覧表 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9d1e4945526a862074e73e608185696328946be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 C# 型の実際の型を表示するには、`GetType()` システム メソッドを使用します。 たとえば、次のステートメントは、`myVariable` の型を表すシステムの別名を表示します。  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) 演算子も使用できます。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [値型](../../../csharp/language-reference/keywords/value-types.md)  
 [既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)  
 [数値結果テーブルの書式設定](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [型のリファレンス表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
