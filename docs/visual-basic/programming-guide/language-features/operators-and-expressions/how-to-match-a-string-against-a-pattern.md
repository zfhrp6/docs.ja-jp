---
title: "How to: Match a String against a Pattern (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comparison operators, comparing strings"
  - "pattern matching"
  - "strings [Visual Basic], comparing"
  - "string comparison [Visual Basic], operators"
  - "Visual Basic code, operators"
  - "pattern matching, string comparison"
  - "string comparison [Visual Basic]"
  - "Like operator [Visual Basic], pattern matching"
  - "pattern matching, empty strings"
  - "operators [Visual Basic], comparison"
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Match a String against a Pattern (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) の式がパターンと一致しているかどうかを調べるには、[Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)を使います。  
  
 `Like` は 2 つのオペランドを受け取ります。  左のオペランドは文字列式で、右のオペランドは一致するかどうかを調べるパターンを格納する文字列です。  `Like` は文字列式がパターンと一致するかどうかを示す `Boolean` 値を返します。  
  
 文字列式の各文字が、特定の文字、ワイルドカード文字、文字リスト、または文字範囲と一致するかを調べることができます。  パターン文字列に指定された位置が、文字列式の一致するかどうかを調べる文字の位置に対応します。  
  
### 文字列式の文字が特定の文字と一致するかを調べるには  
  
-   特定の文字をパターン文字列に直接配置します。  その特定の文字は、角かっこ \(`[ ]`\) で囲む必要があります。  詳細については、「[Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)」を参照してください。  
  
     次の例では、`myString` が単一の文字 `H` で構成されるかどうかを調べます。  
  
     [!CODE [VbVbalrOperators#70](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#70)]  
  
### 文字列式の文字がワイルドカード文字と一致するか調べるには  
  
-   疑問符 \(`?`\) をパターン文字列に入れます。  この位置に、有効などの文字が入っていても、一致すると見なされます。  
  
     次の例は、`myString` が単一の文字 `W` と、それに続く任意の 2 文字で構成されるかどうかを調べます。  
  
     [!CODE [VbVbalrOperators#71](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#71)]  
  
### 文字列式の文字が文字のリストと一致するか調べるには  
  
-   パターン文字列内に角かっこ \(`[ ]`\) を置き、その内部に文字のリストを入れます。  文字をコンマやその他の区切り記号で区切らないでください。  リスト内のどの 1 文字が見つかっても、一致すると見なされます。  
  
     次の例は、`myString` が有効な任意の文字と、それに続く 1 文字 \(`A`、`C`、または `E` のいずれか\) で構成されるかどうかを調べます。  
  
     [!CODE [VbVbalrOperators#72](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#72)]  
  
     この一致では、大文字と小文字が区別されます。  
  
### 文字列式の文字が文字の範囲と一致するか調べるには  
  
-   パターン文字列内に角かっこ \(`[ ]`\) を置き、その内部に範囲の開始文字と終了文字をハイフン \(`–`\) で区切って指定します。  範囲内のどの 1 文字が見つかっても、一致すると見なされます。  
  
     次の例は、`myString` が文字列 `num` と、それに続く 1 文字 \(`i`、`j`、`k`、`l`、`m`、または `n` のいずれか\) で構成されるかどうかを調べます。  
  
     [!CODE [VbVbalrOperators#73](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#73)]  
  
     この一致では、大文字と小文字が区別されます。  
  
## 空の文字列との一致  
 `Like` は `[]` を長さ 0 の文字列 \(`""`\) として扱います。  `[]` を使うと文字列式全体が空かどうかを調べることができます。ただし、文字列式の特定の位置が空かどうかを調べることはできません。  特定の位置が空である場合も含めて調べる必要がある場合は、`Like` を 2 度以上使用します。  
  
#### 文字列式の文字が文字のリストと一致するか、または空かを調べるには  
  
1.  `Like` 演算子を同じ文字列式で 2 度呼び出して、2 つの呼び出しを [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) または [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) でつなぎます。  
  
2.  1 つ目の `Like` 句のパターン文字列に、文字リストを角かっこ \(`[ ]`\) で囲んで指定します。  
  
3.  2 つ目の `Like` 句のパターン文字列では、調べる位置に文字を入れずに指定します。  
  
     次の例では、7 桁の電話番号 `phoneNum` が、3 桁の数字の後に空白、ハイフン \(`–`\)、ピリオド \(`.`\) のいずれかが続くか、または文字が何も入らずに 4 桁の数字がそのまま続くかを調べます。  
  
     [!CODE [VbVbalrOperators#74](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#74)]  
  
## 参照  
 [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)   
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)