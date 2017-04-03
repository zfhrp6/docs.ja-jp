---
title: "uint (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
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
ms.openlocfilehash: fe4f7fcbbadee600e0ba6de70508312173d098ff
ms.lasthandoff: 03/13/2017

---
# <a name="uint-c-reference"></a>uint (C# リファレンス)
`uint` キーワードは、次の表に示すサイズと範囲で値を格納する整数型を示します。  
  
|型|範囲|サイズ|.NET Framework 型|  
|----------|-----------|----------|-------------------------|  
|`uint`|0 ～ 4,294,967,295|符号なし 32 ビット整数|<xref:System.UInt32?displayProperty=fullName>|  
  
 **メモ** `uint` 型は CLS に準拠していません。 可能な場合は、`int` を使用します。  
  
## <a name="literals"></a>リテラル  
 `uint` 型の変数の宣言と初期化の例を次に示します。  
  
```  
  
uint myUint = 4294967290;  
```  
  
 サフィックスがない整数リテラルの場合、整数リテラルの型は、[int](../../../csharp/language-reference/keywords/int.md)、`uint`、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) のうち、その値を表すことができる最初の型になります。 この例では、`uint` です。  
  
```  
  
uint uInt1 = 123;  
```  
  
 また、次の例のように、サフィックス u または U を付けることもできます。  
  
```  
  
uint uInt2 = 123U;  
```  
  
 サフィックス `U` または `u` を使用すると、リテラルの型は、リテラルの数値に応じて `uint` または `ulong` のいずれかに決まります。 例:  
  
```  
Console.WriteLine(44U.GetType());  
Console.WriteLine(323442434344U.GetType());  
```  
  
 このコードでは、2 番目のリテラルが `uint` 型で格納するには大きすぎるため、`System.UInt32`、`System.UInt64` の順に表示します。これはそれぞれ、`uint` および `ulong` の基になる型です。  
  
## <a name="conversions"></a>変換  
 `uint` から [long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。 例:  
  
```  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `uint` への、定義済みの暗黙的な変換が組み込まれています。 それ以外の場合は、キャストを使用する必要があります。 たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。  
  
```  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 浮動小数点型から `uint` への暗黙的な変換が行われないことにも注意してください。 たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。  
  
```  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」および「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.UInt32>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
