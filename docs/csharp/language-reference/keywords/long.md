---
title: "long (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
dev_langs:
- CSharp
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 17
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
ms.openlocfilehash: c28c8308d7ed32f7240f56113a77a0794cb1ba62
ms.lasthandoff: 03/13/2017

---
# <a name="long-c-reference"></a>long (C# リファレンス)
`long` キーワードは、次の表に示されたサイズと範囲に基づいて値を格納する整数型を示します。  
  
|型|範囲|サイズ|.NET Framework 型|  
|----------|-----------|----------|-------------------------|  
|`long`|– 9,223,372,036,854,775,808 ～ 9,223,372,036,854,775,807|符号付き 64 ビット整数|<xref:System.Int64?displayProperty=fullName>|  
  
## <a name="literals"></a>リテラル  
 `long` 変数の宣言と初期化の例を次に示します。  
  
```  
  
long long1 = 4294967296;  
```  
  
 サフィックスがない整数リテラルの場合、整数リテラルの型は、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、`long`、[ulong](../../../csharp/language-reference/keywords/ulong.md) のうち、その値を表すことができる最初の型になります。 上の例では、整数リテラルが [uint](../../../csharp/language-reference/keywords/uint.md) の範囲を超えているため、`long` 型になります (整数型の記憶サイズについては、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください)。  
  
 また、次の例のように、`long` 型にサフィックス L を付けることもできます。  
  
```  
  
long long2 = 4294967296L;  
```  
  
 サフィックス L を使用する場合、整数リテラルの型は、そのサイズに応じて `long` または [ulong](../../../csharp/language-reference/keywords/ulong.md) のいずれかに決まります。 この場合、整数リテラルが [ulong](../../../csharp/language-reference/keywords/ulong.md) の範囲より小さいため、`long` になります。  
  
 サフィックスは、オーバーロードされたメソッドの呼び出しでよく使用されます。 たとえば、`long` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用してオーバーロードされたメソッドがあるとします。  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 サフィックス L を使用すると、正しい型が呼び出されます。次に例を示します。  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 `long` 型とその他の数値の整数型を同じ式で使用できます。その場合、式は `long` (関係式またはブール式の場合は [bool](../../../csharp/language-reference/keywords/bool.md)) として評価されます。 たとえば、次の式は `long` として評価されます。  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  小文字の "l" もサフィックスとして使用できます。 ただし、文字の "l" は数字の "1" と混同しやすいため、コンパイラから警告が出されます。 明確にするには、"L" を使用します。  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
## <a name="conversions"></a>変換  
 `long` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。 それ以外の型の場合は、キャストを使用する必要があります。 たとえば、次の代入ステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[char](../../../csharp/language-reference/keywords/char.md) から `long` への暗黙の型変換が組み込まれています。  
  
 また、浮動小数点型から `long` への暗黙の型変換が行われないことにも注意してください。 たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。  
  
```  
  
      long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Int64>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
