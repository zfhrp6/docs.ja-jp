---
title: "How to: Declare an Object by Using an Object Initializer (Visual Basic) | Microsoft Docs"
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
  - "declaring objects using object initializer"
  - "object initializers [Visual Basic]"
  - "initializers [Visual Basic]"
  - "Video How tos, Visual Basic"
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare an Object by Using an Object Initializer (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

オブジェクト初期化子を使用すると、クラスのインスタンスの宣言と初期化を単一のステートメントで実行できます。  さらに、パラメーター化されたコンストラクターを呼び出さずに、インスタンスの 1 つ以上のメンバーを同時に初期化できます。  
  
 オブジェクト初期化子を使用して名前付きの型のインスタンスを作成すると、クラスの既定のコンストラクターが呼び出された後、指定したメンバーの初期化が指定した順序で実行されます。  
  
 次の手順では、`Student` クラスのインスタンスを 3 つの異なる方法で作成する方法を示します。  このクラスには、名、姓、学年などのプロパティがあります。  3 つの宣言では、いずれも `Student` の新しいインスタンスを作成し、`First` プロパティを "Michael" に、`Last` プロパティを "Tucker" に、それ以外のすべてのメンバーを既定値に設定します。  この手順のそれぞれの宣言の結果は、オブジェクト初期化子を使用しない次の例と同等になります。  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 `Student` クラスの実装については、「[How to: Create a List of Items](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md)」を参照してください。  このトピックからコードをコピーして、クラスのセットアップおよび `Student` オブジェクトのリストの作成に使用できます。  
  
### オブジェクト初期化子を使用して名前付きクラスのオブジェクトを作成するには  
  
1.  コンストラクターを使用する場合と同じように宣言を開始します。  
  
     `Dim student1 As New Student`  
  
2.  「`With`」というキーワードを入力し、その後に初期化リストを中かっこで囲んで入力します。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  初期化リストには、初期化するプロパティと、各プロパティに割り当てる初期値を指定します。  プロパティの名前の前にはピリオドを付けます。  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     クラスの 1 つ以上のメンバーを初期化できます。  
  
4.  別の方法として、クラスの新しいインスタンスを宣言し、そのインスタンスに値を割り当てることもできます。  最初に、`Student` のインスタンスを宣言します。  
  
     `Dim student2 As Student`  
  
5.  `Student` のインスタンスの作成を通常の方法で開始します。  
  
     `Dim student2 As Student = New Student`  
  
6.  「`With`」と入力し、その後に新しいインスタンスの 1 つ以上のメンバーを初期化するオブジェクト初期化子を入力します。  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  上の手順での定義は、`As Student` を省略することで簡略化できます。  この場合、コンパイラはローカル型の推論を使用して、`student3` が `Student` のインスタンスであると判断します。  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     詳細については、「[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。  
  
## 参照  
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [How to: Create a List of Items](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)