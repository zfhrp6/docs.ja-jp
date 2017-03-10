---
title: "How to: Create a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "Visual Basic code, reusing"
  - "procedure declarations"
  - "procedures, about procedures"
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# How to: Create a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャは、開始宣言ステートメント \(`Sub` または `Function`\) と終了宣言ステートメント \(`End Sub` または `End Function`\) で囲みます。  プロシージャのコードは、すべてこれらのステートメントの間に作成します。  
  
 プロシージャの内部に別のプロシージャを含めることはできません。つまり、開始ステートメントと終了ステートメントは他のプロシージャの外部に置く必要があります。  
  
 同じタスクを複数の場所で実行するコードがある場合は、そのタスクをプロシージャとして一度記述し、コード内の複数の場所からそれを呼び出します。  
  
### 値を返さないプロシージャを作成するには  
  
1.  他のプロシージャの外側で `Sub` ステートメントを記述し、続けて `End Sub` ステートメントを記述します。  
  
2.  `Sub` ステートメント内で、`Sub` キーワードの後ろにプロシージャ名を指定し、続けてパラメーター リストをかっこで囲んで記述します。  
  
3.  `Sub` ステートメントと `End Sub` ステートメントの間にプロシージャのコード ステートメントを記述します。  
  
### 値を返すプロシージャを作成するには  
  
1.  その他のプロシージャの外部で、`Function` ステートメントと `End Function` ステートメントを使用します。  
  
2.  `Function` ステートメント内で、`Function` キーワードの後にプロシージャ名を定義し、パラメーター リストをかっこで囲んで記述してから、戻り値のデータ型を指定する `As` 句を記述します。  
  
3.  プロシージャのコード ステートメントは、`Function` と `End Function` ステートメントの間に記述します。  
  
4.  `Return` ステートメントを使用して、呼び出し元のコードに値を返します。  
  
### 作成したプロシージャを、ブロックが繰り返し出現する古いコードにリンクさせるには  
  
1.  作成したコードが、古いコードからアクセス可能な場所にあることを確認します。  
  
2.  ブロックが繰り返し出現する古いコードで、同じタスクを実行しているステートメントを、`Sub` プロシージャまたは `Function` プロシージャを呼び出す単一のステートメントに置き換えます。  
  
3.  値を返す `Function` プロシージャで置き換える場合は、呼び出しステートメントが戻り値を使ってアクション \(変数に格納するなど\) を実行していることを確認します。実行していなければ、値は失われます。  
  
## 使用例  
 次の `Function` プロシージャは、直角三角形の最も長い辺 \(斜辺\) を他の 2 つの辺の値を基に計算します。  
  
 [!code-vb[VbVbcnProcedures#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-create-a-procedure_1.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [オブジェクト指向プログラミング](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)