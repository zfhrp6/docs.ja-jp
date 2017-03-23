---
title: "long (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "long_CSharpKeyword"
  - "long"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "long キーワード [C#]"
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# long (C# リファレンス)
`long` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を表します。  
  
|種類|範囲|サイズ|.NET Framework 型|  
|--------|--------|---------|----------------------|  
|`long`|\-9,223,372,036,854,775,808 ～ 9,223,372,036,854,775,807|符号付き 64 ビット整数|<xref:System.Int64?displayProperty=fullName>|  
  
## リテラル  
 `long` 変数の宣言と初期化の例を次に示します。  
  
```  
  
long long1 = 4294967296;  
```  
  
 サフィックスがない整数リテラルの型は、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、`long`、[ulong](../../../csharp/language-reference/keywords/ulong.md) のうち、その整数の値を表すことができる最も範囲の狭い型になります。  上の例では、[uint](../../../csharp/language-reference/keywords/uint.md) の範囲を超えているので、`long` 型になります。整数型の記憶サイズについては、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください。  
  
 また、`long` 型にサフィックス L を付けることもできます。次に例を示します。  
  
```  
  
long long2 = 4294967296L;  
```  
  
 サフィックス L を使用した場合、リテラル整数の型は、サイズに応じて `long` または [ulong](../../../csharp/language-reference/keywords/ulong.md) のいずれかに決まります。  この例では、[ulong](../../../csharp/language-reference/keywords/ulong.md) の範囲よりも小さいため、`long` になります。  
  
 サフィックスは、オーバーロードされたメソッドの呼び出しでよく使われます。  たとえば、`long` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用したオーバーロードされたメソッドがあるとします。  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 サフィックス L を使用すると、正しい型が呼び出されます。次に例を示します。  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 `long` 型とその他の数値の整数型を同じ式で使用できます。その場合、式は `long` として評価されます。関係式またはブール式の場合は [bool](../../../csharp/language-reference/keywords/bool.md) として評価されます。  `long` として評価される式の例を次に示します。  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  小文字の "l" もサフィックスとして使用できます。  ただし、文字 "l" は数字の "1" と混同しやすいので、コンパイラから警告が出されます。明確にするには "L" を使用します。  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
## 変換  
 `long` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、または [decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。  その他の型の場合は、キャストを使用する必要があります。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `long` への暗黙の型変換が組み込まれています。  
  
 また、浮動小数点型から `long` への暗黙の型変換が行われないことに注意してください。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。  
  
```  
  
        long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.Int64>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)