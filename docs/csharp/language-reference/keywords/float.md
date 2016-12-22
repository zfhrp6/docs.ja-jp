---
title: "float (C# リファレンス) | Microsoft Docs"
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
  - "float"
  - "float_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "float キーワード [C#]"
  - "浮動小数点数 [C#], float キーワード"
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# float (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`float` キーワードは、32 ビットの浮動小数点数値を格納する単純型を表します。  `float` 型の有効桁数とおおよその範囲は、次のとおりです。  
  
|種類|おおよその範囲|有効桁数|.NET Framework 型|  
|--------|-------------|----------|----------------------|  
|`float`|\-3.4 × 10<sup>38</sup> ～\+3.4 × 10<sup>38</sup>|7 桁|<xref:System.Single?displayProperty=fullName>|  
  
## リテラル  
 既定では、代入演算子の右側にある実数値リテラルは [double](../../../csharp/language-reference/keywords/double.md) として扱われます。  したがって、float 変数を初期化するには、次の例のように、サフィックス `f` または `F` を使用します。  
  
```  
  
float x = 3.5F;  
```  
  
 上の宣言でサフィックスを使用しなかった場合は、[double](../../../csharp/language-reference/keywords/double.md) 値を `float` 変数に格納することになるため、コンパイル エラーになります。  
  
## 変換  
 数値の整数型と浮動小数点型を 1 つの式に混在させることができます。  混在する場合は、整数型が浮動小数点型に変換されます。  式の評価は、次の規則に従います。  
  
-   浮動小数点型のうちの 1 つが [double](../../../csharp/language-reference/keywords/double.md) である場合、式は [double](../../../csharp/language-reference/keywords/double.md) になります。関係式またはブール式では [bool](../../../csharp/language-reference/keywords/bool.md) になります。  
  
-   式に [double](../../../csharp/language-reference/keywords/double.md) 型が 1 つも存在しない場合、式は `float` になります。関係式またはブール式では [bool](../../../csharp/language-reference/keywords/bool.md) になります。  
  
 浮動小数点の式に含まれる値は、次のとおりです。  
  
-   正および負の 0  
  
-   正および負の無限大  
  
-   非数 \(NaN\)  
  
-   有限の 0 以外の値  
  
 値の詳細については、「IEEE Standard for Binary Floating\-Point Arithmetic」\([IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) の Web サイト\) を参照してください。  
  
## 使用例  
 次の例では、[int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、および `float` は数式で使用されているため、`float` 型を結果として返します。  `float` は、<xref:System.Single?displayProperty=fullName> 型のエイリアスです。この式には [double](../../../csharp/language-reference/keywords/double.md) が存在しない点に注意してください。  
  
 [!CODE [csrefKeywordsTypes#13](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#13)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 <xref:System.Single>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)