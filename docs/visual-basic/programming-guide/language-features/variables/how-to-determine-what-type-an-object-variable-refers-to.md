---
title: "How to: Determine What Type an Object Variable Refers To (Visual Basic) | Microsoft Docs"
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
  - "TypeOf operator [Visual Basic], determining object variable type"
  - "variables [Visual Basic], object"
  - "object variables, determining type"
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Determine What Type an Object Variable Refers To (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

オブジェクト変数には、別の場所に格納されているデータへのポインターが含まれています。  データの型は、実行時に変わる可能性があります。  任意のタイミングで、<xref:System.Type.GetTypeCode%2A> メソッドを使用して、現在の実行時型を確認することや、[TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) を使用して、現在の実行時型と指定の型に互換性があるかどうかを確認できます。  
  
### オブジェクト変数で現在参照している正確な型を確認するには  
  
1.  オブジェクト変数で、<xref:System.Object.GetType%2A> メソッドを呼び出して、<xref:System.Type?displayProperty=fullName> オブジェクトを取得します。  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <xref:System.Type?displayProperty=fullName> クラスで、共有メソッド <xref:System.Type.GetTypeCode%2A> を呼び出してそのオブジェクト型の <xref:System.TypeCode> 列挙値を取得します。  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     `Double` など、<xref:System.TypeCode> の列挙値と突き合わせると、取得した列挙型のメンバーがどの列挙値なのかを確認できます。  
  
### オブジェクト変数の型と指定の型に互換性があるかどうかを確認するには  
  
-   [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) と組み合わせて `TypeOf` 演算子を使用し、`TypeOf`...`Is` 式を用いてオブジェクトをテストします。  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`...`Is` 式は、オブジェクトの実行時型と指定の型に互換性がある場合は、`True` を返します。  
  
     互換性の基準は、指定の型がクラス、構造体、またはインターフェイスのいずれであるかによって異なります。  一般に、オブジェクトの型と指定の型が同じ型である場合、オブジェクトの型が指定の型から派生した型である場合、またはオブジェクトの型が指定した型を実装した型である場合、オブジェクトの型と指定の型には互換性があります。  詳細については、「[TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md)」を参照してください。  
  
## コードのコンパイル  
 変数または式を型として指定することはできなません。  指定する型は、クラス、構造体、インターフェイスなど、定義済みの型の名前である必要があります。  これには、`Integer` および `String` などの組み込み型の型も含まれます。  
  
## 参照  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.GetTypeCode%2A>   
 <xref:System.TypeCode>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)