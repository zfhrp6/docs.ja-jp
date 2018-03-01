---
title: "値型 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 281b811f2a8a1f2c364405b563f9f103899b492c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-c-reference"></a>値型 (C# リファレンス)
値型は、次の 2 つの主要なカテゴリで構成されます。  
  
-   [構造体](../../../csharp/language-reference/keywords/struct.md)  
  
-   [列挙型](../../../csharp/language-reference/keywords/enum.md)  
  
 構造体は、次のカテゴリに分類されます。  
  
-   数値型  
  
    -   [整数型](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [浮動小数点型](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   ユーザー定義の構造体  
  
## <a name="main-features-of-value-types"></a>値型の主な機能  
 値型に基づく変数には、値が直接含まれます。 ある値型の変数を別の変数に代入することで、含まれている値がコピーされます。 これは、オブジェクトそのものではなく、参照をオブジェクトにコピーする、参照型の変数の代入とは異なります。  
  
 すべての値型が <xref:System.ValueType?displayProperty=nameWithType> から暗黙的に派生されます。  
  
 参照型とは異なり、値型から新しい型を派生することはできません。 ただし、参照型の場合と同様に、構造体はインターフェイスを実装できます。  
  
 参照型とは異なり、値型に `null` 値を含めることはできません。 ただし、[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)機能では、値型の `null` への代入が許可されます。  
  
 各値型には、その型の既定値を初期化する暗黙の既定のコンストラクターがあります。 値型の既定値の詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
## <a name="main-features-of-simple-types"></a>単純型の主な機能  
 C# 言語に不可欠なすべての単純型は、.NET Framework システム型のエイリアスです。 たとえば、[int](../../../csharp/language-reference/keywords/int.md) は <xref:System.Int32?displayProperty=nameWithType> のエイリアスです。 エイリアスの完全な一覧については、「[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)」を参照してください。  
  
 オペランドがすべて単純型の定数式は、コンパイル時に評価されます。  
  
 単純型はリテラルを使用して初期化できます。 たとえば、'A' は `char` 型のリテラルで、2001 は `int` 型のリテラルです。  
  
## <a name="initializing-value-types"></a>値型の初期化  
 C# では、ローカル変数を使用する前に初期化する必要があります。 たとえば、次の例のように、初期化せずにローカル変数を宣言した場合、  
  
```  
int myInt;  
```  
  
 初期化してからでないとこれを使用することはできません。 次のステートメントを使用して初期化できます。  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 このステートメントは、次のステートメントと同じです。  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 もちろん、次の例のように、宣言と初期化を同じステートメントに含めることができます。  
  
```  
int myInt = new int();  
```  
  
 または  
  
```  
int myInt = 0;  
```  
  
 [new](../../../csharp/language-reference/keywords/new.md) 演算子を使用すると、特定の型の既定のコンストラクターを呼び出し、既定値を変数に代入します。 前の例では、既定のコンス トラクターが値 `0` を `myInt` に代入しました。 既定のコンストラクターの呼び出しにより値を代入する詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
 ユーザー定義型では、[new](../../../csharp/language-reference/keywords/new.md) を使用して既定のコンストラクターを呼び出します。 たとえば、次のステートメントは、`Point` 構造体の既定のコンストラクターを呼び出します。  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 この呼び出しの後、構造体は明示的に代入されると見なされます。つまり、すべてのメンバーがその既定値に初期化されます。  
  
 new 演算子の詳細については、「[new](../../../csharp/language-reference/keywords/new.md)」を参照してください。  
  
 数値型の出力の書式設定については、「[数値結果テーブルの書式設定](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [型](../../../csharp/language-reference/keywords/types.md)  
 [型のリファレンス表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)
