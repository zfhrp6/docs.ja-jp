---
title: "ulong (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
dev_langs:
- CSharp
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 36de0add1d7fdf58745c65d231f3789c532ab69f
ms.lasthandoff: 03/13/2017

---
# <a name="ulong-c-reference"></a>ulong (C# リファレンス)
`ulong` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。  
  
|型|範囲|サイズ|.NET Framework 型|  
|----------|-----------|----------|-------------------------|  
|`ulong`|0 ～ 18,446,744,073,709,551,615|符号なし 64 ビット整数|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a>リテラル  
 `ulong` 変数の宣言と初期化の例を次に示します。  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 サフィックスがない整数リテラルの場合、整数リテラルの型は、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、`ulong` のうち、その値を表すことができる最初の型になります。 上記の例では、これは `ulong` 型です。  
  
 サフィックスを使用して、リテラルの型を次の規則に従って指定することもできます。  
  
-   L または l を使用した場合、リテラル整数の型は、そのサイズに応じて [long](../../../csharp/language-reference/keywords/long.md) または `ulong` になります。  
  
    > [!NOTE]
    >  小文字の "l" はサフィックスとして使用できます。 ただし、文字の "l" は数字の "1" と混同しやすいため、コンパイラから警告が出されます。 明確にするには、"L" を使用します。  
  
-   `U` または `u` を使用した場合、リテラル整数の型は、そのサイズに応じて [uint](../../../csharp/language-reference/keywords/uint.md) または `ulong` になります。  
  
-   UL、ul、Ul、uL、LU、lu、Lu または lU を使用した場合、リテラル整数の型は `ulong` になります。  
  
     たとえば、次の 3 つのステートメントの出力は、システム型 `UInt64` になります。これは、エイリアス `ulong` に対応します。  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
 サフィックスは、オーバー ロードされたメソッドの呼び出しでよく使用されます。 たとえば、`ulong` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 サフィックスを `ulong` パラメーターと共に使用すると、正しい型が呼び出されます。次に例を示します。  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a>変換  
 `ulong` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。  
  
 `ulong` から整数型への暗黙的な変換は行われません。 たとえば、次の代入ステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `ulong` への、定義済みの暗黙的な変換が組み込まれています。  
  
 浮動小数点型から `ulong` への暗黙の型変換はありません。 たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙的な数値変換規則について詳しくは、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.UInt64>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
