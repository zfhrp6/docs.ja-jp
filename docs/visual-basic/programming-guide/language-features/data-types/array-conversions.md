---
title: "Array Conversions (Visual Basic) | Microsoft Docs"
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
  - "arrays [Visual Basic], converting type"
  - "type conversion, arrays"
  - "conversions, type"
  - "arrays [Visual Basic], data types"
  - "conversions, data type"
  - "object arrays, converting type"
  - "data type conversion, array conversions"
  - "conversions, array types"
  - "object arrays"
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

以下の条件が満たされる場合は、配列型を異なる配列型に変換できます。  
  
-   **ランクが等しいこと。**2 つの配列のランクが同じである、つまり、次元数が同じである必要があります。  ただし、それぞれの次元の長さは同じでなくてもかまいません。  
  
-   **要素のデータ型。**両方の配列の要素のデータ型が、参照型である必要があります。  整数型 \(`Integer`\) の配列を長整数型 \(`Long`\) またはオブジェクト型 \(`Object`\) の配列には変換できません。これは、少なくとも 1 つの値型が関連するためです。  詳細については、「[Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
-   **変換性。**2 つの配列の要素型の間で、変換 \(拡張または縮小\) できる必要があります。  この要件を満たさない例としては、`String` 配列と、<xref:System.Attribute?displayProperty=fullName> から派生したクラスの配列との間での変換があります。  これらの 2 つの型には共通する点はありません。また、両者の間では変換は行われません。  
  
 ある配列型から別の配列型への変換は、それぞれの要素の変換が拡張か縮小かによって、拡大変換または縮小変換になります。  詳細については、「[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
## オブジェクト型 \(Object\) の配列への変換  
 オブジェクト型 \(`Object`\) の配列を初期化せずに宣言すると、初期化されない限り、要素型はオブジェクト型 \(`Object`\) のままです。  要素型を特定のクラスの配列に設定すると、そのクラスの型になります。  ただし、基になる型はオブジェクト型 \(`Object`\) のままで、その後要素型を関係のないクラスの別な配列に設定できます。  すべてのクラスがオブジェクト型 \(`Object`\) から派生するため、配列の要素型を任意のクラスから任意の他のクラスへ変更できます。  
  
 次の例では、`student` 型と `String` 型の間で変換は行われていませんが、共に `Object` から派生しているため、すべての代入が有効になります。  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### 基になる配列の型  
 最初に特定のクラスを使用して配列を宣言していた場合、配列の基となる要素型はそのクラスになります。  後で要素型を他のクラスの配列に設定する場合は、2 つのクラス間で変換が必要になります。  
  
 次の例では、`students` が `student` 配列になります。  `String` と `student` との変換はできないため、最後のステートメントはエラーになります。  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)