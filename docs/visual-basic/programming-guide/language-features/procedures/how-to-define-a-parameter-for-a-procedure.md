---
title: "How to: Define a Parameter for a Procedure (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "procedure parameters, defining data types for"
  - "procedures, parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters, defining"
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Define a Parameter for a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*パラメーター* は、呼び出し元のコードが値をプロシージャに渡すために使用します。  プロシージャのパラメーターを宣言する場合には、変数を宣言するときと同じように、パラメーターの名前とデータ型を指定します。  また、渡す方法や、パラメーターを省略できるかどうかも指定できます。  
  
 詳細については、「[Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)」を参照してください。  
  
### プロシージャのパラメーターを定義するには  
  
1.  プロシージャの宣言中に、プロシージャのパラメーター一覧に、他のパラメーターとの間をコンマで区切ってパラメーター名を追加します。  
  
2.  パラメーターのデータ型を決定します。  
  
3.  パラメーター名の後に `As` 句を入力し、データ型を指定します。  
  
4.  パラメーターの渡し方を決定します。  通常、パラメーターは値によって渡されますが、呼び出し元のコード内の値をプロシージャが変更できるように指定することもできます。  
  
5.  パラメーター名の前には [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) または [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) を指定して、渡し方を指定します。  詳細については、「[Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)」を参照してください。  
  
6.  パラメーターが省略可能である場合、渡し方の前に [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) を指定して、パラメーターのデータ型の後に等号 \(`=`\) と既定値を指定します。  
  
     次の例では、3 つのパラメーターを持つ `Sub` プロシージャの骨組みを定義します。  最初の 2 つのパラメーターは必須で、3 つ目は省略可能です。  パラメーターの一覧の中で、各パラメーターの定義はコンマで区切られます。  
  
     [!code-vb[VbVbcnProcedures#33](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     最初のパラメーターは  `customer`  オブジェクトを受け入れ、引数は [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) で渡されているので、`updateCustomer` は `c` に渡された変数を直接更新できます。  最後の 2 つの引数は [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) で渡されているので、プロシージャはこれらの値を変更することはできません。  
  
     呼び出し元のコードに `level` パラメーターの値が指定されていない場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はこれを既定値である 0 に設定します。  
  
     型チェックのスイッチ \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) が `Off` の場合、パラメーターの定義時に `As` 句を省略できます。  しかし、いずれかのパラメーターが `As` 句を使用している場合は、すべてのパラメーターがこれを使用する必要があります。  型チェックのスイッチが `On` の場合、`As` 句はすべてのパラメーター定義で必須です。  
  
     すべてのプログラミング要素についてデータ型を指定することは、*厳密な型指定*と呼ばれます。  `Option Strict On` を設定した場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は厳密な型指定を強制します。  これは、次の理由で強く推奨されています。  
  
    -   変数に対する IntelliSense サポートが有効になります。  これにより、コードの入力時に、プロパティや他のメンバーを表示できます。  
  
    -   コンパイラで型チェックを実行できます。  これは、実行時にオーバーフローなどのエラーで失敗するステートメントを検出するのに役立ちます。  また、オブジェクトでサポートされていないメソッドの呼び出しも検出されます。  
  
    -   コードの実行速度が速くなります。  この理由の 1 つは、プログラミング要素にデータ型を指定しなかった場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラが `Object` タイプを割り当てるためです。  コンパイル済みのコードが、`Object` および他のデータ型との間で変換を行う必要がある場合、パフォーマンスが低下します。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [オブジェクト指向プログラミング](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)