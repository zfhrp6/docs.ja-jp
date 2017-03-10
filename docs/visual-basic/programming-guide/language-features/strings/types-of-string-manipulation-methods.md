---
title: "Types of String Manipulation Methods in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], manipulating [Visual Basic]"
  - "string manipulation"
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Types of String Manipulation Methods in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

文字列を分析し、操作する方法はいくつかあります。  ここで紹介するメソッドには、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 言語の一部であるメソッドと、`String` クラス固有のメソッドがあります。  
  
## Visual Basic 言語と .NET Framework  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のメソッドは、言語に固有の関数として使用されます。  したがって、コード内で修飾子を付けずに使用できます。  次のコードは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の文字列操作コマンドの典型的な使用例です。  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/types-of-string-manipula_1.vb)]  
  
 この例では、`Mid` 関数が `aString` を直接処理し、値を `bString` に代入しています。  
  
 Visual Basic における文字列操作メソッドの一覧については、「[String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)」を参照してください。  
  
### 共有メソッドとインスタンス メソッド  
 `String` クラスのメソッドを使って文字列を操作することもできます。  `String` には、*共有*メソッドと*インスタンス* メソッドの 2 種類のメソッドがあります。  
  
#### 共有メソッド  
 共有メソッドは、`String` クラス自体のメソッドであり、クラスのインスタンスを必要としません。  これらのメソッドを修飾するには、`String` クラスのインスタンスではなく、クラスの名前 \(`String`\) を使います。  次に例を示します。  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/types-of-string-manipula_2.vb)]  
  
 この例の <xref:System.String.Copy%2A?displayProperty=fullName> メソッドは静的メソッドであり、指定された式を処理し、結果値を `bString` に代入します。  
  
#### インスタンス メソッド  
 これに対して、インスタンス メソッドは、`String`の特定のインスタンスのメソッドであり、インスタンス名で修飾する必要があります。  次に例を示します。  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/types-of-string-manipula_3.vb)]  
  
 この例の <xref:System.String.Substring%2A?displayProperty=fullName> メソッドは、`String` のインスタンス \(`aString`\) のメソッドです。  `aString` に対して処理を実行し、値を `bString` に代入します。  
  
 詳細については、<xref:System.String> クラスのドキュメントを参照してください。  
  
## 参照  
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)