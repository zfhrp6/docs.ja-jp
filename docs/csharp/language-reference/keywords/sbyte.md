---
title: "sbyte (C# リファレンス)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 010ac98f523eca5929100f7c51b8b6ef5d11de30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-c-reference"></a>sbyte (C# リファレンス)

`sbyte` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。  
  
|型|範囲|サイズ|.NET Framework 型|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 ～ 127|符号付き 8 ビット整数|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>リテラル  

`sbyte` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。 

次の例では、整数 -102 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](../../../csharp/language-reference/keywords/int.md) から `sbyte` 値に変換されています。    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> 16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。 10 進リテラルには、プレフィックスはありません。

以降で c# 7、いくつかの機能が追加されて読みやすさを強化するためにします。 
 - C# 7.0 により、アンダー スコア文字の使用法`_`、桁区切り記号として。
 - により、c# 7.2`_`プレフィックスの後に、バイナリまたは 16 進数リテラルの桁区切り記号として使用します。 10 進数のリテラルはない、先頭にアンダー スコアを持つことができます。

 いくつかの例は、以下に示します。

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

整数リテラルが `sbyte` の範囲外にある場合 (つまり、<xref:System.SByte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.SByte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。 サフィックスがない整数リテラルの場合、整数リテラルの型は、[int](int.md)、[uint](uint.md)、[long](long.md)、[ulong](ulong.md) のうち、その値を表すことができる最初の型になります。 つまり、この例では、数値リテラル `0x9A` と `0b10011010` は値が 156 の 32 ビット符号付き整数として解釈され、これは <xref:System.SByte.MaxValue?displayProperty=nameWithType> を超えています。 このため、キャスト演算子が必要であり、割り当ては [unchecked](unchecked.md) コンテキストで行われる必要があります。 

## <a name="compiler-overload-resolution"></a>コンパイラのオーバーロード解決

 オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。 たとえば、`sbyte` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 `sbyte` キャストを使用すると、正しい型が呼び出されます。次に例を示します。  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>変換  
 `sbyte` から [short](../../../csharp/language-reference/keywords/short.md)、[int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。  
  
 記憶領域が大きなリテラル以外の数値型を暗黙的に `sbyte` に変換することはできません (整数型の記憶領域については、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください)。 たとえば、2 つの `sbyte` 変数 `x` と `y` があるとします。  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 次の代入ステートメントは、代入演算子の右側にある算術式が既定で [int](../../../csharp/language-reference/keywords/int.md) に評価されるため、コンパイル エラーになります。  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 この問題を解決するには、次の例のように式をキャストします。  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 浮動小数点型から `sbyte` への暗黙的な変換が行われないことにも注意してください。 たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」および「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.SByte>  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
