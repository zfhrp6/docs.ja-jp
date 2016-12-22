---
title: "double (C# リファレンス) | Microsoft Docs"
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
  - "double"
  - "double_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "倍精度浮動小数点数型 (Double) [C#]"
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# double (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`double` キーワードは、64 ビットの浮動小数点数値を格納する単純型を表します。  `double` 型の有効桁数とおおよその範囲は、次のとおりです。  
  
|種類|おおよその範囲|有効桁数|.NET Framework 型|  
|--------|-------------|----------|----------------------|  
|`double`|±1.5 × 10<sup>−324</sup> ～ ±1.7 × 10<sup>308</sup>|15 ～ 16 桁|<xref:System.Double?displayProperty=fullName>|  
  
## リテラル  
 既定では、代入演算子の右側にある実数値リテラルは `double` として扱われます。  ただし、整数を `double` として扱う必要がある場合は、サフィックス d または D を使用します。次に例を示します。  
  
```  
  
double x = 3D;  
```  
  
## 変換  
 数値の整数型と浮動小数点型を 1 つの式に混在させることができます。  混在する場合は、整数型が浮動小数点型に変換されます。  式の評価は、次の規則に従います。  
  
-   浮動小数点型のうちの 1 つが `double` である場合、式は `double` になります。関係式またはブール式では [bool](../../../csharp/language-reference/keywords/bool.md) になります。  
  
-   式に `double` 型が 1 つも存在しない場合、式は [float](../../../csharp/language-reference/keywords/float.md) になります。関係式またはブール式では [bool](../../../csharp/language-reference/keywords/bool.md) になります。  
  
 浮動小数点の式に含まれる値は、次のとおりです。  
  
-   正および負の 0  
  
-   正および負の無限大  
  
-   非数 \(NaN\)  
  
-   有限の 0 以外の値  
  
 値の詳細については、「IEEE Standard for Binary Floating\-Point Arithmetic」\([IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) の Web サイト\) を参照してください。  
  
## 使用例  
 次の例では、[int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md)、および `double` を加算した結果が、`double` 型として出力されます。  
  
 [!CODE [csrefKeywordsTypes#9](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#9)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [浮動小数点型の一覧表](../../../csharp/language-reference/keywords/floating-point-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)