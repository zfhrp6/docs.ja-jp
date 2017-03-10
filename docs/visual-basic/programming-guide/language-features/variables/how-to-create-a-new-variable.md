---
title: "How to: Create a New Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Dim statement"
  - "variables [Visual Basic], creating"
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# How to: Create a New Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数を作成する場合は、[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を使用します。  
  
### 新しい変数を作成するには  
  
1.  `Dim` ステートメントで変数を宣言します。  
  
    ```  
  
    Dim newCustomer  
    ```  
  
2.  [Private](../../../../visual-basic/language-reference/modifiers/private.md)、[Static](../../../../visual-basic/language-reference/modifiers/static.md)、[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)、[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) など変数の特性を指定します。  詳細については、「[Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)」を参照してください。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     宣言で他のキーワードを使用する場合は、`Dim` キーワードは必要ありません。  
  
3.  変数名の規則に従います。この規則は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の規則および規約に従う必要があります。  詳細については、「[Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  名前の後に [As](../../../../visual-basic/language-reference/statements/as-clause.md) 句を付けて、変数のデータ型を指定します。  
  
    ```  
    Public Static newCustomer As Customer   
    ```  
  
     データ型を指定しなかった場合は、既定の `Object` 型が使用されます。  
  
5.  `As` 句の後に等号 \(`=`\) を指定し、等号の後に変数の初期値を指定します。  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、`Dim` ステートメントを実行するたびに、指定した値が変数に代入されます。  初期値を指定しなかった場合、`Dim` ステートメントを含むコードが最初に実行されるとき、変数のデータ型に応じた既定の初期値が [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって代入されます。  
  
     変数が参照型の場合は、`As` 句に [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) キーワードを含めることによって、クラスのインスタンスを作成できます。  `New` を指定しない場合、変数の初期値は [Nothing](../../../../visual-basic/language-reference/nothing.md) となります。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## 参照  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)