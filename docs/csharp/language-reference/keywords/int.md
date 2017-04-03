---
title: "int (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
dev_langs:
- CSharp
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
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
ms.openlocfilehash: 910b23cb0048d5d9f21c9c32e8f34219a425622a
ms.lasthandoff: 03/13/2017

---
# <a name="int-c-reference"></a>int (C# リファレンス)
`int` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。  
  
|型|範囲|サイズ|.NET Framework 型|既定値|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|-2,147,483,648 ～ 2,147,483,647|符号付き 32 ビット整数|<xref:System.Int32?displayProperty=fullName>|0|  
  
## <a name="literals"></a>リテラル  
 `int` 型の変数の宣言と初期化の例を次に示します。  
  
```  
  
int i = 123;  
```  
  
 サフィックスがない整数リテラルの場合、その型は、`int`、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) のうち、その値を表すことができる最初の型になります。 この例では、`int` 型です。  
  
## <a name="conversions"></a>変換  
 `int` から [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙の型変換が組み込まれています。 例:  
  
```  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[char](../../../csharp/language-reference/keywords/char.md) から `int` への、定義済みの暗黙の型変換が組み込まれています。 たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。  
  
```  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 浮動小数点型から `int` への暗黙的な変換が行われないことにも注意してください。 たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。  
  
```  
  
      int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Int32>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
