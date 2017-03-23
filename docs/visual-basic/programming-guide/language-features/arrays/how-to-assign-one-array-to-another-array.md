---
title: "How to: Assign One Array to Another Array (Visual Basic) | Microsoft Docs"
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
  - "covariance, arrays"
  - "arrays [Visual Basic], assigning"
  - "arrays [Visual Basic], covariance"
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Assign One Array to Another Array (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

配列はオブジェクトであるため、他のオブジェクト型と同じように代入ステートメントで使用できます。  配列変数には、配列の要素、ランク、および長さの情報を構成するデータへのポインターが保持されています。代入ではこのポインターのみがコピーされます。  
  
### 配列を別の配列に代入するには  
  
1.  2 つの配列が同じランク \(次元数\) であり、要素のデータ型に互換性があることを確認します。  
  
2.  標準の代入ステートメントを使用して、代入する配列を代入先の配列に割り当てます。  いずれの配列名の後にも、かっこを指定しないでください。  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 配列を別の配列に代入する場合、次の規則が適用されます。  
  
-   **ランクが等しいこと。**代入先の配列と代入元の配列のランク \(次元数\) が一致している必要があります。  
  
     両方の配列のランクが一致している場合、要素数は一致していなくてもかまいません。  次元の要素の数は、代入するときに変更できます。  
  
-   **要素の型。**両方の配列の要素が*参照型*であるか、両方の配列の要素が*値型*である必要があります。  詳細については、「[Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
    -   両方の配列の要素が値型である場合、要素のデータ型は完全に一致している必要があります。  これには 1 つだけ例外があり、`Enum` 要素の配列を、その `Enum` の基本型の配列に代入することはできます。  
  
    -   両方の配列の要素が参照型である場合、代入元の要素型が代入先の要素型から派生している必要があります。  これに該当する場合、2 つの配列は、それらの配列の要素と同じ継承関係にあることになります。  これは、*配列の共変性*と呼ばれます。  
  
 データ型に互換性がない場合や、ランクが一致していない場合など、上記の規則に対する違反がある場合は、コンパイラによってエラーが報告されます。  コードにエラー処理を追加すると、代入を実行する前に配列の互換性を確認できます。  また、例外がスローされるのを回避する必要がある場合は [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) キーワードを使用することもできます。  
  
## 参照  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)