---
title: "ulong (C# リファレンス) | Microsoft Docs"
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
  - "ulong_CSharpKeyword"
  - "ulong"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ulong キーワード [C#]"
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ulong (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`ulong` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を表します。  
  
|種類|範囲|サイズ|.NET Framework 型|  
|--------|--------|---------|----------------------|  
|`ulong`|0 ～ 18,446,744,073,709,551,615|符号なし 64 ビット整数|<xref:System.UInt64?displayProperty=fullName>|  
  
## リテラル  
 `ulong` 変数の宣言と初期化の例を次に示します。  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 サフィックスがない整数リテラルの型は、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、`ulong` のうち、その整数の値を表すことができる最も範囲の狭い型になります。  上記の例では、`ulong` 型です。  
  
 サフィックスを使用してリテラルの型を指定する場合は、次の規則に従います。  
  
-   L または l を使用した場合、リテラル整数の型は、サイズに応じて [long](../../../csharp/language-reference/keywords/long.md) または `ulong` のいずれかに決まります。  
  
    > [!NOTE]
    >  小文字の "l" をサフィックスとして使用できます。  ただし、文字 "l" は数字の "1" と混同しやすいので、コンパイラから警告が出されます。明確にするには "L" を使用します。  
  
-   `U` または `u` を使用した場合、リテラル整数の型は、サイズに応じて [uint](../../../csharp/language-reference/keywords/uint.md) または `ulong` のいずれかに決まります。  
  
-   UL、ul、Ul、uL、LU、lu、Lu、lU を使用した場合、リテラル整数の型は `ulong` です。  
  
     たとえば、次の 3 つのステートメントの出力は、エイリアス `ulong` に対応したシステム型 `UInt64` になります。  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
 サフィックスは、オーバーロードされたメソッドの呼び出しでよく使われます。  たとえば、`ulong` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用したオーバーロードされたメソッドがあるとします。  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 `ulong` パラメーターでサフィックスを使用すると、正しい型が呼び出されます。次に例を示します。  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## 変換  
 `ulong` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、または [decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。  
  
 `ulong` から整数型への暗黙の型変換はありません。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `ulong` への暗黙の型変換が組み込まれています。  
  
 浮動小数点型から `ulong` への暗黙の型変換はありません。  たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙の数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 <xref:System.UInt64>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)