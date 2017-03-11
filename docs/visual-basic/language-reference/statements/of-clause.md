---
title: "Of Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Of"
  - "vb.Of"
  - "vb.of"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Of keyword"
  - "arguments [Visual Basic], data types"
  - "constraints, Visual Basic generic types"
  - "generic parameters"
  - "generics [Visual Basic], constraints"
  - "parameters, type"
  - "types [Visual Basic], generic"
  - "parameters, generic"
  - "type parameters"
  - "data type arguments"
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Of Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Of` 句を使用すると、*ジェネリック*であるクラス、構造体、インターフェイス、デリゲート、またはプロシージャに*型パラメーター*を定義できます。  ジェネリック型の詳細については、「[Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)」を参照してください。  
  
## Of キーワードの使用方法  
 次のコード例は、キーワード `Of` を使って、2 つの型パラメーターを受け取るクラスのアウトラインを定義します。  <xref:System.IComparable> インターフェイスによって、`keyType` パラメーターに *制約* が指定されています。そのため、このクラスを使用するコードは、<xref:System.IComparable> を実装する型引数を渡す必要があります。  これは、`add` プロシージャが <xref:System.IComparable.CompareTo%2A?displayProperty=fullName> メソッドを呼び出すために必要です。  制約の詳細については、「[Type List](../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 上記のクラス定義を作成すると、そこからさまざまな `dictionary` クラスが作成できます。  `entryType` と `keyType` に指定する型によって、クラスが保持するエントリの型と、クラスが各エントリに関連付けるキーの型が決まります。  制約が定義されているため、`keyType` には <xref:System.IComparable> を実装する型を指定する必要があります。  
  
 次のコード例は、文字列 \(`String`\) のエントリを保持するオブジェクトを作成し、各エントリに整数 \(`Integer`\) のキーを関連付けます。  `Integer` は <xref:System.IComparable> を実装しているため、`keyType` に対する制約を満たします。  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 キーワード `Of` は、次の構文で使用します。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 参照  
 <xref:System.IComparable>   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)