---
title: "Boolean Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.FALSE"
  - "vb.TRUE"
  - "vb.Boolean"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean data type"
  - "Boolean values, False keyword"
  - "False keyword [Visual Basic]"
  - "True keyword [Visual Basic]"
  - "Boolean values, True keyword"
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Boolean Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`True` または `False` の値だけを格納します。  キーワード `True` および `False` は、`Boolean` 変数の 2 つの状態に相当します。  
  
## 解説  
 ブール型 \([Boolean Data Type \(Visual Basic\)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)\) は、true\/false、yes\/no、on\/off など、2 つの状態を表す値を格納するために使用します。  
  
 ブール型 \(`Boolean`\) の既定値は `False` です。  
  
 `Boolean` 値は数字としては格納されず、格納された値は数字と等しくなりません。  コードを作成する際、`True` および `False` に相当する数値を利用しないようにしてください。  ブール型 \(`Boolean`\) の変数に対しては、できるだけ本来の論理値だけを使用してください。  
  
## 型変換  
 Visual Basic で数値型の値をブール型 \(`Boolean`\) に変換すると、0 は `False` になり、その他の値はすべて `True` になります。  Visual Basic でブール型 \(`Boolean`\) の値を数値型に変換すると、`False` は 0 になり、`True` は \-1 になります。  
  
 `Boolean` 値と数値型との間で変換を行う場合は、.NET フレームワークの変換メソッドが必ずしも Visual Basic の変換キーワードと同じ結果を出力するとは限らないことに注意してください。  これは、Visual Basic の変換処理が、前バージョンと互換性のある動作を保持しているからです。  詳細については、「[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」の「Boolean 型が数値型に正確に変換されない」を参照してください。  
  
## プログラミングのヒント  
  
-   **負の数。** ブール型 \(`Boolean`\) は数値型ではないので、負の値を表現できません。  どのような場合でも、`Boolean` を使って数値を格納しないでください。  
  
-   **型文字。** ブール型 \(`Boolean`\) にはリテラルの型文字も、識別子の型文字もありません。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Boolean?displayProperty=fullName> 構造体です。  
  
## 使用例  
 次の例では、`runningVB` はブール型 \(`Boolean`\) の変数であり、単純な Yes\/No の設定が格納されます。  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## 参照  
 <xref:System.Boolean?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)