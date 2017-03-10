---
title: "int (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "int_CSharpKeyword"
  - "int"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "int キーワード [C#]"
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# int (C# リファレンス)
`int` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。  
  
|型|範囲|サイズ|.NET Framework 型|既定値|  
|-------|--------|---------|----------------------|---------|  
|`int`|\-2,147,483,648 ～ 2,147,483,647。|符号付き 32 ビット整数|<xref:System.Int32?displayProperty=fullName>|0|  
  
## リテラル  
 `int` 型の変数の宣言と初期化の例を次に示します。  
  
```  
  
int i = 123;  
```  
  
 サフィックスがない整数リテラルの型は、`int`、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) のうち、その整数の値を表すことができる最も範囲の狭い型になります。  この例では、`int` 型です。  
  
## 変換  
 `int` から [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。  次に例を示します。  
  
```  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `int` への暗黙の型変換が組み込まれています。  たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。  
  
```  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 また、浮動小数点型から `int` への暗黙の型変換が行われないことに注意してください。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。  
  
```  
  
        int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float \(C\# リファレンス\)](../../../csharp/language-reference/keywords/float.md)」と「[double \(C\# リファレンス\)](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.Int32>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)