---
title: "How to: Pass Arguments to a Procedure (Visual Basic) | Microsoft Docs"
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
  - "arguments [Visual Basic], passing to procedures"
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, calling"
  - "argument passing, procedures"
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Pass Arguments to a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャを呼び出すときには、プロシージャ名に続けて、引数をかっこ内に並べて指定します。  プロシージャに定義されたすべての必須パラメーターに対応する引数を指定します。`Optional` のパラメーターへの引数の指定は省略することもできます。  `Optional` のパラメーターの指定を省略した場合、その後に続けて別の引数を指定するのであれば、リスト内で引数を省略した位置を示すためにコンマを入力する必要があります。  
  
 `String` 型のパラメーターに `Byte` 型を渡すなど、パラメーターの型とは異なるデータ型の引数を渡す場合は、型チェックのスイッチ \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) に `Off` を設定してください。  `Option Strict` が `On` である場合は、拡大変換を使用するか、型変換のキーワードを明示的に使用する必要があります。  詳細については、「[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」および「[Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)」を参照してください。  
  
 詳細については、「[Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)」を参照してください。  
  
### 1 つ以上の引数をプロシージャに渡すには  
  
1.  呼び出しを行っているステートメントで、プロシージャ名に続けてかっこを入力します。  
  
2.  かっこの内側に引数リストを入力します。  プロシージャに定義された各必須パラメーターに対する引数を、コンマで区切って入力します。  
  
3.  各引数が、対応するパラメーターのデータ型 \(プロシージャで定義された型\) に変換可能な型に評価される、有効な式であることを確認してください。  
  
4.  パラメーターが [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) で定義されている場合は、引数リストに指定することも省略することもできます。  省略した場合は、そのパラメーターに定義された既定値がプロシージャで使用されます。  
  
5.  `Optional` のパラメーターの引数を省略し、その後に別のパラメーターを指定する場合は、引数リスト内にコンマを追加して引数を省略した位置を示すようにします。  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 関数を呼び出す例を次に示します。  
  
     [!code-vb[VbVbcnProcedures#34](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-pass-arguments-to_1.vb)]  
  
     この例では、必須である最初の引数が指定されています。この引数は表示されるメッセージの文字列です。  オプションである 2 つ目のパラメーターは省略されています。これはメッセージ ボックスに表示するボタンを指定する引数です。  値を指定せずに呼び出しているため、`MsgBox` は既定値である `MsgBoxStyle.OKOnly` を使用し、**\[OK\]** ボタンだけを表示します。  
  
     引数リストにある 2 つ目のコンマが、省略された 2 番目の引数の位置を示し、最後の文字列が `MsgBox` の 3 番目のパラメーター \(オプション\) に渡されます。これはタイトル バーに表示されるテキストです。  
  
## 参照  
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [オブジェクト指向プログラミング](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)