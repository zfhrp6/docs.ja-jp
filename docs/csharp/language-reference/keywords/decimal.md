---
title: "decimal (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- decimal_CSharpKeyword
- decimal
dev_langs:
- CSharp
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 32
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 336a4a7bb485a48282dd740bafb81421e0cba693
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="decimal-c-reference"></a>decimal (C# リファレンス)
`decimal` キーワードは、128 ビットのデータ型を示します。 `decimal` 型は、浮動小数点型よりも有効桁数が多く、範囲が狭いので、財務や金融の計算に適しています。 `decimal` 型の概算の範囲と有効桁数は、次のとおりです。  
  
|型|おおよその範囲|有効桁数|.NET Framework 型|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|(-7.9 x 10<sup>28</sup> ～ 7.9 x 10<sup>28</sup>) / (10<sup>0 ～ 28</sup>)|有効桁数 28 ～ 29|<xref:System.Decimal?displayProperty=fullName>|  
  
## <a name="literals"></a>リテラル  
 実数値リテラルを `decimal` として扱うには、サフィックス m または M を使用します。次に例を示します。  
  
```  
  
decimal myMoney = 300.5m;  
```  
  
 サフィックス m がない場合は [double](../../../csharp/language-reference/keywords/double.md) として扱われ、コンパイラ エラーになります。  
  
## <a name="conversions"></a>変換  
 整数型は、暗黙的に `decimal` に変換され、結果は `decimal` になります。 したがって、サフィックスなしで整数リテラルを使用して 10 進変数を初期化できます。次に例を示します。  
  
```  
  
decimal myMoney = 300;  
```  
  
 浮動小数点型と `decimal` 型の間に暗黙の型変換はありません。2 つの型の間で変換を実行するには、キャストを使用する必要があります。 例:  
  
```  
  
      decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 `decimal` 型と数値の整数型を同じ式に混在させることもできます。 ただし、`decimal` 型と浮動小数点型をキャストなしで混在させると、コンパイル エラーになります。  
  
 暗黙的な数値変換の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
 明示的な数値変換の詳細については、「[明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)」を参照してください。  
  
## <a name="formatting-decimal-output"></a>10 進出力の書式指定  
 結果の書式を指定するには、`String.Format` メソッドを使用するか、<xref:System.Console.Write%2A?displayProperty=fullName> を呼び出す `String.Format()` メソッドを使用します。 通貨書式を指定するには、この記事の 2 番目の例に示されているように、標準の通貨の書式指定文字列である "C" または "c" を使用します。 `String.Format` メソッドの詳細については、<xref:System.String.Format%2A?displayProperty=fullName> を参照してください。  
  
## <a name="example"></a>例  
 次の例では、[double](../../../csharp/language-reference/keywords/double.md) の変数と `decimal` の変数を加算しようとして、コンパイラ エラーが発生します。  
  
```csharp  
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
  
```  
  
 実行の結果、次のエラーが生成されます。  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 この例では、同じ式に `decimal` と [int](../../../csharp/language-reference/keywords/int.md) が混在しています。 結果は `decimal` 型になります。  
  
 [!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a>例  
 ここでは、通貨の書式指定文字列を使用して、出力の書式を指定する例を示します。 小数点以下の桁数が $0.99 を超えるため、`x` を丸めている点に注意してください。 変数 `y` は最大固定桁数を表し、正しい書式で正確に表示されます。  
  
 [!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Decimal>   
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md)
