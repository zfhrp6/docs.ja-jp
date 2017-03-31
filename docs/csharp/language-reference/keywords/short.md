---
title: "short (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
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
ms.openlocfilehash: 3c14ae463021fbeed9de24610292fa7516a453fe
ms.lasthandoff: 03/13/2017

---
# <a name="short-c-reference"></a>short (C# リファレンス)
`short` キーワードは、次の表に示すサイズと範囲で値を格納する整数データ型を示します。  
  
|型|範囲|サイズ|.NET Framework 型|  
|----------|-----------|----------|-------------------------|  
|`short`|-32,768 ～ 32,767|符号付き 16 ビット整数|<xref:System.Int16?displayProperty=fullName>|  
  
## <a name="literals"></a>リテラル  
 `short` 変数の宣言と初期化の例を次に示します。  
  
```  
  
short x = 32767;  
```  
  
 上のように宣言すると、整数リテラル `32767` は暗黙的に [int](../../../csharp/language-reference/keywords/int.md) から `short` に変換されます。 整数リテラルを `short` の格納場所に格納できない場合は、コンパイル エラーになります。  
  
 オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。 たとえば、`short` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 `short` キャストを使用すると、正しい型が呼び出されます。次に例を示します。  
  
```  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>変換  
 `short` から [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。  
  
 記憶領域が大きなリテラル以外の数値型を暗黙的に `short` に変換することはできません (整数型の記憶領域については、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください)。 たとえば、2 つの `short` 変数 `x` と `y` があるとします。  
  
```  
  
short x = 5, y = 12;  
```  
  
 次の代入ステートメントは、代入演算子の右側にある算術式が既定で [int](../../../csharp/language-reference/keywords/int.md) に評価されるため、コンパイル エラーになります。  
  
 `short`   `z = x + y;   // Error: no conversion from int to short`  
  
 この問題を解決するには、キャストを使用します。  
  
 `short`   `z = (`  `short`  `)(x + y);   // OK: explicit conversion`  
  
 ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 浮動小数点型から `short` への暗黙的な変換は行われません。 たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。  
  
```  
  
      short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。  
  
 暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Int16>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
