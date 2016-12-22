---
title: "値型 (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.valuetypes"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 値型"
  - "型 [C#], 値型"
  - "値型 [C#]"
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 値型 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

値型は、次の 2 つの主要カテゴリで構成されます。  
  
-   [構造体](../../../csharp/language-reference/keywords/struct.md)  
  
-   [列挙型](../../../csharp/language-reference/keywords/enum.md)  
  
 構造体は、次のカテゴリに分類されます。  
  
-   数値型  
  
    -   [整数型](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [浮動小数点型](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   ユーザー定義の struct 型。  
  
## 値型の主な機能  
 値型に基づく変数は、値を直接含みます。  ある値型の変数を別の変数に代入すると、含まれている値がコピーされます。  これは参照型の変数の代入とは異なります。参照型の変数の代入では、オブジェクト自体ではなく、オブジェクトへの参照がコピーされます。  
  
 すべての値型は、<xref:System.ValueType?displayProperty=fullName> から暗黙的に派生します。  
  
 参照型とは異なり、値型から新しい型を派生させることができません。  ただし、参照型と同様に、struct 型はインターフェイスを実装できます。  
  
 参照型とは異なり、値型には `null` 値を含めることはできません。  ただし、[&#91;Null 許容型&#93;](../../../csharp/programming-guide/nullable-types/index.md) の機能は、値型が `null`に割り当てることができます。  
  
 それぞれの値型には、その型の既定値を初期化する既定のコンストラクターが暗黙的に存在します。  値型の既定値の詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
## 単純型の主な機能  
 C\# 言語に不可欠なすべての単純型は、.NET Framework System 型のエイリアスです。  たとえば、[int](../../../csharp/language-reference/keywords/int.md) は <xref:System.Int32?displayProperty=fullName> のエイリアスです。  すべてのエイリアスの一覧については、「[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)」を参照してください。  
  
 定数式のオペランドがすべて単純型の定数である場合、定数式はコンパイル時に評価されます。  
  
 単純型は、リテラルを使用して初期化できます。  たとえば、'A' は `char` 型のリテラルであり、2001 は `int` 型のリテラルです。  
  
## 値型の初期化  
 C\# のローカル変数は、使用する前に初期化する必要があります。  たとえば、次の例のように、初期化せずにローカル変数を宣言するとします。  
  
```  
int myInt;  
```  
  
 この変数は、初期化した後でないと使用できません。  初期化するには、次のステートメントを使用します。  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 このステートメントは、次のステートメントと同等です。  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 次の例のように、宣言と初期化を 1 つのステートメントで行うことができます。  
  
```  
int myInt = new int();  
```  
  
 または  
  
```  
int myInt = 0;  
```  
  
 [new](../../../csharp/language-reference/keywords/new.md) 演算子を使用すると、それぞれの型の既定のコンストラクターが呼び出され、既定値が変数に代入されます。  前の例では、既定のコンストラクターが `myInt` に値 `0` を代入します。  既定のコンストラクターによる値の代入の詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
 ユーザー定義型の場合は、[new](../../../csharp/language-reference/keywords/new.md) を使用して既定のコンストラクターを呼び出します。  たとえば、`Point` struct の既定のコンストラクターを呼び出すステートメントは、次のとおりです。  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 既定のコンストラクターが呼び出されると、struct は明示的に代入するものと見なされ、すべてのメンバーがそれぞれの既定値に初期化されます。  
  
 new 演算子の詳細については、「[new](../../../csharp/language-reference/keywords/new.md)」を参照してください。  
  
 数値型の出力書式の詳細については、「[数値結果の書式指定の一覧表](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [型のリファレンス表](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)