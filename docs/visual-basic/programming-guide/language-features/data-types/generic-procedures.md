---
title: "Generic Procedures in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
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
  - "generic methods, type inference"
  - "generics [Visual Basic], type inference"
  - "procedures, generic"
  - "generic procedures"
  - "type inference, generics"
  - "generic methods"
  - "type inference"
  - "generics [Visual Basic], procedures"
  - "generic procedures, type inference"
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Generic Procedures in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*ジェネリック プロシージャ*は、少なくとも 1 つの型パラメーターで定義されるプロシージャであり、*ジェネリック メソッド*とも呼ばれます。  これを使用すると、呼び出し元のコードは、プロシージャを呼び出すたびにその要件に合わせてデータ型を調整できます。  
  
 プロシージャは、ジェネリック クラスまたはジェネリックな構造体内で定義されていることだけでジェネリックになるわけではありません。  ジェネリックであるためには、プロシージャは、必要に応じて使用される通常のパラメーター以外に、少なくとも 1 つの型パラメーターを使用する必要があります。  ジェネリック クラスまたはジェネリックな構造体が、非ジェネリック プロシージャを含むことも、非ジェネリックなクラス、構造体、またはモジュールが、ジェネリック プロシージャを含むこともできます。  
  
 ジェネリック プロシージャは、その型パラメーターを、その通常のパラメーター リスト、その戻り値の型があればその型、およびそのプロシージャ コードで使用できます。  
  
## 型の推定  
 型引数を一切指定しないでジェネリック プロシージャを呼び出すことができます。  この方法で呼び出す場合、コンパイラは、プロシージャの型引数に渡す適切なデータ型を決定しようとします。  これは、*型の推定*と呼ばれます。  コンパイラが `String` 型を型パラメーター `t` に渡すと推定する呼び出しを次のコードに示します。  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 コンパイラが呼び出しのコンテキストから型引数を推定できない場合、エラーが報告されます。  このようなエラーの原因の 1 つは、配列ランクの不一致です。  たとえば、通常のパラメーターを型パラメーターの配列として定義するとします。  異なるランク \(次元数\) の配列を指定するジェネリック プロシージャを呼び出すと、不一致により型の推定が失敗します。  1 次元配列を受け取るプロシージャに 2 次元配列が渡される呼び出しを次のコードに示します。  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 型の推定は、すべての型引数を省略することによってのみ呼び出すことができます。  型引数を 1 つでも指定する場合は、すべての型引数を指定する必要があります。  
  
 型の推定がサポートされるのは、ジェネリック プロシージャの場合だけです。  型の推定を、ジェネリック クラス、構造体、インターフェイス、またはデリゲートで呼び出すことはできません。  
  
## 例  
  
### Description  
 次の例では、配列内の特定の要素を検索するためのジェネリック `Function` プロシージャを定義しています。  これは、1 つの型パラメーターを定義し、それを使用して、パラメーター リストに 2 つのパラメーターを構築します。  
  
### コード  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### コメント  
 前の例では、`searchValue` と `searchArray` の各要素を比較する機能が必要です。  この機能が確実に動作するように、型パラメーター `T` は <xref:System.IComparable%601> インターフェイスを実装するように制限されています。  コードでは、`=` 演算子の代わりに <xref:System.IComparable%601.CompareTo%2A> メソッドを使用します。これは、`T` によって提供される型引数が `=` 演算子をサポートしているという保証がないからです。  
  
 `findElement` プロシージャをテストするためには、次のコードを使用してください。  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 前の `MsgBox` 呼び出しでは、それぞれ "0"、"1"、および "\-1" が表示されます。  
  
## 参照  
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [方法 : 複数のデータ型に同一の機能を提供できるクラスを定義する](../Topic/How%20to:%20Define%20a%20Class%20That%20Can%20Provide%20Identical%20Functionality%20on%20Different%20Data%20Types%20\(Visual%20Basic\).md)   
 [方法 : ジェネリック クラスを使用する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)   
 [Parameter List](../../../../visual-basic/language-reference/statements/parameter-list.md)