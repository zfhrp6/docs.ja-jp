---
title: "uint (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "uint"
  - "uint_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "uint キーワード [C#]"
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# uint (C# リファレンス)
`uint` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を表します。  
  
|種類|範囲|サイズ|.NET Framework 型|  
|--------|--------|---------|----------------------|  
|`uint`|0 ～ 4,294,967,295|符号なし 32 ビット整数|<xref:System.UInt32?displayProperty=fullName>|  
  
 **メモ** `uint` 型は CLS に準拠していません。  できるだけ `int` を使用します。  
  
## リテラル  
 `uint` 型の変数の宣言と初期化の例を次に示します。  
  
```  
  
uint myUint = 4294967290;  
```  
  
 サフィックスがない整数リテラルの型は、[int](../../../csharp/language-reference/keywords/int.md)、`uint`、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) のうち、その整数の値を表すことができる最も範囲の狭い型になります。  この例では、`uint` です。  
  
```  
  
uint uInt1 = 123;  
```  
  
 また、サフィックス u または U を使用することもできます。次に例を示します。  
  
```  
  
uint uInt2 = 123U;  
```  
  
 サフィックス `U` または `u` を使用すると、リテラルの型は、リテラルの数値に応じて `uint` または `ulong` のいずれかに決まります。  次に例を示します。  
  
```  
Console.WriteLine(44U.GetType());  
Console.WriteLine(323442434344U.GetType());  
```  
  
 このコードでは、2 番目のリテラルが `uint` 型で格納するには大きすぎるため、`System.UInt32`、`System.UInt64` の順に表示します。これはそれぞれ、`uint` および `ulong` の基になる型です。  
  
## 変換  
 `uint` から [long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、または [decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。  次に例を示します。  
  
```  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `uint` への暗黙の型変換が組み込まれています。  その他の型の場合は、キャストを使用する必要があります。  たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。  
  
```  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 また、浮動小数点型から `uint` への暗黙の型変換が行われないことに注意してください。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。  
  
```  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float \(C\# リファレンス\)](../../../csharp/language-reference/keywords/float.md)」と「[double \(C\# リファレンス\)](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙の数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.UInt32>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)