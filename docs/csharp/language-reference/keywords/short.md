---
title: "short (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "short"
  - "short_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "short キーワード [C#]"
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# short (C# リファレンス)
`short` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数データ型を示します。  
  
|種類|範囲|サイズ|.NET Framework 型|  
|--------|--------|---------|----------------------|  
|`short`|\-32,768 ～ 32,767。|符号付き 16 ビット整数|<xref:System.Int16?displayProperty=fullName>|  
  
## リテラル  
 `short` 変数の宣言と初期化の例を次に示します。  
  
```  
  
short x = 32767;  
```  
  
 上のように宣言すると、整数リテラル `32767` は暗黙的に [int](../../../csharp/language-reference/keywords/int.md) から `short` に変換されます。  整数リテラルを `short` の格納場所に格納できない場合は、コンパイル エラーになります。  
  
 オーバーロードされたメソッドを呼び出す場合は、キャストを使用する必要があります。  たとえば、`short` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用したオーバーロードされたメソッドがあるとします。  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 `short` キャストを使用すると、正しい型が呼び出されます。次に例を示します。  
  
```  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## 変換  
 `short` から [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。  
  
 記憶サイズがより大きいリテラル以外の数値型は、`short` への暗黙の型変換ができません。整数型の記憶サイズについては、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください。  たとえば、2 つの `short` 変数 `x` と `y` があるとします。  
  
```  
  
short x = 5, y = 12;  
```  
  
 次の代入ステートメントは、代入演算子の右側にある算術式が既定で [int](../../../csharp/language-reference/keywords/int.md)に評価されるため、コンパイル エラーになります。  
  
 `short`   `z = x + y;   // Error: no conversion from int to short`  
  
 このエラーを修正するには、キャストを使用します。  
  
 `short`   `z = (`  `short`  `)(x + y);   // OK: explicit conversion`  
  
 ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶サイズは元のサイズ以上になります。  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 浮動小数点型から `short` への暗黙の型変換はありません。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。  
  
```  
  
        short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙の数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.Int16>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)