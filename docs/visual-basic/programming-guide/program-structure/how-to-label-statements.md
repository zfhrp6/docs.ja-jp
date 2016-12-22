---
title: "How to: Label Statements (Visual Basic) | Microsoft Docs"
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
  - "colons (:)"
  - "statements [Visual Basic], labels"
  - ": separator character"
  - "Visual Basic code, labeling statements"
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Label Statements (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ステートメント ブロックは、コロン区切りのコード行から構成されます。  識別文字列または識別番号を先頭に付加したコード行は、"ラベル付けされた" と表現されます。  ステートメント ラベルは、コード行のマーキングに使用します。このマーキングによって、`On Error Goto` などのステートメントで使用する行を識別します。  
  
 ラベルとしてプログラミング要素または整数リテラルを識別するもの識別このようないずれかの有効な Visual Basic である場合があります。  ラベルはソース コード行の先頭に記述し、ラベルの直後にはコロンを記述する必要があります。同じ行にステートメントが続くかどうかに関係なく、コロンは必ず記述してください。  
  
 コンパイラは、行の先頭が、定義済み識別子と一致するかどうかでラベルを識別します。  一致しない場合、コンパイラはそれをラベルと判断します。  
  
 ラベルにはそれぞれの宣言空間があり、それぞれの識別子で干渉することはありません。  ラベルのスコープは、メソッドの本体です。  あいまいな場合は、ラベル宣言が優先されます。  
  
> [!NOTE]
>  ラベルは、メソッド内の実行可能なステートメントに対してだけ使用できます。  
  
### コード行にラベル付けするには  
  
-   識別子とそれに続くコロンをソース コード行の先頭に置きます。  
  
     たとえば、次に示すコード行には、それぞれ `Jump` と `120` のラベルが付けられています。  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## 参照  
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)